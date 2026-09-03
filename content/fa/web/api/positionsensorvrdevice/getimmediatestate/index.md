---
title: "PositionSensorVRDevice: getImmediateState() method"
---

---
title: "PositionSensorVRDevice: getImmediateState() method"
short-title: getImmediateState()
slug: Web/API/PositionSensorVRDevice/getImmediateState
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.PositionSensorVRDevice.getImmediateState
---

{{deprecated_header}}{{APIRef("WebVR API")}}{{Non-standard_header}}

متد **`getImmediateState()`** از رابط {{domxref("VRDisplay")}} وضعیت لحظه‌ای فعلی حسگر موقعیت را برمی‌گرداند. این متد فقط برای استفاده‌های نادر و موارد خاص در نظر گرفته شده است؛ برای مثال نمونه‌برداری از موقعیت لحظه‌ای یک حسگر جهت دست — یا دست‌کم در آینده چنین کاربردی خواهد داشت.

برای بیشتر کاربردهای استاندارد، احتمالاً بهتر است از {{domxref("PositionSensorVRDevice.getState")}} استفاده کنید.

## Syntax

```js-nolint
getImmediateState()
```

### Parameters

هیچ.

### Return value

یک شیء {{domxref("VRPose")}}.

## Examples

دموی زیر از WebVR API برای به‌روزرسانی نمای یک صحنهٔ سادهٔ {{domxref("CanvasRenderingContext2D")}} در هر فریم از حلقهٔ {{domxref("window.requestAnimationFrame()","requestAnimationFrame")}} استفاده می‌کند. تابع اصلی که داده‌های نما را به‌روزرسانی می‌کند به این صورت است:

```js
function setView() {
  const posState = gPositionSensor.getImmediateState();
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

در اینجا ما یک شیء {{domxref("VRPose")}} را با استفاده از `getImmediateState()` دریافت کرده و در `posState` ذخیره می‌کنیم (دموی زندهٔ واقعی از `getState()` استفاده می‌کند، اما در حال حاضر هر دو به نظر کار یکسانی انجام می‌دهند.) سپس با استفاده از {{domxref("VRPose.position")}} و {{domxref("VRPose.orientation")}} بررسی می‌کنیم که اطلاعات موقعیت و جهت در فریم فعلی موجود باشند (اگر مثلاً هدست نمایشگر خاموش باشد یا رو به حسگر موقعیت نباشد، این ویژگی‌ها `null` برمی‌گردانند که می‌تواند باعث خطا شود.)

سپس مقادیر x، y و z موقعیت و جهت را برای اهداف اطلاعاتی خروجی می‌گیریم و از آن مقادیر برای به‌روزرسانی متغیرهای `xPos`، `yPos`، `zPos`، `xOrient`، `yOrient` و `zOrient` استفاده می‌کنیم که برای به‌روزرسانی رندر صحنه در هر فریم به کار می‌روند.

## Browser compatibility

{{Compat}}

## See also

- [WebVR API](/en-US/docs/Web/API/WebVR_API)