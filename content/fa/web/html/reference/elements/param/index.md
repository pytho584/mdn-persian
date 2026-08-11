---
title: "<param> HTML object parameter element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/param"
translated_by: "n8n + AI"
---

# `<param>` — المان پارامتر HTML

> **منسوخ:** این ویژگی دیگر توصیه نمی‌شود.

المان **`<param>`** در [HTML](/en-US/docs/Web/HTML) پارامترهایی را برای المان `<object>` تعریف می‌کند.

> **توجه:** از المان `<object>` با attribute [`data`](/en-US/docs/Web/HTML/Reference/Elements/object#data) استفاده کنید تا URL یک منبع خارجی را تنظیم کنید.

## ویژگی‌ها (Attributes)

این المان شامل [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- `name` (منسوخ) (غیراستاندارد)
  - : نام پارامتر.
- `value` (منسوخ) (غیراستاندارد)
  - : مقدار پارامتر را مشخص می‌کند.
- `type` (منسوخ) (غیراستاندارد)
  - : فقط زمانی استفاده می‌شود که `valuetype` برابر با `ref` باشد. نوع MIME مقادیری را که در URI مشخص‌شده توسط `value` یافت می‌شوند، تعیین می‌کند.
- `valuetype` (منسوخ) (غیراستاندارد)
  - : نوع attribute `value` را مشخص می‌کند. مقادیر ممکن عبارت‌اند از:
    - `data`: مقدار پیش‌فرض. مقدار به‌صورت رشته به پیاده‌سازی object منتقل می‌شود.
    - `ref`: مقدار یک URI برای منبعی است که مقادیر زمان اجرا (run-time values) در آن ذخیره شده‌اند.
    - `object`: شناسه (ID) یک المان `<object>` دیگر در همان سند.

## خلاصه فنی

| مورد | توضیح |
| --- | --- |
| دسته‌بندی محتوا (Content categories) | هیچ. |
| محتوای مجاز (Permitted content) | هیچ؛ این یک void element است. |
| حذف تگ (Tag omission) | باید تگ شروع داشته باشد و نباید تگ پایانی داشته باشد. |
| والدین مجاز (Permitted parents) | یک `<object>` قبل از هر [flow content](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content). |
| نقش ARIA ضمنی (Implicit ARIA role) | [نقش متناظری ندارد](https://w3c.github.io/html-aria/#dfn-no-corresponding-role). |
| نقش‌های ARIA مجاز (Permitted ARIA roles) | هیچ `role` مجاز نیست. |
| رابط DOM (DOM interface) | `HTMLParamElement` |

## همچنین ببینید

- [`<object>`](/en-US/docs/Web/HTML/Reference/Elements/object)