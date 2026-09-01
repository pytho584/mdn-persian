---
title: "GamepadPose"
---

---
title: GamepadPose
slug: Web/API/GamepadPose
page-type: web-api-interface
status:
  - experimental
browser-compat: api.GamepadPose
---

{{APIRef("Gamepad API")}}{{SeeCompatTable}}

رابط **`GamepadPose`** از [Gamepad API](/en-US/docs/Web/API/Gamepad_API) وضعیت یک کنترل‌کننده [WebVR](/en-US/docs/Web/API/WebVR_API) را در یک زمان مشخص (که شامل اطلاعات جهت‌گیری، موقعیت، سرعت و شتاب است) نمایش می‌دهد.

این رابط از طریق ویژگی {{domxref("Gamepad.pose")}} قابل دسترسی است.

## ویژگی‌های نمونه

- {{domxref("GamepadPose.hasOrientation")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک مقدار بولین برمی‌گرداند که نشان می‌دهد آیا گیم‌پد قادر به بازگرداندن اطلاعات جهت‌گیری است (`true`) یا خیر (`false`).
- {{domxref("GamepadPose.hasPosition")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک مقدار بولین برمی‌گرداند که نشان می‌دهد آیا گیم‌پد قادر به بازگرداندن اطلاعات موقعیت است (`true`) یا خیر (`false`).
- {{domxref("GamepadPose.position")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : موقعیت {{domxref("Gamepad")}} را به صورت یک بردار سه‌بعدی برمی‌گرداند.
- {{domxref("GamepadPose.linearVelocity")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : سرعت خطی {{domxref("Gamepad")}} را بر حسب متر بر ثانیه برمی‌گرداند.
- {{domxref("GamepadPose.linearAcceleration")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : شتاب خطی {{domxref("Gamepad")}} را بر حسب متر بر مجذور ثانیه برمی‌گرداند.
- {{domxref("GamepadPose.orientation")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : جهت‌گیری {{domxref("Gamepad")}} را به عنوان یک مقدار چهارتایی (quaternion) برمی‌گرداند.
- {{domxref("GamepadPose.angularVelocity")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : سرعت زاویه‌ای {{domxref("Gamepad")}} را بر حسب رادیان بر ثانیه برمی‌گرداند.
- {{domxref("GamepadPose.angularAcceleration")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : شتاب زاویه‌ای {{domxref("Gamepad")}} را بر حسب متر بر مجذور ثانیه برمی‌گرداند.

## مثال‌ها

در دست تکمیل.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebVR API](/en-US/docs/Web/API/WebVR_API)
- [Gamepad API](/en-US/docs/Web/API/Gamepad_API)