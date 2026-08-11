---
title: "<meta name> HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/meta/name"
translated_by: "n8n + AI"
---

ویژگی **`name`** در عنصر `<meta>` ابرداده را به‌صورت جفت‌های نام-مقدار فراهم می‌کند.  
وقتی یک عنصر `<meta>` دارای ویژگی `name` باشد، ویژگی [`content`](/en-US/docs/Web/HTML/Reference/Attributes/content) مقدار متناظر را تعریف می‌کند. این ابرداده، _ابرداده‌ی سطح سند_ است که به کل صفحه اعمال می‌شود.

برای مثال، تگ `<meta>` زیر یک `description` را به‌عنوان ابرداده برای یک سند فراهم می‌کند:

```html
<meta
  name="description"
  content="The HTML reference describes all elements and attributes of HTML, including global attributes that apply to all elements." />
```

## مقدار

### نام‌های متا تعریف‌شده در مشخصات HTML

مشخصات HTML مجموعه نام‌های استاندارد زیر را برای ابرداده تعریف می‌کند:

- `application-name`
  - : مرورگرها ممکن است از این مقدار برای شناسایی برنامه‌ای که در صفحه وب در حال اجراست استفاده کنند.  
    این مقدار با عنصر `<title>` متفاوت است؛ `<title>` ممکن است نام برنامه (یا وب‌سایت) را داشته باشد، اما می‌تواند اطلاعات زمینه‌ای مانند نام سند یا وضعیت را نیز اضافه کند.  
    صفحات جداگانه نباید `application-name` یکتا و مخصوص خودشان تعریف کنند.  
    برای ارائه ترجمه‌ها، از چندین تگ `<meta>` با ویژگی `lang` برای هر زبان استفاده کنید:

    ```html
    <meta name="application-name" content="Weather Wizard" lang="en" />
    <meta name="application-name" content="Mago del Clima" lang="es" />
    ```

- `author`
  - : نام نویسنده سند.
- [`color-scheme`](/en-US/docs/Web/HTML/Reference/Elements/meta/name/color-scheme)
  - : یک یا چند طرح رنگی که سند با آن‌ها سازگار است را مشخص می‌کند.  
    مرورگر از این اطلاعات همراه با تنظیمات مرورگر یا دستگاه کاربر استفاده می‌کند تا تعیین کند چه رنگ‌هایی را برای همه چیز از پس‌زمینه و پیش‌زمینه گرفته تا کنترل‌های فرم و اسکرول‌بارها استفاده کند.  
    کاربرد اصلی `<meta name="color-scheme">` تعیین سازگاری و ترتیب اولویت برای حالت‌های رنگی روشن و تاریک است.
- `description`
  - : خلاصه‌ای کوتاه و دقیق از محتوای صفحه که معمولاً به آن «متا توضیحات» (meta description) گفته می‌شود.  
    موتورهای جستجو مانند گوگل از این ابرداده برای تنظیم [ظاهر یک صفحه وب در نتایج جستجو](https://developers.google.com/search/docs/appearance/snippet#meta-descriptions) استفاده می‌کنند.
- `generator`
  - : شناسه نرم‌افزاری که صفحه را تولید کرده است.
- `keywords`
  - : کلمات مرتبط با محتوای صفحه که با کاما از هم جدا می‌شوند.
- [`referrer`](/en-US/docs/Web/HTML/Reference/Elements/meta/name/referrer)
  - : هدر HTTP `Referer` در درخواست‌هایی که از سند ارسال می‌شوند را کنترل می‌کند.
- [`theme-color`](/en-US/docs/Web/HTML/Reference/Elements/meta/name/theme-color)
  - : رنگی پیشنهادی را نشان می‌دهد که عامل کاربر باید برای سفارشی‌سازی نمایش صفحه یا رابط کاربری اطراف آن استفاده کند.  
    ویژگی [`content`](/en-US/docs/Web/HTML/Reference/Attributes/content) شامل یک `<color>` معتبر CSS است.  
    ویژگی [`media`](/en-US/docs/Web/HTML/Reference/Elements/meta#media) با یک لیست رسانه‌ای معتبر می‌تواند اضافه شود تا مشخص کند ابرداده رنگ تم برای کدام رسانه اعمال می‌شود.

### نام‌های متا تعریف‌شده در سایر مشخصات

- [`responsive-embedded-sizing`](/en-US/docs/Web/HTML/Reference/Elements/meta/name/responsive-embedded-sizing)
  - : سند جاسازی‌شده را برای به اشتراک‌گذاری اطلاعات اندازهٔ خود با صفحهٔ والد انتخاب می‌کند. این قابلیت در [ماژول Box Sizing در CSS](/en-US/docs/Web/CSS/Guides/Box_sizing) تعریف شده است.
- [`text-scale`](/en-US/docs/Web/HTML/Reference/Elements/meta/name/text-scale)
  - : این امکان را برای صفحه فراهم می‌کند که `font-size` عنصر ریشهٔ `<html>` متناسب با تنظیمات مقیاس متن در سطح سیستم‌عامل و مرورگر تغییر کند. در [ماژول Fonts در CSS](/en-US/docs/Web/CSS/Guides/Fonts) تعریف شده است.
- [`viewport`](/en-US/docs/Web/HTML/Reference/Elements/meta/name/viewport)
  - : نکاتی دربارهٔ اندازهٔ اولیهٔ viewport ارائه می‌دهد. در [ماژول Viewport در CSS](/en-US/docs/Web/CSS/Guides/Viewport) تعریف شده است.

### نام‌های متا تعریف‌شده در ویکی WHATWG MetaExtensions

صفحهٔ [WHATWG Wiki MetaExtensions](https://wiki.whatwg.org/wiki/MetaExtensions) شامل مجموعهٔ بزرگی از نام‌های متادیتای غیراستاندارد است. برخی از این نام‌ها در عمل بسیار رایج هستند، به‌ویژه موارد زیر:

- `creator`
  - : نام خالق سند، مانند یک سازمان یا مؤسسه. اگر بیش از یک خالق وجود داشته باشد، باید از چند عنصر `<meta>` استفاده کرد.
- `googlebot`
  - : مترادفی برای `robots` است و فقط توسط Googlebot (خزندهٔ نمایه‌سازی گوگل) دنبال می‌شود.
- `publisher`
  - : نام ناشر سند.
- [`robots`](/en-US/docs/Web/HTML/Reference/Elements/meta/name/robots)
  - : فهرستی از مقادیر جدا‌شده با کاما که رفتار خزش را برای ربات‌های همکار (یا «robots») در این صفحه مشخص می‌کند.

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- [فراداده: عنصر `<meta>`](/en-US/docs/Learn_web_development/Core/Structuring_content/Webpage_metadata#metadata_the_meta_element)