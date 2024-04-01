---
layout: single
title: "Part1-언리얼 코딩표준"
categories: unreal
tag: [unreal]
---

## Unreal C++ 코딩 표준

#### 구조 

* public class - interface 에서 먼저 선언한 후, 클래스의 private 구현을 한다

#### 명명 규칙 

* Pascal Casing 을 사용 ▶ 합성어의 시작을 모두 대문자로 
* 타입 이름 앞에 **접두사**를 붙임
  * UObject 상속클래스 -> U를 붙임
  * AActor 상속 클래스 -> A를 붙임 ( UObject 하위이지만 A를 씀 )
  * SWidger 상솓 클래스 -> S를 붙임 
  * 추상 인터페이스 -> I를 붙임
  * 부울변수 -> **b**를 붙임 ( 소문자 / 예외 케이스)
  * 그외의 클래스 -> 대부분 F를 붙임

#### 포터블 C++ 코드

| 부울 | 문자  | 정수                         |         부호없는 바이트          | 단정밀도 부동소수점 | 배정밀도 부동소수점 |
| ---- | ----- | ---------------------------- | :------------------------------: | ------------------- | ------------------- |
| bool | TCHAR | int8 / int16 / int32 / int64 | uint8 / uint16 / uint32 / uint64 | float               | double              |

💛 int  타입의 최소크기는 32bit로 보장



#### 세부사항

* c++ 의 표준라이브러리는 이용하지 않음. 
* const 명명 가급적이면 해주는 것 필요 ( EX . 루프를 돌 때에 횟수같은 것은 const로 지정하여 깨지지않게 관리 )
* 주석 - 문서화 프로그램이 있음 ~
* include 최소한 적게 해라

#### 포안터 포맷

```c++
FShaderType* Ptr
```

위와 같이 포인터 기호 후 한칸을 띄고 변수명 적기 

```c++
FShaderType *Ptr
FShaderType * Ptr
```

위와 같은 형식은 x
