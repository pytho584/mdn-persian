---
title: "ProgressEvent: loaded property"
short-title: loaded
slug: Web/API/ProgressEvent/loaded
page-type: web-api-instance-property
browser-compat: api.ProgressEvent.loaded
---

{{APIRef("XMLHttpRequest API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`ProgressEvent.loaded`** عددی است که اندازهٔ داده‌های ارسال‌شده یا پردازش‌شده را نشان می‌دهد. نسبت پیشرفت را می‌توان با تقسیم مقدار این ویژگی بر {{domxref("ProgressEvent.total")}} محاسبه کرد.

برای `ProgressEvent`هایی که مرورگر در پیام‌های HTTP ارسال می‌کند، این مقدار به تعداد بایت‌های تکمیل‌شدهٔ یک منبع اشاره دارد و از هدر `Content-Length` گرفته می‌شود. برای درخواست‌های فشرده با اندازهٔ کل نامعلوم، مقدار `loaded` ممکن است بسته به مرورگر، اندازهٔ دادهٔ فشرده یا فشرده‌نشده را در خود داشته باشد. از سال ۲۰۲۴، در Firefox این مقدار شامل اندازهٔ دادهٔ فشرده و در Chrome شامل اندازهٔ دادهٔ فشرده‌نشده است.

در یک `ProgressEvent` که خودتان می‌سازید، می‌توانید هر مقدار عددی را به `loaded` اختصاص دهید که بیانگر میزان کار انجام‌شده نسبت به مقدار `total` باشد.

## مقدار

یک عدد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("ProgressEvent")}} که این ویژگی به آن تعلق دارد.