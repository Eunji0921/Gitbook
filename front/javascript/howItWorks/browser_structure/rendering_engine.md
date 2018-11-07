---
description: 랜더링 엔진의 주요 역할은 브라우저 화면에 요청된 페이지를 표시하는 것
---

#### 렌더링 엔진 동작 과정

##### 렌더링 엔진 종류 

* **Gecko** -  Firefox
* **WebKit** -  Safari
* **Blink** -  Chrome, Opera \(15 버전부터\)

##### 렌더링 과정

![&amp;lt; &#xB80C;&#xB354;&#xB9C1; &#xACFC;&#xC815; &amp;gt;](https://camo.githubusercontent.com/43527d0e95b9fe6f9e8efb74cc19bb5c46b45207/68747470733a2f2f63646e2d696d616765732d312e6d656469756d2e636f6d2f6d61782f313630302f312a39623175454d635a4c57754750755963496e375a58512e706e67)

  
1. HTML을 파싱해 DOM 트리를 구성한다.
2. 렌더 트리를 구성한다.
3. 렌더 트리를 레이아웃한다.
4. 렌더 트리를 그린다.

##### DOM 트리 구성

```markup
<html>
  <head>
    <meta charset="UTF-8">
    <link rel="stylesheet" type="text/css" href="theme.css">
  </head>
  <body>
    <p> Hello, <span> friend! </span> </p>
    <div> 
      <img src="smiley.gif" alt="Smiley face" height="42" width="42">
    </div>
  </body>
</html>

```

이 HTML에 대한 DOM 트리는 다음과 같다.  


![&amp;lt; DOM &#xD2B8;&#xB9AC; &amp;gt;](https://camo.githubusercontent.com/49a42ee85440c6cbedaa7761ae4116e5974051a4/68747470733a2f2f63646e2d696d616765732d312e6d656469756d2e636f6d2f6d61782f313630302f312a657a466f587167663931756d6c733946714f304873512e706e67)

##### CSSOM 트리 구성

CSSOM는 `CSS 객체 모델(CSS Object Model)`을 말한다. 브라우저가 페이지 내 DOM을 구성하는 동안, `head` 영역에서 외부 CSS 스타일 시트 `theme.css` 를 참조하는 `link` 태그를 만난다. 페이지를 그리기 위해 해당 파일이 필요한 것을 예상하면서 즉시 자원 요청을 한다.

`theme.css` 파일이 다음과 같은 내용을 가지고 있다고 가정해보자.  


```css
body { 
  font-size: 16px;
}

p { 
  font-weight: bold; 
}

span { 
  color: red; 
}

p span { 
  display: none; 
}

img { 
  float: right; 
}

```

브라우저에서 동작할수 있는 CSSOM 트리로 재구성 한다.



![&amp;lt; CSSOM &#xD2B8;&#xB9AC; &amp;gt;](https://camo.githubusercontent.com/8d3471d1f38252fe785c3e558a229ab891f41fdb/68747470733a2f2f63646e2d696d616765732d312e6d656469756d2e636f6d2f6d61782f313630302f312a355955317375326d647a48455135694469734b5579772e706e67)

CSSOM이 트리구조로 되어 있는 이유?

자식 엘리먼트는 부모엘리먼트의 css의 영향을 받기 때문

##### 렌더 트리 구성

CSSOM 트리 + DOM 트리의 결합체

것은 시각적 요소들이 화면에 표시되는 순서대로 구성된 트리이다. 렌더 트리는 CSS와 함께 HTML을 시각적으로 표현한 것이다. 이 트리의 목적은 정확한 순서로 콘텐츠를 그릴 수 있도록 하는 것



![&amp;lt; &#xB80C;&#xB354;&#xB9C1; &#xD2B8;&#xB9AC;\(CSSOM + DOM\) &amp;gt;](https://camo.githubusercontent.com/26bd9038788e24141d1cf3f57bed43f93705b25f/68747470733a2f2f63646e2d696d616765732d312e6d656469756d2e636f6d2f6d61782f313630302f312a5748525f30384144384150444954512d3443464467672e706e67)



* DOM 트리의 루트에서부터 시작해, 각각의 시각적 노드들을 순회한다. 
  * script, meta 태그는 노출되지 않고 생략
  * CSS속성에 의해 생략되는 경우 \( `span` 노드는 `display: none` 속성을 설정하는 명확한 규칙에 의해 렌더 트리에서 보이지 않음\)
* 각각의 시각적인 노드들로부터 브라우저는 적절한 CSSOM 규칙을 찾아 적용한다.
* 브라우저는 콘텐츠와 계산된 스타일과 함께 시각적인 노드들을 보여준다.

##### 렌더트리 레이아웃 & 페인팅

1. **레이아웃**

   렌더러가 생성되고 트리에 추가될 때, 이 렌더러는 위치와 크기를 가지지 않는다. 이러한 값들을 계산하는 것을 레이아웃이라고 부른다.

   HTML은 흐름-기반\(flow-based\) 레이아웃 모델이다. 이것은 대부분 단일 방향에서 기하학적 값들을 계산할 수 있음을 의미한다. 좌표계는 루트 렌더러를 기준으로 한다. top, left 좌표가 사용된다.

   레이아웃은 재귀적인 과정이다. 이것은 루트 렌더러\(HTML 도큐먼트 엘리먼트에서 `<html>`에 해당\)에서 시작된다. 레이아웃은 부분 또는 전체 렌더러의 계층을 통과하면서 재귀적으로 반복되고, 이를 필요로 하는 렌더러의 기하학적 정보를 계산한다.

2. **페인팅**

   렌더링 엔진은 가능한 한 빠르게 화면상에 콘텐츠를 보여줄 수 있도록 시도할 것이다. 이 렌더링 엔진은 렌더 트리를 만들고 레이아웃하기 위해 모든 HTML이 파싱될 때까지 기다리지 않는다. 콘텐츠 일부는 파싱되고 표시되며, 나머지 콘텐츠 항목들을 네트워크상에서 계속 처리된다.

##### 스크립트 & 스타일시트 처리 순서

스크립트는 파서가 `<script>` 태그에 도달했을 때 즉시 파싱되고 실행된다. 문서의 파싱은 스크립트 실행이 끝날 때까지 대기한다. 이것은 처리가 **동기적** 임을 의미한다.

만약 스크립트가 외부 스크립트라면, 먼저 네트워크에서 동기적으로 이 파일을 가져와야 한다. 파일을 모두 가져오기 전까지 모든 파싱 과정은 정지된다.

HTML5에는 스크립트를 비동기로 표시하여 다른 스레드에서 파싱되고 실행될 수 있는 옵션을 추가했다.

reference

[https://github.com/codepink/codepink.github.com.wiki.git](https://github.com/codepink/codepink.github.com.wiki.git)



