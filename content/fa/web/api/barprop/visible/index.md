---
title: "BarProp: visible property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BarProp/visible"
translated_by: "n8n + AI"
---

{{APIRef("DOM")}}

ویژگی فقط خواندنی **`visible`** از رابط {{domxref("BarProp")}} در صورتی که عنصر رابط کاربری که نمایش می‌دهد قابل مشاهده باشد، `true` برمی‌گرداند.

## مقدار

یک {{jsxref("Boolean")}} که اگر پنجره سطح بالا توسط {{domxref("window.open")}} با ویژگی [`popup`](/en-US/docs/Web/API/Window/open#popup) فعال باز شده باشد، `true` است.

> [!NOTE]
> از نظر تاریخی این نشان‌دهنده قابل مشاهده بودن عنصر رابط کاربری استفاده شده بود. اما به دلایل حریم خصوصی، این دیگر نشان‌دهنده دید واقعی هر عنصر رابط کاربری نیست.

## مثال‌ها

مثال زیر اگر پنجره یک پاپ‌آپ نباشد، `true` را در کنسول چاپ می‌کند.

```js
console.log(window.locationbar.visible);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}