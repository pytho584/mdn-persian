---
title: "Location: pathname property"
short-title: pathname
slug: Web/API/Location/pathname
page-type: web-api-instance-property
browser-compat: api.Location.pathname
---

{{ApiRef("Location")}}

ویژگی **`pathname`** در رابط {{domxref("Location")}} رشته‌ای است که مسیرِ URLِ آن مکان را شامل می‌شود. اگر مسیری وجود نداشته باشد، `pathname` خالی خواهد بود؛ در غیر این صورت، `pathname` شامل یک `/` در ابتدا و سپس مسیر URL است، بدون اینکه رشتهٔ پرس‌وجو (query string) یا قطعه (fragment) را در بر بگیرد.

## مقدار

یک رشته.

## مثال‌ها

```js
// Let's say we are on the URL https://developer.mozilla.org/en-US/docs/Web/API/Location/pathname#examples
console.log(location.pathname); // '/en-US/docs/Web/API/Location/pathname'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}