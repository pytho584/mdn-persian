---
title: "ImageDecoder: completed property"
short-title: completed
slug: Web/API/ImageDecoder/completed
page-type: web-api-instance-property
browser-compat: api.ImageDecoder.completed
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

خاصیت **`completed`** (فقط خواندنی) از رابط {{domxref("ImageDecoder")}} یک قول (Promise) برمی‌گرداند که پس از پایان بافر کردن داده‌های رمزگذاری‌شده، حل می‌شود.

## مقدار

یک {{jsxref("Promise")}} که با {{jsxref("undefined")}} حل می‌شود وقتی {{domxref("ImageDecoder.complete")}} برابر `true` باشد.

## مثال‌ها

در مثال زیر، مقدار `completed` پس از حل شدن promise، `undefined` خواهد بود.

```js
let completed = await imageDecoder.completed;
console.log(completed);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}