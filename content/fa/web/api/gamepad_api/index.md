---
title: "Gamepad API"
---
---
title: Gamepad API
slug: Web/API/Gamepad_API
page-type: web-api-overview
browser-compat: api.Gamepad
---

{{DefaultAPISidebar("Gamepad API")}}

**رابط Gamepad API** راهی است برای توسعه‌دهندگان تا بتوانند به سیگنال‌های دریافتی از گیم‌پدها و سایر کنترل‌کننده‌های بازی به روشی ساده و یکسان دسترسی پیدا کرده و به آن‌ها پاسخ دهند. این رابط شامل سه واسط (interface)، دو رویداد (event) و یک تابع تخصصی است که برای پاسخ به اتصال و قطع اتصال گیم‌پدها و همچنین دسترسی به سایر اطلاعات مربوط به خود گیم‌پدها و دکمه‌ها و کنترل‌هایی که در حال فشار داده شدن هستند، به کار می‌رود.

## واسط‌ها (Interfaces)

- [`Gamepad`](/en-US/docs/Web/API/Gamepad)
  - : نمایانگر یک گیم‌پد/کنترل‌کننده متصل به رایانه است.
- [`GamepadButton`](/en-US/docs/Web/API/GamepadButton)
  - : نمایانگر یک دکمه روی یکی از کنترل‌کننده‌های متصل است.
- [`GamepadEvent`](/en-US/docs/Web/API/GamepadEvent)
  - : شیء رویدادی که رویدادهای مرتبط با گیم‌پدها را نمایش می‌دهد.

### افزونه‌های آزمایشی Gamepad

- [`GamepadHapticActuator`](/en-US/docs/Web/API/GamepadHapticActuator)
  - : نمایانگر سخت‌افزاری در کنترل‌کننده است که برای ارائه بازخورد لمسی (haptic feedback) به کاربر طراحی شده است (در صورت وجود)، که معمولاً سخت‌افزار لرزش است.
- [`GamepadPose`](/en-US/docs/Web/API/GamepadPose)
  - : نمایانگر وضعیت (pose) یک کنترل‌کننده (به‌عنوان مثال موقعیت و جهت در فضای سه‌بعدی) در مورد یک کنترل‌کننده [WebVR](/en-US/docs/Web/API/WebVR_API) است. این واسط _برای_ استاندارد جدیدتر [WebXR](/en-US/docs/Web/API/WebXR_Device_API) استفاده نمی‌شود.

### افزونه‌های سایر واسط‌ها

#### Navigator

- {{domxref("Navigator.getGamepads()")}}
  - : یک افزونه به شیء {{domxref("Navigator")}} که آرایه‌ای از اشیاء {{domxref("Gamepad")}} را برمی‌گرداند، یکی برای هر گیم‌پد متصل.

#### رویدادهای Window

- {{domxref("Window.gamepadconnected_event", "gamepadconnected")}}
  - : رویدادی که هنگام اتصال یک گیم‌پد فعال می‌شود.
- {{domxref("Window.gamepaddisconnected_event", "gamepaddisconnected")}}
  - : رویدادی که هنگام قطع اتصال یک گیم‌پد فعال می‌شود.

## آموزش‌ها و راهنماها

- [استفاده از Gamepad API](/en-US/docs/Web/API/Gamepad_API/Using_the_Gamepad_API)
- [پیاده‌سازی کنترل‌ها با استفاده از Gamepad API](/en-US/docs/Games/Techniques/Controls_Gamepad_API)

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [The Gamepad API](https://hacks.mozilla.org/2013/12/the-gamepad-api/) نوشته Ted Mielczarek و Robert Nyman
- [صفحه دموی ساده API](https://luser.github.io/gamepadtest/) ([منبع](https://github.com/luser/gamepadtest))