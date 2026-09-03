---
title: PositionSensorVRDevice
slug: Web/API/PositionSensorVRDevice
page-type: web-api-interface
status:
  - deprecated
  - non-standard
browser-compat: api.PositionSensorVRDevice
---

{{APIRef("WebVR API")}}{{Deprecated_Header}}{{Non-standard_Header}}

رابط **`PositionSensorVRDevice`** در [WebVR API](/en-US/docs/Web/API/WebVR_API)، حسگر موقعیت سخت‌افزار واقعیت مجازی را نشان می‌دهد. از طریق متد {{domxref("PositionSensorVRDevice.getState()")}} می‌توانید به اطلاعاتی مانند موقعیت و جهت‌گیری فعلی حسگر نسبت به هدست دسترسی پیدا کنید.

## متدهای نمونه

- {{domxref("PositionSensorVRDevice.getState()")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : وضعیت فعلی حسگر موقعیت را برای فریم فعلی (مثلاً در داخل callback مربوط به {{domxref("window.requestAnimationFrame")}}) یا برای فریم قبلی، در قالب یک شیء {{domxref("VRPose")}} برمی‌گرداند. این متدی است که معمولاً ترجیح می‌دهید به‌جای `getImmediateState()` استفاده کنید.
- {{domxref("PositionSensorVRDevice.getImmediateState()")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : وضعیت لحظه‌ای فعلی حسگر موقعیت را برمی‌گرداند. این متد فقط برای موارد خاص و به‌ندرت باید استفاده شود؛ برای مثال، نمونه‌برداری از موقعیت لحظه‌ای حسگر جهت‌گیری دست — یا دست‌کم در آینده چنین کاربردی خواهد داشت.
- {{domxref("PositionSensorVRDevice.resetSensor()")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : _در صورت تمایل می‌توان از آن برای بازنشانی حسگر استفاده کرد و_ مقادیر موقعیت و جهت‌گیری به صفر بازگردانده می‌شوند.

## ویژگی‌های نمونه

_این رابط هیچ ویژگی خاص خود را تعریف نمی‌کند، اما ویژگی‌های رابط والد خود، {{domxref("VRDisplay")}} را به ارث می‌برد._

- {{domxref("VRDisplay.displayId")}} {{ReadOnlyInline}}
  - : شناسه مربوط به این `VRDevice` خاص را برمی‌گرداند. این شناسه نباید در راه‌اندازی مجدد مرورگر تغییر کند و امکان ذخیره‌سازی داده‌های پیکربندی بر اساس آن را فراهم می‌کند.
- {{domxref("VRDisplay.displayName")}} {{ReadOnlyInline}}
  - : یک نام قابل‌خواندن برای انسان که برای شناسایی `VRDevice` به کار می‌رود.

## مثال‌ها

مثال زیر از WebVR API برای به‌روزرسانی نمای یک صحنهٔ سادهٔ [2D canvas](/en-US/docs/Web/API/CanvasRenderingContext2D) در هر فریم از حلقهٔ {{domxref("window.requestAnimationFrame()","requestAnimationFrame")}} استفاده می‌کند.

```js
function setView() {
  const posState = gPositionSensor.getState();
  if (posState.hasPosition) {
    posPara.textContent = `Position: x${roundToTwo(
      posState.position.x,
    )} y${roundToTwo(posState.position.y)} z${roundToTwo(posState.position.z)}`;
    xPos = -posState.position.x * WIDTH * 2;
    yPos = posState.position.y * HEIGHT * 2;
    zPos = -posState.position.z > 0.01 ? -posState.position.z : 0.01;
  }

  if (posState.hasOrientation) {
    orientPara.textContent = `Orientation: x${roundToTwo(
      posState.orientation.x,
    )} y${roundToTwo(posState.orientation.y)} z${roundToTwo(
      posState.orientation.z,
    )}`;
    xOrient = posState.orientation.x * WIDTH;
    yOrient = -posState.orientation.y * HEIGHT * 2;
    zOrient = posState.orientation.z * 180;
  }
}
```

در اینجا یک شیء {{domxref("VRPose")}} را با استفاده از {{domxref("PositionSensorVRDevice.getState()")}} دریافت کرده و آن را در `posState` ذخیره می‌کنیم. سپس با استفاده از {{domxref("VRPose.position")}} و {{domxref("VRPose.orientation")}} بررسی می‌کنیم که اطلاعات موقعیت و جهت‌گیری در فریم فعلی وجود دارد. این دو اگر مثلاً هدست خاموش باشد یا به سمت حسگر موقعیت نشانه نرفته باشد، `null` برمی‌گردانند که می‌تواند باعث خطا شود.

سپس مقادیر موقعیت و جهت‌گیری x، y و z را برای اطلاع‌رسانی خروجی می‌گیریم و از آن‌ها برای به‌روزرسانی متغیرهای `xPos`، `yPos`، `zPos`، `xOrient`، `yOrient` و `zOrient` استفاده می‌کنیم. این متغیرها در هر فریم برای به‌روزرسانی رندر صحنه به کار می‌روند.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebVR API](/en-US/docs/Web/API/WebVR_API)