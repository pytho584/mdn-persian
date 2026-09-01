---
title: "Element: nextElementSibling property"
short-title: nextElementSibling
slug: Web/API/Element/nextElementSibling
page-type: web-api-instance-property
browser-compat: api.Element.nextElementSibling
---

{{APIRef("DOM")}}

خاصیت فقط-خواندنی **`Element.nextElementSibling`**، عنصر بلافاصله بعد از عنصر مشخص‌شده را در فهرست {{domxref("Element.children", "children")}} (فرزندان) والد آن برمی‌گرداند، یا اگر عنصر مشخص‌شده آخرین عنصر در فهرست باشد، `null` را برمی‌گرداند.

## مقدار

یک شیء {{domxref("Element")}}، یا `null`.

## مثال‌ها

```html
<div id="div-01">Here is div-01</div>
<div id="div-02">Here is div-02</div>
```

```js
let el = document.getElementById("div-01").nextElementSibling;
console.log("Siblings of div-01:");
while (el) {
  console.log(el.nodeName);
  el = el.nextElementSibling;
}
```

این مثال پس از بارگیری، خروجی زیر را در کنسول نمایش می‌دهد:

```plain
Siblings of div-01:
DIV
SCRIPT
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.previousElementSibling")}}