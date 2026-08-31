---
title: "AnimationEffect"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnimationEffect"
translated_by: "n8n + AI"
slug: Web/API/AnimationEffect
page-type: web-api-interface
browser-compat: api.AnimationEffect
---

{{ APIRef("Web Animations") }}

رابط `AnimationEffect` از [API انیمیشن‌های وب](/en-US/docs/Web/API/Web_Animations_API) یک رابط است که جلوه‌های انیمیشن را نشان می‌دهد.

`AnimationEffect` یک رابط انتزاعی است و بنابراین مستقیماً قابل نمونه‌سازی نیست. با این حال، رابط‌های عینی مانند {{domxref("KeyframeEffect")}} از آن ارث‌بری می‌کنند، و نمونه‌هایی از این رابط‌ها می‌توانند به اشیاء {{domxref("Animation")}} برای پخش منتقل شوند، و همچنین ممکن است توسط [انیمیشن‌های CSS](/en-US/docs/Web/CSS/Guides/Animations) و [انتقال‌ها](/en-US/docs/Web/CSS/Guides/Transitions) استفاده شوند.

## روش‌های نمونه

- {{domxref("AnimationEffect.getTiming()")}}
  - : بازگرداندن شیء مرتبط با انیمیشن که شامل تمام مقادیر زمان‌بندی انیمیشن است.
- {{domxref("AnimationEffect.getComputedTiming()")}}
  - : بازگرداندن ویژگی‌های زمان‌بندی محاسبه‌شده برای این `AnimationEffect`.
- {{domxref("AnimationEffect.updateTiming()")}}
  - : به‌روزرسانی ویژگی‌های زمان‌بندی مشخص شده این `AnimationEffect`.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("Animation.effect")}}