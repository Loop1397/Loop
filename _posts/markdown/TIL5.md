<video controls src="/img/posts/2021-11-07/avi1.mov" width="100%"></video>

*<center>5개의 동적 의사 클래스를 사용한 예시</center>*

CSS의 의사 클래스(pseudo-class)는 HTML요소가 어떠한 상태인지를 명시할 때 사용한다. 그 중 특히 많이 사용되는 5가지를 동적 의사 클래스라 부르는데, 사용법은 아래와 같다.

```html
선택자:의사클래스이름 { 속성:속성값; }
```

상태 의사 클래스, 구조 의사 클래스, 기타 의사 클래스도 사용법은 같지만, 사용빈도가 동적 의사 클래스에 비해 적다.



> 동적 의사 클래스 종류 5가지

## 1. link

-사용자가 한 번도 해당 링크를 통해 연결된 사이트를 방문하지 않은 상태

## 2. visited

-사용자가 한 번이라도 해당 링크를 통해 연결된 사이트를 방문한 상태

## 3. hover

-마우스 커서가 해당 요소 위에 올라가 있는 상태

## 4. active 

-사용자가 마우스로 해당 요소를 클릭하고 있는 상태

## 5. focus

-input요소가 focus(키보드, 마우스)를 갖고 있는 상태

> 기타 속성

### ✏️ transition-duration

-값으로 지정한 시간(s)동안 동적 의사 클래스의 애니메이션이 실행됨

---



아래로는 동적 의사 클래스를 사용해보기 위해 작성한 코드 및 주석이다.

![image](/Users/nochan-u/Documents/info/Loop/img/posts/2021-11-07/src1.png)

*<center>main.html</center>*

![image](/Users/nochan-u/Documents/info/Loop/img/posts/2021-11-07/src2.png)

*<center>main.css</center>*