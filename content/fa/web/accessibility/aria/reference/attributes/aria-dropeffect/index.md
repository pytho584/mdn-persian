---
title: "ARIA: aria-dropeffect attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-dropeffect"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-dropeffect attribute"
short-title: aria-dropeffect
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-dropeffect
page-type: aria-attribute
status:
  - deprecated
spec-urls: https://w3c.github.io/aria/#aria-dropeffect
sidebar: accessibilitysidebar
---

ویژگی سراسری `aria-dropeffect` نشان می‌دهد که هنگام رها شدن یک شیء کشیده‌شده روی هدف رهاسازی، چه عملکردهایی ممکن است انجام شود. {{deprecated_inline}}

## توضیحات

ویژگی `aria-dropeffect` که در ARIA 1.1 منسوخ شده است، نشان می‌دهد که هنگام رها شدن یک شیء کشیده‌شده روی هدف رهاسازی، چه عملکردهایی ممکن است انجام شود. ویژگی سراسری `aria-dropeffect` اطلاعاتی را که کاربران فناوری‌های کمکی از طریق [`DataTransfer.dropEffect`](/en-US/docs/Web/API/DataTransfer/dropEffect) دریافت می‌کنند، به همان شکلی که کاربران بینا از طریق آیکون dropeffect دریافت می‌کنند، فراهم می‌کند.

انتخاب‌های متنی، تصاویر و پیوندها به‌طور پیش‌فرض قابل کشیدن هستند. تنظیم ویژگی سراسری [`draggable="true"`](/en-US/docs/Web/HTML/Reference/Global_attributes/draggable) که بخشی از [API کشیدن و رها کردن HTML5](/en-US/docs/Web/API/HTML_Drag_and_Drop_API) است، به همراه یک [مدیر رویداد `dragstart`](/en-US/docs/Web/API/HTMLElement/dragstart_event)، به این معناست که هر گره DOM نیز می‌تواند قابل کشیدن شود.

هنگامی که یک رویداد کشیدن رخ می‌دهد، یک تصویر نیمه‌شفاف از عنصر کشیده‌شده تولید می‌شود که در طول کشیدن، مکان‌نمای کاربر را دنبال می‌کند. تصویر پیش‌فرض را می‌توان با [`setDragImage`](/en-US/docs/Web/API/DataTransfer/setDragImage) به هر تصویری تغییر داد. در کنار تصویر پیش‌فرض که عنصر در حال کشیده‌شدن را شناسایی می‌کند، یک ویژگی [`dataTransfer.dropEffect`](/en-US/docs/Web/API/DataTransfer/dropEffect) وجود دارد که می‌تواند برای کنترل بازخورد بصری که به کاربر در طول عملیات کشیدن و رها کردن داده می‌شود، استفاده شود. ویژگی `aria-dropeffect` باید برای ارائه همان بازخوردی که کاربران بینا از طریق ویژگی `dataTransfer.dropEffect` دریافت می‌کنند، به کاربران فناوری‌های کمکی استفاده شود.

`dropeffect` تعیین می‌کند که مرورگر هنگام کشیدن، کدام مکان‌نما را نمایش می‌دهد و روی عنصری تنظیم می‌شود که ممکن است عنصر روی آن رها شود. در طول عملیات کشیدن، وقتی عنصر قابل کشیدن روی نواحی مختلف رهاسازی کشیده می‌شود، اثرات کشیدن — هم `dataTransfer.dropeffect` و هم `aria-dropeffect` — باید تغییر کنند تا نوع عملیاتی که در صورت رها شدن عنصر کشیده‌شده انجام می‌شود، نشان داده شود.

ممکن است بیش از یک اثر رهاسازی برای یک عنصر خاص پشتیبانی شود. بنابراین، مقدار ویژگی `aria-dropeffect` یک لیست جدا شده با فاصله از عملکردها است. عملکردها شامل `copy`، `execute`، `link` و `move` هستند. مقدار پیش‌فرض `none` است، به این معنی که هیچ عملکرد پشتیبانی‌شده‌ای در برنامه وجود ندارد. تنظیم `aria-dropeffect="popup"` به کاربران فناوری‌های کمکی اطلاع می‌دهد که یک منوی بازشو یا گفتگوی عملیات کشیدن وجود دارد که کاربر می‌تواند از بین آن‌ها انتخاب کند.

گنجاندن این ویژگی به فناوری‌های کمکی امکان می‌دهد که گزینه‌های کشیدن احتمالی موجود را به کاربر فناوری کمکی منتقل کنند، اما هیچ عملکرد واقعی اضافه نمی‌کند.

انتظار می‌رود ویژگی `aria-dropeffect` در نسخه آینده WAI-ARIA با یک ویژگی جدید جایگزین شود و منسوخ در نظر گرفته می‌شود.

به طور معمول، عملکردهای اثر رهاسازی فقط زمانی می‌توانند ارائه شوند که یک شیء برای عملیات کشیدن گرفته شده باشد، زیرا عملکردهای اثر رهاسازی موجود به شیء در حال کشیده‌شدن بستگی دارند. بنابراین، معمولاً `aria-dropeffect` را به همه اهداف رهاسازی بالقوه وقتی رویداد {{domxref("HTMLElement/dragstart_event", "dragstart")}} رخ می‌دهد، اضافه می‌کنید.

## مقادیر

مقدار، یک لیست جدا شده با فاصله از اقدامات ممکن است. توکن‌های معتبر عبارتند از:

- `copy`
  - : یک نسخه تکراری از شیء مبدأ روی هدف رها می‌شود.
- `execute`
  - : یک عملکرد پشتیبانی‌شده توسط هدف رهاسازی با استفاده از منبع کشیدن به عنوان ورودی اجرا می‌شود.
- `link`
  - : یک مرجع یا میانبر به شیء کشیده‌شده در شیء هدف ایجاد می‌شود.
- `move`
  - : شیء مبدأ از مکان فعلی خود حذف و روی هدف رها می‌شود.
- `none` (پیش‌فرض)
  - : هیچ عملیاتی نمی‌تواند انجام شود؛ در صورت تلاش برای رها کردن روی این شیء، عملیات کشیدن عملاً لغو می‌شود. اگر با هر مقدار توکن دیگری ترکیب شود نادیده گرفته می‌شود؛ به عنوان مثال، 'none copy' معادل مقدار 'copy' است.
- `popup`
  - : یک منوی بازشو یا گفتگو وجود دارد که به کاربر اجازه می‌دهد یکی از عملیات کشیدن (کپی، انتقال، پیوند، اجرا) و هر عملکرد کشیدن دیگری مانند لغو را انتخاب کند.

## نقش‌های مرتبط

در **همه** نقش‌ها استفاده می‌شود.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`aria-grabbed`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-grabbed)
- [ویژگی سراسری HTML `draggable`](/en-US/docs/Web/HTML/Reference/Global_attributes/draggable)
- [API کشیدن و رها کردن HTML](/en-US/docs/Web/API/HTML_Drag_and_Drop_API)
- {{domxref('dataTransfer')}}
- {{domxref('DataTransfer.dropEffect')}}
- {{domxref("HTMLElement/dragstart_event", "dragstart")}}