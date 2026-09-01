---
title: "HTMLInputElement: required property"
short-title: required
slug: Web/API/HTMLInputElement/required
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.required
---

{{ APIRef("HTML DOM") }}

ویژگی **`required`** از رابط {{DOMxRef("HTMLInputElement")}} مشخص می‌کند که کاربر باید قبل از ارسال فرم، مقداری را پر کند. این ویژگی منعکس‌کنندهٔ صفت [`required`](/en-US/docs/Web/HTML/Reference/Elements/input#required) عنصر {{htmlelement("input")}} است.

در حالی که صفت بولی `required` در HTML اگر نوع `hidden`، `range`، `color`، `submit`، `reset`، `button` و `image` باشد نادیده گرفته می‌شود، ویژگی `required` برای این انواع ورودی در صورت وجود صفت `true` و در غیر این صورت `false` است.

اگر یک ورودی اجباری (required) مقداری نداشته باشد، ویژگی فقط‌خواندنی {{domxref('ValidityState.valueMissing','valueMissing')}} از شیء {{domxref('ValidityState')}} برابر با `true` خواهد بود.

## مقدار

یک مقدار بولی.

## مثال‌ها

```js
const inputElement = document.getElementById("name");
console.log(inputElement.required);
inputElement.required = true;
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("input")}}
- {{DOMXref("HTMLInputElement.validity")}}
- شبه‌کلاس {{cssxref(":required")}}