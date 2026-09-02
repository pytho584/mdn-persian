---
title: "KeyframeEffect: getKeyframes() method"
short-title: getKeyframes()
slug: Web/API/KeyframeEffect/getKeyframes
page-type: web-api-instance-method
browser-compat: api.KeyframeEffect.getKeyframes
---

{{ APIRef("Web Animations") }}

متد **`getKeyframes()`** از یک {{domxref("KeyframeEffect")}} آرایه‌ای از keyframe‌های محاسبه‌شده‌ای که این انیمیشن را تشکیل می‌دهند به همراه offset‌های محاسبه‌شده آنها برمی‌گرداند.

## نحو

```js-nolint
getKeyframes()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

دنباله‌ای از اشیاء با قالب زیر را برمی‌گرداند:

- جفت‌های مقدار-ویژگی
  - : هر تعداد جفت مقدار-ویژگی که در هر keyframe از انیمیشن وجود دارد.
- `offset`
  - : offset keyframe که به صورت عددی بین `0.0` و `1.0` (شامل خودشان) یا `null` مشخص شده است. این معادل تعیین حالت‌های شروع و پایان به درصد در stylesheetهای CSS با استفاده از `@keyframes` است. اگر keyframe به طور خودکار فاصله‌گذاری شده باشد، این مقدار `null` خواهد بود.
- `computedOffset`
  - : offset محاسبه‌شده برای این keyframe که هنگام تولید لیست keyframe‌های محاسبه‌شده تعیین می‌شود. برخلاف **`offset`** در بالا، **`computedOffset`** هرگز `null` نیست.
- `easing`
  - : [تابع آهنگین](/en-US/docs/Web/CSS/Reference/Values/easing-function) که از این keyframe تا keyframe بعدی در سری استفاده می‌شود.
- `composite`
  - : عملیات {{domxref("KeyframeEffect.composite")}} که برای ترکیب مقادیر مشخص شده در این keyframe با مقدار زیرین استفاده می‌شود. اگر از عملیات composite مشخص شده روی افکت استفاده شود، این ویژگی وجود نخواهد داشت.

## مثال‌ها

در مثال زیر، می‌توانیم انیمیشن چرخشی را برای دیدن keyframe‌های آن با استفاده از متد `getKeyframes()` بررسی کنیم:

```js
const emoji = document.querySelector("div"); // element to animate

const rollingKeyframes = new KeyframeEffect(
  emoji,
  [
    { transform: "translateX(0) rotate(0)" }, // keyframe
    { transform: "translateX(200px) rotate(1.3turn)" }, // keyframe
  ],
  {
    // keyframe options
    duration: 2000,
    direction: "alternate",
    easing: "ease-in-out",
    iterations: "Infinity",
  },
);

const rollingAnimation = new Animation(rollingKeyframes, document.timeline);
rollingAnimation.play();

// Array [ {…}, {…} ]
console.log(rollingAnimation.effect.getKeyframes());
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

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- متدی از اشیاء {{domxref("KeyframeEffect")}}.