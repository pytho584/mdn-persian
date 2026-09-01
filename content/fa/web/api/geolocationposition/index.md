---
title: GeolocationPosition
slug: Web/API/GeolocationPosition
page-type: web-api-interface
browser-compat: api.GeolocationPosition
---

{{securecontext_header}}{{APIRef("Geolocation API")}}

رابط **`GeolocationPosition`** موقعیت دستگاه مورد نظر را در یک زمان معین نشان می‌دهد. این موقعیت که توسط یک شیء {{domxref("GeolocationCoordinates")}} نمایش داده می‌شود، موقعیت دوبعدی دستگاه را روی یک شبه‌کره که نمایانگر زمین است، به همراه ارتفاع و سرعت آن در بر می‌گیرد.

## ویژگی‌های نمونه

_رابط `GeolocationPosition` هیچ ویژگی‌ای را به ارث نمی‌برد._

- {{domxref("GeolocationPosition.coords")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("GeolocationCoordinates")}} برمی‌گرداند که موقعیت فعلی را تعریف می‌کند.
- {{domxref("GeolocationPosition.timestamp")}} {{ReadOnlyInline}}
  - : یک برچسب زمانی برمی‌گرداند که به‌صورت {{Glossary("Unix time")}} بر حسب میلی‌ثانیه ارائه شده و نشان‌دهندهٔ زمانی است که مکان بازیابی شده است.

## متدهای نمونه

_رابط `GeolocationPosition` هیچ متدی را به ارث نمی‌برد._

- {{domxref("GeolocationPosition.toJSON()")}}
  - : یک نمایش JSON از شیء `GeolocationPosition` برمی‌گرداند و سریال‌سازی را با {{jsxref("JSON.stringify()")}} امکان‌پذیر می‌کند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Using the Geolocation API](/en-US/docs/Web/API/Geolocation_API/Using_the_Geolocation_API)
- {{domxref("Geolocation")}}