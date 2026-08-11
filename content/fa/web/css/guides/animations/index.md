---
title: "CSS animations"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Animations"
translated_by: "n8n + AI"
---

ماژول **انیمیشن‌های CSS** به شما این امکان را می‌دهد که مقادیر ویژگی‌های CSS مثل `background-position` و `transform` را در طول زمان و با استفاده از `keyframes` تغییر دهید. هر `keyframe` مشخص می‌کند که عنصر متحرک در هر لحظه از توالی انیمیشن چگونه نمایش داده شود. با ویژگی‌های این ماژول می‌توانید مدت‌زمان، تعداد تکرار، تأخیر شروع و دیگر جنبه‌های انیمیشن را کنترل کنید.

## انیمیشن‌ها در عمل

برای مشاهدهٔ انیمیشن در جعبهٔ زیر، روی چک‌باکس «پخش انیمیشن» کلیک کنید یا نشانگر موس را روی جعبه ببرید. وقتی انیمیشن فعال باشد، ابر در بالا تغییر شکل می‌دهد، دانه‌های برف می‌بارند و سطح برف در پایین بالا می‌آید. برای توقف انیمیشن، تیک چک‌باکس را بردارید یا نشانگر موس را از روی جعبه بردارید.

```html hidden live-sample___animation
<!-- See aria-label: https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label -->
<input
  type="checkbox"
  id="animate"
  aria-label="Toggle the play state of the animation" />
<label for="animate">the animation</label>
<div class="root">
  <i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i
  ><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i
  ><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i
  ><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i
  ><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i>
  <div class="cloud"></div>
  <div class="ground"></div>
</div>
```

```css hidden live-sample___animation
i {
  display: inline-block;
  height: 16px;
  width: 16px;
  border-radius: 50%;
  animation: falling 3s linear 0s infinite backwards;
  /* Snowflakes are made with CSS linear gradients (https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Images/Using_gradients) */
  background-image:
    linear-gradient(180deg, transparent 40%, white 40% 60%, transparent 60%),
    linear-gradient(90deg, transparent 40%, white 40% 60%, transparent 60%),
    linear-gradient(45deg, transparent 43%, white 43% 57%, transparent 57%),
    linear-gradient(135deg, transparent 43%, white 43% 57%, transparent 57%);
}
i:nth-of-type(4n) {
  /* Using tree structural pseudo-classes to create randomness - https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Selectors/:nth-of-type */
  height: 30px;
  width: 30px;
  transform-origin: right -30px;
}
i:nth-of-type(4n + 1) {
  height: 24px;
  width: 24px;
  transform-origin: left 30px;
}
i:nth-of-type(4n + 2) {
  height: 10px;
  width: 10px;
  transform-origin: -30px 0;
}
i:nth-of-type(4n + 3) {
  height: 40px;
  width: 40px;
  transform-origin: -50px 0;
}
i:nth-of-type(4n) {
  animation-duration: 5.3s;
  animation-iteration-count: 12;
  transform-origin: -10px -20px;
}
i:nth-of-type(4n + 1) {
  animation-duration: 3.1s;
  animation-iteration-count: 20;
  transform-origin: 10px -20px;
}
i:nth-of-type(4n + 2) {
  animation-duration: 1.7s;
  animation-iteration-count: 35;
  transform-origin: right -20px;
}
i:nth-of-type(3n) {
  animation-delay: 2.3s;
}
i:nth-of-type(3n + 1) {
  animation-delay: 1.5s;
}
i:nth-of-type(3n + 2) {
  animation-delay: 3.4s;
}
i:nth-of-type(5n) {
  animation-timing-function: ease-in-out;
}
i:nth-of-type(5n + 1) {
  animation-timing-function: ease-out;
}
i:nth-of-type(5n + 2) {
  animation-timing-function: ease;
}
i:nth-of-type(5n + 3) {
  animation-timing-function: ease-in;
}
i:nth-of-type(5n + 4) {
  animation-timing-function: linear;
}
i:nth-of-type(11n) {
  animation-timing-function: cubic-bezier(0.2, 0.3, 0.8, 0.9);
}
i:nth-of-type(7n) {
  opacity: 0.5;
}
i:nth-of-type(7n + 2) {
  opacity: 0.3;
}
i:nth-of-type(7n + 4) {
  opacity: 0.7;
}
i:nth-of-type(7n + 6) {
  opacity: 0.6;
  animation-timing-function: ease-in;
  transform-origin: left 10px;
}
i:nth-of-type(7n + 1) {
  opacity: 0.8;
}

.root {
  height: 580px;
  background-color: skyblue;
  border: 1px solid darkgrey;
  position: relative;
  overflow: hidden;
}
.ground,
.cloud {
  position: absolute;
  top: 0;
  right: 0;
  left: 0;
  background-repeat: no-repeat;
}
.cloud {
  width: 100%;
  height: 150px;
  background: white;
  border-radius: 0 0 90px 33% / 0 0 45px 50px;
  box-shadow:
    5px 15px 15px white,
    -5px 15px 15px white,
    0 20px 20px rgb(125 125 125 / 0.5);
  animation:
    clouds ease 5s alternate infinite 0.2s,
    wind ease-out 4s alternate infinite;
}
.ground {
  bottom: 0;
  background-image: linear-gradient(to top, white 97%, 99%, #bbbbbb 100%);
  background-position: center 580px;
  animation: snowfall linear 300s forwards;
  border: 1px solid grey;
  /* Put the ground into a 3D rendering context (because the snow flakes are in a 3d rendering context) */
  transform: translate3d(0, 0, 0);
}

@keyframes snowfall {
  from {
    background-position: center 580px;
  }
  to {
    background-position: center 280px;
  }
}

@keyframes clouds {
  from {
    border-radius: 0 0 90px 33% / 0 0 45px 50px;
  }
  to {
    border-radius: 0 0 40px 50% / 0 0 55px 80px;
  }
}

@keyframes wind {
  from {
    height: 150px;
  }
  to {
    height: 100px;
  }
}

@keyframes falling {
  from {
    transform: translate(0, -50px) rotate(0deg) scale(0.9, 0.9);
  }
  to {
    transform: translate(30px, 600px) rotate(360deg) scale(1.1, 1.1);
  }
}
```

```css
/* By default, the animations are paused. */
i,
div[class] {
  animation-play-state: paused;
}
/* When the div is hovered, the animation plays. Also,
when the input is checked, the animation coming after the checked checkbox plays */
div:hover *,
input:checked ~ div * {
  animation-play-state: running;
}

/* Change the content of the label that comes right after the input. Included aria-label on the label to improve accessibility. */
input + label::before {
  content: "Play ";
}
input:checked + label::before {
  content: "Pause ";
}
```

در این نمونه از انیمیشن، از `animation-iteration-count` برای تکرار ریزش دانه‌های برف، از `animation-direction` برای حرکت رفت و برگشتی ابر، از `animation-fill-mode` برای بالا آمدن سطح برف متناسب با حرکت ابر، و از `animation-play-state` برای مکث انیمیشن استفاده شده است.

روی «Play» در مثال بالا کلیک کنید تا کد انیمیشن را در MDN Playground ببینید یا ویرایش کنید.

## مرجع

### خصوصیات (Properties)

- `animation` (ویژگی خلاصه‌نویس)
- `animation-composition`
- `animation-delay`
- `animation-direction`
- `animation-duration`
- `animation-fill-mode`
- `animation-iteration-count`
- `animation-name`
- `animation-play-state`
- `animation-timeline`
- `animation-timing-function`

ماژول سطح ۲ انیمیشن‌های CSS همچنین خصوصیات `animation-trigger`، `animation-trigger-exit-range`، `animation-trigger-exit-range-end`، `animation-trigger-exit-range-start`، `animation-trigger-range`، `animation-trigger-range-end`، `animation-trigger-range-start`، `animation-trigger-timeline` و `animation-trigger-type` را معرفی می‌کند. در حال حاضر هیچ مرورگری از این ویژگی‌ها پشتیبانی نمی‌کند.

### قواعد at و توصیف‌کننده‌ها (At-rules and descriptors)

- `@keyframes`
- [`<keyframe-selector>`](/en-US/docs/Web/CSS/Reference/Selectors/Keyframe_selectors)

### رویدادها (Events)

تمامی انیمیشن‌ها، حتی آن‌هایی که مدت زمان صفر دارند، رویدادهای انیمیشن را تولید می‌کنند.

- `animationstart`
- `animationend`
- `animationcancel`
- `animationiteration`

### رابط‌ها (Interfaces)

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- `AnimationEvent`
- `CSSAnimation`
- `CSSKeyframeRule`
- `CSSKeyframesRule`

## راهنماها

- [استفاده از انیمیشن‌های CSS](/en-US/docs/Web/CSS/Guides/Animations/Using)
  - : آموزش گام‌به‌گام نحوه ساخت انیمیشن با CSS. این مقاله خصوصیات و قاعده at مرتبط با انیمیشن و نحوه تعامل آن‌ها با یکدیگر را شرح می‌دهد.
- [خصوصیات قابل انیمیشن CSS](/en-US/docs/Web/CSS/Guides/Animations/Animatable_properties)
  - : مروری بر چگونگی انیمیشن‌سازی خصوصیات مختلف CSS، از جمله انواع انیمیشن و روش‌های درون‌یابی.
- [استفاده از Web Animations API](/en-US/docs/Web/API/Web_Animations_API/Using_the_Web_Animations_API)
  - : نیازمندی‌های رایج انیمیشن که با چند خط کد جاوااسکریپت قابل حل هستند.

## مفاهیم مرتبط

- خاصیت CSS `will-change`
- نوع داده `easing-function`
- [`prefers-reduced-motion`](/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-reduced-motion) (media query)
- عبارت `Bezier curve` (منحنی بزیه)

## مشخصات (Specifications)

## همچنین ببینید

- ماژول [CSS scroll-driven animations](/en-US/docs/Web/CSS/Guides/Scroll-driven_animations).
- ویژگی‌های ماژول CSS [transitions](/en-US/docs/Web/CSS/Guides/Transitions) برای فعال‌سازی انیمیشن‌ها بر اساس اقدامات کاربر.
- ویژگی `interpolate-size` و تابع `calc-size()` برای فعال‌سازی انیمیشن‌ها از و به مقادیر [اندازه ذاتی](/en-US/docs/Glossary/Intrinsic_Size).
- عنصر HTML `canvas` به همراه [canvas API](/en-US/docs/Web/API/Canvas_API) و [WebGL API](/en-US/docs/Web/API/WebGL_API) برای رسم گرافیک و انیمیشن.
- رابط `SVGAnimationElement` برای تمام رابط‌های عنصر مرتبط با انیمیشن، شامل `SVGAnimateElement`، `SVGSetElement`، `SVGAnimateColorElement`، `SVGAnimateMotionElement`، و `SVGAnimateTransformElement`.