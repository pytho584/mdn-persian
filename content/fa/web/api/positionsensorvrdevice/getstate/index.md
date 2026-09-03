---
title: "PositionSensorVRDevice: getState() method"
short-title: getState()
slug: Web/API/PositionSensorVRDevice/getState
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.PositionSensorVRDevice.getState
---

{{deprecated_header}}{{APIRef("WebVR API")}}{{Non-standard_header}}

متد **`getState()`** از رابط {{domxref("PositionSensorVRDevice")}} وضعیت کنونی حسگر موقعیت را برای فریم جاری (مثلاً در درون callback کنونی {{domxref("window.requestAnimationFrame")}}) یا برای فریم قبلی، در قالب یک شیء {{domxref("VRPose")}} برمی‌گرداند. این همان متدی است که معمولاً بهتر است به‌جای {{domxref("PositionSensorVRDevice.getImmediateState")}} استفاده کنید.

## سینتکس

```js-nolint
getState()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء {{domxref("VRPose")}}.

## مثال‌ها

مثال زیر از WebVR API استفاده می‌کند تا نمای یک صحنه ساده {{domxref("CanvasRenderingContext2D")}} را در هر فریم از یک حلقه {{domxref("window.requestAnimationFrame()","requestAnimationFrame")}} به‌روزرسانی کند.

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

در اینجا یک شیء {{domxref("VRPose")}} را با استفاده از `getState()` دریافت کرده و آن را در متغیر `posState` ذخیره می‌کنیم. سپس با استفاده از {{domxref("VRPose.position")}} و {{domxref("VRPose.orientation")}} بررسی می‌کنیم که اطلاعات موقعیت و جهت‌گیری در فریم جاری موجود باشد. این ویژگی‌ها اگر مثلاً نمایشگر سربند (هدست) خاموش باشد یا به سمت حسگر موقعیت نشانه نرفته باشد، مقدار `null` برمی‌گردانند و در صورت عدم بررسی، خطا ایجاد می‌شود.

سپس مقادیر موقعیت و جهت‌گیری در محورهای x، y و z را برای مقاصد اطلاعاتی نمایش می‌دهیم و از همین مقادیر برای به‌روزرسانی متغیرهای `xPos`، `yPos`، `zPos`، `xOrient`، `yOrient` و `zOrient` استفاده می‌کنیم؛ این متغیرها برای به‌روزرسانی رندر صحنه در هر فریم به کار می‌روند.

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebVR API](/en-US/docs/Web/API/WebVR_API)