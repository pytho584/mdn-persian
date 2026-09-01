---
title: "Gamepad: buttons property"
short-title: buttons
slug: Web/API/Gamepad/buttons
page-type: web-api-instance-property
browser-compat: api.Gamepad.buttons
---

{{APIRef("Gamepad API")}}

ویژگی **`buttons`** از رابط {{domxref("Gamepad")}} یک آرایه از اشیاء {{domxref("GamepadButton")}} را برمی‌گرداند که نشان‌دهنده دکمه‌های موجود روی دستگاه است.

هر ورودی در آرایه در صورت فشرده نبودن دکمه `0` و در صورت فشرده بودن مقداری غیر از صفر (معمولاً `1.0`) است.

## مقدار

یک آرایه از اشیاء {{domxref("GamepadButton")}}.

## مثال‌ها

بسته به نوع دکمه، باید به ویژگی‌های {{domxref("GamepadButton.value")}} یا {{domxref("GamepadButton.pressed")}} دسترسی داشته باشیم. این مثال از هر دو پشتیبانی می‌کند:

```js
function gameLoop() {
  const gp = navigator.getGamepads()[0];

  if (gp.buttons[0].value > 0 || gp.buttons[0].pressed) {
    b--;
  } else if (gp.buttons[1].value > 0 || gp.buttons[1].pressed) {
    a++;
  } else if (gp.buttons[2].value > 0 || gp.buttons[2].pressed) {
    b++;
  } else if (gp.buttons[3].value > 0 || gp.buttons[3].pressed) {
    a--;
  }

  ball.style.left = `${a * 2}px`; // ball is a UI widget
  ball.style.top = `${b * 2}px`;

  requestAnimationFrame(gameLoop);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

[استفاده از Gamepad API](/en-US/docs/Web/API/Gamepad_API/Using_the_Gamepad_API)