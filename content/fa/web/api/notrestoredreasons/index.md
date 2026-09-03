---
title: NotRestoredReasons
slug: Web/API/NotRestoredReasons
page-type: web-api-interface
status:
  - experimental
browser-compat: api.NotRestoredReasons
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

رابطهٔ **`NotRestoredReasons`** در {{domxref("Performance API", "Performance API", "", "nocode")}} داده‌های گزارشی را فراهم می‌کند که شامل دلایلی است که باعث شده‌اند سند فعلی در هنگام پیمایش از استفاده از حافظهٔ نهان رفت و برگشت ({{Glossary("bfcache")}}) مسدود شود.

این اشیاء از طریق ویژگی {{domxref("PerformanceNavigationTiming.notRestoredReasons")}} قابل دسترسی هستند.

## ویژگی‌های نمونه

- {{domxref("NotRestoredReasons.children", "children")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : آرایه‌ای از اشیاء `NotRestoredReasons`، یکی برای هر {{htmlelement("iframe")}} فرزندی که در سند فعلی جاسازی شده است. این اشیاء ممکن است حاوی دلایل مسدود شدن فریم سطح بالا مربوط به فریم‌های فرزند باشند. هر شیء همان ساختار شیء والد را دارد — به این ترتیب، هر تعداد سطح از `<iframe>`های تودرتو می‌توانند به صورت بازگشتی در داخل شیء نمایش داده شوند. اگر فریم فرزندی نداشته باشد، آرایه خالی خواهد بود؛ اگر سند در یک `<iframe>` متقاطع‌المنشأ (cross-origin) باشد، `children` مقدار `null` برمی‌گرداند.
- {{domxref("NotRestoredReasons.id", "id")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : رشته‌ای که مقدار ویژگی `id` مربوط به `<iframe>`ای که سند در آن قرار دارد را نشان می‌دهد (مثلاً `<iframe id="foo" src="...">`). اگر سند در یک `<iframe>` نباشد یا `<iframe>` ویژگی `id` را تنظیم نکرده باشد، `id` مقدار `null` برمی‌گرداند.
- {{domxref("NotRestoredReasons.name", "name")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : رشته‌ای که مقدار ویژگی `name` مربوط به `<iframe>`ای که سند در آن قرار دارد را نشان می‌دهد (مثلاً `<iframe name="bar" src="...">`). اگر سند در یک `<iframe>` نباشد یا `<iframe>` ویژگی `name` را تنظیم نکرده باشد، `name` مقدار `null` برمی‌گرداند.
- {{domxref("NotRestoredReasons.reasons", "reasons")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : آرایه‌ای از اشیاء {{domxref("NotRestoredReasonDetails")}} که هر کدام دلیلی را نشان می‌دهد که باعث مسدود شدن صفحهٔ پیمایش‌شده از استفاده از bfcache شده است. اگر سند در یک `<iframe>` متقاطع‌المنشأ باشد، `reasons` مقدار `null` برمی‌گرداند، اما سند والد ممکن است دلیلی به صورت `"masked"` نشان دهد اگر هر یک از `<iframe>`ها استفاده از bfcache را برای فریم سطح بالا مسدود کرده باشند.
- {{domxref("NotRestoredReasons.src", "src")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : رشته‌ای که مسیر منبع `<iframe>`ای که سند در آن قرار دارد را نشان می‌دهد (مثلاً `<iframe src="exampleframe.html">`). اگر سند در یک `<iframe>` نباشد، `src` مقدار `null` برمی‌گرداند.
- {{domxref("NotRestoredReasons.url", "url")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : رشته‌ای که URL صفحهٔ پیمایش‌شده یا `<iframe>` را نشان می‌دهد. اگر سند در یک `<iframe>` متقاطع‌المنشأ باشد، `url` مقدار `null` برمی‌گرداند.

## روش‌های نمونه

- {{domxref("NotRestoredReasons.toJSON", "toJSON()")}} {{Experimental_Inline}}
  - : یک {{Glossary("Serialization","سریال‌ساز")}}؛ یک نمایش JSON از شیء `NotRestoredReasons` برمی‌گرداند.

## مثال‌ها

برای مثال‌ها به [پایش دلایل مسدودسازی bfcache](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [پایش دلایل مسدودسازی bfcache](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons)
- {{domxref("PerformanceNavigationTiming.notRestoredReasons")}}