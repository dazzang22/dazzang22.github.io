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

