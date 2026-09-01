---
title: "GamepadHapticActuator: type property"
short-title: type
slug: Web/API/GamepadHapticActuator/type
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.GamepadHapticActuator.type
---

{{APIRef("Gamepad API")}}{{deprecated_header}}{{non-standard_header}}

ویژگی فقط‌خواندنی **`type`** در رابط {{domxref("GamepadHapticActuator")}} یک مقدار شمارشی را برمی‌گرداند که نوع سخت‌افزار لمسی (هاپتیک) را نشان می‌دهد.

این ویژگی منسوخ شده است: برای تشخیص پشتیبانی از افکت‌ها، از {{domxref("GamepadHapticActuator.effects")}} استفاده کنید.

## مقدار

یک مقدار شمارشی که نوع سخت‌افزار لمسی را نشان می‌دهد. انواع موجود در حال حاضر عبارتند از:

- `"vibration"`
  - : سخت‌افزار لرزش ساده که جلوه‌ای لرزشی ایجاد می‌کند.
- `"dual-rumble"`
  - : یک کنترلر با یک موتور لرزش در هر دسته. هر موتور می‌تواند به‌طور مستقل بلرزد تا جلوه‌های لرزشی موقعیت‌محور ایجاد کند.

## مثال‌ها

```js
const gamepad = navigator.getGamepads()[0];

// "vibration" یا "dual-rumble" را در کنسول ثبت می‌کند
console.log(gamepad.hapticActuators[0].type);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Gamepad API](/en-US/docs/Web/API/Gamepad_API)