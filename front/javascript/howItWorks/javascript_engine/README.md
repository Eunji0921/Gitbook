---
description: 자바스크립트 코드를 실행하는 프로그램 또는 인터프리터
---

# 자바스크립트 엔진

### **종류**

* \*\*\*\*[라이노](https://ko.wikipedia.org/wiki/%EB%9D%BC%EC%9D%B4%EB%85%B8_%28%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8_%EC%97%94%EC%A7%84%29): 모질라 재단이 운영, 오픈 소스, 모두 자바로 개발
* [스파이더몽키](https://ko.wikipedia.org/wiki/%EC%8A%A4%ED%8C%8C%EC%9D%B4%EB%8D%94%EB%AA%BD%ED%82%A4): 최초의 자바스크립트 엔진. [넷스케이프 내비게이터](https://ko.wikipedia.org/wiki/%EB%84%B7%EC%8A%A4%EC%BC%80%EC%9D%B4%ED%94%84_%EB%82%B4%EB%B9%84%EA%B2%8C%EC%9D%B4%ED%84%B0)에서 지원되며 오늘날은 [모질라 파이어폭스](https://ko.wikipedia.org/wiki/%EB%AA%A8%EC%A7%88%EB%9D%BC_%ED%8C%8C%EC%9D%B4%EC%96%B4%ED%8F%AD%EC%8A%A4)를 지원
* [**V8**](https://ko.wikipedia.org/wiki/%ED%81%AC%EB%A1%AC_V8) - 오픈 소스. 덴마크에서 구글이 개발. 구글 크롬의 일부
* [**웹킷**](https://ko.wikipedia.org/wiki/%EC%9B%B9%ED%82%B7) - 오픈 소스. Nitro가 홍보하고 [사파리](https://ko.wikipedia.org/wiki/%EC%82%AC%ED%8C%8C%EB%A6%AC_%28%EC%9B%B9_%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%29)용으로 [애플](https://ko.wikipedia.org/wiki/%EC%95%A0%ED%94%8C_%28%EA%B8%B0%EC%97%85%29)이 개발.
* [KJS](https://ko.wikipedia.org/w/index.php?title=KJS_%28KDE%29&action=edit&redlink=1) - KDE의 ECMAScript/자바스크립트 엔진. 캉커러 웹 브라우저를 위해 KDE 프로젝트의 [Harri Porten](https://ko.wikipedia.org/w/index.php?title=Harri_Porten&action=edit&redlink=1)이 개발
* [차크라 \(JScript9\)](https://ko.wikipedia.org/wiki/%EC%B0%A8%ED%81%AC%EB%9D%BC):[인터넷 익스플로러](https://ko.wikipedia.org/wiki/%EC%9D%B8%ED%84%B0%EB%84%B7_%EC%9D%B5%EC%8A%A4%ED%94%8C%EB%A1%9C%EB%9F%AC)용
* [차크라 \(자바스크립트\)](https://ko.wikipedia.org/w/index.php?title=%EC%B0%A8%ED%81%AC%EB%9D%BC_%28%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8_%EC%97%94%EC%A7%84%29&action=edit&redlink=1): [마이크로소프트 엣지](https://ko.wikipedia.org/wiki/%EB%A7%88%EC%9D%B4%ED%81%AC%EB%A1%9C%EC%86%8C%ED%94%84%ED%8A%B8_%EC%97%A3%EC%A7%80)용
* [Nashorn](https://ko.wikipedia.org/w/index.php?title=Nashorn&action=edit&redlink=1): OpenJDk의 일부인 오픈 소스. Oracle Java Languages and Tool Group이 개발
* [Juce](https://ko.wikipedia.org/w/index.php?title=Juce&action=edit&redlink=1): [C++](https://ko.wikipedia.org/wiki/C%2B%2B) [애플리케이션 프레임워크](https://ko.wikipedia.org/wiki/%EC%95%A0%ED%94%8C%EB%A6%AC%EC%BC%80%EC%9D%B4%EC%85%98_%ED%94%84%EB%A0%88%EC%9E%84%EC%9B%8C%ED%81%AC). 자바스크립트의 문법 일부를 사용한 사용자 지정 임베디드 인터프리터 포함.
* [제리스크립트](https://ko.wikipedia.org/wiki/%EC%A0%9C%EB%A6%AC%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8): 사물 인터넷용의 매우 가벼운 자바스크립트 엔진

### 구조 \( V8기준 \) 



![&amp;lt; V8 &#xC5D4;&#xC9C4; &#xAD6C;&#xC870; &amp;gt;](https://joshua1988.github.io/images/posts/web/translation/how-js-works/js-engine-structure.png)

  


* **Memory Heap** : 메모리 할당이 일어나는 곳
* **Call Stack** : 코드 실행에 따라 호출 스택이 쌓이는 곳



reference

[https://joshua1988.github.io/web-development/translation/javascript/how-js-works-inside-engine/](https://joshua1988.github.io/web-development/translation/javascript/how-js-works-inside-engine/)

