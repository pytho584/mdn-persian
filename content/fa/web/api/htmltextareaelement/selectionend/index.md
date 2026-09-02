---
title: "HTMLTextAreaElement: selectionEnd property"
short-title: selectionEnd
slug: Web/API/HTMLTextAreaElement/selectionEnd
page-type: web-api-instance-property
browser-compat: api.HTMLTextAreaElement.selectionEnd
---

{{APIRef("HTML DOM")}}

ویژگی **`selectionEnd`** در رابط {{domxref("HTMLTextAreaElement")}} موقعیت پایانِ انتخاب متنیِ فعلی را در یک عنصر {{HTMLElement("textarea")}} مشخص می‌کند. این یک عدد است که آخرین ایندکس متن انتخاب‌شده را نشان می‌دهد. می‌توان از آن هم برای دریافت و هم برای تنظیم ایندکس پایانِ متن انتخاب‌شده‌ی یک `<textarea>` استفاده کرد.

وقتی چیزی انتخاب نشده باشد، مقدار هر دو ویژگی {{domxref("HTMLTextAreaElement.selectionStart", "selectionStart")}} و `selectionEnd` برابر با موقعیت مکان‌نما (caret) در داخل عنصر `<textarea>` است.

تنظیم `selectionEnd` به مقداری کمتر از مقدار فعلی {{domxref("HTMLTextAreaElement.selectionStart", "selectionStart")}}، هر دو ویژگی `selectionEnd` و `selectionStart` را به آن مقدار به‌روزرسانی می‌کند. اگر هر دو مقدار کمتر از 0 باشند، هر دو ویژگی به مقدار ویژگی {{domxref("HTMLTextAreaElement.textLength", "textLength")}} تنظیم می‌شوند.

مقدار این ویژگی را می‌توان بدون آنکه `<textarea>` فوکوس داشته باشد دریافت و تنظیم کرد، اما عنصر برای اینکه شبه‌عنصر {{cssxref("::selection")}} با متن انتخاب‌شده مطابقت کند، باید فوکوس داشته باشد.

تنظیم `selectionEnd` به یک مقدار جدید، رویدادهای {{domxref("HTMLTextAreaElement.selectionchange_event", "selectionchange")}} و {{domxref("HTMLTextAreaElement.select_event", "select")}} را فعال می‌کند.

## مقدار

یک عدد غیرمنفی.

## مثال‌ها

```js
const textarea = document.getElementById("text-box");
const end = textarea.selectionEnd;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("textarea")}}
- {{domxref("HTMLTextAreaElement")}}
- {{domxref("HTMLTextAreaElement.selectionStart")}}
- {{domxref("HTMLTextAreaElement.selectionDirection")}}
- {{domxref("HTMLTextAreaElement.textLength")}}
- رویداد {{domxref("HTMLTextAreaElement.selectionChange_event", "selectionChange")}}
- {{domxref("HTMLTextAreaElement.select()")}}
- {{domxref("HTMLTextAreaElement.setSelectionRange()")}}
- {{domxref("HTMLTextAreaElement.setRangeText()")}}
- {{domxref("HTMLInputElement.selectionEnd")}}
- {{domxref("Selection")}}
- شبه‌عنصر {{cssxref("::selection")}}