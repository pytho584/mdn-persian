---
title: "Document: scrollend event"
short-title: scrollend
slug: Web/API/Document/scrollend_event
page-type: web-api-event
browser-compat: api.Document.scrollend_event
---

{{APIRef("CSSOM view API")}}

رویداد **`scrollend`** زمانی رخ می‌دهد که نمای سند (document view) اسکرول را به پایان رسانده باشد. اسکرول زمانی کامل در نظر گرفته می‌شود که موقعیت اسکرول دیگر هیچ به‌روزرسانی معلقی نداشته باشد و کاربر ژست (gesture) خود را به پایان رسانده باشد.

به‌روزرسانی‌های موقعیت اسکرول شامل اسکرول نرم یا آنی با چرخ ماوس، اسکرول با صفحه‌کلید، رویدادهای scroll-snap یا هر API و ژست دیگری که باعث تغییر موقعیت اسکرول می‌شود، هستند. ژست‌های کاربر مانند کشیدن انگشت (touch panning) یا اسکرول با ترک‌پد تا زمانی که انگشت یا کلید رها نشود کامل نمی‌شوند. اگر موقعیت اسکرول تغییری نکرده باشد، رویداد `scrollend` رخ نمی‌دهد.

برای تشخیص پایان اسکرول در داخل یک عنصر، به رویداد {{domxref("Element/scrollend_event", "scrollend")}} مربوط به `Element` مراجعه کنید.

## نحو (Syntax)

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا به‌عنوان یک ویژگی مدیریت‌کننده رویداد استفاده کنید.

```js-nolint
addEventListener("scrollend", (event) => { })

onscrollend = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

### استفاده از `scrollend` سند با شنونده رویداد

مثال زیر نشان می‌دهد که چگونه می‌توان از رویداد `scrollend` با یک شنونده رویداد برای تشخیص زمانی که کاربر اسکرول سند را متوقف کرده است استفاده کرد. در این مثال، محتوایی در iframe تعبیه‌شده وجود دارد که بلندتر و عریض‌تر از خود iframe است، بنابراین اسکرول در هر دو جهت درون iframe امکان‌پذیر است. وقتی کاربر اسکرول را متوقف می‌کند، رویداد `scrollend` رخ می‌دهد:

```css hidden
* {
  margin: 10px;
}

.box-wrapper {
  width: 900px;
  border: 4px dotted;
}

.box {
  height: 100px;
  width: 100px;
  display: block;
  border: 4px dotted;
  border-radius: 10px;
}

#output {
  text-align: center;
  font-size: 1.2em;
  position: sticky;
  bottom: 0;
}
```

```html
<div class="box-wrapper">
  <div class="box"></div>
  <div class="box"></div>
  <div class="box"></div>
  <div class="box"></div>
</div>
<p id="output">Waiting on scroll events...</p>
```

```js
const output = document.querySelector("p#output");

document.addEventListener("scroll", (event) => {
  output.textContent = "Document scroll event fired!";
});

document.addEventListener("scrollend", (event) => {
  output.textContent = "Document scrollend event fired!";
});
```

{{EmbedLiveSample("Using_document_scrollend_with_an_event_listener", "100%", 200)}}

### استفاده از ویژگی مدیریت‌کننده رویداد `onscrollend`

مثال زیر نحوه استفاده از ویژگی مدیریت‌کننده رویداد `scrollend` را برای تشخیص زمانی که کاربر اسکرول سند را متوقف کرده است نشان می‌دهد. در این مثال، محتوایی در iframe تعبیه‌شده وجود دارد که بلندتر و عریض‌تر از خود iframe است، بنابراین اسکرول در هر دو جهت درون iframe امکان‌پذیر است. این مثال بر پایه مثال اول ساخته شده است، اما به جای شنونده رویداد از `document.onscrollend` استفاده می‌کند:

```css hidden
* {
  margin: 10px;
}

.box-wrapper {
  width: 900px;
  border: 4px dotted;
}

.box {
  height: 100px;
  width: 100px;
  display: block;
  border: 4px dotted;
  border-radius: 10px;
}

#output {
  text-align: center;
  font-size: 1.2em;
  position: sticky;
  bottom: 0;
}
```

```html
<div class="box-wrapper">
  <div class="box"></div>
  <div class="box"></div>
  <div class="box"></div>
  <div class="box"></div>
</div>
<p id="output">Waiting on scroll events...</p>
```

```js
document.onscroll = (event) => {
  output.textContent = "Document scroll event fired!";
};

document.onscrollend = (event) => {
  output.textContent = "Document scrollend event fired!";
};
```

{{EmbedLiveSample("Using_scrollend_with_an_event_handler_property", "100%", 200)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [رویداد `scroll` سند](/en-US/docs/Web/API/Document/scroll_event)
- [رویداد `scrollend` عنصر](/en-US/docs/Web/API/Element/scrollend_event)
- [رویداد `scroll` عنصر](/en-US/docs/Web/API/Element/scroll_event)