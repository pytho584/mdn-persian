---
title: "Document: lastElementChild property"
short-title: lastElementChild
slug: Web/API/Document/lastElementChild
page-type: web-api-instance-property
browser-compat: api.Document.lastElementChild
---

{{ APIRef("DOM") }}

ویژگی فقط‌خواندنی **`Document.lastElementChild`** آخرین عنصر فرزند سند را برمی‌گرداند، یا اگر هیچ عنصر فرزندی وجود نداشته باشد، مقدار `null` را برمی‌گرداند.

برای اسناد HTML، این معمولاً تنها فرزند است، یعنی عنصر ریشهٔ `<html>`.

برای دریافت آخرین عنصر فرزند از عناصر خاص درون یک سند، به {{domxref("Element.lastElementChild")}} مراجعه کنید.

## مقدار

عنصر ریشهٔ `<html>`.

## مثال‌ها

```js
document.lastElementChild;
// returns the root <html> element, the only child of the document
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.lastElementChild")}}