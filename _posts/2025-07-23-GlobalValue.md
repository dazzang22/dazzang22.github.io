---
layout: single
title: "[C++] 전역변수 (Global Variable)"
date: 2025-07-23
categories: [tech, cpp]
tags: [cpp, variable, global, scope, memory]
permalink: /tech/cpp/global-variable/
author_profile: false
---

# C++ 전역 변수, 앙딱정

## 1. 전역 변수란?

* 전역 변수(Global Variable) : 함수 밖에서 선언된 변수 
* ↔️지역 변수(Local Variable) : 함수 내부에서 선언된 변수

## 2. Linkage란?

> Linkage determines how names refer to the same entity across different parts of a program.
>
> Linkage는 한 프로그램 상 **다른 부분의 식별자들**이 **같은 entity를 참조**하는 방식을 결정한다.

C++ 에서 개별 소스 파일이 컴파일러에 의해 **컴파일 완료된 후** 소스 파일들을 **Combine** 하는 것이 **'Linking'** 이다. ➡️ Linking  을 해주는 프로그램을 **'Linker'** 라고 한다.

* **External** Linkage : **다른 파일**에서도 사용 가능
  * ex ) `extern int g_a` , `extern void doSomething()` 등과 같이 참조
* **Internal** Linkage : 이 파일 **內**에서만 사용 가능
  * **static, const** 로 선언된 전역변수, etc.
* No linkage : 컴파일러만 알음, Linker는 이 변수들에 대해 모름 ➡️ Linking 시 불필요
  * **지역변수** 

## 3. 지역 변수와 Name Hiding

```c++
int value = 5;

void doSmth(){
    int value = 6;
}
```

위와 같이 기존에 존재하던 전역변수와 이름이 동일한 지역변수가 선언되면, **지역변수**가 더 **우선시** 되는 **'name hiding'** 이 발생한다.

지역변수는 scope 가 끝날 때 까지 존재 ~ !

* 전역 변수를 명시적으로 사용하는 법 : **`::value`** 와 같이 `::` 를 사용하기

## 4. Static 전역 변수

* `static int g_a` 와 같은 static 전역변수는 **internal linkage** 이다. 
* 즉, 다른 cpp 파일(**외부**)에서 **접근이 불가**하다.

```c++
void doSomething() {
    static int a = 1;	// int 로 선언 시 함수 호출 시 마다 1로 초기화됨;
    ++a;
    cout << a << endl;
}
```

* 함수 내에 선언하면 함수 호출이 간 값이 **유지**된다. ➡️ 호출 시 마다 값이 **초기화되지 않음**
* **디버깅** 시 유용

## 5. Const 전역 변수

```c++
const int g_x; 	// 잘못된 코드! 초기화 필수
```

* 기본적으로 const 는 internal linking이다
* 다른 파일에도 쓰고 싶다면 `external const int g_x` 이런 식으로 extern 키워드 필수!
* 단! 위와 같이 쓰는 경우, 한군데에서만 초기화가 필요함

## 6. `extern` 키워드는 언제 사용하는가?

#### 1. 전역 변수 또는 함수의 선언만 하고, 정의는 다른 파일에서 하는 경우

```c++
// --- file1.cpp ---
int g_value = 10;  // 전역 변수 정의 (실제 메모리 공간 할당)

// --- file2.cpp ---
extern int g_value;  // 전역 변수 선언 (정의 아님)

```

#### 2. 다른 파일에 있는 함수 호출

```c++
// --- test.cpp ---
void printHello() {
    std::cout << "Hello!\n";
}

// --- main.cpp ---
extern void printHello();  // forward declaration
int main() {
    printHello();  // test.cpp에 정의된 함수 사용
}
```

#### 3. const 외부 사용 시 

```c++
// --- MyConstants.cpp ---
const int kBufferSize = 512;  // const는 기본적으로 internal linkage

// --- MyConstants.h ---
extern const int kBufferSize;  // 다른 파일에서도 접근 가능하게 만듦

```

#### 주의할 점☠️

헤더 파일에 extern 전역 변수 선언 시 초기화를 절대로 하면 안됨!

WHy ? 여러 cpp에서 include 되면 중복 정의 오류가 발생. ➡️ 선언만 하자

- 
- 
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
