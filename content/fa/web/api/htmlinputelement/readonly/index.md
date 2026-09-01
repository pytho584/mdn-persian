---
title: "HTMLInputElement: readOnly property"
short-title: readOnly
slug: Web/API/HTMLInputElement/readOnly
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.readOnly
---

{{ APIRef("HTML DOM") }}

خاصیت **`readOnly`** در واسط {{DOMxRef("HTMLInputElement")}} نشان می‌دهد که کاربر نمی‌تواند مقدار {{htmlelement("input")}} را تغییر دهد. این خاصیت منعکس‌کنندهٔ ویژگی بولی [`readonly`](/en-US/docs/Web/HTML/Reference/Elements/input#readonly) عنصر {{htmlelement("input")}} است؛ در صورت وجود ویژگی، `true` و در صورت عدم وجود، `false` برمی‌گرداند.

برخلاف یک کنترل فرم با خاصیت {{domxref("HTMLInputElement.disabled", "disabled")}} برابر با `true`، مقدار `true` برای خاصیت `readOnly` از کلیک یا انتخاب کاربر در کنترل جلوگیری نمی‌کند.

اگرچه ویژگی HTML `readonly` برای انواع `hidden`، `range`، `color`، `checkbox`، `radio`، `file`، `submit`، `reset`، `button` و `image` نادیده گرفته می‌شود، خاصیت `readOnly` برای این انواع ورودی در صورت وجود ویژگی `true` و در غیر این صورت `false` است.

## مقدار

یک بولی.

## نمونه‌ها

```js
const inputElement = document.getElementById("total");
console.log(inputElement.readOnly);
inputElement.readOnly = true;
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{HTMLElement("input")}}
- {{DOMXref("HTMLInputElement.disabled")}}
- شبه‌کلاس {{cssxref(":read-only")}}