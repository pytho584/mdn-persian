---
title: "HTMLQuoteElement: cite property"
short-title: cite
slug: Web/API/HTMLQuoteElement/cite
page-type: web-api-instance-property
browser-compat: api.HTMLQuoteElement.cite
---

{{ApiRef("HTML DOM")}}

ویژگی **`cite`** در رابط {{domxref("HTMLQuoteElement")}} نشانی اینترنتی (URL) منبع نقل‌قول را مشخص می‌کند. این ویژگی بازتاب‌دهندهٔ ویژگی [`cite`](/en-US/docs/Web/HTML/Reference/Elements/q#cite) عنصر {{HTMLElement("q")}} است.

## مقدار

یک رشته (string) که یک نشانی اینترنتی را نشان می‌دهد.

## مثال

```js
const quote = document.querySelector("q");
console.log(`Original source: ${quote.cite}`); // the current value
quote.cite = "https://example.com/quotes"; // updates the value
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLQuoteElement")}}
- {{domxref("HTMLModElement.cite")}}