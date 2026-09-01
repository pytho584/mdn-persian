---
title: "HTMLDialogElement: show() method"
short-title: show()
slug: Web/API/HTMLDialogElement/show
page-type: web-api-instance-method
browser-compat: api.HTMLDialogElement.show
---

{{ APIRef("HTML DOM") }}

متد **`show()`** از رابط {{domxref("HTMLDialogElement")}} گفتگو را به‌عنوان یک گفتگوی غیرحالت‌دار (non-modal) نمایش می‌دهد.

گفتگوی غیرحالت‌دار، گفتگویی است که کاربران می‌توانند با محتوای بیرون/پشت گفتگوی باز شده تعامل داشته باشند.

## نحو (Syntax)

```js-nolint
show()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها (Exceptions)

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر گفتگو از قبل باز و حالت‌دار (modal) باشد، پرتاب می‌شود (یعنی اگر گفتگو قبلاً با {{domxref("HTMLDialogElement.showModal()")}} باز شده باشد).

## مثال‌ها

### استفادهٔ پایه

مثال زیر یک دکمهٔ ساده را نشان می‌دهد که با کلیک روی آن، یک {{htmlelement("dialog")}} با استفاده از متد `show()` باز می‌شود.

وقتی گفتگو باز است، همچنان می‌توانید با بقیهٔ صفحه تعامل داشته باشید، از جمله کلیک روی دکمهٔ _Click me_ که یک هشدار (alert) را فعال می‌کند.

می‌توانید روی دکمهٔ _Close dialog_ کلیک کنید تا گفتگو بسته شود (از طریق متد {{domxref("HTMLDialogElement.close()", "close()")}}).

#### HTML

```html
<dialog id="dialog">
  <button type="button" id="close">Close dialog</button>
</dialog>

<p><button id="open">Open dialog</button></p>
<p><button id="alert">Trigger alert</button></p>
```

#### JavaScript

```js
const dialog = document.getElementById("dialog");
const openButton = document.getElementById("open");
const closeButton = document.getElementById("close");
const alertButton = document.getElementById("alert");

// Open button opens a modeless dialog
openButton.addEventListener("click", () => {
  dialog.show();
});

// Alert button triggers an alert
alertButton.addEventListener("click", () => {
  alert("you clicked me!");
});

// Close button closes the dialog box
closeButton.addEventListener("click", () => {
  dialog.close();
});
```

#### نتیجه

{{EmbedLiveSample("Basic usage", '100%', "250px")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML {{htmlelement("dialog")}}
- {{domxref("HTMLDialogElement.showModal()")}}