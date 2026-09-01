---
title: DOMPoint
slug: Web/API/DOMPoint
page-type: web-api-interface
browser-compat: api.DOMPoint
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

یک شیء **`DOMPoint`** یک نقطه دوبعدی یا سه‌بعدی را در یک دستگاه مختصات نشان می‌دهد؛ این شیء شامل مقادیری برای مختصات در حداکثر سه بعد، به همراه یک مقدار پرسپکتیو اختیاری است. `DOMPoint` بر پایه {{domxref("DOMPointReadOnly")}} ساخته شده است اما اجازه می‌دهد مقادیر ویژگی‌های آن تغییر کنند.

به طور کلی، مؤلفه `x` مثبت نشان‌دهنده موقعیتی در سمت راست مبدأ، مؤلفه `y` مثبت به سمت پایین از مبدأ، و مؤلفه `z` مثبت به سمت بیرون از صفحه (به عبارت دیگر، به سمت کاربر) گسترش می‌یابد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("DOMPoint.DOMPoint","DOMPoint()")}}
  - : یک شیء `DOMPoint` جدید با توجه به مقادیر صفر یا چند مؤلفه مختصاتی آن و به صورت اختیاری مقدار پرسپکتیو `w` ایجاد و برمی‌گرداند. همچنین می‌توانید با فراخوانی متد استاتیک {{domxref("DOMPoint.fromPoint_static", "DOMPoint.fromPoint()")}}، از یک `DOMPoint` یا `DOMPointReadOnly` موجود یا یک شیء برای ایجاد یک نقطه جدید استفاده کنید.

## ویژگی‌های نمونه

_`DOMPoint` ممکن است ویژگی‌هایی را نیز از والد خود، {{domxref("DOMPointReadOnly")}}، به ارث ببرد._

- {{domxref("DOMPoint.x")}}
  - : مختصات `x` از `DOMPoint`.
- {{domxref("DOMPoint.y")}}
  - : مختصات `y` از `DOMPoint`.
- {{domxref("DOMPoint.z")}}
  - : مختصات `z` از `DOMPoint`.
- {{domxref("DOMPoint.w")}}
  - : مقدار پرسپکتیو از `DOMPoint`.

## روش‌های نمونه

_`DOMPoint` روش‌های نمونه را از والد خود، {{domxref("DOMPointReadOnly")}}، به ارث می‌برد._

## روش‌های استاتیک

_`DOMPoint` ممکن است روش‌های استاتیک را نیز از والد خود، {{domxref("DOMPointReadOnly")}}، به ارث ببرد._

- {{domxref("DOMPoint/fromPoint_static", "DOMPoint.fromPoint()")}}
  - : یک شیء `DOMPoint` قابل تغییر جدید با توجه به یک نقطه موجود (یا یک شیء حاوی ویژگی‌های منطبق) ایجاد می‌کند که مقادیر ویژگی‌های آن را فراهم می‌کند.

## مثال‌ها

در [WebXR Device API](/en-US/docs/Web/API/WebXR_Device_API)، مقادیر `DOMPointReadOnly` موقعیت‌ها و جهت‌گیری‌ها را نشان می‌دهند. در قطعه کد زیر، حالت دستگاه XR (مانند هدست واقعیت مجازی یا تلفن دارای قابلیت واقعیت افزوده) را می‌توان با فراخوانی {{domxref("XRFrame.getViewerPose()")}} در طول یک فریم انیمیشن {{domxref("XRSession")}} بازیابی کرد و سپس به ویژگی {{domxref("XRPose.transform","transform")}} از {{domxref("XRPose")}} حاصله دسترسی یافت که شامل دو ویژگی `DOMPointReadOnly` است: {{domxref("XRRigidTransform.position","position")}} به عنوان یک بردار و {{domxref("XRRigidTransform.orientation","orientation")}} به عنوان یک چهارتایی.

```js
function onXRFrame(time, xrFrame) {
  let viewerPose = xrFrame.getViewerPose(xrReferenceSpace);

  if (viewerPose) {
    let position = viewerPose.transform.position;
    let orientation = viewerPose.transform.orientation;

    console.log(
      `XR Viewer Position: {x: ${roundToTwo(position.x)}, y: ${roundToTwo(
        position.y,
      )}, z: ${roundToTwo(position.z)}`,
    );

    console.log(
      `XR Viewer Orientation: {x: ${roundToTwo(orientation.x)}, y: ${roundToTwo(
        orientation.y,
      )}, z: ${roundToTwo(orientation.z)}, w: ${roundToTwo(orientation.w)}`,
    );
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMRect")}}
- {{domxref("DOMMatrix")}}