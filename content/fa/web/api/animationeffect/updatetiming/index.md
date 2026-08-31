---
title: "AnimationEffect: updateTiming() method"
short-title: updateTiming()
slug: Web/API/AnimationEffect/updateTiming
page-type: web-api-instance-method
browser-compat: api.AnimationEffect.updateTiming
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnimationEffect/updateTiming"
translated_by: "n8n + AI"
---

{{ APIRef("Web Animations") }}

متد `updateTiming()` از رابط {{domxref("AnimationEffect")}} ویژگی‌های زمان‌بندی مشخص شده برای یک افکت انیمیشن را به‌روزرسانی می‌کند.

## نحو (Syntax)

```js-nolint
updateTiming(timing)
```

### پارامترها

- `timing` {{optional_inline}}
  - : یک شی شامل صفر یا تعداد بیشتری از ویژگی‌های مقدار بازگشتی {{domxref("AnimationEffect.getTiming()")}} که نشان‌دهنده ویژگی‌های زمان‌بندی برای به‌روزرسانی است.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- {{jsxref("TypeError")}}
  - : اگر مقادیر نامعتبر برای هر یک از ویژگی‌های زمان‌بندی ارائه شود، پرتاب می‌شود.

### مثال‌ها

#### اثرات جانبی

`updateTiming()` ممکن است باعث شود هر {{domxref("Animation")}} مرتبط شروع به پخش کند یا متوقف شود، به عنوان مثال اگر افکت یک انیمیشن در حال اجرا به گونه‌ای کوتاه شود که زمان پایان آن قبل از {{domxref("Animation.currentTime")}} باشد یا افکت یک انیمیشن تمام شده به گونه‌ای طولانی شود که زمان پایان آن بعد از {{domxref("Animation.currentTime")}} باشد.

```js
const animation = document.body.animate([], { duration: 1000 });
animation.finish();
console.log(animation.playState); // finished
animation.effect.updateTiming({ duration: 2000 });
console.log(animation.playState); // running
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("AnimationEffect")}}
- {{domxref("Animation")}}
- {{domxref("AnimationEffect.getTiming()")}}
- {{domxref("AnimationEffect.getComputedTiming()")}}