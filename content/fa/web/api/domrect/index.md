---
title: "DOMRect"
---

---
title: DOMRect
slug: Web/API/DOMRect
page-type: web-api-interface
browser-compat: api.DOMRect
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

یک **`DOMRect`** اندازه و موقعیت یک مستطیل را توصیف می‌کند.

نوع جعبه‌ای که توسط `DOMRect` نمایش داده می‌شود، توسط متد یا ویژگی‌ای که آن را بازگردانده است، مشخص می‌شود. برای مثال، {{domxref("Range.getBoundingClientRect()")}} مستطیلی را مشخص می‌کند که محتوای محدوده را با استفاده از چنین اشیایی در بر می‌گیرد.

این رابط از والد خود، {{domxref("DOMRectReadOnly")}}، ارث‌بری می‌کند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("DOMRect.DOMRect","DOMRect()")}}
  - : یک شیء `DOMRect` جدید ایجاد می‌کند.

## ویژگی‌های نمونه

_`DOMRect` ویژگی‌ها را از والد خود، {{domxref("DOMRectReadOnly")}}، به ارث می‌برد. تفاوت در این است که آن‌ها دیگر فقط‌خواندنی نیستند._

- {{domxref("DOMRect.x")}}
  - : مختصات x مبدأ `DOMRect` (معمولاً گوشهٔ بالا-چپ مستطیل).
- {{domxref("DOMRect.y")}}
  - : مختصات y مبدأ `DOMRect` (معمولاً گوشهٔ بالا-چپ مستطیل).
- {{domxref("DOMRect.width")}}
  - : عرض `DOMRect`.
- {{domxref("DOMRect.height")}}
  - : ارتفاع `DOMRect`.
- {{domxref("DOMRectReadOnly.top")}}
  - : مقدار مختصات بالای `DOMRect` را برمی‌گرداند (همان مقدار `y`، یا اگر `height` منفی باشد، `y + height`).
- {{domxref("DOMRectReadOnly.right")}}
  - : مقدار مختصات راست `DOMRect` را برمی‌گرداند (همان مقدار `x + width`، یا اگر `width` منفی باشد، `x`).
- {{domxref("DOMRectReadOnly.bottom")}}
  - : مقدار مختصات پایین `DOMRect` را برمی‌گرداند (همان مقدار `y + height`، یا اگر `height` منفی باشد، `y`).
- {{domxref("DOMRectReadOnly.left")}}
  - : مقدار مختصات چپ `DOMRect` را برمی‌گرداند (همان مقدار `x`، یا اگر `width` منفی باشد، `x + width`).

## متدهای ایستا

_`DOMRect` ممکن است متدهای ایستا را نیز از والد خود، {{domxref("DOMRectReadOnly")}}، به ارث ببرد._

- {{domxref("DOMRect/fromRect_static", "DOMRect.fromRect()")}}
  - : یک شیء `DOMRect` جدید با موقعیت و ابعاد معین ایجاد می‌کند.

## متدهای نمونه

_`DOMRect` ممکن است متدهایی را از والد خود، {{domxref("DOMRectReadOnly")}}، به ارث ببرد._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMPoint")}}