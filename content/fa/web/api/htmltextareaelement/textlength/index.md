---
title: "HTMLTextAreaElement: textLength property"
---

---
title: "HTMLTextAreaElement: textLength property"
short-title: textLength
slug: Web/API/HTMLTextAreaElement/textLength
page-type: web-api-instance-property
browser-compat: api.HTMLTextAreaElement.textLength
---

{{ APIRef("HTML DOM") }}

ویژگی فقطخواندنی **`textLength`** در رابط {{DOMxRef("HTMLTextAreaElement")}} یک عدد صحیح نامنفی است که تعداد نویسه‌های مقدار عنصر {{htmlelement("textarea")}} را بر حسب {{glossary("UTF-16", "UTF-16 code units")}} نشان می‌دهد. این ویژگی میانبری برای دسترسی به {{jsxref("String/length", "length")}} روی ویژگی {{domxref("HTMLTextAreaElement/value", "value")}} آن است.

## مقدار

یک عدد صحیح نامنفی.

## مثال‌ها

```js
const textareaElement = document.getElementById("comment");
console.log(textArea.textLength);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("textarea")}}
- {{DOMXref("HTMLTextAreaElement.rows")}}
- {{DOMXref("HTMLTextAreaElement.cols")}}
- {{DOMXref("HTMLTextAreaElement.minLength")}}
- {{DOMXref("HTMLTextAreaElement.maxLength")}}