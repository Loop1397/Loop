## HTML) Uncaught TypeError: Cannot read properties of null

*오류 해결 과정*

공부도 겸 만들고 있는 페이지에서 호버 기능을 사용하려고 한다. 그를 위해 아래 그림과 같이, 먼저 4개의 사진이 들어갈 공간을 마련해두었다. 

![image](/Users/nochan-u/Documents/info/Loop/img/posts/2021-10-31/src1.png)

*<center>기본 레이아웃</center>*

여기서 마우스를 사진이 들어갈 공간에 올리면 해당 사진의 가로가 길어지고, 마우스를 치우면 원래대로 돌아오는 구조이다.

![image](/Users/nochan-u/Documents/info/Loop/img/posts/2021-10-31/src2.png)

*<center>좌측 박스에 마우스를 올렸을 때의 기대 화면</center>*

*<center>박스의 width 속성을 150px에서 400px로 변경한다</center>*

<br>

이 기능을 만들기위해 html 파일에서 onmouseover속성과 onmouseout속성을 사용해 js파일의 특정 함수를 불러오고, 해당 함수에서 width속성을 변경해주려고 했다.

```html
<!--박스 4개를 만들기 위한 div-->
<div class="gallery">
 	<div id="image1" onmouseover="MouseOn1()" onmouseout="MouseOut1()">
	</div>
	<div id="image2" onmouseover="MouseOn2()" onmouseout="MouseOut2()">
	</div>
	<div id="image3" onmouseover="MouseOn3()" onmouseout="MouseOut3()">
	</div>
	<div id="image4" onmouseover="MouseOn4()" onmouseout="MouseOut4()">
	</div>
</div>
```

```js
//마우스가 박스위에 올라가거나 내려올 때 width속성을 변경해주기위한 js 코드
const image1 = document.getElementById("image1");

MouseOn1=()=> {
    image1.setAttribute("style","width:400px;");
}

MouseOut1=()=> {
    image1.setAttribute("style","width:150px;");
}
```

<br>

하지만, 이 상태로 웹 브라우저에서 실행시켜보니 아래와 같은 오류가 발생했다.

![image]()

*<center>마우스가 박스를 지날때마다 발생하는 에러 메세지.</center>*

<br>

오류를 해결하기 위해 구글링을 해보았다. 그러던 중 **HTML 생명주기**라는 개념을 알게 되었는데, 이 개념으로 인해 해당 오류가 일어나는 것이었다. 아직 HTML 생명주기나 DOM에 대해 자세히 찾아보진 않았지만... (물론 제대로 찾아봐서 공부할 예정이다)

간략하게 이해한 바로는, \<body\>태그 내부의 정보가 로드 되기도 전 \<head\>태그 내부에 들어있던 \<script\>태그에서 \<body\>의 정보를 가져오려하다 쓰레기 값(null)이 변수값으로 들어가버린 것 같다.

결론은, 아래의 두가지가 이 오류를 해결할 방법이었다. 

> 1. js파일을 연결시켜주는 \<script\> 태그를 \<body\>태그의 맨 끝으로 옮기기
> 2. js의 onload함수를 사용해 홈페이지의 로딩이 끝난 후 변수선언하기

1번 방법처럼 \<script\>태그를 \<body\>태그 안으로 집어넣어도 잘 작동했다. 하지만, 앞으로 js파일에 코드를 추가로 작성했을 때 문제가 생길 가능성이 있기 때문에, 2번 방법을 통해서 해당 오류를 해결했다.

```js
let image1, image2, image3, image4;
//const가 아닌 let을 사용한 이유는 image1~4를 아래에서 재선언 해야하기 때문이다.

window.onload=()=>
{
    image1 = document.getElementById("image1");
    image2 = document.getElementById("image2");
    image3 = document.getElementById("image3");
    image4 = document.getElementById("image4");
}

MouseOn1=()=> {
    image1.setAttribute("style","width:400px;");
}

MouseOut1=()=> {
    image1.setAttribute("style","width:150px;");
}
```

![image]()

*<center>오류메세지가 뜨지 않고 잘 작동하는 모습</center>*

