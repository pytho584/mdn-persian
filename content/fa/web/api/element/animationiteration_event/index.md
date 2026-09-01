---
title: "Element: animationiteration event"
short-title: animationiteration
slug: Web/API/Element/animationiteration_event
page-type: web-api-event
browser-compat: api.Element.animationiteration_event
---

{{APIRef("Web Animations")}}

رویداد **`animationiteration`** زمانی رخ می‌دهد که یک تکرار از [پویانمایی CSS](/en-US/docs/Web/CSS/Guides/Animations) به پایان برسد و تکرار دیگری آغاز شود. این رویداد همزمان با رویداد {{domxref("Element/animationend_event", "animationend")}} رخ نمی‌دهد و بنابراین برای پویانمایی‌هایی که `animation-iteration-count` آن‌ها برابر با یک است، رخ نمی‌دهد.

## Syntax

برای استفاده از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت‌کنندهٔ رویداد را تنظیم کنید.

```js-nolint
addEventListener("animationiteration", (event) => { })

onanimationiteration = (event) => { }
```

## Event type

یک {{domxref("AnimationEvent")}}. از {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("AnimationEvent")}}

## Examples

این کد از `animationiteration` برای پیگیری تعداد تکرارهای انجام‌شدهٔ یک پویانمایی استفاده می‌کند:

```js
const animated = document.querySelector(".animated");

let iterationCount = 0;

animated.addEventListener("animationiteration", () => {
  iterationCount++;
  console.log(`Animation iteration count: ${iterationCount}`);
});
```

همین کار، اما با استفاده از ویژگی مدیریت‌کنندهٔ رویداد `onanimationiteration`:

```js
const animated = document.querySelector(".animated");

let iterationCount = 0;

animated.onanimationiteration = () => {
  iterationCount++;
  console.log(`Animation iteration count: ${iterationCount}`);
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

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [پویانمایی‌های CSS](/en-US/docs/Web/CSS/Guides/Animations)
- [استفاده از پویانمایی‌های CSS](/en-US/docs/Web/CSS/Guides/Animations/Using)
- {{domxref("AnimationEvent")}}
- رویدادهای مرتبط: {{domxref("Element/animationstart_event", "animationstart")}}، {{domxref("Element/animationend_event", "animationend")}}، {{domxref("Element/animationcancel_event", "animationcancel")}}