---
title: "HTMLInputElement: required property"
short-title: required
slug: Web/API/HTMLInputElement/required
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.required
---

{{ APIRef("HTML DOM") }}

ویژگی **`required`** از رابط {{DOMxRef("HTMLInputElement")}} مشخص می‌کند که کاربر باید قبل از ارسال فرم، مقدار را پر کند. این ویژگی، منعکس‌کنندهٔ صفت [`required`](/en-US/docs/Web/HTML/Reference/Elements/input#required) عنصر {{htmlelement("input")}} است.

هرچند صفت بولی `required` در HTML برای تایپ‌های ورودی `hidden`، `range`، `color`، `submit`، `reset`، `button` و `image` نادیده گرفته می‌شود، ویژگی `required` برای این تایپ‌ها در صورت وجود این صفت مقدار `true` و در غیر این صورت `false` است.

اگر یک ورودی الزامی مقدار نداشته باشد، ویژگی فقط‌خواندنی {{domxref('ValidityState.valueMissing','valueMissing')}} از شیء {{domxref('ValidityState')}} مقدار `true` خواهد بود.

## مقدار

یک بولی.

## مثال‌ها

```js
const inputElement = document.getElementById("name");
console.log(inputElement.required);
inputElement.required = true;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("input")}}
- {{DOMXref("HTMLInputElement.validity")}}
- {{cssxref(":required")}} شبه‌کلاس
