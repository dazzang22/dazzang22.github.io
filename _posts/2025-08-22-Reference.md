---
layout: single
title: "Reference"
categories: cpp
tag: [cpp]
---

#   reference (참조) 앙딱정

`&` 는 두 가지 의미를 가집니다. **변수 초기화 &**이 있고 **참조 &**이 있습니다.

참조는 alias다. 그래서 주소도 원래 변수랑 같다.

> 포인터와의 차이
>
> 포인터는 포인터 변수의 주소가 따로 있지만 참조는 alias 이기 때문에 주소도 같다.

```c++
int value = 5;
int& ref = value;

ref = 10;
```

참조는 반드시 초기화 필요하다.

* `int &ref;` 이런 건 불허
* `int& ref2 = 104;` 이런 식으로 literal로 초기화도 X  
* 오직 변수만 들어갈 수 있다.

```c++
```



참조는 별명이라는 것을 고려 했을 때, `const int` 와 같은 경우, 참조도 `const`로 선언해야 한다!

➡️ 참조 변수가 값을 변경할 수도 있으니까!

참조(alias) 는 원본 변수, 참조 둘 중 아무거나 재 할당하면 둘 다 반영이 된다. 

```c++
int value1 = 10;
int value2 = 20;

int &ref = value1;
ref = value2;
```

위의 코드에서 `ref`를 `value2`로 재할당 하는 것이 아니라, `value1`의 값을 `value2`로 재할당 하는 것이 된다.



##### 함수 파라미터로 전달되는 참조

- 함수 파라미터로 &를 넘길 수 있다. 세 가지 경우를 살펴보자.

##### Case 1 : 일반 파라미터 전달

```c++
void doSomething(const int n) {
    cout << "In doSomething" << n << endl;
    cout << &n << endl; // n의 주소값 출력
}

int main(){
    int n = 5;
    doSomething();
}
```

main 에서 함수 호출 시, 파라미터 `int n` 에 5가 복사가 된다. 

➡️ main 의 n 이 바뀌는게 아님!

##### Case 2 : 포인터로 파라미터 전달

```c++
void doSomething(const int *n) {
    cout << "In doSomething" << n << endl;
    cout << &n << endl; // n의 주소값 출력
}

int main(){
    int n = 5;
    int *ptr = n;
    doSomething(ptr);
}
```

main 에서 함수 호출 시 포인터로 넘기면 포인터 변수(`int *n`) 의 주소는 따로 정해진다.

➡️그러나 포인터를 통해서 main 의 n값에 접근은 할 수 있다.

##### Case 3 : 참조로 파라미터 전달

```c++
void doSomething(const int &n) {
    cout << "In doSomething" << n << endl;
    cout << &n << endl; // n의 주소값 출력
}

int main(){
    int n = 5;
    int &ref = n;
    doSomething(ref);
}
```

main 에서 함수 호출 시 참조로 넘기면 변수 자체가 넘어가는 것과 같다!

➡️당연히 함수 블록 내에서 값을 변경하면 원본 변수에도 영향이 간다.

포인터 변수로 주소를 한번 복사하는 방식과 다르게 이러한 과정이 아예 없다!

##### 배열과 참조

배열을 참조로 받을 수 있다. 

```c++
void printElements(const int (&arr)[5]) { 
    for (int i = 0; i < 5; ++i) {
		cout << arr[i] << " ";
	}
	cout << endl;
}
```

근데 이때 `const int (&arr)[5]` 와 같이 element 의 개수를 꼭 명시해야 한닷~! 



##### structure 와 참조

structrue 와 참조의 조합이 실무에서 굉장히 많이 쓰인다고 한다 . . .

구조체 내 변수에 접근 시, 경로가 긴 경우 참조 변수를 쓰면 깔끔하게 접근 가능

```c++
struct Something {
    int v1;
    float v2;
};

struct Something2 {
	Something s; // 구조체 안에 구조체를 넣을 수 있음
};

int main(){
    Something2 s2;
    int &v1 = s2.s.v1; // 구조체 안에 있는 int v1을 참조로 받음
    v1 = 20; 
}
```

위와 같이 긴 경로를 간단하게 표현할 수 있다.



#### 참조와 const
참조는 리터럴로 초기화가 안된다고 위에서 설명했다.

➡️그러나! 참조변수가 const면 리터럴로 초기화가 가능하다!

```c++
const int& ref_2 = 4+4;
```

 엥!!! 주소는 컴파일러가 알아서 관리해준다.

중요한 점은 `const`라서 `ref2`을 통해 값을 수정하려 하지 않는다는 것. 수정 불가능하니까 문제가 없닷 ㅡㅡ

#### 참조와 구조체 

```c++
struct Person {
	int age;
	double height;
};
```

위와 같은 구조체를 만든 후 접근하고 싶다. 

- 이때 구조체를 포인터로 받아올수도, 참조로 받아올수도 있다.

##### referencing

```c++
Person person;

Person &ref = person;
ref.age = 10;
```

##### pointer

```c++
Person *ptr = &person;
ptr->age = 32;
```

* 맴버 변수에 접근하고 싶으면 -> 를 쓰거나 ( * ptr). 이런식으로 디레퍼런싱 후 사용
