---
title: "GamepadHapticActuator: effects property"
short-title: effects
slug: Web/API/GamepadHapticActuator/effects
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.GamepadHapticActuator.effects
---

{{APIRef("Gamepad API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`effects`** در رابط {{domxref("GamepadHapticActuator")}} آرایه‌ای از مقادیر شمارشی برمی‌گرداند که نشان‌دهندهٔ جلوه‌های لمسی مختلفی است که عملگر (actuator) از آن‌ها پشتیبانی می‌کند.

## مقدار

آرایه‌ای که جلوه‌های لمسی پشتیبانی‌شده را نشان می‌دهد. مقادیر احتمالی شامل موارد زیر است:

- `"dual-rumble"`
  - : یک جلوهٔ لرزشی موقعیتی ایجادشده توسط دو موتور لرزشی در هر دستهٔ کنترلر که می‌توانند به‌طور مستقل به لرزش درآیند.
- `"trigger-rumble"`
  - : جلوه‌های لرزشی موضعی روی سطح دکمه‌های ماشهٔ کنترلر که توسط موتورهای لرزشی واقع در هر دکمه ایجاد می‌شوند. این دکمه‌ها معمولاً به شکل ماشه‌های فنری هستند.

> [!NOTE]
> اگر جلوه‌ای که مشخص است توسط سخت‌افزار پشتیبانی می‌شود در فهرست نباشد، احتمالاً مرورگر از پخش جلوه‌های آن نوع پشتیبانی نمی‌کند.

## نمونه‌ها

```js
const gamepad = navigator.getGamepads()[0];

// Logs "dual-rumble" or "trigger-rumble"
console.log(gamepad.hapticActuators[0].effects[0]);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Gamepad API](/en-US/docs/Web/API/Gamepad_API)