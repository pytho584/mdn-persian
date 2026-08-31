```
---
title: "ARIA: article role"
short-title: article
slug: Web/Accessibility/ARIA/Reference/Roles/article_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#article
  - https://www.w3.org/WAI/ARIA/apg/patterns/feed/examples/feed/
sidebar: accessibilitysidebar
translated_by: "n8n + AI"
---

نقش `article` (مقاله) نشان‌دهنده بخشی از یک صفحه است که می‌تواند به‌راحتی به‌عنوان یک صفحه، سند یا وب‌سایت مستقل در نظر گرفته شود. این نقش معمولاً روی موارد محتوایی مرتبط مانند دیدگاه‌ها (comments)، پست‌های انجمن (forum posts)، مقالات خبری یا موارد دیگری که در یک صفحه گروه‌بندی شده‌اند، تنظیم می‌شود.

```html
<div role="article">
  <h2>Heading of the segment</h2>
  <p>Paragraph for the segment.</p>
  <p>Another paragraph.</p>
  Controls to interact with the article, share it, etc.
</div>
<div role="article">…</div>
```

این مثال دو مقاله را نشان می‌دهد که در یک صفحه کنار یکدیگر قرار دارند، می‌توانند ساختار مشابهی داشته باشند و مرتبط باشند.

> [!NOTE]
> به جای `<div>` با نقش `article`، از عنصر {{HTMLElement('article')}} استفاده کنید. **در صورت وجود، همیشه از عنصر بومی (native element) استفاده کنید.**

از `role="article"` استفاده نکنید. در عوض از عنصر `<article>` استفاده کنید.

```html
<article>
  <h2>Heading of the segment</h2>
  <p>Paragraph for the segment.</p>
  <p>Another paragraph.</p>
  Controls to interact with the article, share it, etc.
</article>
<article>…</article>
```

## توضیحات

نقش `article` (یکی از [نقش‌های ساختار سند](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#1._document_structure_roles)) به بخشی از یک سند، صفحه یا سایت اشاره دارد که اگر به‌تنهایی می‌بود، می‌توانست به‌عنوان یک سند، صفحه یا سایت کامل در نظر گرفته شود. هدف از مجموعه بخش‌های مقاله، نشان‌دادن ارتباط آن‌ها با یکدیگر است.

مقالات به‌عنوان یک نشانه‌گذاری (landmark) ناوبری در نظر گرفته نمی‌شوند، اما بسیاری از فناوری‌های کمکی که از نشانه‌گذاری‌ها پشتیبانی می‌کنند، از راهکاری برای پیمایش بین مقالات نیز پشتیبانی می‌کنند. آن‌ها ممکن است از نشان‌دادن روابط تودرتو درون مقالات نیز پشتیبانی کنند.

مقالات می‌توانند تودرتو باشند، که نشان می‌دهد یک مقاله تودرتو مستقیماً با مقاله‌ای که در آن قرار گرفته مرتبط است، اما لزوماً با مقالات خارج از سلسله‌مراتب تودرتو مرتبط نیست. برای موارد استفاده خاص به مثال‌ها مراجعه کنید.

اگر مقاله‌ای بخشی از یک فید (feed) باشد، می‌تواند ویژگی‌های [`aria-posinset`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-posinset) و [`aria-setsize`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-setsize) را داشته باشد تا مشخص کند این مقاله خاص چه جایگاهی در فید دارد.

در داخل یک `application` یا سایر ویجت‌هایی که باعث می‌شوند صفحه‌خوان‌ها و سایر فناوری‌های کمکی در حالت عبور مستقیم (pass-through) قرار گیرند، می‌توان از یک مقاله برای نشان دادن این استفاده کرد که آن‌ها باید به حالت پردازش محتوای محصورشده به‌عنوان محتوای وب معمولی بازگردند.

به جای قرار دادن نقش `article` روی یک عنصر غیر معنایی (non-semantic)، باید از عنصر {{HTMLElement('article')}} استفاده شود. عامل‌های کاربر (user agents) این عنصر را دقیقاً مانند نقش `article` به اطلاعات دسترس‌پذیری مناسب ترجمه می‌کنند. استفاده از عنصر {{HTMLElement('article')}} همچنین به موتورهای جستجو کمک می‌کند تا ساختار صفحه را بهتر کشف کنند. نمونه‌های استفاده مناسب از `role="article"` یا ترجیحاً `<article>` شامل پست‌های وبلاگ، پست‌های انجمن، یک دیدگاه روی یک پست انجمن یا وبلاگ، و هر آیتم در یک فید رسانه اجتماعی است.

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

- [`aria-posinset`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-posinset)
  - : در زمینه یک فید، موقعیت این مقاله خاص را در آن فید، بر اساس شمارشی که از ۱ شروع می‌شود، نشان می‌دهد.
- [`aria-setsize`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-setsize)
  - : در زمینه یک فید، تعداد آیتم‌های مقاله موجود در آن فید را نشان می‌دهد.

### تعاملات صفحه‌کلید

این نقش از هیچ تعامل صفحه‌کلید خاصی پشتیبانی نمی‌کند.

### ویژگی‌های جاوااسکریپت مورد نیاز

- مدیریت‌کننده‌های رویداد (Event handlers)
  - : این نقش به وجود هیچ مدیریت‌کننده رویدادی نیاز ندارد.
- تغییر مقادیر ویژگی‌ها
  - : هنگام ساخت یک فید، ویژگی‌های `aria-posinset` و `aria-setsize` را روی هر نقش مقاله با مقادیر مناسب تنظیم کنید، با در نظر گرفتن این نکته که `aria-posinset` مبتنی بر ۱ است.

> [!NOTE]
> **در صورت وجود، همیشه از عنصر بومی استفاده کنید.** به جای `<div>` با نقش `article`، باید از عنصر `<article>` استفاده شود.

## مثال‌ها

- [نمایش فید توصیه‌های رستوران](https://www.w3.org/WAI/ARIA/apg/patterns/feed/examples/feed-display.html) به همراه [مستندات](https://www.w3.org/WAI/ARIA/apg/patterns/feed/examples/feed/) جداگانه آن از الگوی طراحی فید در شیوه‌های نویسندگی WAI-ARIA 1.1

## مشخصات

{{Specifications}}

## ترتیب اولویت

این نقش با عنصر {{HTMLElement('article')}} در HTML مطابقت دارد و در صورت امکان باید از آن عنصر استفاده شود. این نقش به وجود هیچ نقش خاصی در میان فرزندانش نیاز ندارد. این تنها نقشی است که به‌عنوان فرزند مستقیم یک عنصر با نقش [`feed`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/feed_role) مجاز است.

## همچنین ببینید

- [نقش `feed`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/feed_role)
- [نقش `section`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/section_role)
- عنصر {{HTMLElement('article')}}
- تعریف واژه‌نامه {{Glossary("RSS")}}
```