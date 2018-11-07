---
description: 자바스크립트의 런타임 처리과정에 대해 설명
---

#### 처리과정!!

> 자바스크립트 엔진은 하나의 쓰레드에서 동작한다.  
> Event Loop와 Queue를 사용해 비동기를 처리한다.

![&amp;lt; &#xC790;&#xBC14;&#xC2A4;&#xD06C;&#xB9BD;&#xD2B8; &#xB7F0;&#xD0C0;&#xC784; &#xCC98;&#xB9AC;&#xACFC;&#xC815; &amp;gt;](http://sculove.github.io/blog/2018/01/18/javascriptflow/browser-structure.png)

* **호출스택 \( Call stack \)**

  단 하나만 존재.

* **이벤트 루프 \( Event Loop \)**

  자바스크립트는 보통 싱글 쓰레드라고 불리는데, 메인쓰레드인 이벤트 루프가 싱글쓰레드이기 때문

  _내부 while \( 무한루프 \) 로 처리되어있어 항상 실행됨_ 

  * 비동기로 처리되는 작업은 Queue에서 작업을 꺼내어 처리
  * Event Loop는 stack에 처리할 작업이 없는 경우 microtask queue -&gt; requestAnimationFrame -&gt; task quere 순으로 stack에 쌓고 처리함

* **Web API**
* **Task**

  비동기 작업이 순차적으로 수행될 수 있도록 보장하는 형태의 작업 유형

* **Microtask**

  비동기 작업이 현재 실행되는 스크립트 바로 다음에 일어나는 작업이다. 

  따라서 task보다 항상 먼저 실행된다. ex\) Promise

처리과정의 예 \) [http://sculove.github.io/blog/2018/01/18/javascriptflow/](http://sculove.github.io/blog/2018/01/18/javascriptflow/)





reference

[https://www.zerocho.com/category/JavaScript/post/597f34bbb428530018e8e6e2](https://www.zerocho.com/category/JavaScript/post/597f34bbb428530018e8e6e2)[http://sculove.github.io/blog/2018/01/18/javascriptflow/](http://sculove.github.io/blog/2018/01/18/javascriptflow/)

