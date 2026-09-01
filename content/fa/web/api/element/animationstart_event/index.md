---
title: "Element: animationstart event"
short-title: animationstart
slug: Web/API/Element/animationstart_event
page-type: web-api-event
browser-compat: api.Element.animationstart_event
---

{{APIRef("Web Animations")}}

رویداد **`animationstart`** زمانی رخ می‌دهد که یک [انیمیشن CSS](/en-US/docs/Web/CSS/Guides/Animations) شروع شده باشد. اگر {{cssxref("animation-delay")}} تنظیم شده باشد، این رویداد پس از پایان دوره تأخیر فعال می‌شود. تأخیر منفی باعث می‌شود رویداد با {{domxref("AnimationEvent/elapsedTime", "elapsedTime")}} برابر قدر مطلق تأخیر فعال شود (و به همین ترتیب، انیمیشن از همان شاخص زمانی در دنباله شروع به پخش خواهد کرد).

## نحو

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت رویداد تنظیم کنید.

```js-nolint
addEventListener("animationstart", (event) => { })

onanimationstart = (event) => { }
```

## نوع رویداد

یک {{domxref("AnimationEvent")}}. از {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("AnimationEvent")}}

## مثال‌ها

در این مثال به رویداد `animationstart` گوش داده می‌شود و وقتی رخ دهد، پیامی در کنسول ثبت می‌شود:

```js
const animated = document.querySelector(".animated");

animated.addEventListener("animationstart", () => {
  console.log("Animation started");
});
```

همین کار، اما با استفاده از `onanimationstart`:

```js
const animated = document.querySelector(".animated");

animated.onanimationstart = () => {
  console.log("Animation started");
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

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [انیمیشن‌های CSS](/en-US/docs/Web/CSS/Guides/Animations)
- [استفاده از انیمیشن‌های CSS](/en-US/docs/Web/CSS/Guides/Animations/Using)
- {{domxref("AnimationEvent")}}
- رویدادهای مرتبط: {{domxref("Element/animationend_event", "animationend")}}, {{domxref("Element/animationiteration_event", "animationiteration")}}, {{domxref("Element/animationcancel_event", "animationcancel")}}