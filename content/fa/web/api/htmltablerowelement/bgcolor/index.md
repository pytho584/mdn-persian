---
title: "HTMLTableRowElement: bgColor property"
short-title: bgColor
slug: Web/API/HTMLTableRowElement/bgColor
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.HTMLTableRowElement.bgColor
---

{{APIRef("HTML DOM")}}{{deprecated_header}}

خاصیت **`HTMLTableRowElement.bgColor`** برای تنظیم رنگ پس‌زمینهٔ یک ردیف یا دریافت مقدار ویژگی منسوخ [`bgColor`](/en-US/docs/Web/HTML/Reference/Elements/tr#bgcolor) (در صورت وجود) استفاده می‌شود.

> [!NOTE]
> این خاصیت منسوخ شده است و برای تنظیم رنگ پس‌زمینه باید از CSS استفاده شود. به جای آن از خاصیت {{cssxref("background-color")}} استفاده کنید.

## مقدار

یکی از انواع مقدار زیر قابل استفاده است:

- یک رنگ با نام، مانند `red` یا `blue`
- یک کد هگزادسیمال، مانند `#0000dd`

> [!NOTE]
> مقادیر پذیرفته‌شده در اینجا زیرمجموعه‌ای از مقادیر رنگ CSS هستند. می‌توانید مقادیر رنگ HTML را در CSS استفاده کنید، اما نه برعکس: رنگ‌های ناشناخته به شکلی متفاوت از انتظار نمایش داده می‌شوند.

## مثال‌ها

به جای آن از `background-color` در CSS استفاده کنید. یک [مثال](/en-US/docs/Web/CSS/Reference/Properties/background-color#colorized_tables) در صفحهٔ {{cssxref("background-color")}} موجود است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLTableCellElement.bgColor")}}