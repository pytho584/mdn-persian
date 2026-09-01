---
title: DragEvent
slug: Web/API/DragEvent
page-type: web-api-interface
browser-compat: api.DragEvent
---

{{APIRef("HTML Drag and Drop API")}}

رابط **`DragEvent`** یک [رویداد DOM](/en-US/docs/Web/API/Event) است که تعامل کشیدن و رها کردن را نشان می‌دهد. کاربر با قرار دادن یک دستگاه اشاره‌گر (مانند ماوس) روی سطح لمسی و سپس کشیدن اشاره‌گر به مکان جدید (مثلاً یک عنصر DOM دیگر)، کشیدن را آغاز می‌کند. برنامه‌ها مختارند که تعامل کشیدن و رها کردن را به شکلی خاصِ برنامه تفسیر کنند.

این رابط ویژگی‌های خود را از {{domxref("MouseEvent")}} و {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref('DragEvent.dataTransfer')}} {{ReadOnlyInline}}
  - : داده‌ای که در طول تعامل کشیدن و رها کردن منتقل می‌شود.

## سازنده‌ها

اگرچه این رابط دارای سازنده است، اما نمی‌توان از طریق اسکریپت یک شیء DataTransfer کاربردی ایجاد کرد، زیرا اشیاء {{domxref("DataTransfer")}} دارای مدل پردازش و امنیتی هستند که توسط مرورگر در طول عملیات کشیدن و رها کردن هماهنگ می‌شوند.

- {{domxref("DragEvent.DragEvent", "DragEvent()")}}
  - : یک DragEvent ساختگی و غیرقابل‌اعتماد ایجاد می‌کند.

## انواع رویداد

- {{domxref("HTMLElement/drag_event", "drag")}}
  - : این رویداد زمانی رخ می‌دهد که یک عنصر یا انتخاب متن در حال کشیده شدن است.
- {{domxref("HTMLElement/dragend_event", "dragend")}}
  - : این رویداد زمانی رخ می‌دهد که یک عملیات کشیدن به پایان می‌رسد (با رها کردن دکمه ماوس یا فشردن کلید Escape).
- {{domxref("HTMLElement/dragenter_event", "dragenter")}}
  - : این رویداد زمانی رخ می‌دهد که یک عنصر یا انتخاب متنِ در حال کشیده شدن وارد یک هدف رها کردن معتبر می‌شود.
- {{domxref("HTMLElement/dragleave_event", "dragleave")}}
  - : این رویداد زمانی رخ می‌دهد که یک عنصر یا انتخاب متنِ در حال کشیده شدن از یک هدف رها کردن معتبر خارج می‌شود.
- {{domxref("HTMLElement/dragover_event", "dragover")}}
  - : این رویداد به‌طور پیوسته زمانی رخ می‌دهد که یک عنصر یا انتخاب متن در حال کشیدن است و نشانگر ماوس روی یک هدف رها کردن معتبر قرار دارد (هر ۵۰ میلی‌ثانیه وقتی ماوس حرکت نمی‌کند، و در غیر این صورت بسیار سریع‌تر و تقریباً بین ۵ میلی‌ثانیه (حرکت آهسته) تا ۱ میلی‌ثانیه (حرکت سریع). این الگوی رخ دادن با {{domxref("Element/mouseover_event", "mouseover")}} متفاوت است.)
- {{domxref("HTMLElement/dragstart_event", "dragstart")}}
  - : این رویداد زمانی رخ می‌دهد که کاربر کشیدن یک عنصر یا انتخاب متن را آغاز می‌کند.
- {{domxref("HTMLElement/drop_event", "drop")}}
  - : این رویداد زمانی رخ می‌دهد که یک عنصر یا انتخاب متن روی یک هدف رها کردن معتبر رها می‌شود.

## مثال

نمونه‌ای از هر ویژگی، سازنده، نوع رویداد و مدیران رویداد سراسری در صفحه مرجع مربوط به هر یک ارائه شده است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [کشیدن و رها کردن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API)
- [عملیات کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations)
- [کار با مخزن دادهٔ کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_data_store)