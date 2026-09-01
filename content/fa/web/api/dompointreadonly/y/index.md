---
title: "DOMPointReadOnly: y property"
short-title: y
slug: Web/API/DOMPointReadOnly/y
page-type: web-api-instance-property
browser-compat: api.DOMPointReadOnly.y
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

ویژگی **`y`** در رابط **`DOMPointReadOnly`** مختصات عمودی (y) را برای یک نقطهٔ فقط‌خواندنی در فضا نگه می‌دارد.

اگر اسکریپت شما نیاز دارد که بتواند مقدار این ویژگی را تغییر دهد، به‌جای آن باید از شیء {{domxref("DOMPoint")}} استفاده کنید.

به‌طور کلی، مقادیر مثبت `y` به معنی «به سمت پایین» و مقادیر منفی `y` به معنی «به سمت بالا» هستند، مگر اینکه تبدیل‌هایی (transforms) اعمال شده باشد که جهت را معکوس کند.

## مقدار

یک مقدار اعشاری با دقت دوگانه (double-precision floating-point) که مختصات y نقطه را نشان می‌دهد. این مقدار **نامحدود** (unrestricted) است، یعنی می‌تواند بی‌نهایت یا نامعتبر باشد (به عبارت دیگر، مقدار آن ممکن است {{jsxref("NaN")}} یا {{jsxref("Infinity", "±Infinity")}} باشد).

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- سایر ویژگی‌های مختصات: {{domxref("DOMPointReadOnly.x", "x")}}، {{domxref("DOMPointReadOnly.z", "z")}} و مقدار پرسپکتیو {{domxref("DOMPointReadOnly.w", "w")}}.