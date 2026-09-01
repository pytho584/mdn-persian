---
title: "DOMTokenList: toString() method"
---
---
title: "DOMTokenList: toString() method"
short-title: toString()
slug: Web/API/DOMTokenList/toString
page-type: web-api-instance-method
browser-compat: api.DOMTokenList.toString
---

{{APIRef("DOM")}}

میان‌بر **`toString()`** (تبدیل‌کننده به رشته) از رابط {{domxref("DOMTokenList")}} مقادیر فهرست نشانه‌ها را به صورت یک رشته بازمی‌گرداند. مقدار بازگشتی، فهرستی از نشانه‌ها با جداکننده فاصله است که با ویژگی {{domxref("DOMTokenList.value")}} برابر است.

## نحو

```js-nolint
toString()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک رشته.

## مثال‌ها

```js
const element = document.createElement("div");
const classes = element.classList;

element.className = "shop empty-cart";
classes.add("logged-in", "dark-mode");

console.log(classes.toString());
// "shop empty-cart logged-in dark-mode"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.classList")}}
- {{domxref("DOMTokenList.add()")}}