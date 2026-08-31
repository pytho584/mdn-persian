---
title: CaretPosition
slug: Web/API/CaretPosition
page-type: web-api-interface
browser-compat: api.CaretPosition
---

{{APIRef("CSSOM view API")}}

رابط `CaretPosition` موقعیت مکان‌نما را نشان می‌دهد؛ مکان‌نما نشانگری برای نقطه‌ٔ درج متن است. می‌توانید با استفاده از متد {{domxref("Document.caretPositionFromPoint()")}} یک `CaretPosition` دریافت کنید.

## ویژگی‌های نمونه

_این رابط هیچ ویژگی‌ای را به ارث نمی‌برد._

- {{domxref("CaretPosition.offsetNode")}} {{ReadOnlyInline}}
  - : یک {{domxref("Node")}} را برمی‌گرداند که شامل گره‌ٔ یافت‌شده در موقعیت مکان‌نما است.
- {{domxref("CaretPosition.offset")}} {{ReadOnlyInline}}
  - : یک `long` را برمی‌گرداند که افست (offset) انتخاب را در گره‌ٔ موقعیت مکان‌نما نشان می‌دهد. این مقدار، افست کاراکتر در یک گره‌ٔ متنی یا اندیس گره‌ٔ فرزندِ انتخاب‌شده در یک گره‌ٔ عنصری خواهد بود.

## متدهای نمونه

- {{domxref("CaretPosition.getClientRect")}}
  - : مستطیل کلاینت (client rectangle) را برای بازه‌ٔ مکان‌نما برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("Document.caretPositionFromPoint()")}}
- {{domxref("Range")}}
- {{domxref("Node")}}