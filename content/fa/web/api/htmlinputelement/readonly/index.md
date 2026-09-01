---
title: "HTMLInputElement: readOnly property"
short-title: readOnly
slug: Web/API/HTMLInputElement/readOnly
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.readOnly
---

{{ APIRef("HTML DOM") }}

ویژگی **`readOnly`** در رابط {{DOMxRef("HTMLInputElement")}} نشان می‌دهد که کاربر نمی‌تواند مقدار عنصر {{htmlelement("input")}} را تغییر دهد. این ویژگی، صفت بولی [`readonly`](/en-US/docs/Web/HTML/Reference/Elements/input#readonly) عنصر {{htmlelement("input")}} را منعکس می‌کند؛ اگر صفت وجود داشته باشد `true` و در غیر این صورت `false` برمی‌گرداند.

برخلاف یک کنترل فرم با ویژگی {{domxref("HTMLInputElement.disabled", "disabled")}} برابر `true`، مقدار `true` برای ویژگی `readOnly` مانع از کلیک یا انتخاب کاربر در کنترل نمی‌شود.

در حالی که صفت HTML `readonly` برای انواع `hidden`، `range`، `color`، `checkbox`، `radio`، `file`، `submit`، `reset`، `button` و `image` نادیده گرفته می‌شود، ویژگی `readOnly` برای این نوع ورودی‌ها در صورت وجود صفت `true` و در غیر این صورت `false` است.

## مقدار

یک مقدار بولی (boolean).

## مثال

```js
const inputElement = document.getElementById("total");
console.log(inputElement.readOnly);
inputElement.readOnly = true;
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("input")}}
- {{DOMXref("HTMLInputElement.disabled")}}
- شبه-کلاس {{cssxref(":read-only")}}