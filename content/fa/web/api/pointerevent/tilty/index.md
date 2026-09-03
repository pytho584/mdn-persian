---
title: "PointerEvent: tiltY property"
short-title: tiltY
slug: Web/API/PointerEvent/tiltY
page-type: web-api-instance-property
browser-compat: api.PointerEvent.tiltY
---

{{ APIRef("Pointer Events") }}

ویژگی فقطخواندنی **`tiltY`** در رابط {{domxref("PointerEvent")}}، زاویه (برحسب درجه) بین _صفحهٔ X-Z_ اشاره‌گر و صفحه‌نمایش است.
این ویژگی معمولاً فقط برای نوع اشاره‌گر قلم/استایلوس مفید است.

بسته به سخت‌افزار و پلتفرم خاص، عامل‌های کاربر به‌احتمال زیاد تنها یکی از مجموعه‌های مقادیر جهت‌گیری مبدل را نسبت به صفحهٔ نمایش دریافت می‌کنند: یا {{domxref("PointerEvent.tiltX", "tiltX")}} و `tiltY`، یا {{domxref("PointerEvent.altitudeAngle", "altitudeAngle")}} و {{domxref("PointerEvent.azimuthAngle", "azimuthAngle")}}.

![زاویهٔ tiltX یک اشاره‌گر در مقایسه با زاویهٔ tiltY](tilt_x_y_angles.svg)

برای تصویر تکمیلی از این ویژگی، [شکل ۳ در مشخصات](https://w3c.github.io/pointerevents/#dom-pointerevent-tilty) را ببینید.

## مقدار

زاویه برحسب درجه بین صفحهٔ X-Z اشاره‌گر (قلم) و صفحه‌نمایش.
بازهٔ مقادیر از `-90` تا `90` است (هر دو کران شامل می‌شوند)؛ در این بازه، مقدار مثبت به معنای کج‌شدن به سمت کاربر است.
برای دستگاه‌هایی که از این ویژگی پشتیبانی نمی‌کنند، مقدار `0` است.

## مثال‌ها

این مثال دسترسی ساده به ویژگی‌های {{domxref("PointerEvent.tiltX","tiltX")}} و `tiltY` را نشان می‌دهد.

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

- {{domxref("PointerEvent.tiltX")}}
- {{domxref("PointerEvent.altitudeAngle")}}
- {{domxref("PointerEvent.azimuthAngle")}}