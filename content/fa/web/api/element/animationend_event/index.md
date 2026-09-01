---
title: "Element: animationend event"
short-title: animationend
slug: Web/API/Element/animationend_event
page-type: web-api-event
browser-compat: api.Element.animationend_event
---

{{APIRef("Web Animations")}}

رویداد **`animationend`** زمانی راه‌اندازی می‌شود که یک [انیمیشن CSS](/en-US/docs/Web/CSS/Guides/Animations) (CSS Animation) به پایان رسیده باشد. اگر انیمیشن قبل از اتمام لغو شود، مثلاً اگر عنصر از DOM حذف شود یا انیمیشن از عنصر حذف شود، رویداد `animationend` راه‌اندازی نخواهد شد.

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("animationend", (event) => { })

onanimationend = (event) => { }
```

## نوع رویداد

یک {{domxref("AnimationEvent")}}. از {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("AnimationEvent")}}

## مثال‌ها

این مثال یک عنصر را که در حال انیمیشن است انتخاب می‌کند و به رویداد `animationend` گوش می‌دهد:

```js
const animated = document.querySelector(".animated");

animated.addEventListener("animationend", () => {
  console.log("Animation ended");
});
```

همین کار، اما با استفاده از ویژگی کنترل‌کننده رویداد `onanimationend`:

```js
const animated = document.querySelector(".animated");

animated.onanimationend = () => {
  console.log("Animation ended");
};
```

### مثال زنده

#### HTML

```html
<div class="animation-example">
  <div class="container">
    <p class="animation">You chose a cold night to visit our planet.</p>
  </div>
  <button class="activate" type="button">Activate animation</button>
  <div class="event-log"></div>
</div>
```

#### CSS

```css
.container {
  height: 3rem;
}

.event-log {
  width: 25rem;
  height: 2rem;
  border: 1px solid black;
  margin: 0.2rem;
  padding: 0.2rem;
}

.animation.active {
  animation-duration: 2s;
  animation-name: slide-in;
  animation-iteration-count: 2;
}

@keyframes slide-in {
  from {
    transform: translateX(100%) scaleX(3);
  }

  to {
    transform: translateX(0) scaleX(1);
  }
}
```

#### JavaScript

```js
const animation = document.querySelector("p.animation");
const animationEventLog = document.querySelector(
  ".animation-example>.event-log",
);
const applyAnimation = document.querySelector(
  ".animation-example>button.activate",
);
let iterationCount = 0;

animation.addEventListener("animationstart", () => {
  animationEventLog.textContent = `${animationEventLog.textContent}'animation started' `;
});

animation.addEventListener("animationiteration", () => {
  iterationCount++;
  animationEventLog.textContent = `${animationEventLog.textContent}'animation iterations: ${iterationCount}' `;
});

animation.addEventListener("animationend", () => {
  animationEventLog.textContent = `${animationEventLog.textContent}'animation ended'`;
  animation.classList.remove("active");
  applyAnimation.textContent = "Activate animation";
});

animation.addEventListener("animationcancel", () => {
  animationEventLog.textContent = `${animationEventLog.textContent}'animation canceled'`;
});

applyAnimation.addEventListener("click", () => {
  animation.classList.toggle("active");
  animationEventLog.textContent = "";
  iterationCount = 0;
  const active = animation.classList.contains("active");
  applyAnimation.textContent = active
    ? "Cancel animation"
    : "Activate animation";
});
```

#### نتیجه

{{ EmbedLiveSample('Live_example', '100%', '150px') }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [انیمیشن‌های CSS](/en-US/docs/Web/CSS/Guides/Animations) (CSS Animations)
- [استفاده از انیمیشن‌های CSS](/en-US/docs/Web/CSS/Guides/Animations/Using) (Using CSS Animations)
- {{domxref("AnimationEvent")}}
- رویدادهای مرتبط: {{domxref("Element/animationstart_event", "animationstart")}}، {{domxref("Element/animationcancel_event", "animationcancel")}}، {{domxref("Element/animationiteration_event", "animationiteration")}}