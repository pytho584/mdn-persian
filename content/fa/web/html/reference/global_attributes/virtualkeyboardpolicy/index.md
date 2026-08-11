---
title: "virtualkeyboardpolicy HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/virtualkeyboardpolicy"
translated_by: "n8n + AI"
---

**`virtualkeyboardpolicy`** یک ویژگی سراسری (global attribute) و از نوع شمارشی (enumerated attribute) است. وقتی روی عنصری تنظیم شود که محتوایش قابل ویرایش باشد (مثلاً عنصر `<input>` یا `<textarea>`، یا عنصری که ویژگی `contenteditable` روی آن تنظیم شده)، رفتار کیبورد مجازی را در دستگاه‌هایی مانند تبلت، تلفن همراه، یا سایر دستگاه‌هایی که ممکن است کیبورد سخت‌افزاری در دسترس نباشد، کنترل می‌کند.

این ویژگی باید یکی از مقادیر زیر را بپذیرد:

- `auto` یا رشته‌ای _خالی_، که به‌صورت خودکار کیبورد مجازی را وقتی عنصر فوکوس یا لمس می‌شود نشان می‌دهد.
- `manual`، که فوکوس و لمس روی عنصر را از وضعیت کیبورد مجازی جدا می‌کند.

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- [همهٔ ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes)
- `HTMLElement.contentEditable` و `HTMLElement.isContentEditable`
- VirtualKeyboard API