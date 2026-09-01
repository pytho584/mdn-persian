---
title: "ErrorEvent: colno property"
short-title: colno
slug: Web/API/ErrorEvent/colno
page-type: web-api-instance-property
browser-compat: api.ErrorEvent.colno
---

{{APIRef("HTML DOM")}}{{AvailableInWorkers}}

ویژگی **`colno`** (فقط‌خواندنی) از رابط {{domxref("ErrorEvent")}} یک عدد صحیح شامل شماره ستونِ فایل اسکریپتی که خطا در آن رخ داده است را برمی‌گرداند.

## مقدار

یک عدد صحیح.

## مثال‌ها

```js
window.addEventListener("error", (ev) => {
  console.log(`The error occur in column: ${ev.colno}`);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}