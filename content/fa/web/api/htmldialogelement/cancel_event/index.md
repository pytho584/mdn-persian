---
title: "HTMLDialogElement: cancel event"
short-title: cancel
slug: Web/API/HTMLDialogElement/cancel_event
page-type: web-api-event
browser-compat: api.HTMLDialogElement.cancel_event
---

{{APIRef("HTML DOM")}}

رویداد **`cancel`** هنگامی بر روی یک عنصر {{HTMLElement("dialog")}} رخ می‌دهد که کاربر یک درخواست بستن را ایجاد کند.

از کنترل‌کننده رویداد `cancel` می‌توان برای نادیده گرفتن رفتار پیش‌فرض در هنگام دریافت درخواست بستن و جلوگیری از بسته شدن دیالوگ استفاده کرد. اگر رفتار پیش‌فرض لغو نشود، دیالوگ بسته می‌شود و یک رویداد {{domxref("HTMLDialogElement/close_event", "close")}} را فعال می‌کند.

درخواست‌های بستن ممکن است توسط موارد زیر ایجاد شوند:

- فشار دادن کلید <kbd>Esc</kbd> در پلتفرم‌های رومیزی
- فراخوانی متد {{domxref("HTMLDialogElement.requestClose()", "requestClose()")}}
- دکمه بازگشت در پلتفرم‌های موبایل

این رویداد قابل لغو است و حباب نمی‌زند.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("cancel", (event) => { })

oncancel = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

### لغو یک دیالوگ

مثال زیر یک دکمه را نشان می‌دهد که با کلیک روی آن، یک {{htmlelement("dialog")}} با استفاده از متد {{domxref("HTMLDialogElement.showModal()", "showModal()")}} باز می‌شود.

می‌توانید رویداد `cancel` را با کلیک کردن روی دکمه _Request Close_ برای بستن دیالوگ (از طریق متد {{domxref("HTMLDialogElement.requestClose()", "requestClose()")}}) یا با فشار دادن کلید <kbd>Esc</kbd> فعال کنید.

توجه داشته باشید که کنترل‌کننده رویداد `cancel` رویداد را ثبت می‌کند و سپس برمی‌گردد و اجازه می‌دهد دیالوگ بسته شود (که به نوبه خود باعث انتشار رویداد `close` می‌شود). می‌توانید خط حاوی `event.preventDefault()` را از حالت توضیح خارج کنید تا رویداد لغو شود.

#### HTML

```html
<dialog id="dialog">
  <button type="button" id="request-close">Request Close</button>
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

#### JavaScript

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

```js
const dialog = document.getElementById("dialog");
const openButton = document.getElementById("open");
const requestCloseButton = document.getElementById("request-close");

// Open button opens a modal dialog
openButton.addEventListener("click", () => {
  log("open button click event fired", true);
  log("dialog showModal() called");
  dialog.showModal();
});

// Request close
requestCloseButton.addEventListener("click", () => {
  log("request close button click event fired");
  log("dialog requestClose() called");
  // Triggers the cancel event
  dialog.requestClose();
});

// Fired when requestClose() is called
// Prevent the dialog from closing by calling event.preventDefault()
dialog.addEventListener("cancel", (event) => {
  log("dialog cancel event fired");
  // Uncomment the next two lines to prevent the dialog from closing
  // log("dialog close cancelled");
  // event.preventDefault();
});

dialog.addEventListener("close", (event) => {
  log("dialog close event fired");
});
```

#### نتیجه

{{ EmbedLiveSample('Canceling a dialog', '100%', '250px') }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML {{HTMLElement("dialog")}}