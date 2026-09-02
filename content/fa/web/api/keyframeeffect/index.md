---
title: KeyframeEffect
slug: Web/API/KeyframeEffect
page-type: web-api-interface
browser-compat: api.KeyframeEffect
---

{{ APIRef("Web Animations") }}

رابط **`KeyframeEffect`** در [Web Animations API](/en-US/docs/Web/API/Web_Animations_API) به ما امکان می‌دهد مجموعه‌ای از ویژگی‌ها و مقادیر قابل انیمیشن، که **keyframe** نامیده می‌شوند، ایجاد کنیم. سپس می‌توان این keyframeها را با استفاده از سازنده {{domxref("Animation.Animation", "Animation()")}} پخش کرد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("KeyframeEffect.KeyframeEffect", "KeyframeEffect()")}}
  - : یک نمونه جدید از شیء `KeyframeEffect` بازمی‌گرداند؛ همچنین به شما امکان می‌دهد یک نمونه از شیء keyframe effect موجود را شبیه‌سازی کنید.

## ویژگی‌های نمونه

- {{domxref("KeyframeEffect.target")}}
  - : عنصر یا عنصر مبدأ شبه‌عنصری که توسط این شیء متحرک می‌شود را دریافت و تنظیم می‌کند. برای انیمیشن‌هایی که عنصر یا شبه‌عنصر خاصی را هدف قرار نمی‌دهند، این مقدار می‌تواند `null` باشد.
- {{domxref("KeyframeEffect.pseudoElement")}}
  - : انتخابگر شبه‌عنصری که توسط این شیء متحرک می‌شود را دریافت و تنظیم می‌کند. برای انیمیشن‌هایی که شبه‌عنصری را هدف قرار نمی‌دهند، این مقدار می‌تواند `null` باشد.
- {{domxref("KeyframeEffect.iterationComposite")}}
  - : عملیات ترکیب تکرار (iteration composite) برای حل تغییرات مقادیر ویژگی‌های این keyframe effect را دریافت و تنظیم می‌کند.
- {{domxref("KeyframeEffect.composite")}}
  - : ویژگی عملیات ترکیب برای حل تغییرات مقادیر ویژگی‌های بین این keyframe effect و سایر keyframe effectها را دریافت و تنظیم می‌کند.

## روش‌های نمونه

_این رابط برخی از روش‌های خود را از والد خود، {{domxref("AnimationEffect")}}، به ارث می‌برد._

- {{domxref("AnimationEffect.getComputedTiming()")}}
  - : مقادیر زمان‌بندی محاسبه‌شده و جاری برای این keyframe effect را بازمی‌گرداند.
- {{domxref("KeyframeEffect.getKeyframes()")}}
  - : keyframeهای محاسبه‌شده که این اثر را تشکیل می‌دهند، به همراه offsetهای keyframe محاسبه‌شده آن‌ها را بازمی‌گرداند.
- {{domxref("AnimationEffect.getTiming()")}}
  - : شیء مرتبط با انیمیشن که شامل تمام مقادیر زمان‌بندی انیمیشن است را بازمی‌گرداند.
- {{domxref("KeyframeEffect.setKeyframes()")}}
  - : مجموعه keyframeهایی که این اثر را تشکیل می‌دهند جایگزین می‌کند.
- {{domxref("AnimationEffect.updateTiming()")}}
  - : ویژگی‌های زمان‌بندی مشخص‌شده را به‌روزرسانی می‌کند.

## مثال‌ها

در مثال زیر، از سازنده `KeyframeEffect` برای ایجاد مجموعه‌ای از keyframeها استفاده شده است که نحوه غلتیدن شکلک خنده‌دار روی زمین را مشخص می‌کند:

```js
const emoji = document.querySelector("div"); // عنصری که قرار است متحرک شود

const rollingKeyframes = new KeyframeEffect(
  emoji,
  [
    { transform: "translateX(0) rotate(0)" }, // keyframe
    { transform: "translateX(200px) rotate(1.3turn)" }, // keyframe
  ],
  {
    // گزینه‌های keyframe
    duration: 2000,
    direction: "alternate",
    easing: "ease-in-out",
    iterations: "Infinity",
  },
);

const rollingAnimation = new Animation(rollingKeyframes, document.timeline);

// پخش انیمیشن غلتیدن
rollingAnimation.play();
```

```html
<div>🤣</div>
```

```css hidden
body {
  box-shadow: 0 5px 5px pink;
}

div {
  width: fit-content;
  margin-left: calc(50% - 132px);
  font-size: 64px;
  user-select: none;
  margin-top: 1rem;
}
```

{{ EmbedLiveSample("Examples", "100%", "120") }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("Animation")}}