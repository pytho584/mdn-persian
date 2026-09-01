---
title: "HTMLDialogElement: close event"
short-title: close
slug: Web/API/HTMLDialogElement/close_event
page-type: web-api-event
browser-compat: api.HTMLDialogElement.close_event
---

{{APIRef("HTML DOM")}}

رویداد `close` روی یک شیء `HTMLDialogElement` زمانی رخ می‌دهد که عنصر {{htmlelement("dialog")}} که آن را نشان می‌دهد بسته شده باشد.

این رویداد قابل لغو نیست و منتشر نمی‌شود (bubble نمی‌کند).

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("close", (event) => { })

onclose = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

### مدیریت رویدادهای `close`

این مثال نشان می‌دهد که چگونه می‌توان به رویدادهای `close` که توسط روش‌های مختلف بستن یک دیالوگ ایجاد می‌شوند گوش داد:

- فراخوانی روش {{domxref("HTMLDialogElement.close()", "close()")}}
- یک فرم با `method="dialog"`. ارسال فرم، `dialog` را می‌بندد و باعث می‌شود یک رویداد {{domxref("HTMLFormElement/submit_event", "submit")}} رخ دهد، بدون اینکه داده‌ای ارسال شود یا فرم پاک شود.
- کلید <kbd>Esc</kbd>. به رویداد {{domxref("HTMLDialogElement/cancel_event", "cancel")}} مراجعه کنید.

#### HTML

```html
<dialog id="dialog">
  <form method="dialog">
    <button type="submit">Close via method="dialog"</button>
  </form>
  <p><button id="close">Close via .close() method</button></p>
  <p>Or hit the <kbd>Esc</kbd> key</p>
</dialog>

<button id="open">Open dialog</button>
```

```html hidden
<pre id="log"></pre>
```

```css hidden
#log {
  height: 170px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

```js hidden
const logElement = document.getElementById("log");
function log(text, clear = false) {
  if (clear) {
    logElement.innerText = "";
  }
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

#### JavaScript

```js
const dialog = document.getElementById("dialog");
const openButton = document.getElementById("open");
const closeButton = document.getElementById("close");

openButton.addEventListener("click", () => {
  log("open button click event fired", true);
  log("dialog showModal() called");
  dialog.showModal();
});

closeButton.addEventListener("click", () => {
  log("close button click event fired");
  log("dialog close() called");
  dialog.close();
});

dialog.addEventListener("close", (event) => {
  log("dialog close event fired");
});
```

#### نتیجه

{{ EmbedLiveSample('Handling `close` events', '100%', '250px') }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML {{htmlelement("dialog")}}