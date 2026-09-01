---
title: "Element: after() method"
short-title: after()
slug: Web/API/Element/after
page-type: web-api-instance-method
browser-compat: api.Element.after
---

{{APIRef("DOM")}}

متد **`Element.after()`** مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها را در فهرست فرزندان والدِ `Element` درست بعد از خودِ `Element` درج می‌کند. رشته‌ها به صورت گره‌های متنی ({{domxref("Text")}}) معادل درج می‌شوند.

## نحو (Syntax)

```js-nolint
after(node1)
after(node1, node2)
after(node1, node2, /* …, */ nodeN)
```

### پارامترها

- `node1`، …, `nodeN`
  - : مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها برای درج.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها (Exceptions)

- `HierarchyRequestError` {{DOMxRef("DOMException")}}
  - : زمانی پرتاب می‌شود که گره در نقطه مشخص‌شده در سلسله‌مراتب قابل درج نباشد.

## مثال‌ها

### درج یک عنصر

```js
let container = document.createElement("div");
let p = document.createElement("p");
container.appendChild(p);
let span = document.createElement("span");

p.after(span);

console.log(container.outerHTML);
// "<div><p></p><span></span></div>"
```

### درج متن

```js
let container = document.createElement("div");
let p = document.createElement("p");
container.appendChild(p);

p.after("Text");

console.log(container.outerHTML);
// "<div><p></p>Text</div>"
```

### درج یک عنصر و متن

```js
let container = document.createElement("div");
let p = document.createElement("p");
container.appendChild(p);
let span = document.createElement("span");

p.after(span, "Text");

console.log(container.outerHTML);
// "<div><p></p><span></span>Text</div>"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.before()")}}
- {{domxref("Element.append()")}}
- {{domxref("Element.insertAdjacentElement()")}}
- {{domxref("CharacterData.after()")}}
- {{domxref("DocumentType.after()")}}
- {{domxref("Node.appendChild()")}}
- {{domxref("NodeList")}}