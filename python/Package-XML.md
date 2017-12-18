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

&nbsp;

## SAX

xml.sax

&nbsp;

## The ElementTree XML API

XML 문서의 엘리먼트들을 리스트와 dictionary로 다룰 수 있는 인터페이스를 제공하는 패키지이다. Namespace는 xml.etree.ElementTree이다.