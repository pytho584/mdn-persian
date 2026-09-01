---
title: "Gamepad: vibrationActuator property"
short-title: vibrationActuator
slug: Web/API/Gamepad/vibrationActuator
page-type: web-api-instance-property
browser-compat: api.Gamepad.vibrationActuator
---

{{APIRef("Gamepad")}}

ویژگی فقط‌خواندنی **`vibrationActuator`** از رابط {{domxref("Gamepad")}} یک شیء {{domxref("GamepadHapticActuator")}} را برمی‌گرداند که نشان‌دهنده سخت‌افزار بازخورد لمسی (haptic feedback) موجود در کنترلر است.

> [!NOTE]
> پشتیبانی از این ویژگی ممکن است در ترکیب‌های مختلف پلتفرم‌ها و کنترلرها متفاوت باشد. حتی اگر کنترلر از بازخورد لمسی پشتیبانی کند، ممکن است پلتفرم از آن پشتیبانی نکند.

## مقدار

یک شیء {{domxref("GamepadHapticActuator")}}.

## مثال‌ها

```js
const gamepad = navigator.getGamepads()[0];

gamepad.vibrationActuator.playEffect("dual-rumble", {
  startDelay: 0,
  duration: 200,
  weakMagnitude: 1.0,
  strongMagnitude: 1.0,
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Gamepad API](/en-US/docs/Web/API/Gamepad_API)