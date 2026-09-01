---
title: "Element: transitionrun event"
short-title: transitionrun
slug: Web/API/Element/transitionrun_event
page-type: web-api-event
browser-compat: api.Element.transitionrun_event
---

{{APIRef}}

رویداد **`transitionrun`** زمانی رخ می‌دهد که یک [CSS transition](/en-US/docs/Web/CSS/Guides/Transitions/Using) برای اولین بار ایجاد می‌شود، یعنی قبل از شروع هر {{cssxref("transition-delay")}}.

این رویداد قابل‌لغو نیست.

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("transitionrun", (event) => { })

ontransitionrun = (event) => { }
```

## Event type

یک {{domxref("TransitionEvent")}} که از {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("TransitionEvent")}}

## Examples

این کد یک شنونده به رویداد `transitionrun` اضافه می‌کند:

```js
el.addEventListener("transitionrun", () => {
  console.log(
    "Transition is running but hasn't necessarily started transitioning yet",
  );
});
```

همین کار، اما با استفاده از ویژگی `ontransitionrun` به‌جای `addEventListener()`:

```js
el.ontransitionrun = () => {
  console.log(
    "Transition started running, and will start transitioning when the transition delay has expired",
  );
};
```

### Live example

در مثال زیر، یک عنصر ساده {{htmlelement("div")}} داریم که با یک transition شامل تأخیر، استایل‌سازی شده است:

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

برای این کار، کمی جاوااسکریپت اضافه می‌کنیم تا مشخص کند رویدادهای {{domxref("Element/transitionstart_event", "transitionstart")}} و `transitionrun` در چه زمانی رخ می‌دهند.

```js
const el = document.querySelector(".transition");
const message = document.querySelector(".message");

el.addEventListener("transitionrun", () => {
  message.textContent = "transitionrun fired";
});

el.addEventListener("transitionstart", () => {
  message.textContent = "transitionstart fired";
});

el.addEventListener("transitionend", () => {
  message.textContent = "transitionend fired";
});
```

{{ EmbedLiveSample('Live_example', '100%', '150px') }}

تفاوت در این است که:

- `transitionrun` زمانی رخ می‌دهد که transition ایجاد می‌شود (یعنی در شروع هر تأخیر).
- `transitionstart` زمانی رخ می‌دهد که انیمیشن واقعی آغاز شده است (یعنی در پایان هر تأخیر).

رویداد `transitionrun` حتی اگر transition قبل از پایان تأخیر لغو شود نیز رخ می‌دهد. اگر تأخیر transition وجود نداشته باشد یا transition-delay منفی باشد، هر دو رویداد `transitionrun` و `transitionstart` رخ می‌دهند.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- رابط {{domxref("TransitionEvent")}}
- ویژگی‌های CSS: {{cssxref("transition")}}, {{cssxref("transition-delay")}}, {{cssxref("transition-duration")}}, {{cssxref("transition-property")}}, {{cssxref("transition-timing-function")}}
- رویدادهای مرتبط: {{domxref("Element/transitionend_event", "transitionend")}}, {{domxref("Element/transitionstart_event", "transitionstart")}}, {{domxref("Element/transitioncancel_event", "transitioncancel")}}
