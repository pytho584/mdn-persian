---
title: "MediaStreamTrack: getSettings() method"
short-title: getSettings()
slug: Web/API/MediaStreamTrack/getSettings
page-type: web-api-instance-method
browser-compat: api.MediaStreamTrack.getSettings
---

{{APIRef("Media Capture and Streams")}}

متد **`getSettings()`** در رابط {{domxref("MediaStreamTrack")}} یک شیء {{domxref("MediaTrackSettings")}} برمی‌گرداند که شامل مقادیر فعلی هر یک از ویژگی‌های قابل‌قید (constrainable) برای `MediaStreamTrack` جاری است.

برای جزئیات کار با ویژگی‌های قابل‌قید، به [قابلیت‌ها، قیدها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints) مراجعه کنید.

## نحو (Syntax)

```js-nolint
getSettings()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء {{domxref("MediaTrackSettings")}} که پیکربندی فعلی ویژگی‌های قابل‌قیدِ مسیر (track) را توصیف می‌کند.

> [!NOTE]
> شیء بازگشتی مقادیر فعلی تمام ویژگی‌های قابل‌قید را مشخص می‌کند، از جمله آنهایی که مقادیر پیش‌فرض پلتفرم هستند و نه آنهایی که صریحاً توسط کد وب‌سایت تنظیم شده‌اند. برای دریافت آخرین قیدهای تعیین‌شده برای ویژگی‌های مسیر، به شکلی که توسط کد وب‌سایت مشخص شده است، از {{domxref("MediaStreamTrack.getConstraints", "getConstraints()")}} استفاده کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}