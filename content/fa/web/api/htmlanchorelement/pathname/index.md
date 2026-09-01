---
title: "HTMLAnchorElement: pathname property"
short-title: pathname
slug: Web/API/HTMLAnchorElement/pathname
page-type: web-api-instance-property
browser-compat: api.HTMLAnchorElement.pathname
---

{{ApiRef("HTML DOM")}}

ویژگی **`HTMLAnchorElement.pathname`** رشته‌ای است که شامل یک `'/'` ابتدایی و به دنبال آن مسیر URL است، به‌جز رشته جستار (query string) یا fragment. (یا اگر مسیری وجود نداشته باشد، رشته خالی است.)

## مقدار

یک رشته.

## مثال‌ها

```js
// An <a id="myAnchor" href="/en-US/docs/HTMLAnchorElement"> element is in the document
const anchor = document.getElementById("myAnchor");
anchor.pathname; // returns '/en-US/docs/HTMLAnchorElement'
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("HTMLAnchorElement")}} که این ویژگی به آن تعلق دارد.