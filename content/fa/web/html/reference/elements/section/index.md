---
title: "<section> HTML generic section element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/section"
translated_by: "n8n + AI"
---

عنصر `<section>` یک بخش عمومی و مستقل در سند HTML است که برای آن عنصر معنایی خاص‌تری وجود ندارد. بخش‌ها باید تقریباً همیشه یک heading داشته باشند.

## Attributes

این عنصر فقط شامل [Global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## نکات استفاده

همان‌طور که گفته شد، `<section>` یک عنصر بخش‌بندی عمومی است و تنها زمانی باید استفاده شود که عنصر معنایی خاص‌تری برای آن بخش وجود نداشته باشد. مثلاً منوی ناوبری را باید درون `<nav>` قرار داد، اما لیست نتایج جستجو یا نمایش نقشه و کنترل‌های آن عنصر مشخصی ندارند و می‌توانند درون `<section>` باشند.

موارد زیر را هم در نظر بگیرید:

- اگر محتوای عنصر یک واحد مستقل و اتمی باشد که به‌تنهایی قابل انتشار است (مثلاً یک پست وبلاگ یا نظر، یا مقاله خبری)، بهتر است از `<article>` استفاده کنید.
- اگر محتوا اطلاعات جانبی مفید در کنار محتوای اصلی است، اما بخش مستقیمی از آن نیست (مثل لینک‌های مرتبط یا بیوگرافی نویسنده)، از `<aside>` استفاده کنید.
- اگر محتوا نمایانگر ناحیه اصلی محتوای سند است، از `<main>` استفاده کنید.
- اگر فقط به‌عنوان wrapper برای استایل‌دهی استفاده می‌کنید، بهتر است از `<div>` استفاده کنید.

باز هم تأکید می‌شود: هر `<section>` باید شناسایی شود، معمولاً با قرار دادن یک heading (از `<h1>` تا `<h6>` به‌عنوان فرزند `<section>`) تا جایی که ممکن است. در ادامه مثال‌هایی از `<section>` بدون heading می‌بینید.

## مثال‌ها

### مثال استفادهٔ پایه

#### قبل از استفاده از `<section>`

```html
<div>
  <h2>Heading</h2>
  <p>مقداری محتوای عالی</p>
</div>
```

##### نتیجه

{{EmbedLiveSample('Before')}}

#### بعد از استفاده از `<section>`

```html
<section>
  <h2>Heading</h2>
  <p>مقداری محتوای عالی</p>
</section>
```

##### نتیجه

{{EmbedLiveSample('After')}}

### استفاده از `<section>` بدون heading

شرایطی که ممکن است `<section>` بدون heading ببینید معمولاً در بخش‌های برنامه‌های کاربردی/UI است، نه در ساختارهای سنتی سند. در یک سند، وجود یک بخش محتوای جداگانه بدون heading برای توصیف محتوایش منطقی نیست. چنین headingهایی برای همهٔ خوانندگان مفیدند، به‌ویژه برای کاربران تکنولوژی‌های کمکی مثل screen reader، و همچنین برای SEO خوب هستند.

اما یک مکانیسم ناوبری ثانویه را در نظر بگیرید. اگر ناوبری سراسری قبلاً درون `<nav>` قرار گرفته، می‌توانید یک منوی قبلی/بعدی را درون `<section>` بگذارید:

```html
<section>
  <a href="#">مقالهٔ قبلی</a>
  <a href="#">مقالهٔ بعدی</a>
</section>
```

یا یک نوار دکمه برای کنترل اپلیکیشن خودتان. این بخش ممکن است لزوماً نیازی به heading نداشته باشد، اما باز هم یک بخش مجزا از سند است:

```html
<section>
  <button class="reply">پاسخ</button>
  <button class="reply-all">پاسخ به همه</button>
  <button class="fwd">ارسال به بعد</button>
  <button class="del">حذف</button>
</section>
```

#### نتیجه

بسته به محتوا، افزودن یک heading می‌تواند برای سئو (SEO) هم مفید باشد؛ پس این گزینه را در نظر بگیرید.

## خلاصه فنی

| ویژگی | توضیحات |
|-------|---------|
| دسته‌های محتوا | [Flow content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، [Sectioning content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#sectioning_content)، [palpable content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#palpable_content) |
| محتوای مجاز | [Flow content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#flow_content) |
| حذف تگ | هیچ‌کدام؛ هر دو تگ شروع و پایان اجباری هستند. |
| والدین مجاز | هر عنصری که [flow content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#flow_content) بپذیرد. توجه داشته باشید که عنصر `<section>` نباید از نسل عنصر `<address>` باشد. |
| نقش ARIA ضمنی | اگر عنصر [نام دسترس‌پذیر (accessible name)](https://developer.mozilla.org/en-US/docs/Glossary/Accessible_name) داشته باشد، نقش [`region`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/region_role)؛ در غیر این صورت نقش [`generic`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role) |
| نقش‌های ARIA مجاز | [`alert`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alert_role)، [`alertdialog`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alertdialog_role)، [`application`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role)، [`banner`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/banner_role)، [`complementary`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/complementary_role)، [`contentinfo`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/contentinfo_role)، [`dialog`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/dialog_role)، [`document`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/document_role)، [`feed`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/feed_role)، [`log`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/log_role)، [`main`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/main_role)، [`marquee`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/marquee_role)، [`navigation`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/navigation_role)، [`none`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role)، [`note`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/note_role)، [`presentation`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role)، [`search`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/search_role)، [`status`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/status_role)، [`tabpanel`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tabpanel_role) |
| رابط DOM | `HTMLElement` |

## مشخصات

## سازگاری مرورگر

## جستارهای وابسته

- عناصر مرتبط با بخش: `body`، `nav`، `article`، `aside`، `h1`، `h2`، `h3`، `h4`، `h5`، `h6`، `hgroup`، `header`، `footer`، `address`
- [استفاده از بخش‌ها و طرح کلی HTML](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements)
- [ARIA: نقش ناحیه](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/region_role)
- [چرا باید HTML5 article را به section ترجیح بدهید؟](https://www.smashingmagazine.com/2020/01/html5-article-section/)، اثر بروس لاسون