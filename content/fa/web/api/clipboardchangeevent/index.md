---
title: "ClipboardChangeEvent"
slug: Web/API/ClipboardChangeEvent
page-type: web-api-interface
status:
  - experimental
browser-compat: api.ClipboardChangeEvent
---

{{APIRef("Clipboard API")}}{{SeeCompatTable}}

رابط **`ClipboardChangeEvent`** از {{domxref("Clipboard API", "", "", "nocode")}} نشان‌دهنده رویدادهایی است که هرگاه محتویات کلیپ‌برد سیستم تغییر می‌کنند، فعال می‌شوند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("ClipboardChangeEvent.ClipboardChangeEvent", "ClipboardChangeEvent()")}} {{experimental_inline}}
  - : یک رویداد `ClipboardChangeEvent` جدید با پارامترهای داده شده ایجاد می‌کند.

## ویژگی‌های نمونه

_همچنین ویژگی‌هایی را از والد خود {{domxref("Event")}} به ارث می‌برد._

- {{domxref("ClipboardChangeEvent.types")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : آرایه‌ای از رشته‌ها که نشان‌دهنده انواع داده‌های اجباری موجود در کلیپ‌برد سیستم در زمان فعال شدن رویداد است.
- {{domxref("ClipboardChangeEvent.changeId")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک عدد صحیح ۱۲۸ بیتی که نشان‌دهنده یک شناسه یکتا برای این عملیات تغییر کلیپ‌برد خاص است.

## روش‌های نمونه

_روش خاصی ندارد؛ روش‌ها را از والد خود {{domxref("Event")}} به ارث می‌برد._

## مثال‌ها

در این مثال، وقتی محتویات کلیپ‌برد تغییر می‌کنند، شنونده رویداد انواع داده‌ها، شناسه تغییر و کل شیء رویداد را در کنسول ثبت می‌کند. این یک شیء `ClipboardChangeEvent` از نوع `clipboardchange` است.

```js
navigator.clipboard.addEventListener("clipboardchange", (event) => {
  console.log(`MIME types: ${event.types}`);
  console.log(`ID: ${event.changeId}`);
  console.dir(event);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- رویدادهای مرتبط با کپی: {{domxref("Element/copy_event", "copy")}}، {{domxref("Element/cut_event", "cut")}}، {{domxref("Element/paste_event", "paste")}}
- {{domxref("ClipboardEvent")}}
- [Clipboard API](/en-US/docs/Web/API/Clipboard_API)