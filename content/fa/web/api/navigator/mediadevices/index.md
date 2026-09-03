---
title: "Navigator: mediaDevices property"
short-title: mediaDevices
slug: Web/API/Navigator/mediaDevices
page-type: web-api-instance-property
browser-compat: api.Navigator.mediaDevices
---

{{securecontext_header}}{{APIRef("Media Capture and Streams")}}

ویژگی فقط‌خواندنی **`mediaDevices`** در رابط {{domxref("Navigator")}} یک شیء {{domxref("MediaDevices")}} را برمی‌گرداند که دسترسی به دستگاه‌های ورودی رسانه‌ای متصل مانند دوربین‌ها و میکروفون‌ها و همچنین اشتراک‌گذاری صفحه را فراهم می‌کند.

## مقدار

این شیء، شیءِ تکنمونه (singleton) {{domxref("MediaDevices")}} است. معمولاً به‌طور مستقیم از اعضای این شیء استفاده می‌کنید؛ مثلاً با فراخوانی {{domxref("MediaDevices.getUserMedia", "navigator.mediaDevices.getUserMedia()")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API): نقطه ورود به مستندات کل API ضبط رسانه و جریان‌ها (Media Capture and Streams).
- [WebRTC API](/en-US/docs/Web/API/WebRTC_API): مستندات مربوط به WebRTC API که ارتباط نزدیکی با این ویژگی دارد.