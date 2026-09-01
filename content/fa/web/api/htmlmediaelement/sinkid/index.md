---
title: "HTMLMediaElement: sinkId property"
short-title: sinkId
slug: Web/API/HTMLMediaElement/sinkId
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.sinkId
---

{{APIRef("Audio Output Devices API")}}{{securecontext_header}}

ویژگی فقط‌خواندنی **`sinkId`** در رابط {{domxref("HTMLMediaElement")}} رشته‌ای را برمی‌گرداند که شناسهٔ یکتای دستگاهی است که برای پخش خروجی صوتی استفاده می‌شود.

این شناسه باید یکی از مقادیر {{domxref("MediaDeviceInfo.deviceId")}} باشد که از {{domxref("MediaDevices.enumerateDevices()")}} بازگردانده می‌شود. اگر دستگاه پیش‌فرض عامل کاربر استفاده شود، این ویژگی رشتهٔ خالی برمی‌گرداند.

## مقدار

رشته‌ای که دستگاه فعلی خروجی صوتی را نشان می‌دهد؛ یا رشتهٔ خالی، اگر دستگاه خروجی پیش‌فرض عامل کاربر استفاده شود.

## الزامات امنیتی

دسترسی به این ویژگی تابع محدودیت‌های زیر است:

- این ویژگی باید در یک [زمینهٔ امن](/en-US/docs/Web/Security/Defenses/Secure_Contexts) فراخوانی شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Audio Output Devices API](/en-US/docs/Web/API/Audio_Output_Devices_API)
- {{domxref("MediaDevices.selectAudioOutput()")}}
- {{domxref("HTMLMediaElement.setSinkId()")}}