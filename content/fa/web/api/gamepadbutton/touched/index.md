---
title: "GamepadButton: touched property"
short-title: touched
slug: Web/API/GamepadButton/touched
page-type: web-api-instance-property
browser-compat: api.GamepadButton.touched
---

{{APIRef("Gamepad API")}}{{SecureContext_Header}}

ویژگی **`touched`** از رابط {{domxref("GamepadButton")}} یک مقدار بولی برمی‌گرداند که نشان می‌دهد دکمه‌ای که قادر به تشخیص لمس است در حال حاضر لمس شده (`true`) یا نشده (`false`) است.

اگر دکمه قادر به تشخیص لمس نباشد اما بتواند مقدار آنالوگ ارائه دهد، این ویژگی `true` خواهد بود اگر مقدار بزرگ‌تر از `0` باشد، و در غیر این صورت `false`. اگر دکمه قادر به تشخیص لمس نباشد و فقط بتواند مقدار دیجیتال گزارش دهد، آنگاه باید ویژگی {{domxref("GamepadButton.pressed")}} را منعکس کند.

## مقدار

یک {{jsxref("Boolean")}}. اگر لمس شده باشد `true` است.

## نمونه‌ها

```js
let gp = navigator.getGamepads()[0]; // Get the first gamepad object

if (gp.buttons[0].touched) {
  // respond to button being touched
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از API گیم‌پد](/en-US/docs/Web/API/Gamepad_API/Using_the_Gamepad_API)