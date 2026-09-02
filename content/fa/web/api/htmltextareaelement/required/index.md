---
title: "HTMLTextAreaElement: required property"
short-title: required
slug: Web/API/HTMLTextAreaElement/required
page-type: web-api-instance-property
browser-compat: api.HTMLTextAreaElement.required
---

{{ APIRef("HTML DOM") }}

خاصیت **`required`** در رابط {{DOMxRef("HTMLTextAreaElement")}} مشخص می‌کند که کاربر باید قبل از ارسال فرم، مقداری را وارد کند. این ویژگی، صفت [`required`](/en-US/docs/Web/HTML/Reference/Elements/textarea#required) عنصر {{htmlelement("textarea")}} را منعکس می‌کند.

## مقدار

یک مقدار بولین.

## مثال‌ها

```js
const textareaElement = document.getElementById("comment");
console.log(textArea.required);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{HTMLElement("textarea")}}
- {{DOMXref("HTMLTextAreaElement.validity")}}
- شبه‌کلاس {{cssxref(":required")}}