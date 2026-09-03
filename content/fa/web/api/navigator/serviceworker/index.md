---
title: "Navigator: serviceWorker property"
short-title: serviceWorker
slug: Web/API/Navigator/serviceWorker
page-type: web-api-instance-property
browser-compat: api.Navigator.serviceWorker
---

{{securecontext_header}}{{APIRef("Service Workers API")}}

ویژگی فقط‌خواندنی **`serviceWorker`** در رابط {{domxref("Navigator")}}، شیء {{domxref("ServiceWorkerContainer")}} را برای [سند مرتبط](https://html.spec.whatwg.org/multipage/browsers.html#concept-document-window) برمی‌گرداند که دسترسی به ثبت، حذف، ارتقا و ارتباط با {{domxref("ServiceWorker")}} را فراهم می‌کند.

این قابلیت ممکن است در حالت خصوصی (Private Mode) در دسترس نباشد.

توجه داشته باشید که یک worker نیز می‌تواند به‌طور مشابه با استفاده از {{domxref("WorkerNavigator.serviceWorker")}} به {{domxref("ServiceWorkerContainer")}} مربوط به یک سند دسترسی یابد.

## مقدار

یک شیء {{domxref("ServiceWorkerContainer")}}.

## مثال‌ها

این کد بررسی می‌کند که آیا مرورگر از service workerها پشتیبانی می‌کند یا نه.

```js
if ("serviceWorker" in navigator) {
  // Supported!
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("Service Worker API", "", "", "nocode")}}
- [استفاده از Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)