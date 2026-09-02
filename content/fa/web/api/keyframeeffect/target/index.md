```markdown
---
title: "KeyframeEffect: target property"
short-title: target
slug: Web/API/KeyframeEffect/target
page-type: web-api-instance-property
browser-compat: api.KeyframeEffect.target
---

{{ APIRef("Web Animations") }}

ویژگی **`target`** در رابط {{domxref("KeyframeEffect")}} نشان‌دهنده‌ی عنصر یا شبه‌عنصری است که در حال انیمیشن‌سازی است. برای انیمیشن‌هایی که عنصر خاصی را هدف قرار نمی‌دهند، ممکن است `null` باشد. این ویژگی به عنوان هم دریافت‌کننده و هم تنظیم‌کننده عمل می‌کند، به جز در انیمیشن‌ها و transitionهای تولیدشده توسط CSS.

## مقدار

یک {{domxref("Element")}} یا `null`.

## مثال‌ها

در مثال زیر، `emoji` به عنوان عنصر `target` برای انیمیشن تنظیم شده است:

```js
const emoji = document.querySelector("div"); // عنصری که باید انیمیشن بگیرد

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
rollingAnimation.play();

// خروجی: "<div>🤣</div>"
console.log(rollingKeyframes.target);
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

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- ویژگی از اشیاء {{domxref("KeyframeEffect")}}
```