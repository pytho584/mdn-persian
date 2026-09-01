---
title: "Element: compositionupdate event"
short-title: compositionupdate
slug: Web/API/Element/compositionupdate_event
page-type: web-api-event
browser-compat: api.Element.compositionupdate_event
---

{{APIRef("UI Events")}}

رویداد **`compositionupdate`** زمانی رخ می‌دهد که یک نویسهٔ جدید در بافت یک نشستِ ترکیب متن (text composition) دریافت شود؛ نشستی که توسط یک سامانهٔ ترکیب متن، مانند {{glossary("input method editor")}} (ویرایشگر روش ورودی)، کنترل می‌شود.

به‌عنوان مثال، این رویداد می‌تواند هنگام وارد کردن یک نویسهٔ چینی توسط کاربر با استفاده از یک {{glossary("Input method editor")}} مبتنی بر [پینیین](https://en.wikipedia.org/wiki/Pinyin) پرتاب شود.

## نحو (Syntax)

برای استفاده، نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به‌کار ببرید، یا یک ویژگی مدیریت‌کنندهٔ رویداد (event handler) تنظیم کنید.

```js-nolint
addEventListener("compositionupdate", (event) => { })

oncompositionupdate = (event) => { }
```

## نوع رویداد

یک {{domxref("CompositionEvent")}} که از {{domxref("UIEvent")}} و {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("CompositionEvent")}}

## نمونه‌ها

```js
const inputElement = document.querySelector('input[type="text"]');

inputElement.addEventListener("compositionupdate", (event) => {
  console.log(`generated characters were: ${event.data}`);
});
```

### مثال زنده

#### HTML

```html
<div class="control">
  <p>First select textbox, then to open IME:</p>
  <ul>
    <li>on macOS type <kbd>option</kbd> + <kbd>`</kbd></li>
    <li>on Windows type <kbd>windows</kbd> + <kbd>.</kbd></li>
  </ul>
  <label for="example">Example input</label>
  <input type="text" id="example" name="example" />
</div>

<div class="event-log">
  <label for="eventLog">Event log:</label>
  <textarea
    readonly
    class="event-log-contents"
    rows="8"
    cols="25"
    id="eventLog"></textarea>
  <button class="clear-log">Clear</button>
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

- رویدادهای مرتبط: {{domxref("Element/compositionstart_event", "compositionstart")}}, {{domxref("Element/compositionend_event", "compositionend")}}.