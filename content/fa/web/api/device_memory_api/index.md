---
title: "Device Memory API"
---

---
title: Device Memory API
slug: Web/API/Device_Memory_API
page-type: web-api-overview
browser-compat:
  - api.Navigator.deviceMemory
  - api.WorkerNavigator.deviceMemory
  - http.headers.Sec-CH-Device-Memory
spec-urls: https://www.w3.org/TR/device-memory/
---

{{DefaultAPISidebar("Device Memory API")}}{{securecontext_header}}{{AvailableInWorkers}}

توانایی‌های یک دستگاه کلاینت تا حد زیادی به میزان RAM موجود بستگی دارد. به‌طور سنتی، توسعه‌دهندگان مجبور بودند از روش‌های اکتشافی استفاده کنند و یا به بنچمارک دستگاه بپردازند، یا توانایی‌های دستگاه را بر اساس عوامل دیگری مانند سازنده دستگاه یا رشته‌های User Agent استنتاج کنند.

## تعیین حافظه دستگاه

دو روش برای تعیین تقریبی میزان RAM دستگاه وجود دارد: استفاده از Device Memory JavaScript API یا پذیرش Client Hints.

### API جاوااسکریپت

می‌توانید میزان تقریبی RAM دستگاه را با دریافت {{DOMxRef("Navigator.deviceMemory")}} یا {{DOMxRef("WorkerNavigator.deviceMemory")}} پرس‌وجو کنید.

```js
const RAM = navigator.deviceMemory;
```

### Client Hints

همچنین می‌توانید از هدر HTTP [Client Hints](/en-US/docs/Web/HTTP/Guides/Client_hints) با دایرکتیو `Device-Memory` برای دریافت همان ظرفیت تقریبی RAM استفاده کنید.

## رابط‌ها

### افزونه‌هایی به رابط‌های دیگر

- {{domxref("Navigator.deviceMemory")}} {{ReadOnlyInline}}
  - : میزان تقریبی حافظه دستگاه را بر حسب گیگابایت برمی‌گرداند.
- {{domxref("WorkerNavigator.deviceMemory")}} {{ReadOnlyInline}}
  - : میزان تقریبی حافظه دستگاه را بر حسب گیگابایت برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- هدر {{HTTPHeader("Sec-CH-Device-Memory")}}