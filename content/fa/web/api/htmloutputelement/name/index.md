---
title: "HTMLOutputElement: name property"
short-title: name
slug: Web/API/HTMLOutputElement/name
page-type: web-api-instance-property
browser-compat: api.HTMLOutputElement.name
---

{{ApiRef("HTML DOM")}}

ویژگی **`name`** در رابط {{domxref("HTMLOutputElement")}} نام عنصر {{HTMLElement("output")}} را نشان می‌دهد. این ویژگی منعکس‌کنندهٔ ویژگی [`name`](/en-US/docs/Web/HTML/Reference/Elements/output#name) عنصر است.

## مقدار

یک رشته (string) که نام عنصر را نمایش می‌دهد.

## مثال

```js
const outputElement = document.querySelector("#log");
console.log(`Element's name: ${outputElement.name}`);
outputElement.name = "sum"; // sets or updates the element's name
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLOutputElement.defaultValue")}}
- {{domxref("HTMLOutputElement.htmlFor")}}
- {{domxref("HTMLOutputElement.labels")}}