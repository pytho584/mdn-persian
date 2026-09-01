---
title: "Element: compositionstart event"
short-title: compositionstart
slug: Web/API/Element/compositionstart_event
page-type: web-api-event
browser-compat: api.Element.compositionstart_event
---

{{APIRef("UI Events")}}

هنگامی که یک سیستم ترکیب متن مانند {{glossary("input method editor")}} یک نشست جدیدِ ترکیب را آغاز می‌کند، رویداد **`compositionstart`** فعال می‌شود.

برای مثال، این رویداد ممکن است پس از آن‌که کاربر با استفاده از یک {{glossary("Input method editor")}} مبتنی بر [پینیین](https://en.wikipedia.org/wiki/Pinyin) شروع به وارد کردن یک کاراکتر چینی می‌کند، فعال شود.

## نحو (Syntax)

برای استفاده از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا تنظیم ویژگیِ کنترل‌کننده رویداد، آن را به کار ببرید.

```js-nolint
addEventListener("compositionstart", (event) => { })

oncompositionstart = (event) => { }
```

## نوع رویداد

یک {{domxref("CompositionEvent")}}. به ارث‌برده از {{domxref("UIEvent")}} و {{domxref("Event")}}.

{{InheritanceDiagram("CompositionEvent")}}

## مثال‌ها

```js
const inputElement = document.querySelector('input[type="text"]');

inputElement.addEventListener("compositionstart", (event) => {
  console.log(`generated characters were: ${event.data}`);
});
```

### مثال زنده

#### HTML

```html
<div class="control">
  <label for="example">
    روی فیلد متنی تمرکز کنید، سپس روش ورودی (IME) خود را باز کرده و شروع به تایپ کنید.
  </label>
  <input type="text" id="example" name="example" />
</div>

<div class="event-log">
  <label for="eventLog">گزارش رویداد:</label>
  <textarea
    readonly
    class="event-log-contents"
    rows="8"
    cols="25"
    id="eventLog"></textarea>
  <button class="clear-log">پاک کردن</button>
</div>
```

```css hidden
body {
  padding: 0.2rem;
  display: grid;
  grid-template-areas: "control log";
}

.control {
  grid-area: control;
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

input[type="text"] {
  margin: 0.5rem 0;
}

kbd {
  border-radius: 3px;
  padding: 1px 2px 0;
  border: 1px solid black;
}
```

#### JavaScript

```js
const inputElement = document.querySelector('input[type="text"]');
const log = document.querySelector(".event-log-contents");
const clearLog = document.querySelector(".clear-log");

clearLog.addEventListener("click", () => {
  log.textContent = "";
});

function handleEvent(event) {
  log.textContent += `${event.type}: ${event.data}\n`;
}

inputElement.addEventListener("compositionstart", handleEvent);
inputElement.addEventListener("compositionupdate", handleEvent);
inputElement.addEventListener("compositionend", handleEvent);
```

#### نتیجه

{{ EmbedLiveSample('Live_example', '100%', '180px') }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویدادهای مرتبط: {{domxref("Element/compositionend_event", "compositionend")}}، {{domxref("Element/compositionupdate_event", "compositionupdate")}}.