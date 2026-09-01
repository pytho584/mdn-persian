---
title: "HTMLSelectElement: required property"
short-title: required
slug: Web/API/HTMLSelectElement/required
page-type: web-api-instance-property
browser-compat: api.HTMLSelectElement.required
---

{{ APIRef("HTML DOM") }}

ویژگی **`required`** در رابط {{DOMxRef("HTMLSelectElement"}} مشخص می‌کند که کاربر باید قبل از ارسال فرم، گزینه‌ای با مقدار رشته‌ای غیرخالی انتخاب کند. این ویژگی بازتاب‌دهنده ویژگی [`required`](/en-US/docs/Web/HTML/Reference/Elements/select#required) عنصر {{htmlelement("select")}} است.

## مقدار

یک مقدار بولی (boolean).

## مثال‌ها

```js
const selectElement = document.getElementById("fruits");
console.log(selectElement.required);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{HTMLElement("select")}}
- {{DOMXref("HTMLSelectElement.validity")}}
- شبه‌کلاس {{cssxref(":required")}}