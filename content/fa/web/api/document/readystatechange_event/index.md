---
title: "Document: readystatechange event"
short-title: readystatechange
slug: Web/API/Document/readystatechange_event
page-type: web-api-event
browser-compat: api.Document.readystatechange_event
---

{{APIRef("DOM")}}

رویداد **`readystatechange`** زمانی فعال می‌شود که ویژگی {{domxref("Document.readyState", "readyState")}} یک سند تغییر کند.

این رویداد قابل لغو نیست و به صورت حباب‌وار منتشر نمی‌شود.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("readystatechange", (event) => { })

onreadystatechange = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

### مثال زنده

#### HTML

```html
<div class="controls">
  <button id="reload" type="button">Reload</button>
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

#### CSS

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

#reload {
  height: 2rem;
}
```

#### JavaScript

```js
const log = document.querySelector(".event-log-contents");
const reload = document.querySelector("#reload");

reload.addEventListener("click", () => {
  log.textContent = "";
  setTimeout(() => {
    window.location.reload(true);
  }, 200);
});

window.addEventListener("load", (event) => {
  log.textContent = `${log.textContent}load\n`;
});

document.addEventListener("readystatechange", (event) => {
  log.textContent = `${log.textContent}readystate: ${document.readyState}\n`;
});

document.addEventListener("DOMContentLoaded", (event) => {
  log.textContent = `${log.textContent}DOMContentLoaded\n`;
});
```

#### نتیجه

{{ EmbedLiveSample('Live_example', '100%', '160px') }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رویدادهای مرتبط: [`DOMContentLoaded`](/en-US/docs/Web/API/Document/DOMContentLoaded_event)، [`load`](/en-US/docs/Web/API/Window/load_event)، [`beforeunload`](/en-US/docs/Web/API/Window/beforeunload_event)، [`unload`](/en-US/docs/Web/API/Window/unload_event)