---
title: "Document: selectionchange event"
---

---
title: "Document: selectionchange event"
short-title: selectionchange
slug: Web/API/Document/selectionchange_event
page-type: web-api-event
browser-compat: api.Document.selectionchange_event
---

{{APIRef("Selection API")}}

مرورگر رویداد **`selectionchange`** را از [Selection API](/en-US/docs/Web/API/Selection) زمانی که {{domxref("Selection")}} فعلی یک {{domxref("Document")}} تغییر می‌کند، فعال می‌کند. انتخاب سند (document selection) یا یک محدوده از محتوای انتخاب‌شده در میان گره‌های DOM را نشان می‌دهد یا یک موقعیت مکان‌نمای جمع‌شده (collapsed caret) را.

این رویداد قابل لغو نیست و حباب نمی‌زند.

## Syntax

برای نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("selectionchange", (event) => {})

onselectionchange = (event) => {}
```

## Event type

یک {{domxref("Event")}} عمومی.

## Description

رویداد `selectionchange` شیء `Document` در این موارد فعال می‌شود:

- کاربر یا اسکریپت یک انتخاب را ایجاد یا پاک کند.
- نقطه مرزی شروع یا پایان یک محدوده انتخاب‌شده جابه‌جا شود.
- یک محدوده انتخاب‌شده به‌کلی تغییر کند.
- یک انتخاب به یک موقعیت مکان‌نمای واحد جمع شود.

خود شیء رویداد حاوی جزئیات به‌روزرسانی‌شده انتخاب نیست. می‌توانید انتخاب فعلی را با فراخوانی {{domxref("Document.getSelection()", "document.getSelection()")}} در شنونده رویداد خود دریافت کنید.

این رویداد به‌طور قابل توجهی با رویداد `selectionchange` که روی عناصر کنترل متنی {{HTMLElement("input")}} و {{HTMLElement("textarea")}} فعال می‌شود، تفاوت دارد:

- انتخاب‌های سندی از موقعیت گره‌های DOM استفاده می‌کنند و برای بررسی نیاز به {{domxref("Document.getSelection()")}} دارند. ورودی‌های متنی انتخاب‌های مستقلی را در مقادیر متنی داخلی خود حفظ می‌کنند و از آفست‌های کاراکتری استفاده می‌کنند که از طریق `selectionStart`، `selectionEnd` و `selectionDirection` بررسی می‌شوند.
- رویداد `selectionchange` در سطح سند مستقیماً روی {{domxref("Document")}} فعال می‌شود و حباب نمی‌کند. رویداد `selectionchange` ورودی متنی روی عنصر input/textarea فعال می‌شود و در درخت DOM به بالا حباب می‌کند.

برای جزئیات بیشتر درباره رویدادهای ورودی متنی، رویداد {{domxref("HTMLInputElement.selectionchange_event", "selectionchange")}} مربوط به `HTMLInputElement` و رویداد {{domxref("HTMLTextAreaElement.selectionchange_event", "selectionchange")}} مربوط به `HTMLTextAreaElement` را ببینید.

## Examples

### استفاده پایه

```js
// addEventListener version
document.addEventListener("selectionchange", () => {
  console.log(document.getSelection());
});

// onselectionchange version
document.onselectionchange = () => {
  console.log(document.getSelection());
};
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## همچنین ببینید

- {{domxref("Node/selectstart_event", "selectstart")}}
- {{domxref("Document.getSelection()")}}
- {{domxref("Selection", "Selection")}}