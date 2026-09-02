---
title: InputDeviceInfo
slug: Web/API/InputDeviceInfo
page-type: web-api-interface
browser-compat: api.InputDeviceInfo
---

{{APIRef("Media Capture and Streams")}}{{securecontext_header}}

رابط **`InputDeviceInfo`** از {{domxref("Media Capture and Streams API", "", "", "nocode")}} امکان دسترسی به قابلیت‌های دستگاه ورودی‌ای را فراهم می‌کند که این رابط نمایانگر آن است.

اشیاء `InputDeviceInfo` توسط {{domxref("MediaDevices.enumerateDevices()")}} بازگردانده می‌شوند، اگر دستگاه بازگشتی یک دستگاه ورودی صوتی یا تصویری باشد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_همچنین ویژگی‌های رابط والد خود، {{DOMxRef("MediaDeviceInfo")}} را به ارث می‌برد._

## روش‌های نمونه

_همچنین روش‌های رابط والد خود، {{DOMxRef("MediaDeviceInfo")}} را به ارث می‌برد._

- {{domxref("InputDeviceInfo.getCapabilities()")}}
  - : یک شیء `MediaTrackCapabilities` برمی‌گرداند که جریان (track) اصلی صوتی یا تصویری `MediaStream` دستگاه را توصیف می‌کند.

## مثال‌ها

مثال زیر همه دستگاه‌های رسانه‌ای را با {{domxref("MediaDevices.enumerateDevices()")}} دریافت می‌کند. اگر هر یک از دستگاه‌ها دستگاه ورودی باشند، `console.log(device)` یک شیء `InputDeviceInfo` را در کنسول چاپ می‌کند.

```js
navigator.mediaDevices.enumerateDevices().then((devices) => {
  devices.forEach((device) => {
    console.log(device); // an InputDeviceInfo object if the device is an input device, otherwise a MediaDeviceInfo object.
  });
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}