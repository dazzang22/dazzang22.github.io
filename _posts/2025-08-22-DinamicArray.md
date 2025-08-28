---
layout: single
title: "Dynamic Array"
categories: cpp
tag: [cpp]
---

#   동적 할당 배열 앙딱정

c에서는 정적 배열 할당 시 const가 아닌 int로 크기를 지정할 수 없다.

```c++ 
itn length = 10;
int array[length];
```

위와 같은 코드는 컴파일 에러가 난다 

➡️ 크기는 컴파일 타임에 고정되어야 하는데 컴파일러가 length 를 알 수 없어서!

RUn TiMe에 크기를 정하고 싶다면? 동적 할당 배열을 사용하자

```c++
int length;
cin >> length;
int* array = new int[length] {11,12,13,14,15};
```

초기화 방법은 정적 배열과 동일하다. **0으로 초기화->()or {}**

위 코드와 같은 방법은 [크기] 보다 원소개수가 작으면 오류소리가 난다.

```c++
int* array = new int[5] {11,12,13};	// NoNo
```

또한 크기 지정은 ㅈㄴ 필수닷ㅋ.int * array2 = new int[]; 이런 거 안됨 ;;

- > 동적 배열은 크기가 런타임에 결정되는데 코드에서 미리 값을 변경하면 초록줄이 뜸 
  >
  > 왜? 컴파일타임엔 결정된게 없으니깐

- 동적 할당 배열도 당여니 delete [] 해야 한다.

```c++ 
delete []array;
```

포인터 + new = 동적 할당이다

## 2. 이중 포인터와 동적 다차원 배열

이중포인터란? 

이중 포인터(double pointer, `**`)는 **포인터를 가리키는 포인터**를 말하는 것.

1. ##### 이차원배열을 정적으로 구현할 수 있다.

```c++
const int row = 3;
const int col = 5;

const int s2da[row][col] = {
    {1,2,3,4,5},
    {6,7,8,9,10},
    {11,12,13,14,15}

};
```

##### 2. 이차원 배열을 노가다로 동적 할당 할 수 있다.

```c++
int* r1 = new int[col] {1, 2, 3, 4, 5};
int* r2 = new int[col] {6, 7, 8, 9, 10};
int* r3 = new int[col] {11, 12, 13, 14, 15};

int** rows = new int* [row] {
	r1, r2, r3
};
```

delete 필수 !

근데 for문으로 좀 빨리 만들고싶다? 그럼 이중 포인터를 더 잘 쓸 수 있다.

```c++
int **matrix = new int* [row];

for (int r = 0; r <row; r++){
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

- 더쉬운방법이 잇은. 그건 단일포인터를 쓰는것인.

```c++
int* matrix = new int[row*col];

for (int r = 0; r < row; r++){
    for (int c = 0; c < col; c++){
        matrix[r*col +c] = s2da[r][c];
    }
}
```