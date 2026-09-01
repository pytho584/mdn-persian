---
title: "HTMLInputElement: رویداد selectionchange"
short-title: selectionchange
slug: Web/API/HTMLInputElement/selectionchange_event
page-type: web-api-event
browser-compat: api.HTMLInputElement.selectionchange_event
---

{{APIRef("Selection API")}}

رویداد **`selectionchange`** از [Selection API](/en-US/docs/Web/API/Selection) زمانی رخ می‌دهد که انتخاب متن درون یک عنصر {{HTMLElement("input")}} تغییر کند. این شامل تغییرات در محدوده انتخاب‌شده کاراکترها یا حرکت مکان‌نما می‌شود.

این رویداد لغوپذیر نیست.

این رویداد معمولاً با افزودن یک شنونده رویداد روی عنصر {{HTMLElement("input")}} پردازش می‌شود و در تابع مدیریت‌کننده، مقادیر خصوصیات `selectionStart`، `selectionEnd` و `selectionDirection` شیء {{domxref("HTMLInputElement")}} خوانده می‌شوند.

همچنین می‌توان یک شنونده روی مدیریت‌کننده رویداد `onselectionchange` اضافه کرد و درون تابع مدیریت‌کننده از {{domxref("Document.getSelection()")}} برای دریافت {{domxref("Selection", "Selection")}} استفاده کرد. با این حال، این روش برای دریافت تغییرات انتخاب‌های _متن_ چندان مفید نیست.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("selectionchange", (event) => { })

onselectionchange = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

مثال زیر نحوه به‌دست آوردن متن انتخاب‌شده در یک عنصر {{HTMLElement("input")}} را نشان می‌دهد.

### HTML

```html
<div>
  متن را اینجا وارد و انتخاب کنید:<br /><input id="my-text" rows="2" cols="20" />
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