---
title: GamepadEvent
slug: Web/API/GamepadEvent
page-type: web-api-interface
browser-compat: api.GamepadEvent
---

{{APIRef("Gamepad API")}}

رابط `GamepadEvent` در API گیم‌پد، شامل ارجاعاتی به گیم‌پدهای متصل به سیستم است. رویدادهای گیم‌پد یعنی {{domxref("Window.gamepadconnected_event", "gamepadconnected")}} و {{domxref("Window.gamepaddisconnected_event", "gamepaddisconnected")}} در پاسخ به این رابط فعال می‌شوند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("GamepadEvent.GamepadEvent","GamepadEvent()")}}
  - : یک شیء جدید از نوع `GamepadEvent` برمی‌گرداند.

## ویژگی‌های نمونه

- {{ domxref("GamepadEvent.gamepad") }} {{ReadOnlyInline}}
  - : یک شیء {{ domxref("Gamepad") }} برمی‌گرداند که دسترسی به داده‌های گیم‌پد مرتبط با رویداد فعال‌شده را فراهم می‌کند.

## مثال‌ها

فراخوانی ویژگی `gamepad` روی یک رویداد {{domxref("Window.gamepadconnected_event", "gamepadconnected")}} فعال‌شده:

```js
window.addEventListener("gamepadconnected", (e) => {
  console.log(
    "Gamepad connected at index %d: %s. %d buttons, %d axes.",
    e.gamepad.index,
    e.gamepad.id,
    e.gamepad.buttons.length,
    e.gamepad.axes.length,
  );
});
```

و روی یک رویداد {{domxref("Window.gamepaddisconnected_event", "gamepaddisconnected")}}:

```js
window.addEventListener("gamepaddisconnected", (e) => {
  console.log(
    "Gamepad disconnected from index %d: %s",
    e.gamepad.index,
    e.gamepad.id,
  );
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

[استفاده از API گیم‌پد](/en-US/docs/Web/API/Gamepad_API/Using_the_Gamepad_API)