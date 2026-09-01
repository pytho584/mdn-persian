---
title: "GamepadPose: orientation property"
short-title: orientation
slug: Web/API/GamepadPose/orientation
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.GamepadPose.orientation
---

{{APIRef("WebVR API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`orientation`** در رابط {{domxref("GamepadPose")}}، جهت‌گیری {{domxref("Gamepad")}} را به‌صورت یک مقدار کواترنیون برمی‌گرداند.

این مقدار یک {{jsxref("Float32Array")}} است که از مقادیر زیر تشکیل شده است:

- pitch — چرخش حول محور X.
- yaw — چرخش حول محور Y.
- roll — چرخش حول محور Z.
- w — بُعد چهارم (معمولاً 1).

یاو (yaw) جهت‌گیری (چرخش حول محور y) نسبت به یاو اولیهٔ سنسور، در زمانی که برای اولین بار خوانده شد، محاسبه می‌شود.

## مقدار

یک {{jsxref("Float32Array")}}، یا اگر سنسور واقعیت مجازی (VR) نتواند داده‌های جهت‌گیری را ارائه دهد، `null`.

## مثال‌ها

TBD

> [!NOTE]
> یک جهت‌گیری به شکل `{ x: 0, y: 0, z: 0, w: 1 }` به‌عنوان «جلو» در نظر گرفته می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebVR API](/en-US/docs/Web/API/WebVR_API)
- [Gamepad API](/en-US/docs/Web/API/Gamepad_API)