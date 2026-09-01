---
title: "GamepadPose: position property"
short-title: position
slug: Web/API/GamepadPose/position
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.GamepadPose.position
---

{{APIRef("WebVR API")}}{{SeeCompatTable}}

ویژگی فقطخواندنی **`position`** در رابط {{domxref("GamepadPose")}}، موقعیت {{domxref("Gamepad")}} را به‌صورت یک بردار سه‌بعدی بازمی‌گرداند.

سیستم مختصات به‌صورت زیر است:

- X مثبت به سمت راست کاربر است.
- Y مثبت به سمت بالا است.
- Z مثبت پشت سر کاربر است.

موقعیت‌ها بر حسب متر از یک نقطه مبدأ اندازه‌گیری می‌شوند — این نقطه همان موقعیتی است که سنسور برای اولین بار در آن خوانده شده است.

## مقدار

یک {{jsxref("Float32Array")}}، یا اگر گیم‌پد قادر به ارائهٔ داده‌های موقعیت نباشد، مقدار `null`.

> [!NOTE]
> عوامل کاربر ممکن است از طریق تکنیک‌هایی مقادیر موقعیت شبیه‌سازی‌شده را ارائه دهند؛ در این صورت، همچنان باید {{domxref("GamepadPose.hasPosition")}} را به‌صورت false گزارش کنند.

## مثال‌ها

TBD

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebVR API](/en-US/docs/Web/API/WebVR_API)
- [Gamepad API](/en-US/docs/Web/API/Gamepad_API)