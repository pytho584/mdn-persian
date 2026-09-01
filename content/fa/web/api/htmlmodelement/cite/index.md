---
title: "HTMLModElement: cite property"
short-title: cite
slug: Web/API/HTMLModElement/cite
page-type: web-api-instance-property
browser-compat: api.HTMLModElement.cite
---

{{ApiRef("HTML DOM")}}

ویژگی **`cite`** در رابط {{domxref("HTMLModElement")}} نشانی اینترنتی (URL) منبعی را نشان می‌دهد که دلیل تغییر را توضیح می‌دهد. این ویژگی، صفت `cite` عناصر {{HTMLElement("del")}} و {{HTMLElement("ins")}} را منعکس می‌کند.

## مقدار

یک رشته (string) که یک نشانی اینترنتی (URL) را نشان می‌دهد.

## مثال

```js
const mod = document.querySelector("edit");
console.log(`Explanation: ${mod.cite}`); // the current value
mod.cite = "https://example.com/edits"; // updates the element's cite
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLModElement.dateTime")}}
- {{domxref("HTMLQuoteElement.cite")}}