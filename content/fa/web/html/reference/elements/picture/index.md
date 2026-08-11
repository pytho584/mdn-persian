---
title: "<picture> HTML picture element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/picture"
translated_by: "n8n + AI"
---

# عنصر `<picture>` در HTML

عنصر **`<picture>`** در [HTML](/en-US/docs/Web/HTML) شامل صفر یا چند عنصر `<source>` و یک عنصر `<img>` است تا نسخه‌های جایگزینی از یک تصویر را برای سناریوهای مختلف نمایش یا دستگاه ارائه دهد.

مرورگر هر `<source>` فرزند را بررسی می‌کند و بهترین گزینه را میان آن‌ها انتخاب می‌کند. اگر هیچ گزینه‌ای مطابق پیدا نشود—یا مرورگر از عنصر `<picture>` پشتیبانی نکند—آدرس مشخص‌شده در ویژگی [`src`](/en-US/docs/Web/HTML/Reference/Elements/img#src) عنصر `<img>` انتخاب می‌شود. سپس تصویر انتخاب‌شده در فضایی که عنصر `<img>` اشغال کرده نمایش داده می‌شود.

```html interactive-example
<!--Change the browser window width to see the image change.-->

<picture>
  <source
    srcset="/shared-assets/images/examples/surfer.jpg"
    media="(orientation: portrait)" />
  <img src="/shared-assets/images/examples/painted-hand.jpg" alt="" />
</picture>
```

برای تصمیم‌گیری درباره اینکه کدام URL بارگذاری شود، user agent ویژگی‌های [`srcset`](/en-US/docs/Web/HTML/Reference/Elements/source#srcset)، [`media`](/en-US/docs/Web/HTML/Reference/Elements/source#media) و [`type`](/en-US/docs/Web/HTML/Reference/Elements/source#type) هر `<source>` را بررسی می‌کند و تصویری سازگار انتخاب می‌کند که بهترین تطابق را با چیدمان فعلی و قابلیت‌های دستگاه نمایش‌دهنده داشته باشد.

عنصر `<img>` دو هدف دارد:

1. اندازه و دیگر ویژگی‌های تصویر و نحوه نمایش آن را توصیف می‌کند.
2. در صورتی که هیچ‌یک از `<source>`های ارائه‌شده نتوانند تصویر قابل‌استفاده‌ای فراهم کنند، به‌عنوان جایگزین (fallback) عمل می‌کند.

کاربردهای رایج `<picture>`:

- **هنرگردانی (Art direction).** برش یا تغییر تصاویر برای شرایط `media` مختلف (مثلاً بارگذاری نسخه ساده‌تری از تصویری که جزئیات زیادی دارد، در نمایشگرهای کوچک‌تر).
- **ارائه فرمت‌های جایگزین تصویر**، برای مواردی که برخی فرمت‌ها پشتیبانی نمی‌شوند.

  > [!NOTE]
  > برای مثال، فرمت‌های جدیدتر مانند [AVIF](/en-US/docs/Web/Media/Guides/Formats/Image_types#avif_image) یا [WEBP](/en-US/docs/Web/Media/Guides/Formats/Image_types#webp_image) مزیت‌های زیادی دارند، اما ممکن است توسط مرورگر پشتیبانی نشوند. فهرست فرمت‌های تصویری پشتیبانی‌شده را در [راهنمای نوع و فرمت فایل تصویری](/en-US/docs/Web/Media/Guides/Formats/Image_types) ببینید.

- **صرفه‌جویی در پهنای باند و افزایش سرعت بارگذاری صفحه** با بارگذاری مناسب‌ترین تصویر برای نمایشگر کاربر.

اگر می‌خواهید نسخه‌هایی با تراکم بالاتر از یک تصویر را برای نمایشگرهای با تراکم بالا (Retina) ارائه دهید، به‌جای آن از [`srcset`](/en-US/docs/Web/HTML/Reference/Elements/img#srcset) روی عنصر `<img>` استفاده کنید. این کار به مرورگر اجازه می‌دهد در حالت‌های ذخیره‌سازی داده نسخه‌های کم‌تراکم‌تر را انتخاب کند و شما مجبور نیستید شرایط `media` صریح بنویسید.

## ویژگی‌ها

این عنصر فقط [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) را شامل می‌شود.

## نکات استفاده

برای تنظیم موقعیت تصویر در قاب عنصر می‌توانید از ویژگی {{cssxref("object-position")}} و برای کنترل نحوه تغییر اندازه تصویر برای قرار گرفتن در قاب از {{cssxref("object-fit")}} استفاده کنید.

> [!NOTE]
> این ویژگی‌ها را روی `<img>` فرزند اعمال کنید، **نه** روی عنصر `<picture>`.

## مثال‌ها

این مثال‌ها نشان می‌دهند که ویژگی‌های مختلف عنصر `<source>` چگونه انتخاب تصویر داخل `<picture>` را تغییر می‌دهند.

### ویژگی media

ویژگی `media` یک شرط رسانه‌ای (مشابه media query) مشخص می‌کند که user agent برای هر عنصر `<source>` ارزیابی می‌کند.

اگر شرط رسانه‌ای `<source>` ارزیابی‌اش `false` باشد، مرورگر آن را رد می‌کند و عنصر بعدی داخل `<picture>` را بررسی می‌کند.

می‌توانید با استفاده از media feature با نام `prefers-color-scheme`، فایل‌های تصویر را بین تم روشن و تاریک جابه‌جا کنید:

```html
<picture>
  <source srcset="mdn-logo-wide.png" media="(width >= 600px)" />
  <img src="mdn-logo-narrow.png" alt="MDN" />
</picture>
```

```html
<picture>
  <source srcset="logo-dark.png" media="(prefers-color-scheme: dark)" />
  <source srcset="logo-light.png" media="(prefers-color-scheme: light)" />
  <img src="logo-light.png" alt="Product logo" />
</picture>
```

### ویژگی `srcset`

ویژگی [srcset](/en-US/docs/Web/HTML/Reference/Elements/source#srcset) برای ارائه فهرستی از تصاویر ممکن بر اساس اندازه یا تراکم پیکسلی نمایشگر استفاده می‌شود.

این ویژگی شامل فهرستی از توصیفگرهای تصویر است که با کاما از هم جدا شده‌اند. هر توصیفگر تصویر شامل URL تصویر و _یکی_ از موارد زیر است:

- یک _توصیفگر عرض_ که با حرف `w` همراه است (مانند `300w`)؛
  _یا_
- یک _توصیفگر تراکم پیکسل_ که با حرف `x` همراه است (مانند `2x`) تا برای صفحه‌نمایش‌های با DPI بالا، تصویری با وضوح بالا ارائه دهد.

حتماً به این نکات توجه کنید:

- توصیفگر عرض و توصیفگر تراکم پیکسل را نباید همزمان استفاده کرد.
- نبود توصیفگر تراکم پیکسل به معنای `1x` است.
- مقادیر تکراری مجاز نیستند (مثلاً `2x` و `2x` یا `100w` و `100w`).

مثال زیر کاربرد ویژگی `srcset` را با عنصر `<source>` برای تعیین تصویر با تراکم بالا و تصویر با وضوح استاندارد نشان می‌دهد:

```html
<picture>
  <source srcset="logo.png, logo-1.5x.png 1.5x" />
  <img src="logo.png" alt="MDN Web Docs logo" height="320" width="320" />
</picture>
```

ویژگی `srcset` را می‌توان مستقیماً روی عنصر `<img>` نیز استفاده کرد، بدون نیاز به عنصر `<picture>`. مثال زیر نحوه استفاده از `srcset` را برای تعیین تصویر با وضوح استاندارد و تصویر با تراکم بالا، به ترتیب، نشان می‌دهد:

```html
<img
  srcset="logo.png, logo-2x.png 2x"
  src="logo.png"
  height="320"
  width="320"
  alt="MDN Web Docs logo" />
```

### ویژگی `sizes`

ویژگی [`sizes`](/en-US/docs/Web/HTML/Reference/Elements/source#sizes) در عنصر `<source>` به شما امکان می‌دهد مجموعه‌ای از جفت‌های «شرط رسانه و طول» را مشخص کنید و اندازه نمایش تصویر را برای هر شرط تعیین کنید. این کار به مرورگر کمک می‌کند مناسب‌ترین تصویر را از فهرست `srcset` انتخاب کند؛ فهرستی که تصاویر را با [عرض ذاتی](/en-US/docs/Glossary/Intrinsic_Size) آن‌ها معرفی می‌کند.

مرورگر پیش از دانلود هر تصویر، شرط‌های رسانه را در ویژگی `sizes` ارزیابی می‌کند. برای اطلاعات بیشتر، ویژگی `sizes` عناصر [`<img>`](/en-US/docs/Web/HTML/Reference/Elements/img#sizes) و [`<source>`](/en-US/docs/Web/HTML/Reference/Elements/source#sizes) را ببینید.

برای مثال:

```html
<picture>
  <source
    srcset="small.jpg 480w, medium.jpg 800w, large.jpg 1200w"
    sizes="(max-width: 600px) 400px, 800px"
    type="image/jpeg" />
  <img src="fallback.jpg" alt="Example image" />
</picture>
```

در این مثال:

- اگر عرض viewport کمتر یا مساوی 600px باشد، اندازه اسلات 400px است؛ در غیر این صورت 800px است.
- مرورگر اندازه اسلات را در نسبت پیکسل دستگاه ضرب می‌کند تا عرض ایده‌آل تصویر مشخص شود و سپس نزدیک‌ترین تصویر موجود را از `srcset` انتخاب می‌کند.

بدون `sizes`، مرورگر از اندازه پیش‌فرض تصویر بر اساس ابعاد پیکسلی آن استفاده می‌کند. این اندازه ممکن است برای همه دستگاه‌ها بهترین گزینه نباشد، به‌ویژه اگر تصویر در اندازه‌های مختلف صفحه یا در بافت‌های متفاوت نمایش داده شود.

توجه داشته باشید که `sizes` تنها زمانی اثر می‌کند که در `srcset` به‌جای مقادیر نسبت پیکسل، توصیفگرهای عرض داده شده باشند (مثلاً `200w` به‌جای `2x`).  
برای اطلاعات بیشتر درباره استفاده از `srcset`، مستندات [تصاویر واکنش‌گرا](/en-US/docs/Web/HTML/Guides/Responsive_images) را ببینید.

### ویژگی `type`

ویژگی `type` یک [نوع MIME](/en-US/docs/Web/HTTP/Guides/MIME_types) را برای URLهایی که در ویژگی `srcset` عنصر `<source>` هستند مشخص می‌کند. اگر مرورگر از نوع مشخص‌شده پشتیبانی نکند، عنصر `<source>` نادیده گرفته می‌شود.

```md
<picture>
  <source srcset="photo.avif" type="image/avif" />
  <source srcset="photo.webp" type="image/webp" />
  <img src="photo.jpg" alt="photo" />
</picture>
```

## خلاصه فنی

| ویژگی | توضیحات |
| --- | --- |
| [دسته‌بندی محتوا](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories) | Flow content, phrasing content, embedded content |
| محتوای مجاز | صفر یا چند عنصر `<source>`، سپس یک عنصر `<img>`؛ به‌صورت اختیاری با عناصر پشتیبان اسکریپت (script-supporting elements) ترکیب می‌شود. |
| حذف تگ | هیچ‌کدام؛ هر دو تگ شروع و پایان الزامی هستند. |
| والدین مجاز | هر عنصری که محتوای جاسازی‌شده (embedded content) را مجاز می‌داند. |
| نقش ضمنی ARIA | [بدون نقش متناظر](https://w3c.github.io/html-aria/#dfn-no-corresponding-role) |
| نقش‌های مجاز ARIA | هیچ `role` مجاز نیست |
| رابط DOM | `HTMLPictureElement` |

## مشخصات

برای مشاهده جدول مشخصات به نسخه اصلی مستندات مراجعه کنید.

## سازگاری مرورگر

جدول سازگاری مرورگرها در نسخه اصلی MDN موجود است.

## همچنین ببینید

- عنصر `<img>`
- عنصر `<source>`
- موقعیت‌دهی و اندازه‌گذاری تصویر در قاب خود: `object-position` و `object-fit`
- [راهنمای نوع فایل تصویر و فرمت‌ها](https://developer.mozilla.org/en-US/docs/Web/Media/Guides/Formats/Image_types)
- ویژگی رسانه‌ای `@media/prefers-color-scheme`