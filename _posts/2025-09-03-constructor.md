---
layout: single
title: "생성자"
categories: [cpp, oop]
tags: [cpp, oop, encapsulation, access, getter, setter]
toc: true
classes: wide
---

# 💟생성자

## 1. 개념 한 줄 요약

`생성자`는 클래스의 객체가 만들어질 때 자동으로 호출되는 특별한 함수이다.  
즉, 호출하지 않아도 객체를 선언함과 동시에 실행되며, 초기화 작업을 한다.

- private로 생성자를 만들수도잇으나 특별한경우에만 쓰임
- 해결방법이 2가지가 잇은.

------

## 2. 기본 문법

```c++
class Dazzang2{
public:
    Dazzang2(){cout << "기본 생성자 문법입니다." << endl;}
};
```

* 클래스명과 동일한 이름을 가진다.
* 반환 타입이 없다. ( void조차도 쓰지 않음. )
* 객체가 생성될 때 자동으로 실행된다. ➡️ 호출이 필요 없음.
* 오버로딩 가능
* class 생성 시 사용자가 정의하지 않더라도 기본 생성자가 자동으로 생성된다.
  * 그러나 사용자 정의 생성자가 한개 이상인 경우, 기본생성자가 자동생성되지 않는다.

{: .notice--primary}

------

## 3. 맴버 객체의 생성 순서

```c++
class Second {
public:
    Second() {
        cout << "Second Constructor called!" << endl;
    }
};

class First {
    Second sec;
public:
    First() {
		cout << "First Constructor called!" << endl;
	}
};

int main() {
    First fir;
}
```

출력 결과
```C++
Second Constructor called!
First Constructor called!
```

위의 코드와 같이 class 안에 class 객체가 생성되는 경우, 가장 **안쪽의 객체 -> 바깥쪽 객체** 순으로 생성자가 호출됨을 알 수 있다.

------

## 4. 기본 생성자 (Default Constructor)

파라미터가 없는 생성자를 기본 생성자라고 한다.
```c++
class Fraction {
    int m_num;
    int m_den;
public:
    Fraction() {
        m_num = 0;
        m_den = 1;
        cout << "기본 생성자 호출됨" << endl;
    }
};
```

위와 같이 `기본 생성자`를 정의한 경우, 객체를 생성할 시 반드시 괄호를 **생략**해야 한다!  
이유 : **함수와 혼동**할 가능성이 크기 때문

```c++
int main() {
	// 1. 기본 생성자 호출
    Fraction f1;       // ⭕  (기본 생성자 호출)
    //Fraction f2();   // ❌ 함수 선언으로 인식됨 (most vexing parse 문제)
    Fraction f3{};     // ⭕ uniform init (C++11 이후)
    Fraction f4 = Fraction(); // ⭕ 명시적 기본 생성자 호출
}
```

`Fraction f1();` 는 틀린 표현임을 반드시 ~~~ 알아두기  


------

## 5. curly brace init 과 brace init 

| 초기화 방식                              | 문법                | 변환 규칙               | 특징                                 |
| ---------------------------------------- | ------------------- | ----------------------- | ------------------------------------ |
| 괄호 초기화 (Paren init)                 | `Fraction f(1, 3);` | 암시적 변환 허용        | 실수→정수 같은 narrowing 변환도 허용 |
| 중괄호 초기화 (Brace init, Uniform init) | `Fraction f{1, 3};` | narrowing 변환 **금지** | 안전한 초기화, C++11 이후 권장       |

```c++
// 이건 가능
Fraction(2.0, 1);
// 이건 불가능
Fraction{2.0, 1}
```

------

## 6. Default Parameter 와 생성자

```c++
// 가능
Fraction(const int& num_in, const int& den_in = 3);

// 불가능 (앞 파라미터에 기본값 X)
Fraction(const int& num_in = 4, const int& den_in);
```



## 📌 네비게이션

➡️ [다음 글: 캡슐화, 접근 지정자, 접근함수]({% post_url 2025-09-02-encapsulation-access %})