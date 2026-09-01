---
title: GamepadButton
slug: Web/API/GamepadButton
page-type: web-api-interface
browser-compat: api.GamepadButton
---

{{APIRef("Gamepad API")}}

رابط **`GamepadButton`** یک دکمهٔ مجزای یک گیم‌پد یا کنترل‌کنندهٔ دیگر را تعریف می‌کند و امکان دسترسی به وضعیت فعلی انواع مختلف دکمه‌های موجود روی دستگاه کنترل را فراهم می‌آورد.

یک شیء `GamepadButton` با پرس‌وجوی هر مقدار از آرایه‌ای که توسط ویژگی `buttons` رابط {{domxref("Gamepad")}} بازگردانده می‌شود، به دست می‌آید.

## ویژگی‌های نمونه

- {{domxref("GamepadButton.pressed")}} {{ReadOnlyInline}}
  - : یک مقدار بولی که نشان می‌دهد دکمه در حال حاضر فشرده شده است (`true`) یا فشرده نشده است (`false`).
- {{domxref("GamepadButton.touched")}} {{ReadOnlyInline}}
  - : یک مقدار بولی که نشان می‌دهد دکمه در حال حاضر لمس شده است (`true`) یا لمس نشده است (`false`).
- {{domxref("GamepadButton.value")}} {{ReadOnlyInline}}
  - : یک مقدار اعشاری که برای نمایش وضعیت فعلی دکمه‌های آنالوگ، مانند ماشه‌های بسیاری از گیم‌پدهای مدرن، استفاده می‌شود. مقادیر در بازهٔ ۰٫۰ تا ۱٫۰ نرمال‌سازی شده‌اند، که ۰٫۰ نشان‌دهندهٔ دکمه‌ای فشرده‌نشده و ۱٫۰ نشان‌دهندهٔ دکمه‌ای کاملاً فشرده‌شده است.

## مثال

مقادیر دکمه‌ها در مثال زیر به عنوان یک آرایه از اشیاء `GamepadButton` ذخیره شده‌اند. این مثال ساده بررسی می‌کند که آیا {{domxref("GamepadButton.value")}} یک دکمه بزرگ‌تر از `0` است یا اینکه ویژگی {{domxref("GamepadButton.pressed")}} نشان می‌دهد دکمه فشرده شده است.

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

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

[استفاده از رابط Gamepad API](/en-US/docs/Web/API/Gamepad_API/Using_the_Gamepad_API)