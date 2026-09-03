---
title: "Navigator: devicePosture property"
short-title: devicePosture
slug: Web/API/Navigator/devicePosture
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Navigator.devicePosture
---

{{APIRef("Device Posture API")}}{{SeeCompatTable}}

خاصیت فقط‌خواندنی **`Navigator.devicePosture`**، شیء {{domxref("DevicePosture")}} مرورگر را برمی‌گرداند که به توسعه‌دهندگان امکان می‌دهد وضعیت فعلی دستگاه را (یعنی اینکه نمایشگر در حالت تخت یا تاشده است) بررسی کنند و کدی را در پاسخ به تغییرات وضعیت اجرا نمایند.

## مقدار

یک شیء {{domxref("DevicePosture")}}.

## مثال‌ها

```js
const postureOutput = document.getElementById("currentPosture");

function reportPostureOutput() {
  // نوع ویژگی، "continuous" یا "folded" را برمی‌گرداند
  postureOutput.textContent = `Device posture: ${navigator.devicePosture.type}`;
}

navigator.devicePosture.addEventListener("change", reportPostureOutput);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DevicePosture")}}
- {{domxref("devicePosture.type")}}
- [Device Posture API](/en-US/docs/Web/API/Device_Posture_API)
- ویژگی CSS {{cssxref("@media/device-posture", "device-posture")}} در `@media`