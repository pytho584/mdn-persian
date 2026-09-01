---
title: "Gamepad: axes property"
short-title: axes
slug: Web/API/Gamepad/axes
page-type: web-api-instance-property
browser-compat: api.Gamepad.axes
---

{{APIRef("Gamepad API")}}

ویژگی **`Gamepad.axes`** در رابط {{domxref("Gamepad")}} آرایه‌ای را برمی‌گرداند که کنترل‌های دارای محور روی دستگاه را نشان می‌دهد (برای مثال، استیک‌های آنالوگ).

هر عضو این آرایه یک عدد ممیز شناور در بازهٔ ۱.۰- تا ۱.۰ است که موقعیت محور را از کمترین مقدار (۱.۰-) تا بیشترین مقدار (۱.۰) نشان می‌دهد.

## مقدار

آرایه‌ای از اعداد.

## مثال‌ها

```js
function gameLoop() {
  const [gp] = navigator.getGamepads();

  let a = 0;
  let b = 0;
  if (gp.axes[0] !== 0) {
    b -= gp.axes[0];
  } else if (gp.axes[1] !== 0) {
    a += gp.axes[1];
  } else if (gp.axes[2] !== 0) {
    b += gp.axes[2];
  } else if (gp.axes[3] !== 0) {
    a -= gp.axes[3];
  }

  ball.style.left = `${a * 2}px`;
  ball.style.top = `${b * 2}px`;

  const start = requestAnimationFrame(gameLoop);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## جستارهای وابسته

[استفاده از Gamepad API](/en-US/docs/Web/API/Gamepad_API/Using_the_Gamepad_API)