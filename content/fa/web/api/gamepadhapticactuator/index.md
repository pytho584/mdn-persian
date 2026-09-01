---
title: GamepadHapticActuator
slug: Web/API/GamepadHapticActuator
page-type: web-api-interface
browser-compat: api.GamepadHapticActuator
---

{{APIRef("Gamepad API")}}

رابط `GamepadHapticActuator` در [Gamepad API](/en-US/docs/Web/API/Gamepad_API) نمایانگر سخت‌افزاری درونِ کنترل‌کننده است که برای ارائه بازخورد لمسی به کاربر (در صورت موجود بودن) طراحی شده است؛ معمولاً این سخت‌افزار، سخت‌افزار لرزشی است.

این رابط از طریق ویژگی {{domxref("Gamepad.hapticActuators")}} در دسترس است.

## ویژگی‌های نمونه

- {{domxref("GamepadHapticActuator.effects")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک آرایه از مقادیرِ شمارشی را بازمی‌گرداند که نشان‌دهنده اثرات لمسی متفاوتی است که عملگر (actuator) از آن‌ها پشتیبانی می‌کند.
- {{domxref("GamepadHapticActuator.type")}} {{deprecated_inline}} {{ReadOnlyInline}} {{non-standard_inline}}
  - : یک مقدار شمارشی را بازمی‌گرداند که نوع سخت‌افزار لمسی را نشان می‌دهد. این ویژگی منسوخ شده است؛ برای تشخیص پشتیبانی از اثرات، از `GamepadHapticActuator.effects` استفاده کنید.

## متدهای نمونه

- {{domxref("GamepadHapticActuator.playEffect()")}} {{ReadOnlyInline}}
  - : باعث می‌شود سخت‌افزار یک اثر لرزشی مشخص را اجرا کند.
- {{domxref("GamepadHapticActuator.pulse()")}} {{ReadOnlyInline}}
  - : باعث می‌شود سخت‌افزار با شدت معیّن و برای مدت زمان مشخصی پالس (نبض) ایجاد کند.
- {{domxref("GamepadHapticActuator.reset()")}} {{ReadOnlyInline}}
  - : اجرای یک اثر لرزشی فعال توسط سخت‌افزار را متوقف می‌کند.

## مثال‌ها

```js
const gamepad = navigator.getGamepads()[0];

gamepad.hapticActuators[0].pulse(1.0, 200);

gamepad.vibrationActuator.playEffect("dual-rumble", {
  startDelay: 0,
  duration: 200,
  weakMagnitude: 1.0,
  strongMagnitude: 1.0,
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Gamepad API](/en-US/docs/Web/API/Gamepad_API)