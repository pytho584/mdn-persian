---
title: "Navigator: getVRDisplays() method"
short-title: getVRDisplays()
slug: Web/API/Navigator/getVRDisplays
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.Navigator.getVRDisplays
---

{{APIRef("WebVR API")}}{{Deprecated_Header}}{{Non-standard_Header}}

متد **`getVRDisplays()`** در接口 {{domxref("Navigator")}} یک وعده (Promise) برمی‌گرداند که به آرایه‌ای از اشیاء {{domxref("VRDisplay")}} تبدیل می‌شود که نمایانگر هر نمایشگر VR متصل به رایانه هستند.

## Syntax

```js-nolint
getVRDisplays()
```

### Parameters

هیچ‌کدام.

### Return value

یک وعده که به آرایه‌ای از اشیاء {{domxref("VRDisplay")}} تبدیل می‌شود.

## Examples

برای کد نمونه، به [`VRDisplay`](/en-US/docs/Web/API/VRDisplay#examples) مراجعه کنید.

## Specifications

این متد بخشی از [WebVR API](https://immersive-web.github.io/webvr/spec/1.1/) قدیمی بود که توسط [WebXR Device API](https://immersive-web.github.io/webxr/) جایگزین شده است. دیگر در مسیر تبدیل شدن به یک استاندارد قرار ندارد.

تا زمانی که همه مرورگرها [WebXR APIهای](/en-US/docs/Web/API/WebXR_Device_API/Fundamentals) جدید را پیاده‌سازی نکرده‌اند، توصیه می‌شود برای توسعه برنامه‌های WebXR که در همه مرورگرها کار کنند، به چارچوب‌هایی مانند [A-Frame](https://aframe.io/)، [Babylon.js](https://www.babylonjs.com/) یا [Three.js](https://threejs.org/) یا یک [polyfill](https://github.com/immersive-web/webxr-polyfill) تکیه کنید. برای اطلاعات بیشتر، راهنمای [انتقال از WebVR به WebXR در Meta](https://developers.meta.com/horizon/documentation/web/port-vr-xr/) را مطالعه کنید.

## Browser compatibility

{{Compat}}

## See also

- [صفحه اصلی WebVR API](/en-US/docs/Web/API/WebVR_API)