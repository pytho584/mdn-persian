---
title: "HTMLInputElement: selectionchange event"
short-title: selectionchange
slug: Web/API/HTMLInputElement/selectionchange_event
page-type: web-api-event
browser-compat: api.HTMLInputElement.selectionchange_event
---

{{APIRef("Selection API")}}

رویداد **`selectionchange`** از [Selection API](/en-US/docs/Web/API/Selection) زمانی رخ می‌دهد که انتخاب متن درون یک عنصر {{HTMLElement("input")}} تغییر کند. این شامل تغییر در محدوده‌ی کاراکترهای انتخاب‌شده و همچنین حرکت مکان‌نما (caret) می‌شود.

این رویداد قابل لغو (cancelable) نیست.

معمولاً این رویداد با افزودن یک شنونده‌ی رویداد (event listener) روی {{HTMLElement("input")}} پردازش می‌شود و در تابع کنترل‌کننده، مقادیر ویژگی‌های `selectionStart`، `selectionEnd` و `selectionDirection` مربوط به {{domxref("HTMLInputElement")}} خوانده می‌شود.

همچنین می‌توان یک شنونده روی ویژگی کنترل‌کننده‌ی رویداد `onselectionchange` اضافه کرد و درون تابع کنترل‌کننده از {{domxref("Document.getSelection()")}} برای دریافت {{domxref("Selection", "Selection")}} استفاده کرد. با این حال، این روش برای دریافت تغییرات در انتخاب‌های _متن_ چندان کاربردی نیست.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید یا یک ویژگی کنترل‌کننده‌ی رویداد تنظیم کنید.

```js-nolint
addEventListener("selectionchange", (event) => { })

onselectionchange = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

مثال زیر نحوه‌ی دریافت متن انتخاب‌شده در یک عنصر {{HTMLElement("input")}} را نشان می‌دهد.

### HTML

```html
<div>
  Enter and select text here:<br /><input id="my-text" rows="2" cols="20" />
</div>
<div>selectionStart: <span id="start"></span></div>
<div>selectionEnd: <span id="end"></span></div>
<div>selectionDirection: <span id="direction"></span></div>
```

### JavaScript

```js
const myInput = document.getElementById("my-text");

myInput.addEventListener("selectionchange", () => {
  document.getElementById("start").textContent = myInput.selectionStart;
  document.getElementById("end").textContent = myInput.selectionEnd;
  document.getElementById("direction").textContent = myInput.selectionDirection;
});
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}