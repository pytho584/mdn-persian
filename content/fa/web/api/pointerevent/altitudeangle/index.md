---
title: "PointerEvent: altitudeAngle property"
short-title: altitudeAngle
slug: Web/API/PointerEvent/altitudeAngle
page-type: web-api-instance-property
browser-compat: api.PointerEvent.altitudeAngle
---

{{ APIRef("Pointer Events") }}

ویژگی فقط‌خواندنی **`altitudeAngle`** از رابط {{domxref("PointerEvent")}}، زاویه بین محور یک مبدل (نشانگر یا قلم) و صفحه X-Y صفحه نمایش دستگاه را نشان می‌دهد. زاویه ارتفاع توصیف می‌کند که آیا مبدل عمود بر صفحه نمایش است، موازی با آن است یا در زاویه‌ای بین این دو قرار دارد.

بسته به سخت‌افزار و پلتفرم خاص، عامل‌های کاربری احتمالاً تنها یک مجموعه از مقادیر را برای جهت‌گیری مبدل نسبت به صفحه نمایش دریافت می‌کنند — یا {{domxref("PointerEvent.tiltX", "tiltX")}} و {{domxref("PointerEvent.tiltY", "tiltY")}} یا `altitudeAngle` و {{domxref("PointerEvent.azimuthAngle", "azimuthAngle")}}.

![The azimuth angle of a pointer compared to the altitude angle](./azimuth_altitude_angles.svg)

برای تصویرسازی بیشتر این ویژگی، به [شکل ۴ در مشخصات](https://w3c.github.io/pointerevents/#figure_altitudeAngle) مراجعه کنید.

## مقدار

یک زاویه بر حسب رادیان بین `0` و `π/2` که در آن `0` نشان‌دهنده موازی با سطح دستگاه (صفحه X-Y) و `π/2` نشان‌دهنده عمود بر سطح است. مقدار پیش‌فرض `π/2` (عمود بر سطح) است که با [`altitudeAngle` در رویدادهای لمسی](https://w3c.github.io/touch-events/#dom-touch-altitudeangle) که مقدار پیش‌فرض آن `0` (موازی با سطح) است، متفاوت است. برای سخت‌افزارها و پلتفرم‌هایی که شیب یا زاویه را گزارش نمی‌دهند، مقدار `π/2` است.

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

- {{ domxref("PointerEvent.azimuthAngle") }}
- {{ domxref("PointerEvent.tiltX") }}
- {{ domxref("PointerEvent.tiltY") }}
- {{ domxref("Touch.altitudeAngle") }}