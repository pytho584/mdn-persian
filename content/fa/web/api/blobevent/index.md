---
title: "BlobEvent"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BlobEvent"
translated_by: "n8n + AI"
---

{{APIRef("MediaStream Recording")}}

رابط **`BlobEvent`** از [MediaStream Recording API](/en-US/docs/Web/API/MediaStream_Recording_API) رویدادهای مرتبط با یک {{domxref("Blob")}} را نمایش می‌دهد. این Blobها معمولاً، اما نه لزوماً، با محتوای رسانه‌ای مرتبط هستند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("BlobEvent.BlobEvent", "BlobEvent()")}}
  - : یک رویداد `BlobEvent` را با پارامترهای داده‌شده ایجاد می‌کند.

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود {{domxref("Event")}} به ارث می‌برد._

- {{domxref("BlobEvent.data")}} {{ReadOnlyInline}}
  - : یک {{domxref("Blob")}} که داده‌های مرتبط با رویداد را نشان می‌دهد. رویداد روی {{domxref("EventTarget")}} به دلیل رخ دادن چیزی روی همان {{domxref("Blob")}} خاص صادر شد.
- {{domxref("BlobEvent.timecode")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که تفاوت بین برچسب زمانی اولین تکه در داده و برچسب زمانی اولین تکه در اولین BlobEvent تولیدشده توسط این ضبط‌کننده را نشان می‌دهد. توجه داشته باشید که timecode در اولین BlobEvent تولیدشده لازم نیست صفر باشد.

## روش‌های نمونه

_متد خاصی ندارد؛ متدها را از والد خود {{domxref("Event")}} به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط پایه {{domxref("Event")}}.
- [MediaStream Recording API](/en-US/docs/Web/API/MediaStream_Recording_API): هر بار که یک قطعه رسانه آماده باشد، اشیاء `BlobEvent` را ارسال می‌کند.
- [Using the MediaStream Recording API](/en-US/docs/Web/API/MediaStream_Recording_API/Using_the_MediaStream_Recording_API)