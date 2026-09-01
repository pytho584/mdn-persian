---
title: DeferredRequestInit
slug: Web/API/DeferredRequestInit
page-type: web-api-interface
status:
  - experimental
browser-compat: api.Window.fetchLater
---

{{DefaultAPISidebar("Fetch API")}}{{SeeCompatTable}}

واژه‌نامه **`DeferredRequestInit`** از [Fetch API](/en-US/docs/Web/API/Fetch_API) مجموعه‌ای از گزینه‌هایی است که می‌توان برای پیکربندی یک درخواست fetch تأخیری استفاده کرد.

شیء `DeferredRequestInit` مستقیماً به عنوان آرگومان دوم به تابع {{domxref("window.fetchLater()")}} ارسال می‌شود.

## ویژگی‌های نمونه

این واژه‌نامه، واژه‌نامه {{domxref("RequestInit")}} را با افزودن ویژگی‌های زیر گسترش می‌دهد:

- `activateAfter` {{optional_inline}}
  - : یک {{ domxref("DOMHighResTimeStamp") }} که یک مهلت زمانی (بر حسب میلی‌ثانیه) را مشخص می‌کند که پس از آن درخواست fetch باید ارسال شود. در صورت خروج از صفحه، fetch می‌تواند زودتر ارسال شود. زمان _واقعی_ ارسال مشخص نیست، زیرا مرورگر ممکن است مدت زمان بیشتری یا کمتری صبر کند، مثلاً برای بهینه‌سازی دسته‌بندی fetchهای تأخیری. اگر ویژگی `activateAfter` ارائه نشود، fetch تأخیری تا پایان بازدید از صفحه (از جمله ورود به [bfcache](/en-US/docs/Glossary/bfcache)) صبر می‌کند.

### استثناها

- `RangeError` {{domxref("DOMException")}}
  - : زمانی رخ می‌دهد که یک `activateAfter` منفی ارائه شود.

## مثال‌ها

### تأخیر در یک درخواست `GET` تا زمانی که صفحه نابود شود یا وارد bfcache شود

در این مثال، هیچ شیء `DeferredRequestInit` ارائه نشده و از هیچ مهلت زمانی استفاده نشده است:

```js
fetchLater("/send_beacon");
```

### تأخیر در یک درخواست `POST` به مدت حدود ۱ دقیقه

در این مثال، یک {{domxref("Request")}} ایجاد می‌کنیم و یک مقدار `activateAfter` برای تأخیر در ارسال درخواست به مدت ۶۰۰۰۰ میلی‌ثانیه (یا یک دقیقه) ارائه می‌دهیم:

```js
fetchLater("/send_beacon", {
  method: "POST",
  body: getBeaconData(),
  activateAfter: 60000, // 1 دقیقه
});
```

> [!NOTE]
> زمان واقعی ارسال مشخص نیست، زیرا مرورگر ممکن است مدت زمان بیشتری یا کمتری صبر کند، مثلاً برای بهینه‌سازی دسته‌بندی fetchهای تأخیری.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Fetch تأخیری](/en-US/docs/Web/API/Fetch_API/Using_Deferred_Fetch)
- [API ServiceWorker](/en-US/docs/Web/API/Service_Worker_API)
- [کنترل دسترسی HTTP (CORS)](/en-US/docs/Web/HTTP/Guides/CORS)
- [HTTP](/en-US/docs/Web/HTTP)