---
title: "virtualkeyboardpolicy HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/virtualkeyboardpolicy"
translated_by: "n8n + AI"
---

ویژگی سراسری `virtualkeyboardpolicy` یک ویژگی از نوع شمارشی (enumerated) است. وقتی روی عنصری قرار می‌گیرد که محتوایش قابل ویرایش است (مثلاً یک `<input>` یا `<textarea>`، یا عنصری که ویژگی [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable) روی آن تنظیم شده)، رفتار کیبورد مجازی روی صفحه را در دستگاه‌هایی مثل تبلت، تلفن همراه یا هر دستگاهی که کیبورد فیزیکی ندارد کنترل می‌کند.

این ویژگی باید یکی از مقادیر زیر را داشته باشد:

- `auto` یا یک رشتهٔ خالی (_empty string_): کیبورد مجازی وقتی عنصر فوکوس یا tapped شود به‌طور خودکار نمایش داده می‌شود.
- `manual`: فوکوس و tap روی عنصر را از وضعیت کیبورد مجازی جدا می‌کند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## جستارهای وابسته

- همهٔ [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes)
- `HTMLElement.contentEditable` و `HTMLElement.isContentEditable`
- `VirtualKeyboard API`