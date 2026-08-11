---
title: "<meta name=\"robots\"> HTML attribute value"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/meta/name/robots"
translated_by: "n8n + AI"
---

مقدار **`robots`** برای attribute [`name`](/en-US/docs/Web/HTML/Reference/Elements/meta/name) در عنصر `<meta>` (که معمولاً «تگ robots» نامیده می‌شود) رفتار خزش و ایندکس‌کردن (indexing) را مشخص می‌کند که crawlerهای وب هنگام مواجهه با صفحه باید از آن پیروی کنند. اگر این مقدار指定 شود، دستورالعمل‌های crawlerها را در attribute [`content`](/en-US/docs/Web/HTML/Reference/Elements/meta#content) عنصر `<meta>` به صورت فهرستی جدا شده با کاما از یک یا چند قانون تعریف می‌کنید.

برای مثال، برای اینکه به crawlerها بفهمانید صفحه نباید در ایندکس جستجو قرار گیرد، از مقدار `noindex` استفاده می‌شود:

```html
<meta name="robots" content="noindex" />
```

> [!NOTE]
> فقط crawlerهای همکار از این قوانین پیروی می‌کنند. crawler همچنان باید به resource دسترسی داشته باشد تا headerها و meta elementها را بخواند (به [X-Robots-Tag: Interaction with robots.txt](/en-US/docs/Web/HTTP/Reference/Headers/X-Robots-Tag#interaction_with_robots.txt) مراجعه کنید). اگر می‌خواهید از مصرف پهنای باند توسط crawlerها جلوگیری کنید، یک فایل `robots.txt` محدودکننده مؤثرتر از قوانین ایندکس است، زیرا منابع را به طور کلی از خزش مسدود می‌کند.

## نکات استفاده

یک عنصر `<meta name="robots">` می‌تواند attributeهای اضافی زیر را داشته باشد:

- [`content`](/en-US/docs/Web/HTML/Reference/Elements/meta#content)
  - : attribute `content` باید تعریف شود و مقدار آن رفتار ایندکس و خزش را برای ربات‌های موتور جستجوی همکار تنظیم می‌کند. یک یا چند کلمه کلیدی از موارد زیر را به صورت فهرست جدا شده با کاما می‌پذیرد:
    - `index`
      - : به ربات اجازه می‌دهد صفحه را ایندکس کند. این رفتار پیش‌فرض است. توسط تمام crawlerهای اصلی استفاده می‌شود.
    - `noindex`
      - : از ربات می‌خواهد صفحه را ایندکس نکند. توسط تمام crawlerهای اصلی استفاده می‌شود.
    - `follow`
      - : به ربات اجازه می‌دهد لینک‌های داخل صفحه را دنبال کند. این رفتار پیش‌فرض است. توسط تمام crawlerهای اصلی استفاده می‌شود.
    - `nofollow`
      - : از ربات می‌خواهد لینک‌های داخل صفحه را دنبال نکند. توسط تمام crawlerهای اصلی استفاده می‌شود.
    - `all`
      - : معادل `index, follow`. استفاده‌شده توسط: [Google](https://developers.google.com/search/docs/crawling-indexing/special-tags?visit_id=637855965067987211-415685194&rd=1).
    - `none`
      - : معادل `noindex, nofollow`. استفاده‌شده توسط: [Google](https://developers.google.com/search/docs/crawling-indexing/special-tags?visit_id=637855965074074862-574753619&rd=1).
    - `noarchive`
      - : از موتور جستجو می‌خواهد محتوای صفحه را ذخیره (cache) نکند. استفاده‌شده توسط: [Google](https://developers.google.com/search/docs/crawling-indexing/robots-meta-tag), [Yahoo](https://help.yahoo.com/kb/search-for-desktop/SLN2213.html), [Bing](https://www.bing.com/webmasters/help/robots-meta-tags-and-attributes-that-bing-supports-5198d240).
    - `nosnippet`
      - : از نمایش هرگونه توضیح از صفحه در نتایج جستجو جلوگیری می‌کند. استفاده‌شده توسط: [Google](https://developers.google.com/search/docs/crawling-indexing/robots-meta-tag), [Bing](https://www.bing.com/webmasters/help/robots-meta-tags-and-attributes-that-bing-supports-5198d240).
    - `noimageindex`
      - : از ربات می‌خواهد که این صفحه به عنوان صفحه ارجاع‌دهنده یک تصویر ایندکس‌شده ظاهر نشود. استفاده‌شده توسط: [Google](https://developers.google.com/search/docs/crawling-indexing/robots-meta-tag).
    - `nocache`
      - : مترادف `noarchive`. استفاده‌شده توسط: [Bing](https://www.bing.com/webmasters/help/robots-meta-tags-and-attributes-that-bing-supports-5198d240).

## توضیحات

چند نکته مهم هنگام تنظیم مقدار `robots` در meta وجود دارد:

- فقط ربات‌های همکار از این قوانین پیروی می‌کنند. این قوانین نمی‌توانند از عوامل مخرب مثل email harvesterها که دستورالعمل‌ها را نادیده می‌گیرند، جلوگیری کنند.
- اگر قوانین در یک تگ `<meta>` تعریف شوند، ربات‌ها همچنان برای خواندن این قوانین باید به صفحه دسترسی داشته باشند. برای کاهش پهنای باند، بهتر است به جای آن از فایل [robots.txt](/en-US/docs/Web/Security/Practical_implementation_guides/Robots_txt) استفاده کنید.
- تگ `<meta name="robots">` و فایل `robots.txt` وظایف متفاوتی دارند: `robots.txt` crawling را کنترل می‌کند، در حالی که تگ `robots` روی indexing و سایر رفتارها تأثیر می‌گذارد.
- صفحه‌ای که توسط `robots.txt` مسدود شده است، اگر از منابع دیگر به آن لینک داده شود، ممکن است همچنان index شود.
- دستور `noindex` فقط پس از مراجعه مجدد ربات به صفحه اعمال می‌شود، بنابراین مطمئن شوید که `robots.txt` از این کار جلوگیری نمی‌کند.
- برخی مقادیر مانند `index` در مقابل `noindex` یا `follow` در مقابل `nofollow` متقابلاً انحصاری هستند. در صورت استفاده از مقادیر متناقض، رفتار مشخص نیست.
- ربات‌هایی مثل Google، Yahoo و Bing از این دستورالعمل‌ها در HTTP header `X-Robots-Tag` نیز پشتیبانی می‌کنند که برای محتوای غیر HTML مانند PDF یا تصاویر مفید است.

## مثال‌ها

### استفاده از یک کلمه کلیدی robots

مثال زیر از `nofollow` برای درخواست عدم دنبال کردن لینک‌ها توسط خزنده و از `noindex` برای درخواست حذف صفحه از فهرست (indexing) استفاده می‌کند:

```html
<meta name="robots" content="nofollow, noindex" />
```

## مشخصات (Specifications)

اگرچه این ویژگی بخشی از هیچ مشخصه‌ای نیست، اما یک روش استاندارد de facto برای ارتباط با ربات‌های جستجو، خزنده‌های وب و agentهای مشابه است.

## سازگاری مرورگر (Browser compatibility)

این ویژگی برای رعایت توسط خزنده‌ها طراحی شده است، بنابراین سازگاری مرورگر (browser compatibility) معنی ندارد.

## همچنین ببینید

- HTTP header `X-Robots-Tag`
- راهنمای پیکربندی [robots.txt](/en-US/docs/Web/Security/Practical_implementation_guides/Robots_txt)
- مدخل واژه‌نامه `robots.txt`
- مدخل واژه‌نامه `Search engine`
- RFC 9309 (Robots Exclusion Protocol)
- [صفحه MetaExtensions ویکی WHATWG](https://wiki.whatwg.org/wiki/MetaExtensions)
- [استفاده از robots meta tag](https://developers.google.com/search/docs/crawling-indexing/robots-meta-tag#robotsmeta) در developers.google.com