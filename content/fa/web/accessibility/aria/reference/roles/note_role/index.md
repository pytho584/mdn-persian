---
title: "ARIA: note role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/note_role"
translated_by: "n8n + AI"
short-title: note
slug: Web/Accessibility/ARIA/Reference/Roles/note_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#note
sidebar: accessibilitysidebar

یک نقش `note` پیشنهاد می‌دهد که یک بخش، محتوای حاشیه‌ای یا فرعی نسبت به محتوای اصلی دارد.

## توضیحات

نقش `note` را می‌توان به محتوای حاشیه‌ای یا فرعی اضافه کرد، اگر هیچ عنصر بومی یا نقش دیگری مناسب نباشد.

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

- [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) یا [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) (اختیاری)
  - : نام‌گذاری یک یادداشت اختیاری است، اما می‌تواند به کاربران صفحه‌خوان کمک کند تا زمینه و هدف آن را درک کنند. نام را می‌توان با استفاده از `aria-labelledby` در صورت وجود برچسب قابل مشاهده، یا در غیر این صورت با `aria-label` ارائه داد.

## مثال‌ها

```html
<h1>Madam C. J. Walker</h1>
<p>
  Madam C.J. Walker was an African American entrepreneur, philanthropist, and
  political and social activist.
</p>
<h2>Early Life</h2>
…
<h2>Career</h2>
…
<p role="note" class="highlight-box">
  At the height of the depression, Madam C. J. Walker trained 20,000 women to
  sell hair pomade door-to-door
</p>
<h2>Activism and Philanthropy</h2>
…
```

در مدخل بالا به سبک ویکی‌پدیا برای Madam C.J. Walker، `highlight-box` با نقش `note` می‌توانست یک {{HTMLElement('blockquote')}} باشد اگر نقل قول داشت، یا {{HTMLElement('figcaption')}} در یک {{HTMLElement('figure')}} اگر تصویر مرتبطی وجود داشت. در اینجا، چون هیچ‌کدام منطقی نبود، نقش `note` برای افزودن معناشناسی به محتوای حاشیه‌ای اضافه شد.

## مشخصات

{{Specifications}}

## جستارهای وابسته

- [نقش‌های ساختار سند](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#1._document_structure_roles)