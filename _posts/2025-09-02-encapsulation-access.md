---
layout: single
title: "캡슐화, 접근 지정자, 접근함수"
categories: [cpp, oop]
tags: [cpp, oop, encapsulation, access, getter, setter]
toc: true
classes: wide
---

# 💟캡슐화, 접근 지정자, 접근함수

## 1. 개념 한 줄 요약

**`접근 지정자 (access specifier)`** 란 클래스 맴버(변수 및 함수)의 가시성 및 **접근성**을 제어하는 OOP 의 **keyword**이다.

- access function 이라는 것이 잇은. 왜 필요할까?  
- 다른 instance 인데 도대체 우뜨쾌 접근하는거지?  

------

## 2. 종류

| 구분          | 접근 가능 범위                              | 설명                                                  |
| ------------- | ------------------------------------------- | ----------------------------------------------------- |
| **public**    | 어디서나 (외부 코드 포함)                   | 클래스 **외부에서도 접근 가능**. 외부 인터페이스 역할 |
| **protected** | 해당 클래스 + **상속받은** 파생 클래스 내부 | 외부에서는 접근 불가, **상속 계층 내부 공유용**       |
| **private**   | 해당 클래스 **내부**                        | **외부/상속 모두 불가**. 철저한 캡슐화 영역           |

Access Specifier 의 **default value** 는 `private`이다. 그렇기 때문에 아무런 keyword 를 쓰지 않고 코드를 짜게 되면 자동으로 `private` class member가 된닷!

{: .notice--primary}

------

## 3. Access Function ( 접근 함수 )

왜 필요한가?

변수가 `private`인 경우, 어떻게 변수에 접근하는

```c++
class Friend {
public:
    string m_name;
 	string m_address;
 	int m_age;
 	double m_height;
 	double m_weight;
   
    void print() {
        cout << m_name << " " << m_address << " " << m_age << " " << m_height << " " << m_weight << endl;
    }
};
```

------

## 4. 주의할 점

- 클래스 자체의 주소는 찍어볼 수 없고, instanciation 을 한 후 객체에 주소가 할당된다.
- 클래스 맴버의 명명규칙 ( 관용 )
  - `m_name` 과 같이  `m_` 을 붙여 class member 임을 강조 ➡️ 전통적인 방식
  - `_name` 이나 `name_` 과 같이 앞/뒤에 `_` 를 붙임 ➡️ 요즘 트랜드


------

## 5. 예제 with Vector

`Vector` 로 `class`를 다뤄보자>_<

```
// 깔끔한 코드 - 객체지향은 실수할 확률을 줄여줌
vector<Friend> my_friends;
my_friends.resize(2);

for(auto &ele : my_friends)
    ele.print();
```

출력:

```
  0 0 0
  0 0 0
```

class member 를 초기화하지 않으면 defalut value 는 `0` 임을 알 수 있다 ~

------

## 6. 요약



## 📌 네비게이션

➡️ [다음 글: 캡슐화, 접근 지정자, 접근함수]({% post_url 2025-09-02-encapsulation-access %})