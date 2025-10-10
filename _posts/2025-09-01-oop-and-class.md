---
layout: single
title: "객체지향 프로그래밍과 클래스"
categories: [cpp, oop]
tags: [cpp, oop, class, struct, encapsulation]
toc: true
classes: wide
---

# 💟객체지향 프로그래밍과 클래스

## 1. 개념 한 줄 요약

**`객체지향 프로그래밍 (OOP)`** 란 데이터와 함수를 **캡슐화**하는 Software entity 인 **객체 (Object)**를 기반으로 하는 프로그래밍 기법이다. OOP 프로그램은 서로 **상호작용**하는 객체들을 기반으로 구성된다.

------

## 2. 왜 객체지향을 써?

객체지향 프로그래밍(OOP) 사용 시, 재사용 가능한 객체인 `class` 를 만들 수 있으며, 이를 통해 해당 객체의 여러 instance를 생성할 수 있다!
➡️ 코드를 한 번만 작성해도 프로그램의 여러 부분에서 반복적으로 사용이 가능하여 코드의 재사용성 및 프로그램의 효율을 높임~

{: .notice--primary}

##### Struct 대신 Class 를 쓰는 이유는?

간단한 기능을 수행하는 경우 ( data 만 관리한다거나... ) struct 가 효과적이지만, `function`까지 포함시켜야 하는 경우, class 로  관리하는 것이 더 낫다!

여담으로, C 에서는 Struct 안에 `function` 삽입이 안된다고 . . .

------

## 3. 기초 문법

문법을 알아보기 전에 **접근 지정자**라는 것을 먼저 알아보자~

#### Access Specifier ( 접근 지정자 )

class member 에 대한 접근 범위를 설정하는 키워드이다.

➡️ [더 자세히 보기☠️]({% post_url 2025-09-02-encapsulation-access %})

#### 코드 

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