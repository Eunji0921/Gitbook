---
description: 배열 관련 추가된 문법
---

# Array.prototype

## Array.prototype.find\(\)

**`find()`** 메서드는 주어진 판별 함수를 만족하는 **첫 번째 요소**의 **값**을 반환합니다. 그런 요소가 없다면 [`undefined`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/undefined)를 반환합니다.

* **인덱스**를 반환 :  [`findIndex()`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)

```javascript
var array1 = [5, 12, 8, 130, 44];

var found = array1.find(function(element) {
  return element > 10;
});

console.log(found);
// expected output: 12

```



