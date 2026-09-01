---
title: Gamepad
slug: Web/API/Gamepad
page-type: web-api-interface
browser-compat: api.Gamepad
---

{{APIRef("Gamepad API")}}

رابط `Gamepad` از [Gamepad API](/en-US/docs/Web/API/Gamepad_API) یک گیم‌پد یا کنترل‌کنندهٔ منفرد را تعریف می‌کند و امکان دسترسی به اطلاعاتی مانند فشردن دکمه‌ها، موقعیت محورها و شناسه (id) را فراهم می‌سازد.

یک شیء `Gamepad` می‌تواند به یکی از دو روش بازگردانده شود: از طریق ویژگی `gamepad` در رویدادهای {{domxref("Window.gamepadconnected_event", "gamepadconnected")}} و {{domxref("Window.gamepaddisconnected_event", "gamepaddisconnected")}}، یا با گرفتن هر جایگاهی از آرایه‌ای که توسط متد {{domxref("Navigator.getGamepads()")}} بازگردانده می‌شود.

> [!NOTE]
> پشتیبانی از ویژگی‌های گیم‌پد بسته به ترکیب‌های مختلف سیستم‌عامل‌ها و کنترل‌کننده‌ها متفاوت است. حتی اگر کنترل‌کننده از قابلیت خاصی (مثلاً بازخورد لمسی) پشتیبانی کند، ممکن است سیستم‌عامل از آن قابلیت برای آن کنترل‌کننده پشتیبانی نکند.

## ویژگی‌های نمونه

- {{domxref("Gamepad.axes")}} {{ReadOnlyInline}}
  - : آرایه‌ای که نشان‌دهندهٔ کنترل‌های دارای محور روی دستگاه است (مثلاً استیک‌های آنالوگ).
- {{domxref("Gamepad.buttons")}} {{ReadOnlyInline}}
  - : آرایه‌ای از اشیاء {{domxref("gamepadButton")}} که دکمه‌های موجود روی دستگاه را نشان می‌دهند.
- {{domxref("Gamepad.connected")}} {{ReadOnlyInline}}
  - : یک مقدار بولی که نشان می‌دهد آیا گیم‌پد همچنان به سیستم متصل است یا خیر.
- {{domxref("Gamepad.displayId")}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : مقدار {{domxref("VRDisplay.displayId")}} یک {{domxref("VRDisplay")}} مرتبط را برمی‌گرداند (در صورت وجود) — `VRDisplay` که گیم‌پد صحنهٔ نمایش‌داده‌شده توسط آن را کنترل می‌کند.
- {{domxref("Gamepad.hand")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک enum که تعیین می‌کند کنترل‌کننده در کدام دست گرفته شده است یا به احتمال زیاد گرفته خواهد شد.
- {{domxref("Gamepad.hapticActuators")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : آرایه‌ای شامل اشیاء {{domxref("GamepadHapticActuator")}} که هر یک نشان‌دهندهٔ سخت‌افزار بازخورد لمسی موجود روی کنترل‌کننده است.
- {{domxref("Gamepad.vibrationActuator")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("GamepadHapticActuator")}} که سخت‌افزار بازخورد لمسی موجود روی کنترل‌کننده را نشان می‌دهد.
- {{domxref("Gamepad.id")}} {{ReadOnlyInline}}
  - : رشته‌ای حاوی اطلاعات شناسایی دربارهٔ کنترل‌کننده.
- {{domxref("Gamepad.index")}} {{ReadOnlyInline}}
  - : یک عدد صحیح که به‌صورت خودکار افزایش می‌یابد تا برای هر دستگاه متصل به سیستم یکتا باشد.
- {{domxref("Gamepad.mapping")}} {{ReadOnlyInline}}
  - : رشته‌ای که نشان می‌دهد آیا مرورگر کنترل‌ها روی دستگاه را به چیدمانی شناخته‌شده نگاشت مجدد کرده است یا خیر.
- {{domxref("Gamepad.pose")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک شیء {{domxref("GamepadPose")}} که اطلاعات ژست مرتبط با یک کنترل‌کنندهٔ WebVR را نشان می‌دهد (مثلاً موقعیت و جهت آن در فضای سه‌بعدی).
- {{domxref("Gamepad.timestamp")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که آخرین زمان به‌روزرسانی داده‌های این گیم‌پد را نشان می‌دهد.

## مثال

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

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Gamepad API](/en-US/docs/Web/API/Gamepad_API/Using_the_Gamepad_API)
- [Gamepad API](/en-US/docs/Web/API/Gamepad_API)