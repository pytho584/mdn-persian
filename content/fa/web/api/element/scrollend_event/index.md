---
title: "Element: scrollend event"
short-title: scrollend
slug: Web/API/Element/scrollend_event
page-type: web-api-event
browser-compat: api.Element.scrollend_event
---

{{APIRef("CSSOM view API")}}

رویداد **`scrollend`** زمانی رخ می‌دهد که پیمایش (scroll) یک عنصر به پایان رسیده است.
پیمایش زمانی کامل در نظر گرفته می‌شود که موقعیت پیمایش هیچ به‌روزرسانی در انتظاری نداشته باشد و کاربر حرکت خود را به پایان رسانده باشد.

به‌روزرسانی‌های موقعیت پیمایش شامل پیمایش نرم یا آنی با چرخ ماوس، پیمایش با صفحه‌کلید، رویدادهای scroll-snap یا سایر APIها و حرکاتی که باعث به‌روزرسانی موقعیت پیمایش می‌شوند، می‌باشد.
حرکات کاربر مانند پان کردن لمسی یا پیمایش با ترک‌پد تا زمانی که اشاره‌گرها یا کلیدها رها نشوند، کامل نیستند.
اگر موقعیت پیمایش تغییر نکند، هیچ رویداد scrollend‌ای رخ نخواهد داد.

برای تشخیص پایان پیمایش درون یک سند، به رویداد {{domxref("Document/scrollend_event", "scrollend")}} در `Document` مراجعه کنید.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("scrollend", (event) => { })

onscrollend = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال

### استفاده از `scrollend` با یک شنونده رویداد

مثال زیر نحوه استفاده از رویداد `scrollend` برای تشخیص زمانی که کاربر پیمایش را متوقف کرده است را نشان می‌دهد:

```css hidden
#scroll-box {
  height: 100px;
  width: 100px;
  float: left;
  overflow: scroll;
  outline: 4px dotted;
  margin: 4px;
}

#scroll-box-title {
  position: fixed;
  top: 5px;
  left: 5px;
  transform: translateX(0);
}

#large-element {
  height: 200px;
  width: 200px;
}

#output {
  text-align: center;
}
```

```html
<div id="scroll-box">
  <p id="scroll-box-title">Scroll me!</p>
  <p id="large-element"></p>
</div>
<p id="output">Waiting on scroll events...</p>
```

```js
const element = document.querySelector("div#scroll-box");
const output = document.querySelector("p#output");

element.addEventListener("scroll", (event) => {
  output.textContent = "scroll event fired, waiting for scrollend...";
});

element.addEventListener("scrollend", (event) => {
  output.textContent = "scrollend event fired!";
});
```

{{EmbedLiveSample("Using_scrollend_with_an_event_listener", "100%", 130)}}

### استفاده از ویژگی کنترل‌کننده رویداد `onscrollend`

مثال زیر نحوه استفاده از ویژگی کنترل‌کننده رویداد `onscrollend` برای تشخیص زمانی که کاربر پیمایش را متوقف کرده است را نشان می‌دهد:

```css hidden
#scroll-box {
  height: 100px;
  width: 100px;
  float: left;
  overflow: scroll;
  outline: 4px dotted;
  margin: 4px;
}

#scroll-box-title {
  position: fixed;
  top: 5px;
  left: 5px;
  transform: translateX(0);
}

#large-element {
  height: 200px;
  width: 200px;
}

#output {
  text-align: center;
}
```

```html
<div id="scroll-box">
  <p id="scroll-box-title">Scroll me!</p>
  <p id="large-element"></p>
</div>
<p id="output">Waiting on scroll events...</p>
```

```js
const element = document.querySelector("div#scroll-box");
const output = document.querySelector("p#output");

element.onscroll = (event) => {
  output.textContent = "Element scroll event fired, waiting for scrollend...";
};

element.onscrollend = (event) => {
  output.textContent = "Element scrollend event fired!";
};
```

{{EmbedLiveSample("Using_onscrollend_event_handler_property", "100%", 130)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [رویداد `scroll` در عنصر](/en-US/docs/Web/API/Element/scroll_event)
- [رویداد `scrollend` در سند](/en-US/docs/Web/API/Document/scrollend_event)
- [رویداد `scroll` در سند](/en-US/docs/Web/API/Document/scroll_event)