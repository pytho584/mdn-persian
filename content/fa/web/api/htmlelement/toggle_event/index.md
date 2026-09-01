---
title: "HTMLElement: toggle event"
slug: Web/API/HTMLElement/toggle_event
page-type: web-api-event
browser-compat: api.HTMLElement.toggle_event
---

{{APIRef("HTML DOM")}}

رویداد **`toggle`** در رابط {{domxref("HTMLElement")}} دقیقاً پس از نمایش یا پنهان‌شدن یک عنصر {{domxref("Popover_API", "popover", "", "nocode")}}، عنصر {{htmlelement("dialog")}} یا عنصر {{htmlelement("details")}} رخ می‌دهد.

- اگر عنصر از حالت پنهان به حالت نمایش در حال تغییر باشد، ویژگی [`event.oldState`](/en-US/docs/Web/API/ToggleEvent/oldState) روی `closed` تنظیم می‌شود و ویژگی [`event.newState`](/en-US/docs/Web/API/ToggleEvent/newState) روی `open` تنظیم می‌شود.
- اگر عنصر از حالت نمایش به حالت پنهان در حال تغییر باشد، `event.oldState` برابر `open` و `event.newState` برابر `closed` خواهد بود.

این رویداد [cancelable](/en-US/docs/Web/API/Event/cancelable) نیست.

## نحو

برای استفاده از نام رویداد، می‌توانید آن را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید یا یک ویژگی کنترل‌کنندهٔ رویداد (event handler) تنظیم کنید.

```js-nolint
addEventListener("toggle", (event) => { })

ontoggle = (event) => { }
```

## نوع رویداد

یک {{domxref("ToggleEvent")}} که از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("ToggleEvent")}}

## مثال‌ها

کد مثال زیر نشان می‌دهد که چگونه می‌توان از رویداد `toggle` برای {{domxref("Popover_API", "popover", "", "nocode")}} استفاده کرد. از همین کد می‌توان به همین شکل برای عناصر {{htmlelement("dialog")}} یا {{htmlelement("details")}} نیز استفاده کرد.

### مثال پایه

این مثال نشان می‌دهد که چگونه به رویداد `toggle` گوش دهید و نتیجه را ثبت (log) کنید.

#### HTML

HTML شامل یک popover و یک دکمه برای باز و بسته‌کردن آن است.

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

#### جاوااسکریپت

کد، یک شنوندهٔ رویداد (event listener) برای رویداد `toggle` اضافه می‌کند و وضعیت را ثبت می‌کند.

```js
const popover = document.getElementById("mypopover");

popover.addEventListener("toggle", (event) => {
  if (event.newState === "open") {
    log("Popover has been shown");
  } else {
    log("Popover has been hidden");
  }
});
```

#### نتیجه

{{EmbedLiveSample("Basic example", '100%', "250px")}}

### نکته‌ای دربارهٔ ادغام رویداد toggle

اگر چند رویداد `toggle` پیش از آن‌که حلقهٔ رویداد (event loop) فرصت چرخه‌زدن پیدا کند رخ دهند، تنها یک رویداد صادر می‌شود. به این رفتار «ادغام رویداد» (event coalescing) گفته می‌شود.

برای مثال:

```js
popover.addEventListener("toggle", () => {
  // …
});

popover.showPopover();
popover.hidePopover();
// `toggle` only fires once
```

### سایر مثال‌ها

- مثال [باز کردن یک دیالوگ modal](/en-US/docs/Web/API/HTMLDialogElement#open_close_a_modal_dialog) در `HTMLDialogElement`

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) ویژگی سراسری HTML
- [Popover API](/en-US/docs/Web/API/Popover_API)
- رویداد مرتبط: [`beforetoggle`](/en-US/docs/Web/API/HTMLElement/beforetoggle_event)