---
title: "HTMLElement: error event"
short-title: error
slug: Web/API/HTMLElement/error_event
page-type: web-api-event
browser-compat: api.HTMLElement.error_event
---

{{APIRef("HTML DOM")}}

رویداد `error` روی یک عنصر زمانی رخ می‌دهد که منبعی نتواند بارگذاری شود یا قابل استفاده نباشد. برای مثال، اگر یک اسکریپت خطای اجرا داشته باشد یا تصویری پیدا نشود یا نامعتبر باشد.

این رویداد قابل لغو نیست و حباب‌زنی (bubbling) ندارد.

## نحو (Syntax)

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("error", (event) => { })

onerror = (event) => { }
```

## نوع رویداد

شیء رویداد، اگر از یک عنصر رابط کاربری تولید شده باشد، نمونه‌ای از {{domxref("UIEvent")}} و در غیر این صورت نمونه‌ای از {{domxref("Event")}} است.

{{InheritanceDiagram("UIEvent")}}

## مثال‌ها

### مثال زنده

#### HTML

```html
<div class="controls">
  <button id="img-error" type="button">Generate image error</button>
  <img src="bad-image.jpg" class="bad-img" alt="I don't exist" />
</div>

<div class="event-log">
  <label for="eventLog">Event log:</label>
  <textarea
    readonly
    class="event-log-contents"
    rows="8"
    cols="30"
    id="eventLog"></textarea>
</div>
```

```css hidden
body {
  display: grid;
  grid-template-areas: "control log";
}

.controls {
  grid-area: control;
  display: flex;
  align-items: center;
  justify-content: center;
}

.event-log {
  grid-area: log;
}

.event-log-contents {
  resize: none;
}

label,
button {
  display: block;
}

button {
  height: 2rem;
  margin: 0.5rem;
}

img {
  width: 0;
  height: 0;
}
```

#### JavaScript

```js
const log = document.querySelector(".event-log-contents");

const badImg = document.querySelector(".bad-img");
badImg.addEventListener("error", (event) => {
  log.textContent += `${event.type}: Loading image\n`;
  console.log(event);
});

const imgError = document.querySelector("#img-error");
imgError.addEventListener("click", () => {
  badImg.setAttribute("src", "i-dont-exist");
});
```

#### نتیجه

{{ EmbedLiveSample('Live_example', '100%', '150px') }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویدادهای مرتبط
  - Window: رویداد {{domxref("Window/error_event", "error")}}
  - HTMLElement: رویداد {{domxref("HTMLElement/load_event", "load")}}