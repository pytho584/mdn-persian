---
title: "Element: append() method"
short-title: append()
slug: Web/API/Element/append
page-type: web-api-instance-method
browser-compat: api.Element.append
---

{{APIRef("DOM")}}

متد **`Element.append()`** مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها را پس از آخرین فرزندِ `Element` درج می‌کند. رشته‌ها به‌صورت گره‌های {{domxref("Text")}} معادل درج می‌شوند.

تفاوت‌های آن با {{domxref("Node.appendChild()")}}:

- `Element.append()` به شما امکان می‌دهد رشته‌ها را نیز اضافه کنید، در حالی که `Node.appendChild()` فقط اشیاء {{domxref("Node")}} را می‌پذیرد.
- `Element.append()` مقدار بازگشتی ندارد، در حالی که `Node.appendChild()` شیء {{domxref("Node")}} اضافه‌شده را بازمی‌گرداند.
- `Element.append()` می‌تواند چندین گره و رشته را اضافه کند، در حالی که `Node.appendChild()` فقط می‌تواند یک گره را اضافه کند.

## سینتکس

```js-nolint
append(param1)
append(param1, param2)
append(param1, param2, /* …, */ paramN)
```

### پارامترها

- `param1`, …, `paramN`
  - مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها برای درج.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `HierarchyRequestError` {{DOMxRef("DOMException")}}
  - زمانی پرتاب می‌شود که گره نتواند در نقطه‌ی مشخص‌شده در سلسله‌مراتب درج شود.

## مثال‌ها

### افزودن یک عنصر

```js
let div = document.createElement("div");
let p = document.createElement("p");
div.append(p);

console.log(div.childNodes); // NodeList [ <p> ]
```

### افزودن متن

```js
let div = document.createElement("div");
div.append("Some text");

console.log(div.textContent); // "Some text"
```

### افزودن یک عنصر و متن

```js
let div = document.createElement("div");
let p = document.createElement("p");
div.append("Some text", p);

console.log(div.childNodes); // NodeList [ #text "Some text", <p> ]
```

### متد `append()` در محدوده‌ی `with` قرار نمی‌گیرد

متد `append()` در محدوده‌ی عبارت `with` قرار نمی‌گیرد. برای اطلاعات بیشتر به {{jsxref("Symbol.unscopables")}} مراجعه کنید.

```js
let div = document.createElement("div");

with (div) {
  append("foo");
}
// ReferenceError: append is not defined
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.prepend()")}}
- {{domxref("Node.appendChild()")}}
- {{domxref("Element.after()")}}
- {{domxref("Element.insertAdjacentElement()")}}
- {{domxref("NodeList")}}