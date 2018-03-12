---
layout: post
title: bluetooth
category: swift
tags: [swift, bluetooth, ble, iOS]
---



# Bluetooth

Xcode와 Swift를 이용한 블루투스 개발 방법이다. 블루투스는 시뮬레이터 상에서 동작하지 않으니 반드시 실제 폰을 연결해야 한다.

### Dependency

```swift
// viewcontroller.swift
import CoreBluetooth
```

### Add Central Manager Delegate

```swift
// viewcontroller.swift
...
class ViewController: UIViewController {
    ...
    var centralManager: CBCentralManager!
    ...
    override func viewDidLoad() {
        ...
        centralManager = CBCentralManager(delegate: self, queue: nil)
    }
}
...
extension ViewController: CBCentralManagerDelegate {
    func centralManagerDidUpdateState(_ central: CBCentralManager) {
        switch central.state {
            case .unknown:
            	print("central.state is .unknown")
            case .resetting:
            	print("central.state is .resetting")
            case .unsupported:
            	print("central.state is .unsupported")
            case .unauthorized:
            	print("central.state is .unauthorized")
            case .poweredOff:
            	print("central.state is .poweredOff")
            case .poweredOn:
            	print("central.state is .poweredOn")
        }
    }
}
```

정상적으로 세팅이 되었다면 output window에 `central.state is .poweredOn`이 출력된다.

### Scan Peripheral

`.poweredOn` 상태가 되면 바로 peripheral을 scan하도록 한다.

```swift
// viewcontroller.swift
...
extension ViewController: CBCentralManagerDelegate {
    func centralManagerDidUpdateState(_ central: CBCentralManager) {
        switch central.state {
            ...
			case .poweredOn:
				print("central.state is .poweredOn")
            	centralManager.scanForPeripherals(withServices: nil)
		}
	}
    func centralManager(_ central: CBCentralManager, didDiscover peripheral: CBPeripheral, advertisementData: [String: Any], rssi RSSI: NSNumber) {
        print(peripheral)
    }
}
```

특정한 서비스만을 검색하도록 하는 방법은 다음과 같다. 예를 들어 HeartRate Service (0x180D) 만을 검색하도록 한다.

```swift
// viewcontroller.swift
...
import CoreBluetooth
...
let hr_serviceUUID = CBUUID(string: "0x180D")
...
extension ViewController: CBCentralManagerDelegate {
    func centralManagerDidUpdateState(_ central: CBCentralManager) {
        switch central.state {
            ...
			case .poweredOn:
				print("central.state is .poweredOn")
            	centralManager.scanForPeripherals(withServices: [hr_serviceUUID])
		}
	}
    ...
}
```

검색된 peripheral을 저장하고 scan을 종료한다.

```swift
// viewcontroller.swift
...
class ViewController: UIViewController {
    ...
    var centralManager: CBCentralManager!
    var hr_peripheral: CBPeripheral!
    ...
}
extension ViewController: CBCentralManagerDelegate {
    ...
    func centralManager(_ central: CBCentralManager, didDiscover peripheral: CBPeripheral, advertisementData: [String: Any], rssi RSSI: NSNumber) {
        print(peripheral)
        hr_peripheral = peripheral
        centralManager.stopScan()
    }
}
```

### Connecting to a Peripheral

```swift
// viewcontroller.swift
...
extension ViewController: CBCentralManagerDelegate {
    ...
    func centralManager(_ central: CBCentralManager, didDiscover peripheral: CBPeripheral, advertisementData: [String: Any], rssi RSSI: NSNumber) {
        print("discovered peripheral")
        print(peripheral)
        hr_peripheral = peripheral
        centralManager.stopScan()
        centralManager.connect(hr_peripheral)
    }
    func centralManager(_ central: CBCentralManager, didConnect peripheral: CBPeripheral) {
        print("connected")
    }
}
```

### Discovering a Peripheral's Services

```swift
// viewcontroller.swift
...
extension ViewController: CBCentralManagerDelegate {
    ...
    func centralManager(_ central: CBCentralManager, didDiscover peripheral: CBPeripheral, advertisementData: [String: Any], rssi RSSI: NSNumber) {
        ...
        hr_peripheral = peripheral
        hr_peripheral.delegate = self
        ...
    }
    func centralManager(_ central: CBCentralManager, didConnect peripheral: CBPeripheral) {
        print("connected")
        hr_peripheral.discoverServices(nil)
    }
}
extention ViewController: CBPeripheralDelegates {
    func peripheral(_ peripheral: CBPeripheral, didDiscoverServices error: Error?) {}
    	guard let services = peripheral.services else { return }
    	print("discovered service")
    	for service in services {
	        print(service)
	    }
	}
}
```

특정 서비스만 discover 하려면, `hr_peripheral.discoverServices([hr_serviceUUID])`와 같이 한다.

### Discovering a Service's Characteristics

```swift
// viewcontroller.swift
...
extention ViewController: CBPeripheralDelegates {
    func peripheral(_ peripheral: CBPeripheral, didDiscoverServices error: Error?) {}
    	guard let services = peripheral.services else { return }
    	print("discovered service")
    	for service in services {
	        print(service)
        	peripheral.discoverCharacteristics(nil, for: service)
        }
    }
	func peripheral(_ peripheral: CBPeripheral, didDiscoverCharacteristicsFor service: CBService, error: Error?) {
    	guard let characteristics = service.characteristics else { return }
        for characteristic in characteristics {
            print(characteristic)
        }
	}
}
```

검색된 characteristic의 property를 확인하고, 값을 읽어온다.

```swift
// viewcontroller.swift
...
let hr_serviceUUID = CBUUID(string: "0x180D")
let hrm_charUUID = CBUUID(string: "2A37")	// heart rate measurement
let bsl_charUUID = CBUUID(string: "2A38")	// body sensor location
...
extention ViewController: CBPeripheralDelegates {
    func peripheral(_ peripheral: CBPeripheral, didDiscoverCharacteristicsFor service: CBService, error: Error?) {
        ...
        for characteristic in characteristics {
            print(characteristic)
            if characteristic.properties.contains(.read) {
                print("\(characteristic.uuid): properties contains .read")
                // BSL
                peripheral.readValue(for: characteristic)
            }
            if characteristic.properties.contains(.notify) {
                print("\(characteristic.uuid): properties contains .notify")
                // HRM
                peripheral.setNotifyValue(true, for: characteristic)
            }
        }
    }
    func peripheral(_ peripheral: CBPeripheral, didUpdateValueFor characteristic: CBCharacteristic, error: Error?) {
        switch characteristic.uuid {
            case bsl_charUUID:
            	guard let data = characteristic.value,
            		  let loc = data.first else { return }
            	print("Location: \(loc)")
            case bpm_charUUID:
            	guard let data = characteristic.value else { return }
            	let byteArray = [UInt8](data)
            	let flag = byteArray[0] & 0x01
            	if flag == 0 {
                    print("BPM: \(byteArray[1])")                
                }
            default:
            	print("Unhandled Characteristic UUID: \(characteristic.uuid)")
        }
    }
}
```

