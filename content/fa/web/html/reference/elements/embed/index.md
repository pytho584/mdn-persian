---
title: "<embed> HTML embed external content element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/embed"
translated_by: "n8n + AI"
---

عنصر **`<embed>`** یک عنصر [HTML](/en-US/docs/Web/HTML) است که محتوای خارجی را در نقطه‌ای مشخص از سند嵌入 می‌کند. این محتوا توسط یک برنامهٔ خارجی یا منبع محتوای تعاملی دیگر مانند یک افزونهٔ مرورگر تأمین می‌شود.

> [!NOTE]
> این صفحه فقط عنصری را مستند می‌کند که در [HTML Living Standard](https://html.spec.whatwg.org/multipage/iframe-embed-object.html#the-embed-element) تعریف شده است. پیاده‌سازی‌های قدیمی‌تر و غیراستاندارد این عنصر در اینجا پوشش داده نمی‌شوند.

به خاطر داشته باشید که بیشتر مرورگرهای مدرن پشتیبانی از افزونه‌های مرورگر را منسوخ و حذف کرده‌اند، بنابراین تکیه بر `<embed>` معمولاً عاقلانه نیست اگر می‌خواهید سایت شما در مرورگر کاربر معمولی کار کند.

## ویژگی‌ها (Attributes)

این عنصر شامل [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) نیز می‌شود.

- `height`
  - : ارتفاع نمایشی منبع بر حسب [پیکسل CSS](https://drafts.csswg.org/css-values/#px). مقدار باید مطلق باشد و درصد مجاز نیست.
- `src`
  - : URL منبعی که嵌入 می‌شود.
- `type`
  - : [نوع MIME](/en-US/docs/Glossary/MIME_type) برای انتخاب افزونه‌ای که باید نمونه‌سازی شود.
- `width`
  - : عرض نمایشی منبع بر حسب [پیکسل CSS](https://drafts.csswg.org/css-values/#px). مقدار باید مطلق باشد و درصد مجاز نیست.

## نکات استفاده

می‌توانید از ویژگی {{cssxref("object-position")}} برای تنظیم موقعیت شیء嵌入 شده درون قاب عنصر استفاده کنید.

> [!NOTE]
> ویژگی {{cssxref("object-fit")}} روی عناصر `<embed>` تأثیری ندارد.

## دسترسی‌پذیری (Accessibility)

از [ویژگی `title`](/en-US/docs/Web/HTML/Reference/Global_attributes/title) روی عنصر `embed` استفاده کنید تا محتوای آن را برچسب‌گذاری کنید. این کار به افرادی که با فناوری‌های کمکی مانند صفحه‌خوان (screen reader) کار می‌کنند کمک می‌کند بفهمند محتوا چیست. مقدار title باید به طور مختصر محتوای嵌入 شده را توصیف کند. بدون title، ممکن است نتوانند تشخیص دهند محتوای嵌入 شده چیست. این تغییر زمینه می‌تواند گیج‌کننده و وقت‌گیر باشد، به‌ویژه اگر عنصر `embed` حاوی محتوای تعاملی مانند ویدیو یا صدا باشد.

## مثال‌ها

```html
<embed
  type="video/quicktime"
  src="movie.mov"
  width="640"
  height="480"
  title="عنوان ویدیوی من" />
```

| خصوصیت | مقدار |
| --- | --- |
| [دسته‌های محتوا](/en-US/docs/Web/HTML/Guides/Content_categories) | [Flow content](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، [phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content)، embedded content، interactive content، [palpable content](/en-US/docs/Web/HTML/Guides/Content_categories#palpable_content). |
| محتوای مجاز | هیچ؛ یک عنصر void است. |
| حذف تگ | باید تگ شروع داشته باشد و نباید تگ پایان داشته باشد. |
| والدین مجاز | هر عنصری که محتوای embedded را می‌پذیرد. |
| نقش ARIA ضمنی | [هیچ نقش متناظری ندارد](https://w3c.github.io/html-aria/#dfn-no-corresponding-role) |
| نقش‌های ARIA مجاز | [`application`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role)، [`document`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/document_role)، [`img`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/img_role)، [`none`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role)، [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) |
| رابط DOM | `HTMLEmbedElement` |

## همچنین ببینید

- سایر عناصری که برای جاسازی محتوای انواع مختلف استفاده می‌شوند عبارت‌اند از: `<audio>`، `<canvas>`، `<iframe>`، `<img>`، `<math>`، `<object>`، `<svg>` و `<video>`.
- موقعیت‌دهی و اندازه‌دهی محتوای جاسازی‌شده درون قاب آن: `object-position` و `object-fit`.