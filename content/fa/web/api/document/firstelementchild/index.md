---
title: "Document: firstElementChild property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Document/firstElementChild"
---

---
title: "Document: firstElementChild property"
short-title: firstElementChild
slug: Web/API/Document/firstElementChild
page-type: web-api-instance-property
browser-compat: api.Document.firstElementChild
---

{{ APIRef("DOM") }}

خاصیت فقط‌خواندنی **`Document.firstElementChild`** اولین عنصر فرزند سند را برمی‌گرداند، یا اگر هیچ عنصر فرزندی وجود نداشته باشد، `null` را برمی‌گرداند.

برای اسناد HTML، این معمولاً تنها فرزند است، یعنی عنصر ریشه `<html>`.

برای دسترسی به اولین عنصر فرزند عناصر خاص درون یک سند، به {{domxref("Element.firstElementChild")}} مراجعه کنید.

## مقدار

یک شیء {{domxref("Element")}}، یا `null`.

## مثال‌ها

```js
document.firstElementChild;
// returns the root <html> element, the only child of the document
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.firstElementChild")}}