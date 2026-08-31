---
title: "ARIA: aria-placeholder attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-placeholder"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-placeholder attribute"
short-title: aria-placeholder
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-placeholder
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-placeholder
sidebar: accessibilitysidebar
---

ویژگی `aria-placeholder` یک راهنمای کوتاه (یک کلمه یا عبارت کوتاه) را تعریف می‌کند که برای کمک به کاربر در ورود داده‌ها زمانی که یک کنترل فرم مقداری ندارد، در نظر گرفته شده است. این راهنما می‌تواند یک مقدار نمونه یا توضیح مختصری از قالب مورد انتظار باشد.

## توضیحات

placeholder متنی است که در کنترل فرم زمانی که مقداری تنظیم نشده باشد ظاهر می‌شود. ویژگی HTML [`placeholder`](/en-US/docs/Web/HTML/Reference/Elements/input#placeholder) امکان ارائه یک مقدار نمونه یا توضیح مختصری از قالب مورد انتظار برای چندین نوع HTML {{HTMLElement('input')}} و {{HTMLElement('textarea')}} را فراهم می‌کند.

اگر با استفاده از هر عنصر دیگری یک `textbox` ایجاد می‌کنید، `placeholder` پشتیبانی نمی‌شود. اینجاست که `aria-placeholder` وارد عمل می‌شود. ویژگی `aria-placeholder` می‌تواند برای تعریف یک راهنمای کوتاه برای کمک به کاربر در درک نوع داده‌ای که انتظار می‌رود، زمانی که یک کنترل فرم غیرمعنایی مقداری ندارد، استفاده شود.

```html
<span id="date-of-birth">Birthday</span>
<div
  contenteditable
  role="textbox"
  aria-labelledby="date-of-birth"
  aria-placeholder="MM-DD-YYYY">
  MM-DD-YYYY
</div>
```

راهنمای placeholder باید هر زمان که مقدار کنترل خالی است، از جمله زمانی که یک مقدار حذف می‌شود، به کاربر نشان داده شود.

> [!NOTE]
> ARIA فقط درخت دسترسی یک عنصر را اصلاح می‌کند و بنابراین نحوه ارائه محتوا به کاربران توسط فناوری کمکی را تغییر می‌دهد. ARIA هیچ چیزی را در مورد عملکرد یا رفتار یک عنصر تغییر نمی‌دهد. هنگامی که از عناصر HTML معنایی برای هدف مورد نظر و عملکرد پیش‌فرض آنها استفاده نمی‌کنید، باید از JavaScript برای مدیریت رفتار استفاده کنید.

`aria-placeholder` علاوه بر برچسب استفاده می‌شود، نه به جای آن. آنها اهداف و عملکردهای متفاوتی دارند. برچسب توضیح می‌دهد که چه نوع اطلاعاتی انتظار می‌رود. متن placeholder یک راهنمایی در مورد مقدار مورد انتظار ارائه می‌دهد.

> [!WARNING]
> استفاده از placeholder به جای برچسب قابل مشاهده به دسترسی و قابلیت استفاده برای بسیاری از کاربران از جمله کاربران مسن و کاربران دارای اختلالات شناختی، حرکتی، مهارت‌های حرکتی ظریف و بینایی آسیب می‌زند. برچسب‌ها بهتر هستند: آنها همیشه قابل مشاهده هستند و ناحیه ضربه بزرگتری برای تمرکز روی کنترل فراهم می‌کنند. Placeholderها چندین اشکال دارند: زمانی که کنترل هر مقداری داشته باشد، حتی فضای خالی، ناپدید می‌شوند، می‌توانند کاربران را در مورد پر شدن از قبل مقدار گیج کنند، و رنگ پیش‌فرض دارای کنتراست کافی نیست.

> [!NOTE]
> Placeholderها فقط باید برای نشان دادن یک نمونه از نوع داده‌ای که باید در فرم وارد شود استفاده شوند؛ آنها جایگزین یک برچسب مناسب نمی‌شوند.

## مقادیر

- `<string>`
  - : کلمه یا عبارت کوتاهی که در یک کنترل زمانی که کنترل مقداری ندارد نمایش داده می‌شود.

## واسط‌های مرتبط

- {{domxref("Element.ariaPlaceholder")}}
  - : ویژگی [`ariaPlaceholder`](/en-US/docs/Web/API/Element/ariaPlaceholder)، بخشی از واسط {{domxref("Element")}}، مقدار ویژگی `aria-placeholder` را منعکس می‌کند.
- {{domxref("ElementInternals.ariaPlaceholder")}}
  - : ویژگی [`ariaPlaceholder`](/en-US/docs/Web/API/ElementInternals/ariaPlaceholder)، بخشی از واسط {{domxref("ElementInternals")}}، مقدار ویژگی `aria-placeholder` را منعکس می‌کند.

## نقش‌های مرتبط

استفاده شده در نقش‌ها:

- [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)

به ارث برده شده در نقش‌ها:

- [`searchbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/searchbox_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [ویژگی HTML `placeholder`](/en-US/docs/Web/HTML/Reference/Elements/input#placeholder)
- [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby)
- [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label)