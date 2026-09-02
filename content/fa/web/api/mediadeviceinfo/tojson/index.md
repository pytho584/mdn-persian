---
title: "MediaDeviceInfo: toJSON() method"
short-title: toJSON()
slug: Web/API/MediaDeviceInfo/toJSON
page-type: web-api-instance-method
browser-compat: api.MediaDeviceInfo.toJSON
---

{{APIRef("Media Capture and Streams")}}{{securecontext_header}}

متد **`toJSON()`** در رابط {{domxref("MediaDeviceInfo")}} یک {{Glossary("Serialization","سریال‌ساز")}} است؛ این متد یک نمایش JSON از شیء {{domxref("MediaDeviceInfo")}} برمی‌گرداند.

## نحو (Syntax)

```js-nolint
toJSON()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک شیء {{jsxref("JSON")}} که سریال‌سازی شیء {{domxref("MediaDeviceInfo")}} است.

### مثال‌ها

```js
if (!navigator.mediaDevices || !navigator.mediaDevices.enumerateDevices) {
  console.log("enumerateDevices() not supported.");
} else {
  // List cameras and microphones.
  navigator.mediaDevices
    .enumerateDevices()
    .then((devices) => {
      devices.forEach((device) => {
        console.log(device.toJSON());
      });
    })
    .catch((err) => {
      console.log(`${err.name}: ${err.message}`);
    });
}
```

این ممکن است خروجی زیر را تولید کند:

```bash
Object { deviceId: "HJtTemQTM64Bivxv3ZEyKjCi1VR8042lPNpmXKObKJE=", kind: "videoinput", label: "", groupId: "Okm2l1YZTrwy8awTxE8QSLNFoVMdIXx++wLh68tbmv0=" }
Object { deviceId: "EqDubLxPlPeW+5w/ereWTF/3EaAMVHh9QBBHkZHiP0k=", kind: "audioinput", label: "", groupId: "Okm2l1YZTrwy8awTxE8QSLNFoVMdIXx++wLh68tbmv0=" }
Object { deviceId: "CanWttL2RnHOiS7FzzYXMIvLqVFE5S06Lfy8H//nhEw=", kind: "audioinput", label: "", groupId: "nOdLNeXGIw9oL9f2wH69SssQpRVs7cmt9jqZrUWgQwI=" }
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{jsxref("JSON")}}