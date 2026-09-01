---
title: "HTMLTableCellElement: bgColor property"
short-title: bgColor
slug: Web/API/HTMLTableCellElement/bgColor
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.HTMLTableCellElement.bgColor
---

{{APIRef("HTML DOM")}}{{deprecated_header}}

خاصیت **`HTMLTableCellElement.bgColor`** برای تنظیم رنگ پس‌زمینه یک سلول یا دریافت مقدار ویژگی منسوخ [`bgColor`](/en-US/docs/Web/HTML/Reference/Elements/td#bgcolor) (در صورت وجود) استفاده می‌شود.

> [!NOTE]
> این خاصیت منسوخ شده است و برای تنظیم رنگ پس‌زمینه باید از CSS استفاده شود. به جای آن از خاصیت {{cssxref("background-color")}} استفاده کنید.

## مقدار

یکی از انواع مقدار زیر قابل استفاده است:

- یک رنگ نام‌دار، مانند `red` یا `blue`
- یک کد هگز، مانند `#0000dd` یا `#00d`

> [!NOTE]
> مقادیر پذیرفته شده در اینجا زیرمجموعه محدودی از مقادیر رنگ CSS هستند. فقط {{cssxref("named-color")}} و {{cssxref("hex-color")}} سه یا شش رقمی (بدون کانال آلفا). در حالی که تمام مقادیر رنگ HTML در CSS معتبر هستند، این موضوع برعکس صادق نیست.

## مثال‌ها

به جای آن از CSS `background-color` استفاده کنید. یک مثال از استفاده از [`background-color` با عناصر جدول HTML](/en-US/docs/Web/CSS/Reference/Properties/background-color#colorized_tables) در صفحه {{cssxref("background-color")}} موجود است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLTableRowElement.bgColor")}}