---
title: "Navigator: activeVRDisplays property"
short-title: activeVRDisplays
slug: Web/API/Navigator/activeVRDisplays
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.Navigator.activeVRDisplays
---

{{APIRef("WebVR API")}}{{SecureContext_Header}}{{Deprecated_Header}}{{Non-standard_Header}}

خاصیت فقط‌خواندنی **`activeVRDisplays`** از رابط {{domxref("Navigator")}} یک آرایه شامل تمام اشیاء {{domxref("VRDisplay")}} که در حال حاضر در حال نمایش هستند ({{domxref("VRDisplay.isPresenting")}} برابر با `true` است) برمی‌گرداند.

> [!NOTE]
> این ویژگی بخشی از [WebVR API](https://immersive-web.github.io/webvr/spec/1.1/) قدیمی بود. اکنون با [WebXR Device API](https://immersive-web.github.io/webxr/) جایگزین شده است.

## مقدار

یک آرایه از اشیاء {{domxref("VRDisplay")}}.

## مثال‌ها

```js
function showActive() {
  const displays = navigator.activeVRDisplays;
  for (const display of displays) {
    console.log(`Display ${display.displayId} is active.`);
  }
}
```

## مشخصات

این ویژگی بخشی از [WebVR API](https://immersive-web.github.io/webvr/spec/1.1/) قدیمی بود که توسط [WebXR Device API](https://immersive-web.github.io/webxr/) جایگزین شده است. این ویژگی دیگر در مسیر تبدیل شدن به یک استاندارد قرار ندارد.

تا زمانی که همه مرورگرها [WebXR APIs](/en-US/docs/Web/API/WebXR_Device_API/Fundamentals) جدید را پیاده‌سازی نکرده‌اند، توصیه می‌شود برای توسعه برنامه‌های WebXR که در همه مرورگرها کار کنند، از فریم‌ورک‌هایی مانند [A-Frame](https://aframe.io/)، [Babylon.js](https://www.babylonjs.com/) یا [Three.js](https://threejs.org/) یا یک [polyfill](https://github.com/immersive-web/webxr-polyfill) استفاده کنید. برای اطلاعات بیشتر، راهنمای [Meta's Porting from WebVR to WebXR](https://developers.meta.com/horizon/documentation/web/port-vr-xr/) را مطالعه کنید.

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebVR API](/en-US/docs/Web/API/WebVR_API)