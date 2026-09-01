---
title: "Element: hasAttributes() method"
short-title: hasAttributes()
slug: Web/API/Element/hasAttributes
page-type: web-api-instance-method
browser-compat: api.Element.hasAttributes
---

{{ApiRef("DOM")}}

متد **`hasAttributes()`** در رابط {{domxref("Element")}} یک مقدار بولین (boolean) برمی‌گرداند که نشان می‌دهد آیا عنصر جاری ویژگی (attribute) دارد یا نه.

## سینتکس

```js-nolint
hasAttributes()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک مقدار بولین.

## مثال‌ها

```js
let foo = document.getElementById("foo");
if (foo.hasAttributes()) {
  // Do something with 'foo.attributes'
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.attributes")}}
- {{domxref("Element.hasAttribute()")}}
- {{domxref("Element.getAttribute()")}}
- {{domxref("Element.setAttribute()")}}
- {{domxref("Element.removeAttribute()")}}
- {{domxref("Element.toggleAttribute()")}}