---
title: DeviceMotionEvent
slug: Web/API/DeviceMotionEvent
page-type: web-api-interface
browser-compat: api.DeviceMotionEvent
---

{{APIRef("Device Orientation Events")}}{{securecontext_header}}

رابط **`DeviceMotionEvent`** در {{domxref("Device Orientation Events", "", "", "nocode")}} اطلاعاتی دربارهٔ سرعت تغییرات موقعیت و جهت‌گیری دستگاه در اختیار توسعه‌دهندگان وب قرار می‌دهد.

> [!WARNING]
> در حال حاضر، فایرفاکس و کروم مختصات را به یک شکل پردازش نمی‌کنند. هنگام استفاده از آن‌ها به این نکته توجه کنید.

{{InheritanceDiagram}}

## سازنده

- {{domxref("DeviceMotionEvent.DeviceMotionEvent", "DeviceMotionEvent()")}}
  - : یک شیء `DeviceMotionEvent` جدید می‌سازد.

## روش‌های ایستا

- {{DOMxRef("DeviceMotionEvent.requestPermission_static", "DeviceMotionEvent.requestPermission()")}}
  - : اجازهٔ کاربر را برای دسترسی به داده‌های حرکتی دستگاه از سنسورهای شتاب‌سنج و ژیروسکوپ درخواست می‌کند. یک {{jsxref("Promise")}} برمی‌گرداند که با رشته‌ای شامل `"granted"` یا `"denied"` حل می‌شود.

## ویژگی‌های نمونه

- {{DOMxRef("DeviceMotionEvent.acceleration")}} {{ReadOnlyInline}}
  - : شیئی که شتاب دستگاه را در سه محور X، Y و Z ارائه می‌دهد. شتاب بر حسب [m/s²](https://en.wikipedia.org/wiki/Meter_per_second_squared) بیان می‌شود.
- {{DOMxRef("DeviceMotionEvent.accelerationIncludingGravity")}} {{ReadOnlyInline}}
  - : شیئی که شتاب دستگاه را در سه محور X، Y و Z همراه با اثر گرانش ارائه می‌دهد. شتاب بر حسب [m/s²](https://en.wikipedia.org/wiki/Meter_per_second_squared) بیان می‌شود.
- {{DOMxRef("DeviceMotionEvent.rotationRate")}} {{ReadOnlyInline}}
  - : شیئی که نرخ تغییر جهت‌گیری دستگاه را در سه محور جهت‌گیری آلفا، بتا و گاما ارائه می‌دهد. نرخ چرخش بر حسب درجه بر ثانیه بیان می‌شود.
- {{DOMxRef("DeviceMotionEvent.interval")}} {{ReadOnlyInline}}
  - : عددی که بازهٔ زمانی دریافت داده از دستگاه را بر حسب میلی‌ثانیه نشان می‌دهد.

## مثال

```js
window.addEventListener("devicemotion", (event) => {
  console.log(`${event.acceleration.x} m/s2`);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Device orientation events/Detecting device orientation", "Detecting device orientation", "", "nocode")}}
- {{domxref("Device orientation events/Orientation and motion data explained", "Orientation and motion data explained", "", "nocode")}}
- {{DOMxRef("DeviceOrientationEvent")}}
- {{DOMxRef("Window.deviceorientation_event", "deviceorientation")}} رویداد
- {{DOMxRef("Window.deviceorientationabsolute_event", "deviceorientationabsolute")}} رویداد
- {{DOMxRef("Window/devicemotion_event", "devicemotion")}} رویداد
- {{DOMxRef("Accelerometer")}}
- {{DOMxRef("LinearAccelerationSensor")}}