---
title: "HTMLTextAreaElement: selectionStart property"
short-title: selectionStart
slug: Web/API/HTMLTextAreaElement/selectionStart
page-type: web-api-instance-property
browser-compat: api.HTMLTextAreaElement.selectionStart
---

{{APIRef("HTML DOM")}}

ویژگی **`selectionStart`** در رابط {{domxref("HTMLTextAreaElement")}} موقعیت شروع انتخاب متنی فعلی را در یک عنصر {{HTMLElement("textarea")}} مشخص می‌کند. این ویژگی یک عدد است که ایندکس آغازین متن انتخاب‌شده را نشان می‌دهد. می‌توان از آن هم برای دریافت و هم برای تنظیم ایندکس شروع متن انتخاب‌شده در یک `<textarea>` استفاده کرد.

وقتی هیچ متنی انتخاب نشده باشد، مقدار هر دو ویژگی `selectionStart` و {{domxref("HTMLTextAreaElement.selectionEnd", "selectionEnd")}} برابر با موقعیت مکان‌نما (caret) در داخل عنصر `<textarea>` است.

تنظیم `selectionStart` به مقداری بزرگ‌تر از مقدار فعلی {{domxref("HTMLTextAreaElement.selectionEnd", "selectionEnd")}}، هر دو ویژگی `selectionStart` و `selectionEnd` را به آن مقدار به‌روزرسانی می‌کند. اگر آن مقدار برابر یا بزرگ‌تر از {{domxref("HTMLTextAreaElement.textLength", "textLength")}} باشد، هر دو ویژگی به مقدار `textLength` تنظیم می‌شوند.

مقدار این ویژگی را می‌توان بدون اینکه `<textarea>` فوکوس داشته باشد دریافت و تنظیم کرد، اما عنصر برای اینکه شبه‌عنصر {{cssxref("::selection")}} با متن انتخاب‌شده مطابقت پیدا کند، نیاز به فوکوس دارد.

تنظیم `selectionStart` به یک مقدار جدید، رویدادهای {{domxref("HTMLTextAreaElement.selectionchange_event", "selectionchange")}} و {{domxref("HTMLTextAreaElement.select_event", "select")}} را فعال می‌کند.

## مقدار

یک عدد غیرمنفی.

## مثال‌ها

```js
const textarea = document.getElementById("text-box");
const start = textarea.selectionStart;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("textarea")}}
- {{domxref("HTMLTextAreaElement")}}
- {{domxref("HTMLTextAreaElement.selectionEnd")}}
- {{domxref("HTMLTextAreaElement.selectionDirection")}}
- {{domxref("HTMLTextAreaElement.textLength")}}
- {{domxref("HTMLTextAreaElement.select()")}}
- {{domxref("HTMLTextAreaElement.setSelectionRange()")}}
- {{domxref("HTMLTextAreaElement.setRangeText()")}}
- {{domxref("HTMLInputElement.selectionStart")}}
- {{domxref("Selection")}}
- شبه‌عنصر {{cssxref("::selection")}}