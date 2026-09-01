---
title: "Element: previousElementSibling property"
short-title: previousElementSibling
slug: Web/API/Element/previousElementSibling
page-type: web-api-instance-property
browser-compat: api.Element.previousElementSibling
---

{{APIRef("DOM")}}

ویژگی فقط-خواندنی **`Element.previousElementSibling`** عنصر {{domxref("Element")}} بلافاصله قبل از عنصر مشخص‌شده را در فهرست {{domxref("Element.children", "children")}} والد آن برمی‌گرداند، یا اگر عنصر مشخص‌شده اولین عنصر در فهرست باشد، `null` را برمی‌گرداند.

## مقدار

یک شیء {{domxref("Element")}}، یا `null`.

## مثال‌ها

```html
<div id="div-01">Here is div-01</div>
<div id="div-02">Here is div-02</div>
<li>This is a list item</li>
<li>This is another list item</li>
<div id="div-03">Here is div-03</div>
```

```js
let el = document.getElementById("div-03").previousElementSibling;
console.log("Siblings of div-03:");
while (el) {
  console.log(el.nodeName);
  el = el.previousElementSibling;
}
```

این مثال هنگام بارگذاری صفحه، خروجی زیر را نمایش می‌دهد:

```plain
Siblings of div-03:
LI
LI
DIV
DIV
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.nextElementSibling")}}