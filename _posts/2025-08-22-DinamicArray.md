---
layout: single
title: "Dynamic Array"
categories: [cpp]
tags: [cpp, array, pointer]
toc: true
classes: wide
---

# 동적 할당 배열 앙딱정

c에서는 정적 배열 할당 시 **const가 아닌 int로 크기를 지정할 수 없다.**

```c++ 
itn length = 10;
int array[length];
```

위와 같은 코드는 **컴파일 에러**가 난다.

➡️ 크기는 컴파일 타임에 고정되어야 하는데, 컴파일러가 `length` 를 알 수 없어서!

------

## 1. 런타임 크기와 동적 배열

**RunTime에 크기를 정하고 싶다면? → 동적 할당 배열을 사용하자**

```c++
int length;
cin >> length;
int* array = new int[length] {11,12,13,14,15};
```

- 초기화 방법은 정적 배열과 동일하다.
- **0으로 초기화 → () or {}**

------

### ⚠️ 주의할 점

위 코드와 같은 방법은 `[크기]` 보다 원소 개수가 작으면 **오류 발생**

```c++
int* array = new int[5] {11,12,13};	// NoNo
```

또한 크기 지정은 **필수**
 ❌ `int * array2 = new int[];` → 불가능

> 동적 배열은 크기가 런타임에 결정되는데 코드에서 미리 값을 변경하면 초록줄이 뜸
>
> 왜? 컴파일 타임엔 결정된 게 없으니까
>  {: .notice--primary}

------

### 메모리 해제

동적 할당 배열도 **반드시 delete []** 해야 한다.

```c++
delete []array;
```

👉 **포인터 + new = 동적 할당**

------

## 2. 이중 포인터와 동적 다차원 배열

**이중 포인터(double pointer, `\**`)** 는 **포인터를 가리키는 포인터**를 말한다.

------

### 1) 이차원 배열을 정적으로 구현

```c++
const int row = 3;
const int col = 5;

const int s2da[row][col] = {
    {1,2,3,4,5},
    {6,7,8,9,10},
    {11,12,13,14,15}
};
```

------

### 2) 이차원 배열을 노가다로 동적 할당

```c++
int* r1 = new int[col] {1, 2, 3, 4, 5};
int* r2 = new int[col] {6, 7, 8, 9, 10};
int* r3 = new int[col] {11, 12, 13, 14, 15};

int** rows = new int* [row] {
	r1, r2, r3
};
```

➡️ **delete 필수!**

------

### 3) for문으로 동적 이차원 배열 생성

```c++
int **matrix = new int* [row];

for (int r = 0; r < row; r++){
    matrix[r] = new int[col];
}

for (int r = 0; r < row; r++){
    for (int c = 0; c < col; c++){
        matrix[r][c] = s2da[r][c];
    }
}

for (int r = 0; r < row; r++)
    delete[] matrix[r];
delete [] matrix;
```

------

### 4) 더 쉬운 방법: 단일 포인터 활용

```c++
int* matrix = new int[row*col];

for (int r = 0; r < row; r++){
    for (int c = 0; c < col; c++){
        matrix[r*col + c] = s2da[r][c];
    }
}
```

➡️ 이 방법은 **1차원 배열처럼 관리**하면서 이차원처럼 접근 가능.



