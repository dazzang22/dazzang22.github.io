---
layout: single
title: "Part1-Setion3-언리얼 엔진의 자료구조"
categories: unreal
tag: [unreal]
---

#### 문자열 표기법

----

TCHAR : 문자

FString : TCHAR의 동적배열이라고 생각하면 편하다. -> TCHAR* 와 같은 역할

##### FString 출력

```c++
FString LogCharString = LogCharArray;
UE_LOG(LogTemp, Log, TEXT("%s"), *LogCharString);
```

FString 타입의 변수는 앞에 포인터를 붙여야지만 FString 이 감싸고 있는 문자열을 반환할 수 있다.



##### FString 포인터 참조

보통 포인터는 const형으로 참조하게 되어있다.

```c++
const TCHAR* LongCharPtr = *LogCharString;
```

위와 같이 TCHAR의 포인터형(TCHAR*) 변수 LogCharPtr 는 



