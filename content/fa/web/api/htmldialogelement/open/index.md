---
title: "HTMLDialogElement: open property"
---

---
title: "HTMLDialogElement: open property"
short-title: open
slug: Web/API/HTMLDialogElement/open
page-type: web-api-instance-property
browser-compat: api.HTMLDialogElement.open
---

{{ APIRef("HTML DOM") }}

ویژگی **`open`** در رابط {{domxref("HTMLDialogElement")}} یک مقدار بولی است که ویژگی HTML [`open`](/en-US/docs/Web/HTML/Reference/Elements/dialog#open) را منعکس می‌کند و نشان می‌دهد که آیا {{htmlelement("dialog")}} برای تعامل در دسترس است یا نه.

## مقدار

یک مقدار بولی که وضعیت ویژگی HTML [`open`](/en-US/docs/Web/HTML/Reference/Elements/dialog#open) را نشان می‌دهد. مقدار `true` یعنی گفتگو نمایش داده می‌شود، در حالی که مقدار `false` یعنی نمایش داده نمی‌شود.

> [!WARNING]
> اگرچه ویژگی `open` از نظر فنی فقط‌خواندنی نیست و می‌توان آن را مستقیماً تنظیم کرد، اما [مشخصات HTML](https://html.spec.whatwg.org/multipage/interactive-elements.html#note-dialog-remove-open-attribute) به‌شدت این کار را منع می‌کند، زیرا می‌تواند تعاملات عادی گفتگو را به روش‌های غیرمنتظره‌ای مختل کند.
> برای مثال، رویداد [`close`](/en-US/docs/Web/API/HTMLDialogElement/close_event) وقتی `open` به صورت برنامه‌نویسی روی `false` تنظیم شود، رخ نمی‌دهد و فراخوانی‌های بعدی متدهای [`close()`](/en-US/docs/Web/API/HTMLDialogElement/close) و [`requestClose()`](/en-US/docs/Web/API/HTMLDialogElement/requestClose) نیز بی‌اثر خواهند بود.
> در عوض، بهتر است برای تغییر مقدار ویژگی `open` از متدهایی مانند [`show()`](/en-US/docs/Web/API/HTMLDialogElement/show)، [`showModal()`](/en-US/docs/Web/API/HTMLDialogElement/showModal)، `close()` و `requestClose()` استفاده کنید.

## مثال‌ها

### باز کردن یک گفتگو

مثال زیر یک دکمهٔ ساده را نشان می‌دهد که هنگام کلیک، یک {{htmlelement("dialog")}} شامل یک فرم را از طریق متد `showModal()` باز می‌کند. سپس می‌توانید برای بستن گفتگو (از طریق متد {{domxref("HTMLDialogElement.close()")}}) روی دکمهٔ _انصراف_ کلیک کنید، یا فرم را از طریق دکمهٔ ارسال (submit) ارسال کنید.

کد، مقدار `open` را هنگام تغییر وضعیت گفتگو در لاگ ثبت می‌کند.

#### HTML

```html
<!-- Simple pop-up dialog box -->
<dialog id="dialog">
  <form method="dialog">
    <button type="submit">Close</button>
  </form>
</dialog>

<button id="open">Open Dialog</button>
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
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```js
const dialog = document.getElementById("dialog");
const openButton = document.getElementById("open");

function openCheck(dialog) {
  log(dialog.open ? "Dialog: open" : "Dialog: closed");
}

openButton.addEventListener("click", () => {
  dialog.showModal();
  openCheck(dialog);
});

dialog.addEventListener("close", () => {
  openCheck(dialog);
});
```

### نتیجه

{{ EmbedLiveSample('Opening a dialog', '100%', '250px') }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML {{htmlelement("dialog")}}