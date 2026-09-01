---
title: "Element: scroll event"
short-title: scroll
slug: Web/API/Element/scroll_event
page-type: web-api-event
browser-compat: api.Element.scroll_event
---

{{APIRef("CSSOM view API")}}

رویداد **`scroll`** زمانی رخ می‌دهد که یک عنصر اسکرول شده باشد. برای تشخیص زمان تکمیل اسکرول، به رویداد {{domxref("Element/scrollend_event", "scrollend")}} عنصر مراجعه کنید.

## نحو (Syntax)

برای استفاده از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}}، یا برای تنظیم یک ویژگی کنترل‌کننده رویداد، از الگوی زیر استفاده کنید:

```js-nolint
addEventListener("scroll", (event) => { })

onscroll = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

مثال‌های زیر نحوه استفاده از رویداد `scroll` را با یک شنونده رویداد و با ویژگی کنترل‌کننده رویداد `onscroll` نشان می‌دهند. از روش {{DOMxRef("Window.setTimeout", "setTimeout()")}} برای محدودسازی ({{glossary("throttle")}}) کنترل‌کننده رویداد استفاده می‌شود، زیرا رویدادهای `scroll` می‌توانند با نرخ بالایی رخ دهند. برای مثال‌های بیشتری که از {{DOMxRef("Window.requestAnimationFrame()", "requestAnimationFrame()")}} استفاده می‌کنند، به صفحه رویداد `scroll` در سند `Document` مراجعه کنید.

### استفاده از `scroll` با شنونده رویداد

مثال زیر نحوه استفاده از رویداد `scroll` را برای تشخیص زمانی که کاربر در داخل یک عنصر در حال اسکرول است نشان می‌دهد:

```html
<div id="scroll-box">
  <p>Scroll me!</p>
</div>
<p id="output">Waiting on scroll events...</p>
```

```css
#scroll-box {
  overflow: scroll;
  height: 100px;
  width: 100px;
  float: left;
}

#scroll-box p {
  height: 200px;
  width: 200px;
}

#output {
  text-align: center;
}
```

```js
const element = document.querySelector("div#scroll-box");
const output = document.querySelector("p#output");

element.addEventListener("scroll", (event) => {
  output.textContent = "Scroll event fired!";
  setTimeout(() => {
    output.textContent = "Waiting on scroll events...";
  }, 1000);
});
```

{{EmbedLiveSample("Using_scroll_with_an_event_listener", "100%", 120)}}

### استفاده از ویژگی کنترل‌کننده رویداد `onscroll`

مثال زیر نحوه استفاده از ویژگی کنترل‌کننده رویداد `onscroll` را برای تشخیص زمانی که کاربر در حال اسکرول است نشان می‌دهد:

```html
<div id="scroll-box">
  <p>Scroll me!</p>
</div>
<p id="output">Waiting on scroll events...</p>
```

```css
#scroll-box {
  overflow: scroll;
  height: 100px;
  width: 100px;
  float: left;
}

#scroll-box p {
  height: 200px;
  width: 200px;
}

#output {
  text-align: center;
}
```

```js
const element = document.querySelector("div#scroll-box");
const output = document.querySelector("p#output");

element.onscroll = (event) => {
  output.textContent = "Element scroll event fired!";
  setTimeout(() => {
    output.textContent = "Waiting on scroll events...";
  }, 1000);
};
```

{{EmbedLiveSample("Using_onscroll_event_handler_property", "100%", 120)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [رویداد `scrollend` برای عنصر](/en-US/docs/Web/API/Element/scrollend_event)
- [رویداد `scroll` برای سند](/en-US/docs/Web/API/Document/scroll_event)
- [رویداد `scrollend` برای سند](/en-US/docs/Web/API/Document/scrollend_event)