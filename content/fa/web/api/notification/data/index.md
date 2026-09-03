---
title: "Notification: data property"
short-title: data
slug: Web/API/Notification/data
page-type: web-api-instance-property
browser-compat: api.Notification.data
---

{{APIRef("Web Notifications")}}{{securecontext_header}} {{AvailableInWorkers}}

خاصیتِ فقط‌خواندنی **`data`** در رابط {{domxref("Notification")}} یک شبیه‌سازیشدهٔ ساختاریافته (structured clone) از داده‌های اعلان را برمی‌گرداند؛ همان‌طور که در گزینهٔ `data` سازندهٔ {{domxref("Notification.Notification","Notification()")}} مشخص شده است.

دادهٔ اعلان می‌تواند هر دادهٔ دلخواهی باشد که می‌خواهید با اعلان مرتبط کنید.

## مقدار

یک شبیه‌سازیشدهٔ ساختاریافته.

## مثال‌ها

در قطعه‌کد زیر یک اعلان ارسال می‌شود؛ یک شیء سادهٔ `options` ساخته می‌شود و سپس اعلان با استفاده از سازندهٔ `Notification()` ارسال می‌گردد.

```js
const options = {
  body: "Your code submission has received 3 new review comments.",
  data: {
    url: "https://example.com/review/12345",
    status: "open",
  },
};

const n = new Notification("New review activity", options);

console.log(n.data); // Logs the data object
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از API اعلان‌ها](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)