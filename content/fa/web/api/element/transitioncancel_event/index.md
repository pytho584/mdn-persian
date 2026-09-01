---
title: "Element: transitioncancel event"
---

---
title: "Element: transitioncancel event"
short-title: transitioncancel
slug: Web/API/Element/transitioncancel_event
page-type: web-api-event
browser-compat: api.Element.transitioncancel_event
---

{{APIRef}}

رویداد **`transitioncancel`** زمانی رخ می‌دهد که یک [CSS transition](/en-US/docs/Web/CSS/Guides/Transitions/Using) لغو شود.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("transitioncancel", (event) => { })

ontransitioncancel = (event) => { }
```

## نوع رویداد

یک {{domxref("TransitionEvent")}}. از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("TransitionEvent")}}

## مثال‌ها

این کد یک عنصر را که ترنزیشن برای آن تعریف شده است دریافت می‌کند و یک شنونده به رویداد `transitioncancel` اضافه می‌کند:

```js
const transition = document.querySelector(".transition");

transition.addEventListener("transitioncancel", () => {
  console.log("Transition canceled");
});
```

همین کار، اما با استفاده از ویژگی `ontransitioncancel` به جای `addEventListener()`:

```js
const transition = document.querySelector(".transition");

transition.ontransitioncancel = () => {
  console.log("Transition canceled");
};
```

### مثال زنده

در مثال زیر، یک عنصر ساده {{htmlelement("div")}} داریم که با یک ترنزیشن شامل تأخیر (delay) استایل داده شده است:

```html
<div class="transition"></div>
<div class="message"></div>
```

```css
.transition {
  width: 100px;
  height: 100px;
  background: red;
  transition-property: transform, background;
  transition-duration: 2s;
  transition-delay: 2s;
}

.transition:hover {
  transform: rotate(90deg);
  background: transparent;
}
```

برای این کار، کمی جاوااسکریپت اضافه می‌کنیم تا مشخص شود که رویدادهای [`transitionstart`](/en-US/docs/Web/API/Element/transitionstart_event)، [`transitionrun`](/en-US/docs/Web/API/Element/transitionrun_event)، `transitioncancel` و [`transitionend`](/en-US/docs/Web/API/Element/transitionend_event) رخ می‌دهند. در این مثال، برای لغو ترنزیشن، قبل از پایان ترنزیشن، هاور کردن روی جعبه در حال انتقال را متوقف کنید. برای اینکه رویداد پایان ترنزیشن رخ دهد، تا پایان ترنزیشن روی آن هاور بمانید.

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

رویداد `transitioncancel` در صورتی رخ می‌دهد که ترنزیشن در هر جهتی، پس از رخ دادن رویداد `transitionrun` و قبل از رخ دادن `transitionend` لغو شود.

اگر ترنزیشن هیچ تأخیر یا مدتی نداشته باشد، اگر هر دو 0s باشند یا هیچ‌کدام تعریف نشده باشند، ترنزیشنی وجود ندارد و هیچ‌یک از رویدادهای ترنزیشن رخ نمی‌دهند.

اگر رویداد `transitioncancel` رخ دهد، رویداد `transitionend` رخ نخواهد داد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("TransitionEvent")}}
- ویژگی‌های CSS: {{cssxref("transition")}}, {{cssxref("transition-delay")}}, {{cssxref("transition-duration")}}, {{cssxref("transition-property")}}, {{cssxref("transition-timing-function")}}
- رویدادهای مرتبط: {{domxref("Element/transitionrun_event", "transitionrun")}}, {{domxref("Element/transitionstart_event", "transitionstart")}}, {{domxref("Element/transitionend_event", "transitionend")}}