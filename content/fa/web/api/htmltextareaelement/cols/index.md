---
title: "HTMLTextAreaElement: cols property"
short-title: cols
slug: Web/API/HTMLTextAreaElement/cols
page-type: web-api-instance-property
browser-compat: api.HTMLTextAreaElement.cols
---

ویژگی **`cols`** در رابط {{DOMxRef("HTMLTextAreaElement")}} یک عدد صحیح مثبت است که عرض قابل مشاهدهٔ کنترل متن چندخطی را بر حسب میانگین عرض کاراکترها نشان می‌دهد. این ویژگی منعکس‌کنندهٔ ویژگی [`cols`](/en-US/docs/Web/HTML/Reference/Elements/textarea#cols) عنصر `<textarea>` است.

## مقدار

یک عدد صحیح مثبت. پیش‌فرض `20` است.

## مثال‌ها

```js
const textareaElement = document.getElementById("comment");
textArea.cols = 80;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("textarea")}}
- {{DOMXref("HTMLTextAreaElement.rows")}}
- {{DOMXref("HTMLTextAreaElement.wrap")}}
- ویژگی CSS {{cssxref("resize")}}