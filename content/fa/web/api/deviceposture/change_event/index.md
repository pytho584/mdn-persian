---
title: "DevicePosture: change event"
---

---
title: "DevicePosture: change event"
short-title: change
slug: Web/API/DevicePosture/change_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.DevicePosture.change_event
---

{{APIRef("Device Posture API")}}{{SeeCompatTable}}

**`change`** رویدادِ رابط {{domxref("DevicePosture")}} زمانی پرتاب می‌شود که وضعیت (posture) دستگاه تغییر کند، مثلاً وقتی یک دستگاه تاشو از وضعیت `folded` به `continuous` می‌رود.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("change", (event) => { })

onchange = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

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

- ویژگی CSS {{cssxref("@media/device-posture", "device-posture")}} در `@media`
- [Device Posture API](/en-US/docs/Web/API/Device_Posture_API)
- [Origin trial for Foldable APIs](https://developer.chrome.com/blog/foldable-apis-ot) در developer.chrome.com (2024)