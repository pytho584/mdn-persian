---
title: "Gamepad: displayId property"
short-title: displayId
slug: Web/API/Gamepad/displayId
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.Gamepad.displayId
---

{{APIRef("WebVR API")}}{{Deprecated_Header}}{{Non-standard_Header}}

ویژگی فقط‌خواندنی **`displayId`** از رابط {{domxref("Gamepad")}} مقدار {{domxref("VRDisplay.displayId")}} از {{domxref("VRDisplay")}} مرتبط را برمی‌گرداند — یعنی همان `VRDisplay` که گیم‌پد صحنهٔ نمایش‌داده‌شدهٔ آن را کنترل می‌کند.

یک گیم‌پد با یک {{domxref("VRDisplay")}} مرتبط در نظر گرفته می‌شود اگر ژست (pose) گزارش‌شده توسط آن در همان فضای ژست نمایشگر باشد؛ به {{domxref("VRDisplay.getPose()")}} مراجعه کنید.

> [!NOTE]
> این ویژگی بخشی از [WebVR API](https://immersive-web.github.io/webvr/spec/1.1/#gamepad-getvrdisplays-attribute) قدیمی بود. این ویژگی توسط [WebXR Gamepads Module](https://immersive-web.github.io/webxr-gamepads-module/) جایگزین شده است.
>
> هیچ جایگزین مستقیمی برای این ویژگی وجود ندارد. شیء {{domxref("Gamepad")}} مرتبط با یک {{domxref("XRInputSource")}} را می‌توان با استفاده از ویژگی {{domxref("XRInputSource.gamepad")}} به دست آورد.

## مقدار

یک عدد که {{domxref("VRDisplay.displayId")}} مرتبط را نشان می‌دهد. اگر عدد ۰ باشد، گیم‌پد با هیچ نمایشگر VR مرتبط نیست.

## مثال‌ها

```js
window.addEventListener("gamepadconnected", (e) => {
  if (!e.gamepad.displayId) {
    console.log("Gamepad connected");
  } else {
    console.log(
      `Gamepad connected, associated with VR display ${e.gamepad.displayId}`,
    );
  }
});
```

## مشخصات

این ویژگی بخشی از [WebVR API](https://immersive-web.github.io/webvr/spec/1.1/#gamepad-getvrdisplays-attribute) قدیمی بود که توسط [WebXR Gamepads Module](https://immersive-web.github.io/webxr-gamepads-module/) جایگزین شده است. دیگر در مسیر تبدیل شدن به یک استاندارد قرار ندارد.

تا زمانی که همهٔ مرورگرها [WebXR APIs](/en-US/docs/Web/API/WebXR_Device_API/Fundamentals) جدید را پیاده‌سازی نکرده‌اند، توصیه می‌شود برای توسعهٔ برنامه‌های WebXR که در همهٔ مرورگرها کار می‌کنند، به چارچوب‌هایی مانند [A-Frame](https://aframe.io/)، [Babylon.js](https://www.babylonjs.com/) یا [Three.js](https://threejs.org/) یا یک [polyfill](https://github.com/immersive-web/webxr-polyfill) تکیه کنید. برای اطلاعات بیشتر، راهنمای [انتقال از WebVR به WebXR در متا](https://developers.meta.com/horizon/documentation/web/port-vr-xr/) را مطالعه کنید.

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [WebVR API](/en-US/docs/Web/API/WebVR_API)