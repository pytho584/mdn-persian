---
title: "HTMLTextAreaElement: rows property"
---

---
title: "HTMLTextAreaElement: rows property"
short-title: rows
slug: Web/API/HTMLTextAreaElement/rows
page-type: web-api-instance-property
browser-compat: api.HTMLTextAreaElement.rows
---

{{ APIRef("HTML DOM") }}

ویژگی **`rows`** در رابط {{DOMxRef("HTMLTextAreaElement")}} یک عدد صحیح مثبت است که تعداد خطوط متنی قابل مشاهدهٔ کنترل متنی را نشان می‌دهد. این ویژگی منعکس‌کنندهٔ صفت [`rows`](/en-US/docs/Web/HTML/Reference/Elements/textarea#rows) عنصر `<textarea>` است.

## مقدار

یک عدد صحیح مثبت. پیش‌فرض `2` است.

## مثال‌ها

```js
const textareaElement = document.getElementById("comment");
const textLines = textArea.rows;
textArea.rows = textLines + 2;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("textarea")}}
- {{DOMXref("HTMLTextAreaElement.cols")}}
- {{DOMXref("HTMLTextAreaElement.wrap")}}
- ویژگی CSS {{cssxref("resize")}}