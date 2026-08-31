---
title: "Animation: Animation() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Animation/Animation"
translated_by: "n8n + AI"
---

---
title: "Animation: Animation() constructor"
short-title: Animation()
slug: Web/API/Animation/Animation
page-type: web-api-constructor
browser-compat: api.Animation.Animation
---

{{ APIRef("Web Animations") }}

سازنده **`Animation()`** از [Web Animations API](/en-US/docs/Web/API/Web_Animations_API) یک نمونه شیء `Animation` جدید برمی‌گرداند.

## نحو

```js-nolint
new Animation()
new Animation(effect)
new Animation(effect, timeline)
```

### پارامترها

- `effect` {{optional_inline}}
  - : افکت هدف، به‌عنوان یک شیء مبتنی بر رابط {{domxref("AnimationEffect")}}، که به انیمیشن اختصاص داده می‌شود. اگرچه در آینده ممکن است افکت‌های دیگری مانند `SequenceEffect`s یا `GroupEffect`s ممکن باشند، تنها نوع افکت در حال حاضر {{domxref("KeyframeEffect")}} است. این می‌تواند `null` باشد (که مقدار پیش‌فرض است) تا نشان دهد که هیچ افکتی اعمال نشود.
- `timeline` {{optional_inline}}
  - : مشخص‌کننده `timeline` ای که انیمیشن با آن مرتبط می‌شود، به‌عنوان یک شیء از نوع مبتنی بر رابط {{domxref("AnimationTimeline")}}. مقدار پیش‌فرض {{domxref("Document.timeline")}} است، اما می‌تواند روی `null` نیز تنظیم شود.

## مثال‌ها

در [مثال Follow the White Rabbit](/en-US/docs/Web/API/Web_Animations_API/Using_the_Web_Animations_API#pausing_and_playing_animations)، می‌توانیم از سازنده `Animation()` برای ایجاد یک `Animation` برای `rabbitDownKeyframes` با استفاده از `timeline` سند استفاده کنیم:

```js
const whiteRabbit = document.getElementById("rabbit");

const rabbitDownKeyframes = new KeyframeEffect(
  whiteRabbit,
  [{ transform: "translateY(0%)" }, { transform: "translateY(100%)" }],
  { duration: 3000, fill: "forwards" },
);

const rabbitDownAnimation = new Animation(rabbitDownKeyframes);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("Animation")}}