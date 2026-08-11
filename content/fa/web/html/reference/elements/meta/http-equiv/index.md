---
title: "<meta http-equiv> HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/meta/http-equiv"
translated_by: "n8n + AI"
---

ویژگی **`http-equiv`** در عنصر {{htmlemetry("meta")}} به شما امکان می‌دهد دستورالعمل‌های پردازشی برای مرورگر تعیین کنید، انگار که پاسخ برگشتی که سند را برگردانده شامل هدرهای HTTP مشخصی باشد. این ابرداده در سطح سند (document-level metadata) است و برای کل صفحه اعمال می‌شود.

وقتی یک عنصر `<meta>` دارای ویژگی `http-equiv` باشد، یک ویژگی [`content`](/en-US/docs/Web/HTML/Reference/Attributes/content) مقدار متناظر با `http-equiv` را مشخص می‌کند. مثلاً تگ `<meta>` زیر به مرورگر می‌گوید که صفحه را بعد از ۵ دقیقه تازه‌سازی کند:

```html
<meta http-equiv="Refresh" content="300" />
```

## مقدار (Value)

فقط زیرمجموعه‌ای از هدرهای HTTP به عنوان مقادیر `http-equiv` پشتیبانی می‌شوند. این موارد عبارتند از:

- `content-language` {{deprecated_inline}}
  - : زبان پیش‌فرض سند را تنظیم می‌کند که توسط فناوری‌های کمکی یا استایل‌دهی مرورگر استفاده می‌شود. مشابه هدر HTTP {{httpheader("Content-Language")}} است. به جای آن از ویژگی [`lang`](/en-US/docs/Web/HTML/Reference/Global_attributes/lang) استفاده کنید.
- `content-type`
  - : نوع رسانه (MIME type) و رمزگذاری نویسه‌های سند را اعلام می‌کند. اگر مشخص شود، ویژگی `content` باید `"text/html; charset=utf-8"` باشد. این معادل یک عنصر `<meta>` با ویژگی [`charset`](/en-US/docs/Web/HTML/Reference/Elements/meta#charset) است و محدودیت مشابهی در جای‌گیری درون سند دارد. فقط در اسنادی که با نوع رسانه `text/html` ارائه می‌شوند قابل استفاده است – نه در اسناد با نوع XML (`application/xml` یا `application/xhtml+xml`). به هدر HTTP {{httpheader("Content-Type")}} مراجعه کنید.
- `content-security-policy`
  - : به نویسندگان صفحه اجازه می‌دهد یک سیاست امنیت محتوا (CSP) برای صفحه فعلی تعریف کنند، معمولاً برای مشخص کردن منابع مجاز و نقاط پایانی اسکریپت جهت محافظت در برابر حملات اسکریپت‌نویسی بین‌سایتی. به هدر HTTP {{httpheader("Content-Security-Policy")}} مراجعه کنید.
- `default-style`
  - : نام مجموعه‌ی استایل‌نامه‌ی CSS پیش‌فرض را تنظیم می‌کند.
- `refresh`
  - : معادل هدر HTTP {{httpheader("Refresh")}} است. این دستورالعمل مشخص می‌کند:
    - تعداد ثانیه‌هایی که تا تازه‌سازی صفحه باید صبر شود، اگر ویژگی `content` یک عدد صحیح غیرمنفی باشد.
    - تعداد ثانیه‌هایی که تا هدایت به یک URL دیگر باید صبر شود، اگر مقدار `content` یک عدد صحیح غیرمنفی به دنبال `;url=` و یک URL معتبر باشد.

    تایمر از زمانی شروع می‌شود که صفحه به طور کامل بارگذاری شده باشد، یعنی پس از رویدادهای `load` و `pageshow`. برای اطلاعات بیشتر بخش [ملاحظات دسترسی‌پذیری](#accessibility-concerns) را ببینید.

- `set-cookie` {{deprecated_inline}}
  - : یک کوکی برای سند تنظیم می‌کند. مرورگرها اکنون این کار را نادیده می‌گیرند؛ به جای آن از هدر پاسخ HTTP {{httpheader("Set-Cookie")}} یا [`document.cookie`](/en-US/docs/Web/API/Document/cookie) استفاده کنید.
- `x-ua-compatible` {{deprecated_inline}}
  - : توسط نسخه‌های قدیمی از مرورگر منسوخ شده‌ی {{glossary("Microsoft Internet Explorer")}} استفاده می‌شد تا رفتار مشخص‌شده‌تری را دنبال کند. اگر مشخص شود، ویژگی `content` باید مقدار `"IE=edge"` داشته باشد. عامل‌های کاربر (User agents) اکنون این کار را نادیده می‌گیرند. نام آن از هدر HTTP `X-UA-Compatible` گرفته شده است.

> [!WARNING]
> برخی مرورگرها هدرهای اضافی دیگری را نیز پردازش می‌کنند که در بالا ذکر نشده‌اند. از آنجایی که هدرهای ناشناخته یا مقادیر نامعتبر نادیده گرفته می‌شوند، این می‌تواند منجر به رفتار ناهماهنگ در پیاده‌سازی‌های مختلف مرورگر شود. به ویژه، **هدرهای امنیتی دیگر را با استفاده از `<meta http-equiv=...` تنظیم نکنید**، زیرا این کار می‌تواند حس امنیت کاذب ایجاد کند!

## ملاحظات دسترسی‌پذیری (Accessibility concerns)

استفاده از مقدار `refresh` برای تازه‌سازی خودکار صفحه یا هدایت به یک URL دیگر می‌تواند برای کاربران دارای اختلالات حرکتی یا شناختی مشکل‌ساز باشد. تازه‌سازی ناگهانی صفحه ممکن است باعث حواس‌پرتی یا از دست دادن تمرکز شود. همچنین هدایت خودکار می‌تواند برای کاربرانی که از صفحه‌خوان استفاده می‌کنند گیج‌کننده باشد. بهتر است از تازه‌سازی خودکار خودداری کنید و به کاربران اجازه دهید خودشان کنترل کنند. اگر مجبور به استفاده از `refresh` هستید، از مقدار `url` به همراه تاخیر کافی (حداقل چند ثانیه) استفاده کنید و به کاربر هشدار دهید.

صفحه‌هایی که با مقدار `http-equiv="Refresh"` تنظیم شده‌اند، این خطر را دارند که فاصلهٔ زمانی refresh بیش از حد کوتاه باشد.
کاربرانی که با کمک فناوری‌های کمکی مثل صفحه‌خوان (screen reader) از صفحه استفاده می‌کنند، ممکن است نتوانند قبل از redirect خودکار، محتوای صفحه را بخوانند و آن را درک کنند.
همچنین به‌روزرسانی‌های ناگهانی و بدون اطلاع قبلی صفحه می‌تواند برای افراد کم‌بینا گیج‌کننده باشد.

- [درک WCAG از MDN، توضیحات دستورالعمل ۲.۲](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Operable#guideline_2.2_—_enough_time_provide_users_enough_time_to_read_and_use_content)
- [درک WCAG از MDN، توضیحات دستورالعمل ۳.۲](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Understandable#guideline_3.2_—_predictable_make_web_pages_appear_and_operate_in_predictable_ways)
- [درک معیار موفقیت ۲.۲.۱ | درک WCAG 2.0 از W3C](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-required-behaviors.html)
- [درک معیار موفقیت ۲.۲.۴ | درک WCAG 2.0 از W3C](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-postponed.html)
- [درک معیار موفقیت ۳.۲.۵ | درک WCAG 2.0 از W3C](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior-no-extreme-changes-context.html)

## مثال‌ها

### غیرفعال‌سازی کد inline ناامن و اجازه دادن فقط به منابع HTTPS

این المان `<meta>` در HTML، CSP پیش‌فرض را طوری تنظیم می‌کند که بارگذاری منابع (تصاویر، فونت‌ها، اسکریپت‌ها و غیره) فقط از طریق HTTPS مجاز باشد.
چون دستورهای `unsafe-inline` و `unsafe-eval` تنظیم نشده‌اند، اسکریپت‌های inline مسدود می‌شوند:

```html
<meta http-equiv="Content-Security-Policy" content="default-src https:" />
```

همین محدودیت‌ها را می‌توان با هدر HTTP معادل هم اعمال کرد:

```http
Content-Security-Policy: default-src https:
```

### تنظیم redirect برای صفحه

مثال زیر از `http-equiv="refresh"` استفاده می‌کند تا مرورگر را به انجام یک redirect هدایت کند.
ویژگی `content="3;url=https://www.mozilla.org"` بعد از ۳ ثانیه، صفحه را به `https://www.mozilla.org` redirect می‌کند:

```html
<meta http-equiv="refresh" content="3;url=https://www.mozilla.org" />
```

## همچنین ببینید

- [`<meta name="referrer">`](/en-US/docs/Web/HTML/Reference/Elements/meta/name/referrer)
- [فراداده: المان `<meta>`](/en-US/docs/Learn_web_development/Core/Structuring_content/Webpage_metadata#metadata_the_meta_element)
- [جلوگیری از حملات با استفاده از `<meta>`](https://almanac.httparchive.org/en/2022/security#preventing-attacks-using-meta) httparchive.org (2022)