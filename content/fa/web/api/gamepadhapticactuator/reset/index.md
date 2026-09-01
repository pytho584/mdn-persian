---
title: "GamepadHapticActuator: reset() method"
short-title: reset()
slug: Web/API/GamepadHapticActuator/reset
page-type: web-api-instance-method
browser-compat: api.GamepadHapticActuator.reset
---

{{APIRef("Gamepad API")}}

متد **`reset()`** از رابط {{domxref("GamepadHapticActuator")}}، سخت‌افزار را از ادامه‌ی پخش یک افکت لرزش فعال بازمی‌دارد.

## Syntax

```js-nolint
reset()
```

### Parameters

هیچ.

### Return value

یک وعده (Promise) که در صورت موفقیت‌آمیز بودن بازنشانی افکت، با مقدار `"complete"` و در صورت توقف یا جایگزینی افکت توسط افکتی دیگر، با مقدار `"preempted"` حل می‌شود.

وعده ممکن است با انواع استثناهای زیر رد شود:

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر سند جاری فعال یا پنهان نباشد، وعده با `InvalidStateError` رد می‌شود.

## Examples

```js
const gamepad = navigator.getGamepads()[0];

setTimeout(() => {
  gamepad.vibrationActuator.reset();
}, 150);

gamepad.vibrationActuator
  .playEffect("dual-rumble", {
    startDelay: 0,
    duration: 200,
    weakMagnitude: 1.0,
    strongMagnitude: 1.0,
  })
  .then((result) => console.log(result));
// Should log "preempted" because reset() will run before the effect ends
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Gamepad API](/en-US/docs/Web/API/Gamepad_API)