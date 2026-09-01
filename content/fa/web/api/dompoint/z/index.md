---
title: "DOMPoint: z property"
short-title: z
slug: Web/API/DOMPoint/z
page-type: web-api-instance-property
browser-compat: api.DOMPoint.z
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

ویژگی **`z`** در رابط **`DOMPoint`** مختصات عمق یک نقطه در فضا را مشخص می‌کند.

مگر اینکه تبدیل‌ها (transforms) جهت‌گیری را تغییر داده باشند، مقدار `z` برابر ۰، صفحه نمایش است؛ مقادیر مثبت از صفحه به سمت بیرون و رو به کاربر امتداد می‌یابند و مقادیر منفی در پشت صفحه به سمت دور دست می‌روند.

## مقدار

یک عدد اعشاری با دقت دوبرابر (double-precision floating-point) که مقدار مختصات _z_ نقطه را نشان می‌دهد. این مقدار **نامحدود** است؛ به این معنی که می‌تواند بی‌نهایت یا نامعتبر باشد (یعنی مقدار آن ممکن است {{jsxref("NaN")}} یا {{jsxref("Infinity", "±Infinity")}} باشد).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- سایر ویژگی‌های مختصات: {{domxref("DOMPoint.x", "x")}}، {{domxref("DOMPoint.y", "y")}} و مقدار پرسپکتیو {{domxref("DOMPoint.w", "w")}}.