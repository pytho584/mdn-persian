---
title: "Gamepad: mapping property"
short-title: mapping
slug: Web/API/Gamepad/mapping
page-type: web-api-instance-property
browser-compat: api.Gamepad.mapping
---

{{APIRef("Gamepad API")}}

ویژگی **`Gamepad.mapping`** در رابط {{domxref("Gamepad")}} رشته‌ای برمی‌گرداند که نشان می‌دهد آیا مرورگر کنترل‌های دستگاه را به یک چیدمان شناخته‌شده نگاشت مجدد کرده است یا خیر.

چیدمان‌های شناخته‌شده‌ای که در حال حاضر پشتیبانی می‌شوند عبارتند از:

- «standard» برای [دسته استاندارد](https://w3c.github.io/gamepad/#remapping).
- «xr-standard» برای [دسته استاندارد XR](https://immersive-web.github.io/webxr-gamepads-module/#xr-standard-heading). همچنین به {{domxref("XRInputSource.gamepad")}} مراجعه کنید.

## نمونه‌ها

```js
let gp = navigator.getGamepads()[0];
console.log(gp.mapping);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

[استفاده از API دسته بازی](/en-US/docs/Web/API/Gamepad_API/Using_the_Gamepad_API)