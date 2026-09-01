---
title: "Element: replaceWith() method"
short-title: replaceWith()
slug: Web/API/Element/replaceWith
page-type: web-api-instance-method
browser-compat: api.Element.replaceWith
---

{{APIRef("DOM")}}

متد **`Element.replaceWith()`** این `Element` را در لیست فرزندان والد خود با مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها جایگزین می‌کند. رشته‌ها به‌عنوان گره‌های {{domxref("Text")}} معادل درج می‌شوند.

## نحو (Syntax)

```js-nolint
replaceWith(param1)
replaceWith(param1, param2)
replaceWith(param1, param2, /* …, */ paramN)
```

### پارامترها

- `param1`، …، `paramN`
  - : مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها برای جایگزینی.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها (Exceptions)

- `HierarchyRequestError` {{DOMxRef("DOMException")}}
  - : زمانی پرتاب می‌شود که گره در نقطه مشخص‌شده در سلسله‌مراتب قابل درج نباشد.

## مثال‌ها

### استفاده از `replaceWith()`

```js
const div = document.createElement("div");
const p = document.createElement("p");
div.appendChild(p);
const span = document.createElement("span");

p.replaceWith(span);

console.log(div.outerHTML);
// "<div><span></span></div>"
```

### `replaceWith()` غیرقابل دسترسی در `with`

متد `replaceWith()` در محدوده دستور `with` قرار ندارد. برای اطلاعات بیشتر به {{jsxref("Symbol.unscopables")}} مراجعه کنید.

```js
with (node) {
  replaceWith("foo");
}
// ReferenceError: replaceWith is not defined
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Node.replaceChild()")}}
- {{domxref("NodeList")}}
- {{domxref("CharacterData.replaceWith()")}}
- {{domxref("DocumentType.replaceWith()")}}