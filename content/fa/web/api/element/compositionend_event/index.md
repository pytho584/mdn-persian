---
title: "Element: compositionend event"
short-title: compositionend
slug: Web/API/Element/compositionend_event
page-type: web-api-event
browser-compat: api.Element.compositionend_event
---

{{APIRef("UI Events")}}

رویداد **`compositionend`** زمانی پرتاب می‌شود که یک سامانهٔ ترکیب متن، مانند یک {{glossary("input method editor")}} (ویرایشگر روش ورودی)، نشستِ ترکیبِ فعلی را کامل یا لغو کند.

برای نمونه، این رویداد می‌تواند پس از آنکه کاربر با استفاده از یک {{glossary("Input method editor")}} (ویرایشگر روش ورودی) مبتنی بر [پینیین](https://en.wikipedia.org/wiki/Pinyin) یک نویسهٔ چینی را وارد کرد، پرتاب شود.

## نحو (Syntax)

برای استفاده از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا تنظیم یک ویژگیِ کنترل‌کنندهٔ رویداد (event handler property) می‌توانید از آن بهره ببرید.

```js-nolint
addEventListener("compositionend", (event) => { })

oncompositionend = (event) => { }
```

## نوع رویداد

یک {{domxref("CompositionEvent")}}. به ارث‌گرفته‌شده از {{domxref("UIEvent")}} و {{domxref("Event")}}.

{{InheritanceDiagram("CompositionEvent")}}

## مثال‌ها

```js
const inputElement = document.querySelector('input[type="text"]');

inputElement.addEventListener("compositionend", (event) => {
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

#### جاوااسکریپت

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

- رویدادهای مرتبط: {{domxref("Element/compositionstart_event", "compositionstart")}}، {{domxref("Element/compositionupdate_event", "compositionupdate")}}.