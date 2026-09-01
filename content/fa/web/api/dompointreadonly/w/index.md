---
title: "DOMPointReadOnly: w property"
short-title: w
slug: Web/API/DOMPointReadOnly/w
page-type: web-api-instance-property
browser-compat: api.DOMPointReadOnly.w
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

ویژگی **`w`** در رابط **`DOMPointReadOnly`** مقدار پرسپکتیو نقطه (یعنی `w`) را برای یک نقطهٔ فقط‌خواندنی در فضا نگه می‌دارد.

اگر اسکریپت شما نیاز دارد که بتواند مقدار این ویژگی را تغییر دهد، به‌جای آن باید از شیء {{domxref("DOMPoint")}} استفاده کنید.

## مقدار

یک مقدار ممیز شناور با دقت دو برابر (double-precision floating-point) که مقدار پرسپکتیوِ `w` نقطه را نشان می‌دهد. این مقدار **بدون محدودیت** است، به این معنی که می‌تواند بی‌نهایت یا نامعتبر باشد (یعنی مقدار آن ممکن است {{jsxref("NaN")}} یا {{jsxref("Infinity", "±Infinity")}} باشد). پیش‌فرض `1.0` است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- سایر ویژگی‌های مختصات: {{domxref("DOMPointReadOnly.x", "x")}}، {{domxref("DOMPointReadOnly.y", "y")}} و {{domxref("DOMPointReadOnly.z", "z")}}.