---
title: "Element: before() method"
short-title: before()
slug: Web/API/Element/before
page-type: web-api-instance-method
browser-compat: api.Element.before
---

{{APIRef("DOM")}}

متد **`Element.before()`** مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها را در لیست فرزندان والد این `Element`، درست قبل از این `Element` درج می‌کند. رشته‌ها به صورت گره‌های معادل {{domxref("Text")}} درج می‌شوند.

## نحو (Syntax)

```js-nolint
before(param1)
before(param1, param2)
before(param1, param2, /* …, */ paramN)
```

### پارامترها

- `param1`, …, `paramN`
  - : مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها برای درج.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها (Exceptions)

- `HierarchyRequestError` {{DOMxRef("DOMException")}}
  - : زمانی پرتاب می‌شود که گره در نقطه مشخص شده در سلسله‌مراتب قابل درج نباشد.

## مثال‌ها

### درج یک عنصر

```js
let container = document.createElement("div");
let p = document.createElement("p");
container.appendChild(p);
let span = document.createElement("span");

p.before(span);

console.log(container.outerHTML);
// "<div><span></span><p></p></div>"
```

### درج متن

```js
let container = document.createElement("div");
let p = document.createElement("p");
container.appendChild(p);

p.before("Text");

console.log(container.outerHTML);
// "<div>Text<p></p></div>"
```

### درج یک عنصر و متن

```js
let container = document.createElement("div");
let p = document.createElement("p");
container.appendChild(p);
let span = document.createElement("span");

p.before(span, "Text");

console.log(container.outerHTML);
// "<div><span></span>Text<p></p></div>"
```

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید

- {{domxref("Element.after()")}}
- {{domxref("Element.append()")}}
- {{domxref("Element.insertAdjacentElement()")}}
- {{domxref("CharacterData.before()")}}
- {{domxref("DocumentType.before()")}}
- {{domxref("Node.appendChild()")}}
- {{domxref("Node.insertBefore()")}}
- {{domxref("NodeList")}}