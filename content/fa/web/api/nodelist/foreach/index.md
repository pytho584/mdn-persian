---
title: "NodeList: forEach() method"
---

---
title: "NodeList: forEach() method"
short-title: forEach()
slug: Web/API/NodeList/forEach
page-type: web-api-instance-method
browser-compat: api.NodeList.forEach
---

{{APIRef("DOM")}}

متد **`forEach()`** از رابط {{domxref("NodeList")}}، تابع داده‌شده در پارامتر (callback) را یک بار برای هر مقدار در فهرست، به ترتیب درج، اجرا می‌کند.

## نحو

```js-nolint
forEach(callback)
forEach(callback, thisArg)
```

### پارامترها

- `callback`
  - : تابعی است که روی هر عنصر از `someNodeList` اجرا می‌شود. این تابع ۳ پارامتر می‌پذیرد:
    - `currentValue`
      - : عنصر جاری که در `someNodeList` پردازش می‌شود.
    - `currentIndex` {{Optional_inline}}
      - : اندیس `currentValue` در حال پردازش در `someNodeList`.
    - `listObj` {{Optional_inline}}
      - : همان `someNodeList` است که متد `forEach()` روی آن اعمال می‌شود.

- `thisArg` {{Optional_inline}}
  - : مقداری که هنگام اجرای `callback` به‌عنوان [`this`](/en-US/docs/Web/JavaScript/Reference/Operators/this) استفاده می‌شود.

### مقدار بازگشتی

{{jsxref('undefined')}}.

## مثال

```js
const node = document.createElement("div");
const kid1 = document.createElement("p");
const kid2 = document.createTextNode("hey");
const kid3 = document.createElement("span");

node.appendChild(kid1);
node.appendChild(kid2);
node.appendChild(kid3);

const list = node.childNodes;

list.forEach(function (currentValue, currentIndex, listObj) {
  console.log(`${currentValue}, ${currentIndex}, ${this}`);
}, "myThisArg");
```

کد بالا نتیجهٔ زیر را به دست می‌دهد:

```plain
[object HTMLParagraphElement], 0, myThisArg
[object Text], 1, myThisArg
[object HTMLSpanElement], 2, myThisArg
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [پلی‌فیلِ `NodeList.prototype.forEach` در `core-js`](https://github.com/zloirock/core-js#iterable-dom-collections)
- {{domxref("Node")}}
- {{domxref("NodeList")}}