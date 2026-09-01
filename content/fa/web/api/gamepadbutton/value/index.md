---
title: "GamepadButton: value property"
short-title: value
slug: Web/API/GamepadButton/value
page-type: web-api-instance-property
browser-compat: api.GamepadButton.value
---

{{APIRef("Gamepad API")}}{{SecureContext_Header}}

ویژگی **`GamepadButton.value`** از رابط {{domxref("GamepadButton")}} یک مقدار double برمی‌گرداند که برای نمایش وضعیت کنونی دکمه‌های آنالوگ در بسیاری از گیم‌پدهای مدرن، مانند تریگرها، استفاده می‌شود.

مقادیر در محدودهٔ `0.0` تا `1.0` نرمال‌سازی شده‌اند؛ به‌طوری که `0.0` نشان‌دهندهٔ دکمه‌ای است که فشرده نشده و `1.0` نشان‌دهندهٔ دکمه‌ای است که کاملاً فشرده شده است.

## Examples

```js
let gp = navigator.getGamepads()[0];

if (gp.buttons[0].value > 0) {
  // respond to analog button being pressed in
}
```

## Value

یک double.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

[Using the Gamepad API](/en-US/docs/Web/API/Gamepad_API/Using_the_Gamepad_API)