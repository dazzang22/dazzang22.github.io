---
layout: single
title: "전역변수"
categories: cpp
tag: [cpp]
---

## 전역 변수

- internal linkage란
- 전역변수와 지역변수에 관한 name hiding 및 초기화 관점 
- 전역변수를 사용하기 위한 방법 -> :: 사용하기
- 전역변수의 단점 및 명명 추천방법
- static 의 초기화관점에서의 정의 
- static 전역변수 : internal linkag, 다른 cpp에서 접근 x
- static 은 언제 쓰이나?
- 애초에 지역변수는 외부 link 가 안됨을 기억하라. 
- 전역 static을 쓰면 internal linkage가 적용되어 외부 접근 안되노요
- 그럼 external linkage 를 하는 방법은? 다른 cpp 파일에 있는 함수, 변수 forward declaration
- extern 으로 선언
- 헤더파일에서 초기화된 변수를 다른 파일들에서 사용한 함수를 사용할때 같은 변수인데도 메모리 할당이 왜 다르게 되는거지?
- 이거의 문제점과 해결방법이 있엇은
