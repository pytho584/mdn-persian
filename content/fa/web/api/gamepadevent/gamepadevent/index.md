---
title: "GamepadEvent: GamepadEvent() constructor"
---

---
title: "GamepadEvent: GamepadEvent() constructor"
short-title: GamepadEvent()
slug: Web/API/GamepadEvent/GamepadEvent
page-type: web-api-constructor
browser-compat: api.GamepadEvent.GamepadEvent
---

{{APIRef("Gamepad API")}}{{SecureContext_Header}}

سازندهٔ **`GamepadEvent()`** یک شیء جدید {{domxref("GamepadEvent")}} ایجاد می‌کند.

## سینتکس

```js-nolint
new GamepadEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای است با نام رویداد. این رشته به بزرگی و کوچکی حروف حساس است و مرورگرها آن را روی `gamepadconnected` یا `gamepaddisconnected` قرار می‌دهند.
- `options`
  - : شیئی که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `gamepad`
      - : یک شیء {{domxref("Gamepad")}} که گیم‌پد مرتبط با رویداد را توصیف می‌کند.

### مقدار بازگشتی

یک شیء جدید {{domxref("GamepadEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}