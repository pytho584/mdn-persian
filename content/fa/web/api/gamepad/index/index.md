---
title: "Gamepad: index property"
short-title: index
slug: Web/API/Gamepad/index
page-type: web-api-instance-property
browser-compat: api.Gamepad.index
---

{{APIRef("Gamepad API")}}

ویژگی **`Gamepad.index`** از رابط {{domxref("Gamepad")}} یک عدد صحیح را برمی‌گرداند که به صورت خودکار افزایش می‌یابد تا برای هر دستگاه متصل به سیستم منحصربه‌فرد باشد.

می‌توان از این ویژگی برای تشخیص چند کنترلر استفاده کرد؛ یک گیم‌پد که قطع و دوباره وصل شود، همان اندیس قبلی را حفظ خواهد کرد.

## مقدار

یک {{jsxref("number")}}.

## نمونه‌ها

```js
window.addEventListener("gamepadconnected", () => {
  const gp = navigator.getGamepads()[0];
  gamepadInfo.textContent = `Gamepad connected at index ${gp.index}: ${gp.id}.`;
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

[Using the Gamepad API](/en-US/docs/Web/API/Gamepad_API/Using_the_Gamepad_API)