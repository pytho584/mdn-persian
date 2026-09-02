---
title: "HTMLTextAreaElement: selectionchange event"
short-title: selectionchange
slug: Web/API/HTMLTextAreaElement/selectionchange_event
page-type: web-api-event
browser-compat: api.HTMLTextAreaElement.selectionchange_event
---

{{APIRef("Selection API")}}

رویداد **`selectionchange`** از [Selection API](/en-US/docs/Web/API/Selection) زمانی فعال می‌شود که انتخاب متن درون یک عنصر {{HTMLElement("textarea")}} تغییر کند. این شامل تغییرات در محدوده انتخاب شده یا حرکت مکان‌نما (caret) می‌شود.

این رویداد قابل لغو (cancelable) نیست.

معمولاً این رویداد با افزودن یک شنونده رویداد (event listener) به عنصر {{HTMLElement("textarea")}} و در تابع کنترل‌کننده با خواندن خصوصیات `selectionStart`، `selectionEnd` و `selectionDirection` از {{domxref("HTMLTextAreaElement")}} پردازش می‌شود.

همچنین می‌توان یک شنونده روی کنترل‌کننده رویداد سراسری `onselectionchange` اضافه کرد و درون تابع کنترل‌کننده از {{domxref("Document.getSelection()")}} برای دریافت {{domxref("Selection", "Selection")}} استفاده کرد. با این حال، این روش برای دریافت تغییرات در انتخاب‌های _متن_ چندان مفید نیست.

## Syntax (نحو)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("selectionchange", (event) => { })

onselectionchange = (event) => { }
```

## Event type (نوع رویداد)

یک {{domxref("Event")}} عمومی.

## Examples (نمونه‌ها)

مثال زیر نحوه دریافت متن انتخاب شده در یک عنصر {{HTMLElement("textarea")}} را نشان می‌دهد.

### HTML

```html
<div>
  Enter and select text here:<br /><textarea
    id="my-text"
    rows="2"
    cols="20"></textarea>
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

### Result (نتیجه)

{{EmbedLiveSample("Examples")}}

## Specifications (مشخصات)

{{Specifications}}

## Browser compatibility (سازگاری با مرورگرها)

{{Compat}}