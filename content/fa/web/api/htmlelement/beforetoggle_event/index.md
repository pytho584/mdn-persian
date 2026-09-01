---
title: "HTMLElement: beforetoggle event"
slug: Web/API/HTMLElement/beforetoggle_event
page-type: web-api-event
browser-compat: api.HTMLElement.beforetoggle_event
---

{{APIRef("HTML DOM")}}

رویداد **`beforetoggle`** از رابط {{domxref("HTMLElement")}}، درست پیش از نمایش یا پنهان‌شدن یک عنصر {{domxref("Popover_API", "popover", "", "nocode")}} یا {{htmlelement("dialog")}} روی آن عنصر رخ می‌دهد.

- اگر عنصر در حال گذار از حالت پنهان به نمایان باشد، خاصیت [`event.oldState`](/en-US/docs/Web/API/ToggleEvent/oldState) روی `closed` و خاصیت [`event.newState`](/en-US/docs/Web/API/ToggleEvent/newState) روی `open` تنظیم می‌شود.
- اگر عنصر در حال گذار از حالت نمایان به پنهان باشد، آنگاه `event.oldState` برابر `open` و `event.newState` برابر `closed` خواهد بود.

این رویداد زمانی که عنصر به حالت باز («نمایش») تغییر وضعیت می‌دهد [قابل‌لغو](/en-US/docs/Web/API/Event/cancelable) است، اما زمانی که عنصر در حال بسته‌شدن است قابل‌لغو نیست.

از جمله کاربردهای این رویداد می‌توان به موارد زیر اشاره کرد:

- جلوگیری از نمایش یک عنصر.
- افزودن یا حذف کلاس‌ها یا ویژگی‌ها به عنصر یا عناصر مرتبط، مثلاً برای کنترل رفتار انیمیشن یک دیالوگ هنگام باز و بسته شدن.
- پاک‌سازی وضعیت عنصر پیش از باز شدن یا پس از پنهان شدن، مثلاً برای بازنشانی فرم یک دیالوگ و مقدار بازگشتی به حالت خالی، یا مخفی‌کردن هر popover دستی تو در تو هنگام باز کردن مجدد یک popup.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("beforetoggle", (event) => { })

onbeforetoggle = (event) => { }
```

## نوع رویداد

یک {{domxref("ToggleEvent")}}. به ارث‌برده از {{domxref("Event")}}.

{{InheritanceDiagram("ToggleEvent")}}

## مثال‌ها

مثال‌های زیر نشان می‌دهند که چگونه می‌توان از رویداد `beforetoggle` برای یک عنصر {{domxref("Popover_API", "popover", "", "nocode")}} استفاده کرد.
همین مثال‌ها به شکل مشابهی روی عنصر {{htmlelement("dialog")}} نیز کار می‌کنند.

### مثال پایه

این مثال نشان می‌دهد که چگونه به رویداد `beforetoggle` گوش دهید و نتیجه را ثبت کنید.

#### HTML

HTML شامل یک popover و یک دکمه برای باز و بسته کردن آن است.

```html
<button popovertarget="mypopover">Toggle the popover</button>
<div id="mypopover" popover>Popover content</div>
```

```html hidden
<pre id="log"></pre>
```

```css hidden
#log {
  height: 150px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

#### JavaScript

کد یک شنونده رویداد برای رویداد `beforetoggle` اضافه می‌کند و وضعیت را ثبت می‌کند.

```js
const popover = document.getElementById("mypopover");

popover.addEventListener("beforetoggle", (event) => {
  if (event.newState === "open") {
    log("Popover is about to be shown");
  } else {
    log("Popover is about to be hidden");
  }
});
```

#### نتیجه

{{EmbedLiveSample("Basic example", '100%', "250px")}}

### جلوگیری از باز شدن popover

رویداد `beforetoggle` زمانی که هنگام باز شدن یک عنصر رخ می‌دهد قابل‌لغو است.

در زیر نشان می‌دهیم که چگونه یک popover می‌تواند ابتدا بررسی کند که آیا اجازه باز شدن دارد یا خیر، و اگر نه، متد {{domxref("Event.preventDefault()")}} را فراخوانی کند تا رویداد لغو شود.
در این مثال از یک چک‌باکس برای تعیین اینکه آیا popover می‌تواند باز شود یا نه استفاده می‌کنیم؛ در یک مثال «کامل‌تر» این ممکن است به وضعیت برنامه یا آماده بودن داده‌های داخل popover برای نمایش بستگی داشته باشد.

#### HTML

HTML شامل یک popover، یک دکمه برای باز و بسته کردن آن، و یک چک‌باکس برای تعیین اینکه آیا popover می‌تواند باز شود یا نه است.

```html
<button popovertarget="mypopover">Toggle the popover</button>
<label for="allow-popover">
  Allow opening <input type="checkbox" id="allow-popover" checked />
</label>
<div id="mypopover" popover>Popover content</div>
```

```html hidden
<pre id="log"></pre>
```

```css hidden
#log {
  height: 150px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

#### JavaScript

ابتدا کدی را برای شبیه‌سازی وضعیتی که می‌خواهیم اجازه باز شدن popover را بدهیم تنظیم می‌کنیم.
این وضعیت با متغیر `allowOpen` نمایش داده می‌شود که با تغییر وضعیت چک‌باکس مرتبط، تغییر می‌کند.

```js
const allowCheckbox = document.getElementById("allow-popover");

let allowOpen = true;

allowCheckbox.addEventListener("change", (event) => {
  allowOpen = allowCheckbox.checked;
});
```

کد یک شنونده رویداد برای رویداد `beforetoggle` اضافه می‌کند.
اگر `allowOpen` برابر `false` باشد، متد `preventDefault()` فراخوانی می‌شود که از باز شدن popup جلوگیری می‌کند.

```js
const popover = document.getElementById("mypopover");

popover.addEventListener("beforetoggle", (event) => {
  if (event.newState === "open") {
    if (allowOpen) {
      log("Popover is about to be shown");
    } else {
      log("Popover opening prevented");
      event.preventDefault();
    }
  } else {
    log("Popover is about to be hidden");
  }
});
```

#### نتیجه

{{EmbedLiveSample("Prevent a popover opening", '100%', "250px")}}

### سایر مثال‌ها

- مثال [باز کردن یک دیالوگ مودال](/en-US/docs/Web/API/HTMLDialogElement#open_close_a_modal_dialog) در `HTMLDialogElement`

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی سراسری HTML [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover)
- [Popover API](/en-US/docs/Web/API/Popover_API)
- رویداد مرتبط: [`toggle`](/en-US/docs/Web/API/HTMLElement/toggle_event)