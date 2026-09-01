---
title: DeviceOrientationEvent
slug: Web/API/DeviceOrientationEvent
page-type: web-api-interface
browser-compat: api.DeviceOrientationEvent
---

{{apiref("Device Orientation Events")}}{{securecontext_header}}

رابط **`DeviceOrientationEvent`** از {{domxref("Device Orientation Events", "رویدادهای جهت‌گیری دستگاه", "", "nocode")}} اطلاعات مربوط به جهت‌گیری فیزیکی دستگاه در حال اجرای صفحه وب را در اختیار توسعه‌دهندگان وب قرار می‌دهد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("DeviceOrientationEvent.DeviceOrientationEvent","DeviceOrientationEvent.DeviceOrientationEvent()")}}
  - : یک `DeviceOrientationEvent` جدید ایجاد می‌کند.

## روش‌های ایستا

- {{domxref("DeviceOrientationEvent.requestPermission_static", "DeviceOrientationEvent.requestPermission()")}}
  - : درخواست اجازه دسترسی به داده‌های جهت‌گیری دستگاه را از کاربر می‌کند. یک {{jsxref("Promise")}} برمی‌گرداند که با رشته `"granted"` یا `"denied"` حل می‌شود.

## ویژگی‌های نمونه

- {{domxref("DeviceOrientationEvent.absolute")}} {{ReadOnlyInline}}
  - : یک مقدار بولی که نشان می‌دهد آیا دستگاه داده‌های جهت‌گیری را به صورت مطلق ارائه می‌دهد یا نه.
- {{domxref("DeviceOrientationEvent.alpha")}} {{ReadOnlyInline}}
  - : عددی که چرخش دستگاه حول محور z را نشان می‌دهد و بر حسب درجه با مقادیری از ۰ (شامل) تا ۳۶۰ (غیرشامل) بیان می‌شود.
- {{domxref("DeviceOrientationEvent.beta")}} {{ReadOnlyInline}}
  - : عددی که چرخش دستگاه حول محور x را نشان می‌دهد و بر حسب درجه با مقادیری از ۱۸۰- (شامل) تا ۱۸۰ (غیرشامل) بیان می‌شود. این حرکت دستگاه از جلو به عقب را نشان می‌دهد.
- {{domxref("DeviceOrientationEvent.gamma")}} {{ReadOnlyInline}}
  - : عددی که چرخش دستگاه حول محور y را نشان می‌دهد و بر حسب درجه با مقادیری از ۹۰- (شامل) تا ۹۰ (غیرشامل) بیان می‌شود. این حرکت دستگاه از چپ به راست را نشان می‌دهد.
- `DeviceOrientationEvent.webkitCompassHeading` {{Non-Standard_Inline}} {{ReadOnlyInline}}
  - : عددی که تفاوت بین چرخش دستگاه حول محور z سیستم جهانی و جهت شمال را نشان می‌دهد و بر حسب درجه با مقادیری از ۰ تا ۳۶۰ بیان می‌شود.
- `DeviceOrientationEvent.webkitCompassAccuracy` {{Non-Standard_Inline}} {{ReadOnlyInline}}
  - : دقت قطبنما است، به این معنی که انحراف مثبت یا منفی است. معمولاً ۱۰ است.

## مثال

```js
window.addEventListener("deviceorientation", (event) => {
  console.log(`${event.alpha} : ${event.beta} : ${event.gamma}`);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("Device orientation events/Detecting device orientation", "تشخیص جهتگیری دستگاه", "", "nocode")}}
- {{domxref("Device orientation events/Orientation and motion data explained", "توضیح دادههای جهتگیری و حرکت", "", "nocode")}}
- {{domxref("DeviceMotionEvent")}}
- رویداد {{domxref("Window.devicemotion_event", "devicemotion")}}
- رویداد {{domxref("Window.deviceorientation_event", "deviceorientation")}}
- رویداد {{domxref("Window.deviceorientationabsolute_event", "deviceorientationabsolute")}}