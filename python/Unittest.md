---
layout: post
title: Unit Test
category: python
tags: python
---

&nbsp;

# Unit Test

파이썬으로 단위 테스트 개발을 하자.

#### unittest Module

```python
# unittest 모듈을 사용한다.
import unittest

# Test 대상이 될 함수를 정의한다.
def sum(a, b):
    return a + b

# Test case들을 만든다. 반드시 unittest.TestCase를 상속받아야 한다.
class TestCase1(unittest.TestCase):
    def setUp(self):
        # 테스트 수행 전, 테스트 환경을 설정한다.
        pass
    def testSum1(self):
        self.assertEqual(sum(1, 2), 3)
    def testSum2(self):
    	self.assertEqual(sum(1, -1), 0)
    def tearDown(self):
        # 테스트 수행 후, 테스트 환경을 정리한다.
        pass
        
# Test를 시작한다.
if __name__ == "__main__":
    unittest.main()
    
# 실행 순서는 다음과 같다.    
# setUp -> testSum1 -> tearDown -> setUp -> testSum2 -> tearDown
```

```python
import unittest

def sum(a, b):
    return a + b

class TestCase1(unittest.TestCase):
    def setUp(self):
        pass
    def testSum1(self):
        self.assertEqual(sum(1, 2), 3)
    def testSum2(self):
    	self.assertEqual(sum(1, -1), 0)
    def tearDown(self):
        pass
    
class TestCase2(unittest.TestCase)   :
    def setUp(self):
        self.test = [True, True]
    def testList(self):
        for item in self.test:
            self.assertTrue(item)
    def tearDown(self):
        del self.test
        
# Test suite를 만든다.
def makeTS(testcase, tests):
    return unittest.TestSuite(map(testcase, tests))
        
if __name__ == "__main__":
    suite1 = makeTS(TestCase1, ['testSum1', 'testSum2'])
    suite2 = makeTS(TestCase2, ['testList'])
    allSuites = unittest.TestSuite([suite1, suite2])
    unittest.TextTestRunner(verbosity=2).run(allSuites)
```

```python
import unittest

# Test할 함수를 만든다.
def test():
    assert 1 is not None

# setUp() 함수를 만든다.
def init():
    pass

# tearDOwn() 함수를 만든다.
def fin():
    pass

# Test를 시작한다.
if __name__ == "__main__":
    testcase = unittest.FunctionTestCase(test, setUp=init, tearDown=fin)
    suite = unittest.TestSuite([testcase])
    unittest.TextTestEunner(verbosity=2).run(suite)
```

- `assertEqual(first, second, [msg])` : first와 second가 다르면 msg를 출력하고 테스트 실패.
- `assertNotEqual(first, second, [msg])` : first와 second가 같으면 msg를 출력하고 테스트 실패.
- `assertTrue(expr, [msg])` : expr이 False이면 msg를 출력하고 테스트 실패.
- `assertFalse(expr, [msg])` : expr이 True이면 msg를 출력하고 테스트 실패.

