---
title: "GamepadButton: pressed property"
short-title: pressed
slug: Web/API/GamepadButton/pressed
page-type: web-api-instance-property
browser-compat: api.GamepadButton.pressed
---

{{APIRef("Gamepad API")}}{{SecureContext_Header}}

ویژگی **`GamepadButton.pressed`** از رابط {{domxref("GamepadButton")}} یک مقدار `boolean` برمی‌گرداند که نشان می‌دهد دکمه در حال حاظر فشرده شده است (`true`) یا خیر (`false`).

## مثال‌ها

```js
let gp = navigator.getGamepads()[0]; // دریافت اولین شیء gamepad

if (gp.buttons[0].pressed) {
  // واکنش به فشرده شدن دکمه
}
```

## مقدار

یک مقدار بولی.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Gamepad API](/en-US/docs/Web/API/Gamepad_API/Using_the_Gamepad_API)