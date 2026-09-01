---
title: "DOMPointReadOnly: z property"
short-title: z
slug: Web/API/DOMPointReadOnly/z
page-type: web-api-instance-property
browser-compat: api.DOMPointReadOnly.z
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

**ویژگی `z`** در رابط **`DOMPointReadOnly`** مختصات عمق (z) را برای یک نقطهٔ فقط‌خواندنی در فضا نگه می‌دارد.

اگر اسکریپت شما نیاز به تغییر مقدار این ویژگی دارد، باید به جای آن از شیء {{domxref("DOMPoint")}} استفاده کنید.

به‌طور کلی، مقادیر مثبت `z` به معنای حرکت به سمت کاربر (خارج شدن از صفحه) و مقادیر منفی `z` به معنای دور شدن از کاربر (ورود به صفحه) هستند، به شرطی که هیچ تبدیلی باعث وارونگی نشده باشد.

## مقدار

یک مقدار ممیز شناور با دقت دوگانه که مقدار مختصات z را برای نقطه نشان می‌دهد. این مقدار **نامحدود** است، به این معنی که می‌تواند بی‌نهایت یا نامعتبر باشد (یعنی مقدار آن می‌تواند {{jsxref("NaN")}} یا {{jsxref("Infinity", "±Infinity")}} باشد).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- سایر ویژگی‌های مختصات: {{domxref("DOMPointReadOnly.x", "x")}}، {{domxref("DOMPointReadOnly.y", "y")}}، و مقدار پرسپکتیو، {{domxref("DOMPointReadOnly.w", "w")}}.