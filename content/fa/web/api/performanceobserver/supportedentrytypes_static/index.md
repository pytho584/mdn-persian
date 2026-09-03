---
title: "PerformanceObserver: supportedEntryTypes static property"
short-title: supportedEntryTypes
slug: Web/API/PerformanceObserver/supportedEntryTypes_static
page-type: web-api-static-property
browser-compat: api.PerformanceObserver.supportedEntryTypes_static
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی static و فقط‌خواندنی **`supportedEntryTypes`** در رابط {{domxref("PerformanceObserver")}} آرایه‌ای از مقادیر {{domxref("PerformanceEntry.entryType","entryType")}} را که عامل کاربر از آن‌ها پشتیبانی می‌کند برمی‌گرداند.

از آنجا که فهرست ورودی‌های پشتیبانی‌شده در مرورگرهای مختلف متفاوت است و همچنان در حال تکامل است، این ویژگی به توسعه‌دهندگان وب امکان می‌دهد بررسی کنند که کدام انواع در دسترس هستند.

## مقدار

آرایه‌ای از مقادیر {{domxref("PerformanceEntry.entryType")}}.

## مثال‌ها

### بررسی انواع پشتیبانی‌شده با استفاده از کنسول

برای اینکه بدانید یک مرورگر از کدام مقادیر {{domxref("PerformanceEntry.entryType","entryType")}} پشتیبانی می‌کند، عبارت <kbd>PerformanceObserver.supportedEntryTypes</kbd> را در کنسول وارد کنید. این کار آرایه‌ای از مقادیر پشتیبانی‌شده را برمی‌گرداند.

```js
PerformanceObserver.supportedEntryTypes;

// returns ["element", "event", "first-input", "largest-contentful-paint", "layout-shift", "long-animation-frame", "longtask", "mark", "measure", "navigation", "paint", "resource", "visibility-state"] in the main thread in Chrome 129
// returns ["mark", "measure", "resource"] in a worker thread in Chrome 129
```

### بررسی انواع پشتیبانی‌نشده

تابع زیر پشتیبانی از آرایه‌ای از انواع ورودی ممکن را بررسی می‌کند. انواع پشتیبانی‌نشده در کنسول ثبت می‌شوند؛ با این حال، این اطلاعات می‌توانند در تحلیل‌های سمت کلاینت نیز ثبت شوند تا نشان دهند که نوع خاصی قابل مشاهده نبوده است.

```js
function detectSupport(entryTypes) {
  for (const entryType of entryTypes) {
    if (!PerformanceObserver.supportedEntryTypes.includes(entryType)) {
      console.log(entryType);
    }
  }
}

detectSupport(["resource", "mark", "first-input", "largest-contentful-paint"]);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}