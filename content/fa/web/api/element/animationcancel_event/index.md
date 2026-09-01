---
title: "Element: animationcancel event"
short-title: animationcancel
slug: Web/API/Element/animationcancel_event
page-type: web-api-event
browser-compat: api.Element.animationcancel_event
---

{{APIRef("Web Animations")}}

رویداد **`animationcancel`** زمانی رخ می‌دهد که یک [CSS Animation](/en-US/docs/Web/CSS/Guides/Animations) به‌طور غیرمنتظره‌ای لغو شود. به عبارت دیگر، هر زمان که اجرای انیمیشن بدون ارسال رویداد {{domxref("Element/animationend_event", "animationend")}} متوقف شود. این اتفاق ممکن است زمانی رخ دهد که {{cssxref("animation-name")}} به‌گونه‌ای تغییر کند که انیمیشن حذف شود، یا زمانی که گرهٔ در حال انیمیشن با استفاده از CSS پنهان شود؛ بنابراین، چه به‌طور مستقیم و چه به این دلیل که یکی از گره‌های دربرگیرندهٔ آن پنهان شده باشد.

برای افزودن مدیریت‌کنندهٔ رویداد برای این رویداد، می‌توانید ویژگی `onanimationcancel` را تنظیم کنید یا از {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید.

## نحو

در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} از نام رویداد استفاده کنید، یا یک ویژگی مدیریت‌کنندهٔ رویداد را تنظیم کنید.

```js-nolint
addEventListener("animationcancel", (event) => { })

onanimationcancel = (event) => { }
```

## نوع رویداد

یک {{domxref("AnimationEvent")}} که از {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("AnimationEvent")}}

## مثال‌ها

این کد یک عنصر را که در حال حاضر در حال انیمیشن است دریافت می‌کند و یک شنونده برای رویداد `animationcancel` به آن اضافه می‌کند. سپس ویژگی {{cssxref("display")}} عنصر را روی `none` تنظیم می‌کند که باعث فعال شدن رویداد `animationcancel` می‌شود.

```js
const animated = document.querySelector(".animated");

animated.addEventListener("animationcancel", () => {
  console.log("Animation canceled");
});

animated.style.display = "none";
```

همین کار، اما با استفاده از ویژگی `onanimationcancel` به جای `addEventListener()`:

```js
const animated = document.querySelector(".animated");
animated.onanimationcancel = () => {
  console.log("Animation canceled");
};

animated.style.display = "none";
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

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [CSS Animations](/en-US/docs/Web/CSS/Guides/Animations)
- [Using CSS Animations](/en-US/docs/Web/CSS/Guides/Animations/Using)
- {{domxref("AnimationEvent")}}
- رویدادهای مرتبط: {{domxref("Element/animationstart_event", "animationstart")}}، {{domxref("Element/animationend_event", "animationend")}}، {{domxref("Element/animationiteration_event", "animationiteration")}}