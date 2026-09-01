---
title: "HTMLDialogElement: showModal() method"
short-title: showModal()
slug: Web/API/HTMLDialogElement/showModal
page-type: web-api-instance-method
browser-compat: api.HTMLDialogElement.showModal
---

{{ APIRef("HTML DOM") }}

متد **`showModal()`** از رابط {{domxref("HTMLDialogElement")}}، دیالوگ را به‌صورت یک دیالوگ مودال (modal) در بالای هر دیالوگ یا عنصر دیگری که ممکن است قابل مشاهده باشد، نمایش می‌دهد.

یک دیالوگ مودال در {{glossary("top layer")}} (لایهٔ بالایی) به‌همراه یک شبه‌المان {{cssxref('::backdrop')}} نمایش داده می‌شود.
عناصر داخل همان سندی که دیالوگ در آن قرار دارد، به‌جز خود دیالوگ و فرزندانش، _inert_ (غیرفعال) می‌شوند (انگار ویژگی [`inert`](/en-US/docs/Web/HTML/Reference/Global_attributes/inert) روی آن‌ها تنظیم شده باشد).
فقط سندِ حاوی دیالوگ مسدود می‌شود؛ اگر دیالوگ داخل یک iframe رندر شده باشد، بقیهٔ صفحه همچنان قابل تعامل باقی می‌ماند.

## سینتکس

```js-nolint
showModal()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر دیالوگ از قبل باز و غیرمودال باشد (یعنی قبلاً با استفاده از {{domxref("HTMLDialogElement.show()")}} باز شده باشد) پرتاب می‌شود.

## نمونه‌ها

### کاربرد پایه

مثال زیر یک دکمهٔ ساده را نشان می‌دهد که با کلیک‌شدن، یک {{htmlelement("dialog")}} را با استفاده از متد `showModal()` باز می‌کند.

وقتی دیالوگ باز است، نمی‌توانید با بقیهٔ صفحه تعامل کنید، از جمله کلیک روی دکمهٔ _Click me_ که در غیر این صورت یک alert را فعال می‌کرد.

می‌توانید دکمهٔ _Close dialog_ را کلیک کنید تا دیالوگ بسته شود (از طریق متد {{domxref("HTMLDialogElement.close()")}}).

#### HTML

```html
<dialog id="dialog">
  <button type="button" id="close">Close dialog</button>
</dialog>

<p><button id="open">Open dialog</button></p>
<p><button id="alert">Trigger alert</button></p>
```

#### جاوااسکریپت

```js
const dialog = document.getElementById("dialog");
const openButton = document.getElementById("open");
const closeButton = document.getElementById("close");
const alertButton = document.getElementById("alert");

// Open button opens a modal dialog
openButton.addEventListener("click", () => {
  dialog.showModal();
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

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML {{htmlelement("dialog")}}
- {{domxref("HTMLDialogElement.show()")}}