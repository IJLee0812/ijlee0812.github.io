---
title: "[PS] [Tip] C++ 코딩테스트용 템플릿 자동화(MacOS)"
excerpt: "코딩테스트용 템플릿 자동화"
categories: [PS, Tip]
tags: [PS, 코딩테스트, C++, BOJ, 백준, 자동화, 코딩테스트 자동화, 코테]
---

# [PS] [Tip] C++ 코딩테스트용 템플릿 자동화 방법(MacOS)

---

## 포스팅 배경
- C++을 사용하여 코딩테스트를 공부중인데, 매번 문제를 풀 때마다 번거롭게 파일을 생성하고 템플릿을 일일이 입력하기 귀찮아 자동화 방법을 찾아보게 됨
- 추후 다시 세팅하는 상황이 생기거나 다른 방향으로도 활용할 수 있어보여 기록해두려 함

<br>

## 적용 방법

### 1. C++ 코딩테스트 템플릿 생성(C++template.cpp, 파일명 및 템플릿 내용 변경 가능)

```cpp
#include <bits/stdc++.h>
using namespace std;



int main() {
    ios_base::sync_with_stdio(0); cin.tie(0); cout.tie(0);



    return 0;
}
```
<br>

### 2. ~ 디렉토리에서 ls -a 명령어로 '.zshrc' 파일 존재여부 확인, 없으면 (sudo) vi .zshrc로 생성

- cd ~ 
- ls -a 
- (sudo) vi .zshrc : 관리자 권한 요구 시 sudo 명령어 사용하여 생성

<br>

### 3. '.zshrc' 파일에 아래의 스크립트 내용 추가 (vi 편집기 사용)

```plaintext
ctmake() { cat 절대경로/C++template.cpp > "$1.cpp" }
```
- 절대경로는 템플릿이 저장된 파일 위치로, pwd로 확인 가능

- ctmake -> 이름 임의변경 가능(시스템 기본 명령어와 겹쳐도 되는지는 테스트해보지 않았음. 유의하여 사용)

- 적용예시(터미널)

![스크린샷 2024-08-19 오전 11 08 22](https://github.com/user-attachments/assets/2d2b30aa-9a08-4a79-91bb-e9fd17b9ccdf)


<br>

### 4. 터미널에서 source ~/.zshrc 입력하여 적용

<br>

### 5. ctmake filename(ex. BOJ_1234, test, ...) 명령어로 자동생성 정상작동 확인

![스크린샷 2024-08-19 오전 11 10 52](https://github.com/user-attachments/assets/de73631f-1bcb-4e4f-acc4-882d7f00f17c)

- test.cpp 파일이 정상적으로 만들어졌음을 확인할 수 있다.

> ### 📑 References : [코딩테스트 템플릿 코드 자동화](https://notej.tistory.com/entry/OSX-%EC%BD%94%EB%94%A9%ED%85%8C%EC%8A%A4%ED%8A%B8-%ED%85%9C%ED%94%8C%EB%A6%BF-%EC%BD%94%EB%93%9C-%EC%9E%90%EB%8F%99%ED%99%94)