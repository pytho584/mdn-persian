---
title: "HTMLDialogElement: requestClose() method"
short-title: requestClose()
slug: Web/API/HTMLDialogElement/requestClose
page-type: web-api-instance-method
browser-compat: api.HTMLDialogElement.requestClose
---

{{ APIRef("HTML DOM") }}

متد **`requestClose()`** از رابط {{domxref("HTMLDialogElement")}} درخواست بستن عنصر {{htmlelement("dialog")}} را می‌دهد.
یک رشته اختیاری می‌تواند به عنوان آرگومان ارسال شود که مقدار {{domxref("HTMLDialogElement.returnValue", "returnValue")}} دیالوگ را به‌روزرسانی می‌کند.

این متد با متد {{domxref("HTMLDialogElement.close()", "close()")}} تفاوت دارد در این که قبل از فعال‌سازی رویداد {{domxref("HTMLDialogElement.close_event", "close")}}، یک رویداد {{domxref("HTMLDialogElement.cancel_event", "cancel")}} را فعال می‌کند.
نویسندگان می‌توانند در تابع‌درمانگر رویداد {{domxref("HTMLDialogElement.cancel_event", "cancel")}} متد {{domxref("Event.preventDefault()")}} را فراخوانی کنند تا از بسته‌شدن دیالوگ جلوگیری کنند.

این متد همان رفتار ناظر داخلی بستن دیالوگ (close watcher) را ارائه می‌دهد.

## نحو (Syntax)

```js-nolint
requestClose()
requestClose(returnValue)
```

### پارامترها

- `returnValue` {{optional_inline}}
  - : یک رشته که مقدار به‌روزرسانی‌شده برای {{domxref("HTMLDialogElement.returnValue")}} دیالوگ را نشان می‌دهد.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

### استفاده از `requestClose()`

مثال زیر یک دکمه را نشان می‌دهد که با کلیک روی آن، یک {{htmlelement("dialog")}} با استفاده از متد {{domxref("HTMLDialogElement.showModal()", "showModal()")}} باز می‌شود.
سپس می‌توانید روی هر یک از دکمه‌های _بستن_ کلیک کنید تا متد `requestClose()` فراخوانی شده و دیالوگ بسته شود.

دکمه _بستن_ دیالوگ را بدون {{domxref("HTMLDialogElement.returnValue", "returnValue")}} می‌بندد، در حالی که دکمه _بستن با مقدار بازگشتی_ دیالوگ را با یک {{domxref("HTMLDialogElement.returnValue", "returnValue")}} می‌بندد.

جلوگیری از بسته‌شدن دیالوگ با یک چک‌باکس نشان داده شده است.

#### HTML

```html
<dialog id="dialog">
  <div>
    <label><input type="checkbox" id="prevent-close" /> Cancel close</label>
  </div>
  <button type="button" id="close">Close</button>
  <button type="button" id="close-w-value">Close w/ return value</button>
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
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```js
const dialog = document.getElementById("dialog");
const openButton = document.getElementById("open");
const closeButton = document.getElementById("close");
const closeWithValueButton = document.getElementById("close-w-value");
const preventCloseInput = document.getElementById("prevent-close");

// دکمه باز کردن، یک دیالوگ مودال را باز می‌کند
openButton.addEventListener("click", () => {
  // بازنشانی مقدار بازگشتی
  dialog.returnValue = "";
  // نمایش دیالوگ
  dialog.showModal();
});

// دکمه بستن، دیالوگ را می‌بندد
closeButton.addEventListener("click", () => {
  dialog.requestClose();
});

// دکمه بستن با مقدار بازگشتی، دیالوگ را با یک مقدار بازگشتی می‌بندد
closeWithValueButton.addEventListener("click", () => {
  dialog.requestClose("some value");
});

// هنگامی که requestClose() فراخوانی می‌شود فعال می‌گردد
// با فراخوانی event.preventDefault() از بسته‌شدن دیالوگ جلوگیری کنید
dialog.addEventListener("cancel", (event) => {
  if (preventCloseInput.checked) {
    log("Dialog close cancelled");
    event.preventDefault();
  }
});

// رویداد cancel جلوگیری نشده است، بنابراین دیالوگ بسته خواهد شد
dialog.addEventListener("close", () => {
  log(`Dialog closed. Return value: "${dialog.returnValue}"`);
});
```

#### نتیجه

{{ EmbedLiveSample('Using `requestClose()`', '100%', '250px') }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- عنصر HTML {{htmlelement("dialog")}}
- رویداد {{domxref("HTMLDialogElement.cancel_event", "cancel")}}