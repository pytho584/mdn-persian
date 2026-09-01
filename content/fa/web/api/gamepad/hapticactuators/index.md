---
title: "Gamepad: hapticActuators property"
short-title: hapticActuators
slug: Web/API/Gamepad/hapticActuators
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Gamepad.hapticActuators
---

{{APIRef("Gamepad")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`hapticActuators`** از رابط {{domxref("Gamepad")}} آرایه‌ای شامل اشیاء {{domxref("GamepadHapticActuator")}} برمی‌گرداند که هر یک نمایانگر سخت‌افزار بازخورد لمسی (haptic) موجود بر روی کنترلر است.

## مقدار

آرایه‌ای شامل اشیاء {{domxref("GamepadHapticActuator")}}.

## مثال‌ها

```js
const gamepad = navigator.getGamepads()[0];

gamepad.hapticActuators[0].pulse(1.0, 200);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Gamepad API](/en-US/docs/Web/API/Gamepad_API)