---
title: "CSSStyleDeclaration: length property"
short-title: length
slug: Web/API/CSSStyleDeclaration/length
page-type: web-api-instance-property
browser-compat: api.CSSStyleDeclaration.length
---

{{ APIRef("CSSOM") }}

این ویژگی فقط خواندنی یک عدد صحیح برمی‌گرداند که تعداد اعلان‌های سبک در این بلوک اعلان CSS را نشان می‌دهد.

## مقدار

یک عدد صحیح که تعداد سبک‌های تنظیم شده به صورت صریح بر روی والد نمونه را نشان می‌دهد.

## مثال‌ها

کد زیر تعداد سبک‌های تنظیم شده به صورت صریح بر روی عنصر HTML زیر را به دست می‌آورد:

```html
<div
  id="div1"
  style="margin: 0 10px; background-color: #ccaa11; font-family: monospace"></div>
```

کد JavaScript:

```js
const myDiv = document.getElementById("div1");
const divStyle = myDiv.style;
const len = divStyle.length; // 6
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}