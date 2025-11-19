---
layout: single
title: "Array"
categories: cpp
tags: [cpp]
---

### 빠른 입출력 세팅

```c++
ios::sync_with_stdio(false);
cin.tie(nullptr);
```

### string 입력 패턴

##### 공백 없는 토큰

```c++
string s;
cin >> s;
```

##### 한 줄 전체 입력

```c++
string line;
getline(cin, line);
```

##### 출력

```c++
cout << s << '\n';
```

##### 인덱스 접근

```c++
for (int i=0; i < s.size(); i++){
    cout << s[i] << ' ';
}

for (char c : s){
    cout << c << ' ';
}
```

### char[] 입출력 패턴

##### 입력

```c++
char s[100];

// 공백 전까지 읽음
cin >> s;

// 한 줄 전체 입력(공백 포함)
cin.getline(s, 101);
```

##### 출력

```c++
cout << s << '\n';
```

##### 인덱스 접근

```c++
for (int i=0; s[i] != '\0'; i++){
    cout << s[i] << ' ';
}
```

### 알파벳 세기 전략

```c++
cnt[i - 'A']++;
```



# 입력과 출력

c++ 에서 흔히 사용하는 입출력 방식에 대해 간단히 소개하려고 한다.  
입력에는 `cin`, `scanf`가 있고, 출력에는 `cout`, `printf` 가 있다.

---

## 입력

`cin`은 공백 전까지 입력을 받는다.

```c++
#include <bits/stdc++.h>
using namespace std;

// 이름을 입력받는 코드
string name;
int main(){
    cin >> name;
    cout << name << '\n';
    return 0;
}
```

만약 입력이 `Lee Dazzang`과 같이 공백이 포함된 경우

**[출력]**
Lee  
{:  .notice--danger}

공백 전까지 변수에 저장되고, 공백 이후의 "Dazzang\0"은 Buffer에 남게 된다는 것을 명심하라.  

---

`scanf`는 형식을 지정하여 입력 받는 경우 쓰인다.

#### 잘못된 scanf의 사용

```c++
#include <its/stdc++.h>
using namespace std;

//이름을 입력받는 코드 - 이렇게 쓸 순 없음 ;;
string name;
int main(){
    scanf("%s", &name);
    printf("%s\n", name);
}
```

**위와 같은 코드는 절대로 쓸 수 없다!!**

> 왜?
>
> scanf는 string 과 **호환되지 않**는다.

※ string 을 입력 받고 싶다면 공백 없이 `cin`이나 `getline`을 사용해야 함.

#### C++ 스타일의 %s 형식 입력

```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
    char name[100];       // C 스타일 문자열 버퍼
    scanf("%s", name);    // & 붙이지 않음
    printf("이름: %s\n", name);
}

```

**char 형 배열**을 사용하면 "%s"형식으로 지정할 수 있다.

---

`getline`은 공백 문자에서 잘리는 `cin` 대신에 한꺼번에 받기 위한 입력 방식이다.
