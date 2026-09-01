---
title: "ErrorEvent: error property"
short-title: error
slug: Web/API/ErrorEvent/error
page-type: web-api-instance-property
browser-compat: api.ErrorEvent.error
---

{{APIRef("HTML DOM")}}{{AvailableInWorkers}}

ویژگی فقط خواندنی **`error`** در رابط {{domxref("ErrorEvent")}} یک مقدار جاوااسکریپتی، مانند {{jsxref("Error")}} یا {{domxref("DOMException")}} برمی‌گرداند که نشان‌دهندهٔ خطای مرتبط با این رویداد است.

## مقدار

هر مقدار معتبر جاوااسکریپتی.

## مثال‌ها

```js
window.addEventListener("error", (ev) => {
  console.log(`نمونهٔ خطا: ${ev.error}`);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}