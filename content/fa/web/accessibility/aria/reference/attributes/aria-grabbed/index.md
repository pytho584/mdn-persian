---
title: "ARIA: aria-grabbed attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-grabbed"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-grabbed attribute"
short-title: aria-grabbed
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-grabbed
page-type: aria-attribute
status:
  - deprecated
spec-urls: https://w3c.github.io/aria/#aria-grabbed
sidebar: accessibilitysidebar
---

وضعیت `aria-grabbed` حالت «گرفته شده» یک عنصر را در عملیات کشیدن و رها کردن نشان می‌دهد. {{deprecated_inline}}

## توضیحات

انتخاب‌های متنی، تصاویر و پیوندها به‌طور پیش‌فرض قابل کشیدن هستند. تنظیم ویژگی سراسری [`draggable="true"`](/en-US/docs/Web/HTML/Reference/Global_attributes/draggable) که بخشی از [Drag and Drop API](/en-US/docs/Web/API/HTML_Drag_and_Drop_API) در HTML5 است، همراه با [مدیر رویداد `dragstart`](/en-US/docs/Web/API/HTMLElement/dragstart_event)، به این معنی است که هر گره DOM نیز می‌تواند قابل کشیدن شود.

ویژگی `aria-grabbed` برای نشان دادن اینکه آیا یک عنصر در عملیات کشیدن و رها کردن در حالت «گرفته شده» قرار دارد، با `aria-grabbed="true"`، یا اینکه آیا عنصر قابل گرفتن است اما در حال حاضر گرفته نشده است، با `aria-grabbed="false"` استفاده می‌شد.

تنظیم `aria-grabbed="true"` نشان می‌داد که عنصر برای کشیدن انتخاب شده است. تنظیم `aria-grabbed="false"` نشان می‌داد که عنصر می‌تواند برای عملیات کشیدن و رها کردن گرفته شود، اما در حال حاضر گرفته نشده است.

وقتی `aria-grabbed` روی `true` تنظیم شود، ویژگی [`aria-dropeffect`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-dropeffect) همه اهداف رهاسازی بالقوه باید با نوع عملکرد یا اثری که هنگام رها شدن بر عنصر گرفته شده اعمال می‌شود، به‌روزرسانی شود. وقتی هیچ عنصری در حالت گرفته شده نباشد، ویژگی‌های `aria-dropeffect` همه اهداف رهاسازی خود را به حالت اولیه برگردانید.

ویژگی `aria-grabbed` انتظار می‌رود در نسخه آینده WAI-ARIA با یک ویژگی جدید جایگزین شود و منسوخ شده در نظر گرفته می‌شود.

> [!NOTE]
> ARIA قابلیت دسترسی را فعال نمی‌کند. ARIA فقط رفتار مورد نظر عملکرد شما را منتقل می‌کند.

## مقادیر

- `true`
  - : عنصر برای کشیدن انتخاب شده است.
- `false`
  - : عنصر در حال حاضر برای کشیدن انتخاب نشده است، اما می‌توان با تنظیم ویژگی به `true` آن را برای کشیدن در دسترس قرار داد.
- `undefined` (پیش‌فرض)
  - : عنصر از کشیده شدن پشتیبانی نمی‌کند.

## نقش‌های مرتبط

استفاده شده در **همه** [نقش‌ها](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`aria-dropeffect`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-dropeffect)
- [ویژگی سراسری `draggable` در HTML](/en-US/docs/Web/HTML/Reference/Global_attributes/draggable)
- HTML [Drag and Drop API](/en-US/docs/Web/API/HTML_Drag_and_Drop_API)
- {{domxref('dataTransfer')}}
- {{domxref('DataTransfer.dropEffect')}}
- {{domxref("HTMLElement/dragstart_event", "dragstart")}}