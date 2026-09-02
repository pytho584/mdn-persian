---
title: "InputDeviceInfo: getCapabilities() method"
short-title: getCapabilities()
slug: Web/API/InputDeviceInfo/getCapabilities
page-type: web-api-instance-method
browser-compat: api.InputDeviceInfo.getCapabilities
---

{{APIRef("Media Capture and Streams")}}{{securecontext_header}}

متد **`getCapabilities()`** در واسط {{domxref("InputDeviceInfo")}} یک شیء `MediaTrackCapabilities` برمی‌گرداند که ترک اصلی صوتی یا تصویری {{domxref("MediaStream")}} دستگاه را توصیف می‌کند.

## Syntax

```js-nolint
getCapabilities()
```

### Parameters

بدون پارامتر.

### Return value

یک شیء `MediaTrackCapabilities` که مقدار یا محدوده مقادیر پشتیبانی‌شده برای هر یک از خصوصیت‌های قابل‌محدودسازی (constrainable properties) عامل کاربر را مشخص می‌کند. این شیء موظف است دقیقاً همان اطلاعاتی را برگرداند که با فراخوانی `getCapabilities()` روی نخستین {{domxref("MediaStreamTrack")}} از همان `kind` (نوع صوتی یا تصویری) این دستگاه، در `MediaStream` بازگشته از `getUserMedia({ deviceId: deviceInfo.deviceId })` به دست می‌آید.

برای فهرست خصوصیت‌های رایج پشتیبانی‌شده و انواع آن‌ها، به {{domxref("MediaStreamTrack.getCapabilities()")}} مراجعه کنید.

> [!NOTE]
> اگر کاربر به دستگاه ورودی دسترسی (مجوز) نداده باشد، یک شیء خالی برگردانده می‌شود.

## Examples

در مثال زیر، با استفاده از {{domxref("mediaDevices.getUserMedia()")}} اجازه دسترسی به دستگاه‌های صوتی و تصویری را درخواست می‌کنیم؛ زیرا برای استفاده از `getCapabilities()` به اجازه دسترسی به دستگاه‌ها نیاز داریم.

اگر `device` یک شیء `InputDeviceInfo` باشد، آنگاه `getCapabilities()` یک شیء با اعضایی برمی‌گرداند که قابلیت‌های آن دستگاه را نشان می‌دهند. برای نمونه، یک جریان ویدیویی شامل خصوصیت‌های خودکار مانند `noiseSuppression` نخواهد بود.

```js
// Get permission to access audio or video devices
navigator.mediaDevices
  .getUserMedia({ audio: true, video: true })
  // Enumerate media devices
  .then(() => navigator.mediaDevices.enumerateDevices())
  .then((devices) => {
    devices.forEach((device) => {
      if (typeof device.getCapabilities === "function") {
        console.log("Capabilities:", device.getCapabilities()); // A MediaTrackCapabilities object.
      } else {
        console.log("Device does not support getCapabilities:", device);
      }
    });
  })
  .catch((mediaError) => {
    console.error("Error accessing media devices:", mediaError);
  });
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("MediaStreamTrack.getCapabilities()")}}، که آن نیز یک شیء `MediaTrackCapabilities` برمی‌گرداند.