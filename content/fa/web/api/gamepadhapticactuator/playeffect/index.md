---
title: "GamepadHapticActuator: playEffect() method"
---

---
title: "GamepadHapticActuator: playEffect() method"
short-title: playEffect()
slug: Web/API/GamepadHapticActuator/playEffect
page-type: web-api-instance-method
browser-compat: api.GamepadHapticActuator.playEffect
---

{{APIRef("Gamepad API")}}

متد **`playEffect()`** در رابط {{domxref("GamepadHapticActuator")}} باعث می‌شود سخت‌افزار یک افکت لرزش مشخص را پخش کند.

## نحو

```js-nolint
playEffect(type, params)
```

### پارامترها

- `type`
  - : یک رشته (string) است که افکت مورد نظر را نشان می‌دهد. مقادیر ممکن عبارت‌اند از `"dual-rumble"` و `"trigger-rumble"`، و اثر آن‌ها بسته به نوع سخت‌افزار می‌تواند متفاوت باشد. برای جزئیات بیشتر درباره انواع افکت‌ها به {{domxref("GamepadHapticActuator.effects")}} مراجعه کنید.

- `params`
  - : یک شیء برای توصیف افکت لرزشی موردنظر.

    مقادیر مورد انتظار عبارت‌اند از:
    - `duration` {{optional_inline}}
      - : مدت‌زمان افکت به میلی‌ثانیه.
        پیش‌فرض: `0`.
    - `startDelay` {{optional_inline}}
      - : تأخیر (به میلی‌ثانیه) قبل از شروع افکت.
        پیش‌فرض: `0`.
    - `strongMagnitude` {{optional_inline}}
      - : شدت لرزش موتورهای لرزشی فرکانس پایین (قوی)، نرمال‌شده در بازه‌ی بین `0.0` و `1.0`.
        پیش‌فرض: `0.0`.
    - `weakMagnitude` {{optional_inline}}
      - : شدت لرزش موتورهای لرزشی فرکانس بالا (ضعیف)، نرمال‌شده در بازه‌ی بین `0.0` و `1.0`.
        پیش‌فرض: `0.0`.
    - `leftTrigger` (فقط برای افکت‌های `"trigger-rumble"` کاربرد دارد) {{optional_inline}}
      - : شدت لرزش ماشه‌ی جلویی پایین-چپ، نرمال‌شده در بازه‌ی بین `0.0` و `1.0`.
        پیش‌فرض: `0.0`.
    - `rightTrigger` (فقط برای افکت‌های `"trigger-rumble"` کاربرد دارد) {{optional_inline}}
      - : شدت لرزش ماشه‌ی جلویی پایین-راست، نرمال‌شده در بازه‌ی بین `0.0` و `1.0`.
        پیش‌فرض: `0.0`.

> [!NOTE]
> یک فراخوانی جدید از `playEffect()` فراخوانی قبلی که هنوز در جریان است را لغو می‌کند.

### مقدار بازگشتی

یک Promise که در صورت تکمیل موفقیت‌آمیز افکت با مقدار `"complete"` resolve می‌شود، و در صورت توقف یا جایگزینی افکت فعلی با افکتی دیگر، با مقدار `"preempted"` resolve می‌شود.

این Promise ممکن است با انواع استثناهای زیر reject شود:

- `InvalidStateError` {{domxref("DOMException")}}
  - : سند فعلی فعال نیست یا پنهان است.
- `NotSupportedError` {{domxref("DOMException")}}
  - : نوع (`type`) درخواستی توسط actuator گیمپد فعلی پشتیبانی نمی‌شود.
- `TypeError` {{domxref("DOMException")}}
  - : نوع (`type`) درخواستی یک نوع افکت معتبر نیست.

## مثال‌ها

```js
const gamepad = navigator.getGamepads()[0];

gamepad.vibrationActuator
  .playEffect("dual-rumble", {
    startDelay: 0,
    duration: 200,
    weakMagnitude: 1.0,
    strongMagnitude: 1.0,
  })
  .then((result) => console.log(result));
// Should log "complete" if effect successfully runs
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Gamepad API](/en-US/docs/Web/API/Gamepad_API)