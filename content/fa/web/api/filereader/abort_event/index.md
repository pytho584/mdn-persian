---
title: "FileReader: abort event"
short-title: abort
slug: Web/API/FileReader/abort_event
page-type: web-api-event
browser-compat: api.FileReader.abort_event
---

{{APIRef("File API")}}{{AvailableInWorkers}}

رویداد **`abort`** از رابط {{domxref("FileReader")}} زمانی رخ می‌دهد که یک خوانش لغو شده باشد؛ به عنوان مثال به این دلیل که برنامه متد {{domxref("FileReader.abort()")}} را فراخوانی کرده است.

این رویداد قابل لغو (cancelable) نیست و حباب‌زنی (bubble) نمی‌کند.

## نحو (Syntax)

برای استفاده، نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید، یا یک ویژگی رویدادگردان (event handler property) تنظیم کنید.

```js-nolint
addEventListener("abort", (event) => { })

onabort = (event) => { }
```

## نوع رویداد

یک {{domxref("ProgressEvent")}} که از {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("ProgressEvent")}}

## مثال‌ها

### مثال زنده

#### HTML

```html
<div class="example">
  <div class="file-select">
    <label for="avatar">Choose a profile picture:</label>
    <input
      type="file"
      id="avatar"
      name="avatar"
      accept="image/png, image/jpeg" />
  </div>

  <img src="" class="preview" height="200" alt="Image preview" />

  <div class="event-log">
    <label for="eventLog">Event log:</label>
    <textarea readonly class="event-log-contents" id="eventLog"></textarea>
  </div>
</div>
```

```css hidden
img.preview {
  margin: 1rem 0;
}

.event-log-contents {
  width: 18rem;
  height: 5rem;
  border: 1px solid black;
  margin: 0.2rem;
  padding: 0.2rem;
  resize: none;
}

.example {
  display: grid;
  grid-template-areas:
    "select  log"
    "preview log";
}

.file-select {
  grid-area: select;
}

.preview {
  grid-area: preview;
}

.event-log {
  grid-area: log;
}

.event-log > label {
  display: block;
}
```

#### جاوااسکریپت

```js
const fileInput = document.querySelector('input[type="file"]');
const preview = document.querySelector("img.preview");
const eventLog = document.querySelector(".event-log-contents");
const reader = new FileReader();

function handleEvent(event) {
  eventLog.textContent += `${event.type}: ${event.loaded} bytes transferred\n`;

  if (event.type === "load") {
    preview.src = reader.result;
  }
}

function addListeners(reader) {
  reader.addEventListener("loadstart", handleEvent);
  reader.addEventListener("load", handleEvent);
  reader.addEventListener("loadend", handleEvent);
  reader.addEventListener("progress", handleEvent);
  reader.addEventListener("error", handleEvent);
  reader.addEventListener("abort", handleEvent);
}

function handleSelected(e) {
  eventLog.textContent = "";
  const selectedFile = fileInput.files[0];
  if (selectedFile) {
    addListeners(reader);
    reader.readAsDataURL(selectedFile);
  }
  reader.abort();
}

fileInput.addEventListener("change", handleSelected);
```

#### نتیجه

{{ EmbedLiveSample('Live_example', '100%', '300px') }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویدادهای مرتبط: {{domxref("FileReader.loadstart_event", "loadstart")}}، {{domxref("FileReader.loadend_event", "loadend")}}، {{domxref("FileReader.progress_event", "progress")}}، {{domxref("FileReader.error_event", "error")}}، {{domxref("FileReader.load_event", "load")}}.