---
title: "HTMLTextAreaElement: readOnly property"
short-title: readOnly
slug: Web/API/HTMLTextAreaElement/readOnly
page-type: web-api-instance-property
browser-compat: api.HTMLTextAreaElement.readOnly
---

{{ APIRef("HTML DOM") }}

ویژگی **`readOnly`** در رابط {{DOMxRef("HTMLTextAreaElement")}} نشان می‌دهد که کاربر نمی‌تواند مقدار کنترل را تغییر دهد. برخلاف ویژگی {{domxref("HTMLTextAreaElement.disabled", "disabled")}}، ویژگی `readonly` مانع کلیک کردن یا انتخاب کردن کاربر در کنترل نمی‌شود. این ویژگی، ویژگی [`readonly`](/en-US/docs/Web/HTML/Reference/Elements/textarea#readonly) عنصر {{htmlelement("textarea")}} را بازتاب می‌دهد.

## مقدار

یک مقدار بولی.

## مثال‌ها

```js
const textareaElement = document.getElementById("comment");
console.log(textArea.readOnly);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{HTMLElement("textarea")}}
- {{DOMXref("HTMLTextAreaElement.disabled")}}
- شبه‌کلاس {{cssxref(":read-only")}}