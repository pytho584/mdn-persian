---
title: "Element: transitionstart event"
short-title: transitionstart
slug: Web/API/Element/transitionstart_event
page-type: web-api-event
browser-compat: api.Element.transitionstart_event
---

{{APIRef}}

رویداد **`transitionstart`** زمانی رخ می‌دهد که یک [گذر CSS](/en-US/docs/Web/CSS/Guides/Transitions/Using) واقعاً شروع شده باشد، یعنی پس از پایان هر {{cssxref("transition-delay")}}.

این رویداد قابل لغو (cancelable) نیست.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("transitionstart", (event) => { })

ontransitionstart = (event) => { }
```

## نوع رویداد

یک {{domxref("TransitionEvent")}}. از {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("TransitionEvent")}}

## مثال‌ها

این کد یک شنونده (listener) به رویداد `transitionstart` اضافه می‌کند:

```js
element.addEventListener("transitionstart", () => {
  console.log("Started transitioning");
});
```

همین کار، اما با استفاده از ویژگی `ontransitionstart` به جای `addEventListener()`:

```js
element.ontransitionstart = () => {
  console.log("Started transitioning");
};
```

### مثال زنده

در مثال زیر، یک عنصر ساده {{htmlelement("div")}} داریم که با یک گذر (transition) دارای تأخیر (delay) استایل‌دهی شده است:

```html
<div class="transition">Hover over me</div>
<div class="message"></div>
```

```css
.transition {
  width: 100px;
  height: 100px;
  background: red;
  transition-property: transform, background;
  transition-duration: 2s;
  transition-delay: 1s;
}

.transition:hover {
  transform: rotate(90deg);
  background: transparent;
}
```

به این، مقداری جاوااسکریپت اضافه می‌کنیم تا مشخص کند رویدادهای `transitionstart` و {{domxref("Element/transitionrun_event", "transitionrun")}} چه زمانی رخ می‌دهند.

```js
const transition = document.querySelector(".transition");
const message = document.querySelector(".message");

transition.addEventListener("transitionrun", () => {
  message.textContent = "transitionrun fired";
});

transition.addEventListener("transitionstart", () => {
  message.textContent = "transitionstart fired";
});

transition.addEventListener("transitionend", () => {
  message.textContent = "transitionend fired";
});
```

{{ EmbedLiveSample('Live example', '100%', '170') }}

تفاوت در این است که:

- `transitionrun` زمانی رخ می‌دهد که گذر ایجاد می‌شود (یعنی در شروع هر تأخیر).
- `transitionstart` زمانی رخ می‌دهد که انیمیشن واقعی آغاز شده است (یعنی در پایان هر تأخیر).

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید

- رابط {{domxref("TransitionEvent")}}
- خصوصیات CSS: {{cssxref("transition")}}، {{cssxref("transition-delay")}}، {{cssxref("transition-duration")}}، {{cssxref("transition-property")}}، {{cssxref("transition-timing-function")}}
- رویدادهای مرتبط: {{domxref("Element/transitionend_event", "transitionend")}}، {{domxref("Element/transitionrun_event", "transitionrun")}}، {{domxref("Element/transitioncancel_event", "transitioncancel")}}