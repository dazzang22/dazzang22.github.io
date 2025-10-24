---
layout: single
title: "[CS] Design Pattern"
date: 2025-10-23
categories: [cs]
tags: [design-pattern]
permalink: /cs/design-pattern
author_profile: false
toc: true
---

## 디자인 패턴	

디자인 패턴에 대해 알아보자.



디자인 패턴은 크게 생성, 구조, 행위 3가지 종류로 나뉜다.  
생성 패턴 : 객체 인스턴스 생성에 관여하며, 클래스의 정의와 객체 생성 방식을 수행하는 방식에 관함  
구조 패턴 : 객체 간 구조, 즉 더 큰 구조 (확장) 형성에 관함  
행위 패턴 : 클래스, 객체들이 상호 작용하는 방법과 역할 분담에 관함

### 생성 패턴의 종류

* Abstract Factory 
  * 구체적인 class에 의존하지 않고 서로 연관된 객체들의 조합을 만드는 인터페이스 제공
* Bulider
  * 복합 개체 생성을 단계적으로 조립하여 구성
* Factory Method
  * 상위 클래스에서는 인터페이스를 정의하고, 하위 클래스에서는 인스턴스를 생성
* Prototype 
  * 기존 객체를 복제(clone)하여 새 객체를 생성
* Singleton
  * 전역변수를 사용하지 않고 객체를 하나만 생성하고, 어디서든 접근 가능하게 함

### 구조 패턴의 종류

* Adapter
  * 인터페이스가 호환되지 않는 클래스를 연결
* Bridge
  * 추상화 계층과 구현부를 분리하여 독립적으로 확장 가능
* Composite
  * 객체들의 관계를 트리 구조로 구성하여 복합/단일 객체를 동일하게 취급
* Decorator
  * 객체 간 결합을 통해 객체에 기능을 동적으로 추가
* Facade
  * 통합된 단순한 인터페이스 제공
* Flyweight
  * 클래스 공유를 통해 메모리를 절약
* Proxy 
  * 실제 객체의 접근을 제어하는 대리 객체 

> Review
>
> 구조 패턴은 모두 확장 또는 객체에 대한 접근에 관한 패턴이다.

### 행위 패턴의 종류

* Chain of Responsibility 
  * 두 개 이상의 객체가 하나의 요청을 순차처리
* Command
  * 빈번한 요청을 객체로 캡슐화하여 재사용성을 높임
* Interpreter
  * 언어의 문법 해석을 캡슐화하여 사용하는 디자인 패턴
* Iterator
  * 컬랙션의 내부구조를 노출하지 않고 Iterator 를 사용하여 순회
* Mediator
  * 객체 간 통신 시 중재자를 두어 통제 및 지시
* Observer
  * 한 객체의 상태 변화 시, 관련 객체들에 자동 통보 및 갱신
* State
  * 객체의 상태를 캡슐화하여 참조 - 상태에 따른 유연한 동작
* Strategy
  * 알고리즘을 캡슐화하고, 