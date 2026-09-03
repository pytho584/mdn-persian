---
title: "PointerEvent: tiltX property"
short-title: tiltX
slug: Web/API/PointerEvent/tiltX
page-type: web-api-instance-property
browser-compat: api.PointerEvent.tiltX
---

{{ APIRef("Pointer Events") }}

ویژگی **`tiltX`** (فقط‌خواندنی) از رابط {{domxref("PointerEvent")}}، زاویه (برحسب درجه) بین _صفحهٔ Y-Z_ اشاره‌گر و صفحهٔ نمایش است. این ویژگی معمولاً فقط برای نوع اشاره‌گر قلم/استایلوس مفید است.

بسته به سخت‌افزار و پلتفرم خاص، عامل کاربر (user agent) به احتمال زیاد تنها یک مجموعه از مقادیر جهت‌گیری مبدل را نسبت به صفحهٔ نمایش دریافت می‌کند — یا `tiltX` و {{domxref("PointerEvent.tiltY", "tiltY")}} یا {{domxref("PointerEvent.altitudeAngle", "altitudeAngle")}} و {{domxref("PointerEvent.azimuthAngle", "azimuthAngle")}}.

![The tiltX angle of a pointer compared to the tiltY angle](tilt_x_y_angles.svg)

برای تصویرسازی بیشتر دربارهٔ این ویژگی، به [شکل ۲ در مشخصات](https://w3c.github.io/pointerevents/#dom-pointerevent-tiltx) مراجعه کنید.

## مقدار

زاویه برحسب درجه بین صفحهٔ Y-Z اشاره‌گر (قلم) و صفحهٔ نمایش. محدودهٔ مقادیر از `-90` تا `90` به‌صورت شامل است؛ مقدار مثبت به معنای کج‌شدن به راست است. برای دستگاه‌هایی که از این ویژگی پشتیبانی نمی‌کنند، مقدار `0` است.

## مثال‌ها

این مثال دسترسی ساده به ویژگی‌های `tiltX` و {{domxref("PointerEvent.tiltY","tiltY")}} را نشان می‌دهد.

```js
someElement.addEventListener("pointerdown", (event) => {
  processTilt(event.tiltX, event.tiltY);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("PointerEvent.tiltY")}}
- {{domxref("PointerEvent.altitudeAngle")}}
- {{domxref("PointerEvent.azimuthAngle")}}