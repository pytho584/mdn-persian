---
title: "draggable HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/draggable"
translated_by: "n8n + AI"
---

ویژگی سراسری (global attribute) **`draggable`** یک ویژگی شمارشی (enumerated) است که مشخص می‌کند آیا عنصر قابل کشیدن است یا نه — چه با رفتار بومی مرورگر، چه با [HTML Drag and Drop API](/en-US/docs/Web/API/HTML_Drag_and_Drop_API).

ویژگی `draggable` فقط روی عناصری قابل استفاده است که دقیقاً در [HTML namespace](/en-US/docs/Glossary/Namespace) قرار دارند؛ یعنی نمی‌توان آن را روی [SVGها](/en-US/docs/Web/SVG) اعمال کرد. برای آشنایی با ساختار و کارکرد namespaceها، به [Namespace crash course](/en-US/docs/Web/SVG/Guides/Namespaces_crash_course) مراجعه کنید.

`draggable` می‌تواند مقادیر زیر را بگیرد:

- `true`: عنصر قابل کشیدن است.
- `false`: عنصر قابل کشیدن نیست.

> **هشدار:**
> این ویژگی از نوع _enumerated_ است نه _Boolean_. مقدار `true` یا `false` الزامی است و استفادهٔ کوتاه‌شده مانند `<img draggable>` مجاز نیست. استفادهٔ درست `<img draggable="true">` است.

اگر این ویژگی تنظیم نشده باشد، مقدار پیش‌فرض آن `auto` است؛ یعنی رفتار کشیدن مطابق رفتار پیش‌فرض مرورگر است: فقط انتخاب‌های متنی، تصاویر و لینک‌ها قابل کشیدن هستند. برای سایر عناصر، رویداد {{domxref('HTMLElement.dragstart_event', 'ondragstart')}} باید برای کار کردن کشیدن و رها کردن تنظیم شود، همان‌طور که در این [مثال جامع](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations) نشان داده شده است.

## همچنین ببینید

- همهٔ [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes).