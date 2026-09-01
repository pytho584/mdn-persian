---
title: "Element: hasAttribute() method"
short-title: hasAttribute()
slug: Web/API/Element/hasAttribute
page-type: web-api-instance-method
browser-compat: api.Element.hasAttribute
---

{{APIRef("DOM")}}

متد **`Element.hasAttribute()`** یک مقدار **Boolean** (منطقی) برمی‌گرداند که نشان می‌دهد آیا عنصر مشخص‌شده دارای ویژگی (attribute) مشخص‌شده هست یا نه.

## Syntax

```js-nolint
hasAttribute(name)
```

### پارامترها

- `name`
  - : یک رشته (string) است که نام ویژگی را مشخص می‌کند.

### مقدار بازگشتی

یک مقدار boolean.

## مثال‌ها

```js
const foo = document.getElementById("foo");
if (foo.hasAttribute("bar")) {
  // do something
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## جستارهای وابسته

- {{domxref("Element.hasAttributes()")}}
- {{domxref("Element.getAttribute()")}}
- {{domxref("Element.setAttribute()")}}
- {{domxref("Element.removeAttribute()")}}
- {{domxref("Element.toggleAttribute()")}}