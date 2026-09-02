---
title: "HTMLTextAreaElement: selectionDirection property"
short-title: selectionDirection
slug: Web/API/HTMLTextAreaElement/selectionDirection
page-type: web-api-instance-property
browser-compat: api.HTMLTextAreaElement.selectionDirection
---

<!--  -->

{{APIRef("HTML DOM")}}

ویژگی **`selectionDirection`** در رابط {{domxref("HTMLTextAreaElement")}} جهت فعلی انتخاب را مشخص می‌کند. مقادیر ممکن عبارتند از `"forward"`، `"backward"` و `"none"`. مقدار `forward` نشان می‌دهد که انتخاب در جهت شروع به پایانِ locale فعلی انجام شده است و `backward` جهت مخالف را نشان می‌دهد. مقدار `none` زمانی رخ می‌دهد که جهت نامشخص باشد. از این ویژگی می‌توان هم برای دریافت و هم برای تغییر جهت متن انتخاب‌شده در `<textarea>` استفاده کرد.

تنظیم `selectionDirection` روی یک مقدار جدید، رویدادهای {{domxref("HTMLTextAreaElement.selectionchange_event", "selectionchange")}} و {{domxref("HTMLTextAreaElement.select_event", "select")}} را فعال می‌کند.

## مقدار

یک رشته؛ `"forward"`، `"backward"` یا `"none"`.

## نمونه‌ها

```js
const textarea = document.getElementById("text-box");
const end = textarea.selectionDirection;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{HTMLElement("textarea")}}
- {{domxref("HTMLTextAreaElement")}}
- {{domxref("HTMLTextAreaElement.selectionStart")}}
- {{domxref("HTMLTextAreaElement.selectionEnd")}}
- {{domxref("HTMLTextAreaElement.textLength")}}
- {{domxref("HTMLTextAreaElement.select()")}}
- {{domxref("HTMLTextAreaElement.setSelectionRange()")}}
- {{domxref("HTMLTextAreaElement.setRangeText()")}}
- {{domxref("HTMLInputElement.selectionDirection")}}
- {{domxref("Selection")}}
- شبه‌عنصر {{cssxref("::selection")}}
