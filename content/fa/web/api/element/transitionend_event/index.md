---
title: "Element: transitionend event"
short-title: transitionend
slug: Web/API/Element/transitionend_event
page-type: web-api-event
browser-compat: api.Element.transitionend_event
---

{{APIRef}}

رویداد **`transitionend`** زمانی رخ می‌دهد که یک [انتقال CSS](/en-US/docs/Web/CSS/Guides/Transitions/Using) کامل شده باشد. در مواردی که یک transition قبل از تکمیل حذف شود، مثلاً اگر {{cssxref("transition-property")}} حذف شود یا {{cssxref("display")}} روی `none` تنظیم شود، این رویداد تولید نخواهد شد.

رویداد `transitionend` در هر دو جهت رخ می‌دهد — هم زمانی که انتقال به حالت نهایی راه می‌افتد و هم زمانی که به حالت پیش‌فرض یا بدون انتقال بازمی‌گردد. اگر تأخیر (delay) یا مدت (duration) انتقال وجود نداشته باشد، یعنی هر دو ۰s باشند یا هیچ‌کدام تعریف نشده باشند، انتقالی رخ نمی‌دهد و هیچ‌کدام از رویدادهای transition فراخوانی نمی‌شوند. اگر رویداد `transitioncancel` فراخوانی شود، رویداد `transitionend` فراخوانی نخواهد شد.

این رویداد قابل لغو (cancelable) نیست.

## سینتکس

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("transitionend", (event) => { })

ontransitionend = (event) => { }
```

## نوع رویداد

یک {{domxref("TransitionEvent")}} که از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("TransitionEvent")}}

## مثال‌ها

این کد یک عنصر که دارای transition تعریف‌شده است را دریافت کرده و یک شنونده (listener) برای رویداد `transitionend` اضافه می‌کند:

```js
const transition = document.querySelector(".transition");

transition.addEventListener("transitionend", () => {
  console.log("Transition ended");
});
```

همین کار، اما با استفاده از `ontransitionend`:

```js
const transition = document.querySelector(".transition");

transition.ontransitionend = () => {
  console.log("Transition ended");
};
```

### مثال زنده

در مثال زیر، یک عنصر ساده {{htmlelement("div")}} داریم که با یک transition دارای تأخیر استایل داده شده است:

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

برای این کار، کمی جاوااسکریپت اضافه می‌کنیم تا مشخص کند رویدادهای [`transitionstart`](/en-US/docs/Web/API/Element/transitionstart_event)، [`transitionrun`](/en-US/docs/Web/API/Element/transitionrun_event)، [`transitioncancel`](/en-US/docs/Web/API/Element/transitioncancel_event) و `transitionend` فراخوانی می‌شوند. در این مثال، برای لغو transition، قبل از پایان انتقال، هاور کردن روی جعبه در حال انتقال را متوقف کنید. برای اینکه رویداد پایان انتقال فراخوانی شود، تا پایان انتقال روی آن هاور بمانید.

```js
const message = document.querySelector(".message");
const el = document.querySelector(".transition");

el.addEventListener("transitionrun", () => {
  message.textContent = "transitionrun fired";
});

el.addEventListener("transitionstart", () => {
  message.textContent = "transitionstart fired";
});

el.addEventListener("transitioncancel", () => {
  message.textContent = "transitioncancel fired";
});

el.addEventListener("transitionend", () => {
  message.textContent = "transitionend fired";
});
```

{{ EmbedLiveSample('Live_example', '100%', '150px') }}

رویداد `transitionend` در هر دو جهت فراخوانی می‌شود: زمانی که جعبه چرخش را تمام می‌کند و شفافیت (opacity) بسته به جهت به ۰ یا ۱ می‌رسد.

اگر تأخیر یا مدت انتقال وجود نداشته باشد، یعنی هر دو ۰s باشند یا هیچ‌کدام تعریف نشده باشند، انتقالی رخ نمی‌دهد و هیچ‌کدام از رویدادهای transition فراخوانی نمی‌شوند.

اگر رویداد `transitioncancel` فراخوانی شود، رویداد `transitionend` فراخوانی نخواهد شد.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("TransitionEvent")}}
- ویژگی‌های CSS: {{cssxref("transition")}}، {{cssxref("transition-delay")}}، {{cssxref("transition-duration")}}، {{cssxref("transition-property")}}، {{cssxref("transition-timing-function")}}
- رویدادهای مرتبط: {{domxref("Element/transitionrun_event", "transitionrun")}}، {{domxref("Element/transitionstart_event", "transitionstart")}}، {{domxref("Element/transitioncancel_event", "transitioncancel")}}