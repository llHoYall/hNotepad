---
layout: post
title: Package - XML
category: python
tags: python
---

&nbsp;

# Package - XML

## Fast XML parsing usin Expat

빠르게 XML 문서 파싱을 할 수 있게 해주는 패키지이다. Namespace는 xml.parsers.expat이다. 빠른 파싱을 위해 문서의 유효성을 검사하지 않는다.

xmlparser 모듈을 제공하며 `xml.parsers.expat.ParserCreate([encoding[, namespace_delimeter]])`를 이용해 xmlparser 객체를 생성한다.

#### Methods

- **ErrorString(*errno*)** : errno에 해당하는 에러를 반환한다.

### xmlparser Module

#### Attributes

- **buffer_text** : True로 설정하면 문자 엘리먼트를 처리할 때 버퍼를 사용한다.
- **buffer_size** : buffer_text의 속성이 True일 때 버퍼의 크기를 설정할 수 있다.
- **CurrentLineNumber** : 현재 파싱하고 있는 line number이다.
- **ErrorLineNumber** : XML 문서 파싱 중 에러가 발생했을 때 문서의 line number가 기록된다.
- **ordered_attributes** : 0이 아니면 XML이 파싱될 때 속성이 발견되는 순서대로 리스트 형식의 속성 이름과 속성 값을 저장한다. 기본 값은 False이다.
- **specified_attributes** : 0이 아니면 명시된 속성일 때만 처리한다. 기본값은 False이다.
- **ErrorCode** : 에러가 발생했을 때 에러 번호가 저장된다.

#### Methods

- **Parse(*data*[, *isfinal*])** : data를 파싱한다. 더이상 파싱을 하지 않을 것이면 isfinal을 True로 입력한다.
- **ParseFile(*file*)** : 파일의 데이터를 파싱한다.

#### Handler

- **XmlDeclHandler(*version*, *encoding*, *standalone*)** : <?xml version="1.0"?>와 같은 XML 선언문이 파싱될 때 호출된다.
- **ElementDeclHandler(*name*, *model*)** : 파싱 도중 처음 사용되는 엘리먼트를 발견하면 호출된다. name은 엘리먼트의 이름이다.
- **StartElementHandler(*name*, *attributes*)** : 모든 엘리먼트의 시작 부분에서 호출된다. name은 엘리먼트의 이름이고, attributes에는 엘리먼트의 속성 값이 dictionary 형식으로 전달된다.
- **EndElementHandler(*name*)** : 모든 엘리먼트의 끝 부분에서 호출된다.
- **CharacterDataHandler(*data*)** : 문자 데이터를 발견하면 호출된다. data에 문자 정보가 전달된다.
- **CommentHandler(*data*)** : 주석 부분에서 호출된다. data에 주석 내용이 전달된다.

&nbsp;

## DOM (Document Object Model) API

XML 문서의 각 성분을 객체로 표현하고 모든 객체를 메모리에 저장하고 처리하는 패키지이다. Namespace는 xml.dom이다.

파이썬3에서 DOM은 W3C에서 표준으로 정의한 DOM Level2 권고안을 기반으로 만들어졌다.

파이썬3에서는 minidom과 pulldom 모듈을 제공한다. 대부분의 경우 minidom을 사용하고, 메모리가 부족하거나 XML 문서가 아주 클 경우 pulldom을 사용한다.

DOM 안에는 다음과 같은 객체가 들어 있다.

- **DOMImplementation** : DOM을 만드는 기본적인 인터페이스가 들어있는 객체.
- **Node** : 도큐먼트 상에 존재하는 대부분 객체의 부모 객체.
- **NodeList** : 노드 리스트 객체.
- **DocumentType** : 도큐먼트를 처리하는 데 필요한 선언(시스템 ID, entities, notation)을 위한 객체.
- **Document** : 도큐먼트 전체를 나타내는 객체.
- **Element** : 노드 엘리먼트 인터페이스 객체.
- **Attr** : 엘리먼트 안의 속성 값 노드 객체.
- **Comment** : 소스 XML 문서에서 주석 부분을 처리하기 위한 객체.
- **Text** : 도큐먼트에서 문자 정보를 포함하고 있는 노드 객체.
- **ProcessingInstruction** : 도큐먼트 처리를 위한 도구를 나타내는 객체.

### minidom

#### Methods

- **parse(*file*[, *parser*])** : file로부터 XML 문서를 읽어서 document 객체를 반환한다. parser 인자가 입력되면 minidom의 기본 파서가 아닌 사용자가 원하는 파서를 사용할 수 있다. 파서는 SAX2 parser 객체만 사용가능하다.
- **parseString(*data*, *parser*)** : parse9)와 비슷하지만 입력으로 파일대신 문자열을 받는다.

### Document 객체

#### Methods

- **createElement(*tagName*)** : 새로운 엘리먼트 객체를 생성한다. tagName은 생성할 엘리먼트의 이름이된다.
- **createTextNode(*data*)** : 인자 data로부터 문자 노드를 생성하고 반환한다.
- **createAttribute(*name*)** : 속성 노드를 생성하고 생성된 객체를 반환한다. 이 메서드는 단지 속성 개체를 만들 뿐 원하는 엘리먼트와 연결시킬 수 없다. 엘리먼트와 연결하려면 setAttributeNode() 메서드를 사용해야 한다.
- **getElementsByTagName(*tagName*)** : 인자 tagName과 이름이 같은 모든 엘리먼트를 가져온다. 결과값으로 nodeList가 반환된다.

&nbsp;

## SAX (Simple API for XML)

XML 문서를 파싱할 때 구성요소를 발견할 때마다 이벤트를 발생시켜 XML 문서를 처리하는 모듈이다. Namespace는 xml.sax이다.

SAX는 DOM과 달리 XML 문서의 내용을 변경할 수 없고 (Read Only), 파싱은 문서의 처음부터 아래 부분으로만 진행된다 (Forward). 사용자는 원하는 요소를 처리하기 위한 함수를 생성하고 이벤트 핸들러에 함수를 등록한다. 객체 기반 방식보다는 빠르지만 한 번 처리한 문서는 다시 사용할 수 없다.

#### Methods

- **make_parser([*parser_list*])** : SAX XMLReader를 생성하고 반환한다. parser_list가 선언되어 있으면 parser_list의 파서를 먼저 생성한다. parser_list는 create_parser() 메서드가 포함된 모듈들의 리스트이다.
- **parse(*filename_or_stream*, *handler*[, *error_handler*])** : 파일이나 스트림으로부터 입력받은 XML 문서를 파싱한다. 핸들러는 SAXContentHandler 인스턴스여야 한다. Error_handler는 SAX ErrorHandler 인스턴스와 연결해야 하고 만약 생략하면 에러가 발생할 때 SAXParseException 예외가 발생한다.
- **parseString(*string*, *handler*[, *error_handler*])** : parse() 메서드와 비슷하지만, XML 문서 입력을 문자열로 받는 점이 다르다.

### xml.sax.handler

- **ContentHandler** : SAX 중에서 가장 많이 사용되는 핸들러이다. 문서 안의 정보들이 파싱되면서 순서대로 이벤트가 ContentHandler를 통해 호출된다.
- **DTDHandler** : DTD 이벤트를 위한 핸들러이다.
- **ErrorHandler** : 에러 혹은 경고가 발생했을 때 호출된다.

### xml.sax.xmlreader

- **XMLReader** Class : SAX 파서의 기본 클래스이다.
- **Locator** Class : 문서 내부의 locator와 SAX 이벤트와의 연결을 위한 클래스이다.
- **InputSource([*systemId*])** Class : XML 문서의 인코딩을 파서에 알려주거나 바이트 스트림 혹은 캐릭터 스트림을 가져오거나 설정할 수 있다.

### XMLReader Class

#### Methods

- **parse(*source*)** : source로 입력된 XML 문서를 파싱하면서 SAX 이벤트를 발생시킨다.
- **getContentHandler()** : 현재 ContentHandler 객체를 가져온다.
- **setContentHandler(*handler*)** : 인자로 전달된 ContentHandler 인스턴스를 현재 ContentHandler로 설정한다.
- **setLocale(*locale*)** : 경고나 에러 출력을 위한 로케일 정보를 설정한다.

&nbsp;

## The ElementTree XML API

XML 문서의 엘리먼트들을 리스트와 dictionary로 다룰 수 있는 인터페이스를 제공하는 패키지이다. Namespace는 xml.etree.ElementTree이다.