---
title: "Element: prepend() method"
short-title: prepend()
slug: Web/API/Element/prepend
page-type: web-api-instance-method
browser-compat: api.Element.prepend
---

{{APIRef("DOM")}}

متد **`Element.prepend()`** مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها را قبل از اولین فرزند {{domxref("Element")}} درج می‌کند. رشته‌ها به صورت گره‌های {{domxref("Text")}} معادل درج می‌شوند.

## Syntax

```js-nolint
prepend(param1)
prepend(param1, param2)
prepend(param1, param2, /* …, */ paramN)
```

### Parameters

- `param1`, …, `paramN`
  - : مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها که باید درج شوند.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

### Exceptions

- `HierarchyRequestError` {{DOMxRef("DOMException")}}
  - : زمانی که گره نمی‌تواند در نقطه مشخص شده در سلسله‌مراتب درج شود، پرتاب می‌شود.

## Examples

### درج یک عنصر در ابتدا

```js
let div = document.createElement("div");
let p = document.createElement("p");
let span = document.createElement("span");
div.append(p);
div.prepend(span);

console.log(div.childNodes); // NodeList [ <span>, <p> ]
```

### درج متن در ابتدا

```js
let div = document.createElement("div");
div.append("Some text");
div.prepend("Headline: ");

console.log(div.textContent); // "Headline: Some text"
```

### درج یک عنصر و متن در ابتدا

```js
let div = document.createElement("div");
let p = document.createElement("p");
div.prepend("Some text", p);

console.log(div.childNodes); // NodeList [ #text "Some text", <p> ]
```

### متد prepend قابل اسکوپ نیست

متد `prepend()` در محدوده دستور `with` قرار نمی‌گیرد. برای اطلاعات بیشتر به {{jsxref("Symbol.unscopables")}} مراجعه کنید.

```js
let div = document.createElement("div");

with (div) {
  prepend("foo");
}
// ReferenceError: prepend is not defined
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Element.append()")}}
- {{domxref("Node.appendChild()")}}
- {{domxref("Node.insertBefore()")}}
- {{domxref("Element.before()")}}
- {{domxref("Element.insertAdjacentElement()")}}
- {{domxref("NodeList")}}