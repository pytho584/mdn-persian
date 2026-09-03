---
title: "PointerEvent: azimuthAngle property"
---

---
title: "PointerEvent: azimuthAngle property"
short-title: azimuthAngle
slug: Web/API/PointerEvent/azimuthAngle
page-type: web-api-instance-property
browser-compat: api.PointerEvent.azimuthAngle
---

{{ APIRef("Pointer Events") }}

ویژگی فقط‌خواندنیِ **`azimuthAngle`** از رابط {{domxref("PointerEvent")}} نمایانگر زاویهٔ بین صفحهٔ Y-Z و صفحه‌ای است که هم محورِ مبدل (نشانگر یا قلم) و هم محور Y را در بر می‌گیرد.

بسته به سخت‌افزار و پلتفرمِ خاص، عامل‌های کاربر به احتمال زیاد تنها یکی از مجموعه‌های مقادیرِ جهت‌گیریِ مبدل را نسبت به صفحهٔ نمایش دریافت می‌کنند: یا {{domxref("PointerEvent.tiltX", "tiltX")}} و {{domxref("PointerEvent.tiltY", "tiltY")}}، یا {{domxref("PointerEvent.altitudeAngle", "altitudeAngle")}} و `azimuthAngle`.

![The azimuth angle of a pointer compared to the altitude angle](azimuth_altitude_angles.svg)

برای تصویرسازی بیشتر از این ویژگی، به [شکل ۵ در مشخصات](https://w3c.github.io/pointerevents/#figure_azimuthAngle) مراجعه کنید.

## مقدار

زاویه‌ای بر حسب رادیان بین `0` و `2π`؛ مقدار `0` حالتی را نشان می‌دهد که سرِ مبدل در صفحهٔ X-Y به سمت مقادیرِ فزایندهٔ X اشاره می‌کند (اگر از بالا مستقیم به پایین نگاه کنید، به سمت «ساعت ۳» است). این زاویه با حرکت در جهت عقربه‌های ساعت به‌تدریج افزایش می‌یابد (`π/2` در «ساعت ۶»، `π` در «ساعت ۹»، `3π/2` در «ساعت ۱۲»).

هنگامی که مبدل عمود بر سطح باشد ({{domxref("PointerEvent.altitudeAngle", "altitudeAngle")}} برابر `π/2`)، مقدار این ویژگی `0` است. برای سخت‌افزارها و پلتفرم‌هایی که شیب یا زاویه را گزارش نمی‌کنند نیز مقدار `0` است.

## مثال

```js
someElement.addEventListener("pointerdown", (event) => {
  process_angles(event.altitudeAngle, event.azimuthAngle);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{ domxref("PointerEvent.altitudeAngle") }}
- {{ domxref("PointerEvent.tiltX") }}
- {{ domxref("PointerEvent.tiltY") }}
- {{ domxref("Touch.azimuthAngle") }}