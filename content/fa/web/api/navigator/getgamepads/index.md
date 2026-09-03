---
title: "Navigator: getGamepads() method"
short-title: getGamepads()
slug: Web/API/Navigator/getGamepads
page-type: web-api-instance-method
browser-compat: api.Navigator.getGamepads
---

{{APIRef("Gamepad API")}}

متد **`Navigator.getGamepads()`** یک آرایه از اشیاء {{domxref("Gamepad")}} برمی‌گرداند، یکی برای هر گیم‌پدی که به دستگاه متصل است.

اگر در طول یک جلسه یک گیم‌پد از دستگاه جدا شود، عناصر آرایه ممکن است `null` باشند تا گیم‌پدهای باقی‌مانده همان اندیس خود را حفظ کنند.

## نحو

```js-nolint
getGamepads()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک {{jsxref("Array")}} از اشیاء {{domxref("Gamepad")}} که ممکن است خالی باشد.

### استثناها

- `SecurityError` {{domxref("DOMException")}}
  - : استفاده از این ویژگی توسط یک [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) مسدود شده است.

## نمونه‌ها

```js
window.addEventListener("gamepadconnected", (e) => {
  const gp = navigator.getGamepads()[e.gamepad.index];
  console.log(
    `Gamepad connected at index ${gp.index}: ${gp.id} with ${gp.buttons.length} buttons, ${gp.axes.length} axes.`,
  );
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Gamepad API](/en-US/docs/Web/API/Gamepad_API/Using_the_Gamepad_API)
- [Gamepad API](/en-US/docs/Web/API/Gamepad_API)