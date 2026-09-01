---
title: "GamepadHapticActuator: pulse() method"
short-title: pulse()
slug: Web/API/GamepadHapticActuator/pulse
page-type: web-api-instance-method
browser-compat: api.GamepadHapticActuator.pulse
---

{{APIRef("Gamepad API")}}

متد **`pulse()`** از رابط {{domxref("GamepadHapticActuator")}} باعث می‌شود سخت‌افزار با شدت مشخصی برای مدت زمان معینی لرزش (pulse) ایجاد کند.

## نحو (Syntax)

```js-nolint
pulse(value, duration)
```

### پارامترها

- `value`
  - : یک عدد اعشاری (double) که شدت لرزش را مشخص می‌کند. این مقدار بسته به نوع سخت‌افزار می‌تواند متفاوت باشد، اما معمولاً مقداری بین ۰.۰ (بدون شدت) و ۱.۰ (حداکثر شدت) می‌گیرد.
- `duration`
  - : یک عدد اعشاری (double) که مدت زمان لرزش را بر حسب میلی‌ثانیه مشخص می‌کند.

> [!NOTE]
> تماس‌های مکرر با `pulse()` اگر هنوز در حال اجرا باشند، تماس‌های قبلی را لغو می‌کنند.

### مقدار بازگشتی

یک promise که زمانی که لرزش با موفقیت به پایان رسید، با مقدار `true` resolve می‌شود.

## مثال‌ها

```js
const gamepad = navigator.getGamepads()[0];

gamepad.hapticActuators[0].pulse(1.0, 200);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [Gamepad API](/en-US/docs/Web/API/Gamepad_API)