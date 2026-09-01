---
title: "DevicePosture: type property"
short-title: type
slug: Web/API/DevicePosture/type
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.DevicePosture.type
---

{{APIRef("Device Posture API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`type`** از رابط {{domxref("DevicePosture")}} وضعیت فعلی دستگاه را برمی‌گرداند.

## مقدار

رشته‌ای که وضعیت فعلی دستگاه را نشان می‌دهد. مقدار می‌تواند یکی از موارد زیر باشد:

- `continuous` (پیوسته)
  - : نشان‌دهنده وضعیت صفحه‌ی تخت است — این می‌تواند شامل یک دستگاه تاشو در حالی که به‌صورت تخت استفاده می‌شود، یک نمایشگر منحنی بدون درز، یا یک صفحه‌نمایش استاندارد رومیزی، لپ‌تاپ، تبلت یا موبایل باشد.
- `folded` (تا خورده)
  - : نشان‌دهنده وضعیت صفحه‌ی تا خورده است — این می‌تواند شامل یک دستگاه تاشو باشد که در حالت کتاب یا لپ‌تاپ استفاده می‌شود.

## نمونه‌ها

```js
const postureOutput = document.getElementById("currentPosture");

function reportPostureOutput() {
  // type property returns "continuous" or "folded"
  postureOutput.textContent = `Device posture: ${navigator.devicePosture.type}`;
}

navigator.devicePosture.addEventListener("change", reportPostureOutput);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی CSS `@media` برای {{cssxref("@media/device-posture", "device-posture")}}
- [رابط Device Posture API](/en-US/docs/Web/API/Device_Posture_API)
- [آزمایش منبع برای APIهای تاشو (Foldable APIs)](https://developer.chrome.com/blog/foldable-apis-ot) در developer.chrome.com (2024)