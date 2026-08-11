---
title: "rel HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/rel"
translated_by: "n8n + AI"
---

# ویژگی `rel` در HTML

ویژگی **`rel`** رابطه بین یک منبع مرتبط و سند جاری را تعریف می‌کند. این ویژگی روی عناصر `<link>`، `<a>`، `<area>` و `<form>` معتبر است و مقادیر پشتیبانی‌شده به عنصری بستگی دارد که ویژگی روی آن قرار گرفته است.

نوع رابطه با مقدار ویژگی `rel` مشخص می‌شود. اگر این ویژگی حضور داشته باشد، مقدار آن باید مجموعه‌ای نامرتب از کلمات کلیدی یکتا باشد که با فاصله از هم جدا شده‌اند. برخلاف مقدار ویژگی `class` که معنای خاصی را بیان نمی‌کند، ویژگی `rel` باید نشانه‌هایی را بیان کند که هم برای ماشین و هم برای انسان از نظر معنایی معتبر باشند. فهرست‌های کنونی برای مقادیر ممکن ویژگی `rel` عبارت‌اند از [ثبت روابط لینک IANA](https://www.iana.org/assignments/link-relations/link-relations.xhtml)، [HTML Living Standard](https://html.spec.whatwg.org/multipage/links.html#linkTypes) و صفحه‌ی آزاد-قابل‌ویرایش [existing-rel-values](https://microformats.org/wiki/existing-rel-values) در ویکی microformats، همان‌طور که [Living Standard پیشنهاد کرده است](https://html.spec.whatwg.org/multipage/links.html#other-link-types). اگر از ویژگی `rel` استفاده شود که در هیچ‌یک از سه منبع بالا نباشد، برخی اعتبارسنج‌های HTML (مانند [سرویس اعتبارسنجی نشانه‌گذاری W3C](https://validator.w3.org/)) یک هشدار تولید می‌کنند.

جدول زیر برخی از مهم‌ترین کلمات کلیدی موجود را فهرست می‌کند. هر کلمه کلیدی در یک مقدار فاصله‌جدا شده باید در آن مقدار یکتا باشد.

```markdown
| مقدار `rel` | توضیحات | `<link>` | `<a>` و `<area>` | `<form>` |
| --- | --- | --- | --- | --- |
| [`alternate`](#alternate) | نمایش‌های جایگزین سند جاری. | لینک | لینک | مجاز نیست |
| [`author`](#author) | نویسندهٔ سند یا مقالهٔ جاری. | لینک | لینک | مجاز نیست |
| [`bookmark`](#bookmark) | پیوند دائمی (permalink) به نزدیک‌ترین بخش بالادستی (ancestor). | مجاز نیست | لینک | مجاز نیست |
| [`canonical`](#canonical) | URL ترجیحی برای سند جاری. | لینک | مجاز نیست | مجاز نیست |
| [`compression-dictionary`](/en-US/docs/Web/HTML/Reference/Attributes/rel/compression-dictionary) | لینک به یک dictionary فشرده‌سازی (compression dictionary) که می‌توان از آن برای فشرده‌سازی دانلودهای آیندهٔ منابع این سایت استفاده کرد. | لینک | مجاز نیست | مجاز نیست |
| [`dns-prefetch`](/en-US/docs/Web/HTML/Reference/Attributes/rel/dns-prefetch) | به مرورگر می‌گوید که برای origin منبع هدف، پیشاپیش resolution DNS را انجام دهد. | منبع خارجی | مجاز نیست | مجاز نیست |
| [`external`](#external) | سند ارجاع‌شده بخشی از همان سایت سند جاری نیست. | مجاز نیست | حاشیه‌نویسی | حاشیه‌نویسی |
| [`expect`](#expect) | وقتی با `blocking="render"` به کار رود، صفحه می‌تواند تا زمان parse شدن بخش‌های ضروری سند، رندر آن مسدود شود (render-blocked) تا به‌شکل یکدستی نمایش داده شود. | لینک | مجاز نیست | مجاز نیست |
| [`help`](#help) | لینک به راهنمای وابسته به بافتار (context-sensitive). | لینک | لینک | لینک |
| [`icon`](#icon) | یک آیکون که نمایانگر سند جاری است. | منبع خارجی | مجاز نیست | مجاز نیست |
| [`license`](#license) | نشان می‌دهد که محتوای اصلی سند جاری تحت پوشش مجوز کپی‌رایت (copyright license) است که توسط سند ارجاع‌شده توصیف شده است. | لینک | لینک | لینک |
| [`manifest`](/en-US/docs/Web/HTML/Reference/Attributes/rel/manifest) | manifest اپلیکیشن وب. | لینک | مجاز نیست | مجاز نیست |
| [`me`](/en-US/docs/Web/HTML/Reference/Attributes/rel/me) | نشان می‌دهد که سند جاری نمایانگر شخصی است که مالک محتوای لینک‌شده است. | لینک | لینک | مجاز نیست |
| [`modulepreload`](/en-US/docs/Web/HTML/Reference/Attributes/rel/modulepreload) | به مرورگر می‌گوید که پیشاپیش اسکریپت را دریافت کرده و در نقشهٔ ماژول (module map) سند ذخیره کند تا بعداً ارزیابی شود. به‌صورت اختیاری، وابستگی‌های ماژول نیز می‌توانند دریافت شوند. | منبع خارجی | مجاز نیست | مجاز نیست |
| [`next`](#next) | نشان می‌دهد که سند جاری بخشی از یک مجموعه است و سند بعدی در آن مجموعه، سند ارجاع‌شده است. | لینک | لینک | لینک |
| [`nofollow`](#nofollow) | نشان می‌دهد که نویسنده یا ناشر اصلی سند جاری، سند ارجاع‌شده را تأیید نمی‌کند. | مجاز نیست | حاشیه‌نویسی | حاشیه‌نویسی |
| [`noopener`](/en-US/docs/Web/HTML/Reference/Attributes/rel/noopener) | اگر هایپرلینک به‌طور اولیه یکی از آن‌ها را ایجاد می‌کرد (یعنی مقدار مناسبی برای attribute هدف `target` داشته باشد)، یک بافت مرور سطح بالا (top-level browsing context) ایجاد می‌کند که یک بافت مرور کمکی (auxiliary browsing context) نیست. | مجاز نیست | حاشیه‌نویسی | حاشیه‌نویسی |
| [`noreferrer`](/en-US/docs/Web/HTML/Reference/Attributes/rel/noreferrer) | هیچ هدر `Referer` ارسال نخواهد شد. علاوه بر آن، همان اثر `noopener` را دارد. | مجاز نیست | حاشیه‌نویسی | حاشیه‌نویسی |
| [`opener`](#opener) | اگر هایپرلینک در غیر این صورت یک بافت مرور سطح بالا که کمکی نیست ایجاد می‌کرد (یعنی `target` با مقدار `"_blank"`)، یک بافت مرور کمکی (auxiliary browsing context) ایجاد می‌کند. | مجاز نیست | حاشیه‌نویسی | حاشیه‌نویسی |
| [`pingback`](#pingback) | آدرس سرور pingback را می‌دهد که pingbackهای مربوط به سند جاری را مدیریت می‌کند. | منبع خارجی | مجاز نیست | مجاز نیست |
| [`preconnect`](/en-US/docs/Web/HTML/Reference/Attributes/rel/preconnect) | مشخص می‌کند که user agent باید پیشاپیش به origin منبع هدف متصل شود. | منبع خارجی | مجاز نیست | مجاز نیست |
| [`prefetch`](/en-US/docs/Web/HTML/Reference/Attributes/rel/prefetch) | مشخص می‌کند که user agent باید از قبل منبع هدف را دریافت و ذخیره کند (cache) چون احتمالاً در پیمایش بعدی به آن نیاز خواهد بود. | منبع خارجی | مجاز نیست | مجاز نیست |
| [`preload`](/en-US/docs/Web/HTML/Reference/Attributes/rel/preload) | مشخص می‌کند که user agent باید برای پیمایش جاری، منبع هدف را از قبل و بر اساس مقصد احتمالی که در attribute `as` مشخص شده (و اولویت مرتبط با آن مقصد) دریافت و cache کند. | منبع خارجی | مجاز نیست | مجاز نیست |
| [`prerender`](/en-US/docs/Web/HTML/Reference/Attributes/rel/prerender) | مشخص می‌کند که user agent باید از قبل منبع هدف را دریافت و به‌گونه‌ای پردازش کند که در آینده پاسخ سریع‌تری ارائه دهد. این قابلیت با [Speculation Rules API](/en-US/docs/Web/API/Speculation_Rules_API) جایگزین شده است. | منبع خارجی | مجاز نیست | مجاز نیست |
| [`prev`](#prev) | نشان می‌دهد که سند جاری بخشی از یک مجموعه است و سند قبلی در آن مجموعه، سند ارجاع‌شده است. | لینک | لینک | لینک |
| [`privacy-policy`](#privacy-policy) | لینکی به اطلاعات مربوط به جمع‌آوری داده‌ها و شیوه‌های استفاده‌ای فراهم می‌کند که برای سند جاری اعمال می‌شود. | لینک | لینک | مجاز نیست |
| [`search`](#search) | لینکی به منبعی می‌دهد که می‌توان از آن برای جستجو در سند جاری و صفحات مرتبط استفاده کرد. | لینک | لینک | لینک |
| [`stylesheet`](#stylesheet) | یک شیوه‌نامه (style sheet) را وارد می‌کند. | منبع خارجی | مجاز نیست | مجاز نیست |
| [`tag`](#tag) | یک برچسب (tag) (که با آدرس داده‌شده شناسایی می‌شود) ارائه می‌دهد که برای سند جاری اعمال می‌شود. | مجاز نیست | لینک | مجاز نیست |
| [`terms-of-service`](#terms-of-service) | لینک به توافق‌نامه یا شرایط استفاده (terms of service) بین ارائه‌دهندهٔ سند و کاربرانی که می‌خواهند از سند استفاده کنند. | لینک | لینک | مجاز نیست |
```

ویژگی `rel` برای عناصر {{htmlelement('link')}}، {{htmlelement('a')}}، {{htmlelement('area')}} و {{htmlelement('form')}} کاربرد دارد، اما برخی از مقادیر آن فقط برای زیرمجموعه‌ای از این عناصر معنا دارند. مانند تمام مقادیر ویژگی‌های کلیدواژه‌ای در HTML، این مقادیر نیز به بزرگی و کوچکی حروف حساس نیستند.

ویژگی `rel` مقدار پیش‌فرض ندارد. اگر این ویژگی حذف شود یا هیچ‌کدام از مقادیر آن پشتیبانی نشوند، سند رابطه خاصی با منبع مقصد ندارد، جز اینکه یک پیوند (hyperlink) بین آن دو وجود دارد. در این حالت، در عناصر {{htmlelement('link')}} و {{htmlelement('form')}}، اگر `rel` وجود نداشته باشد، کلیدواژه‌ای نداشته باشد، یا یکی از کلیدواژه‌های جداشده با فاصله (که در بالا فهرست شده‌اند) نباشد، عنصر هیچ پیوندی ایجاد نمی‌کند. اما عناصر {{htmlelement('a')}} و {{htmlelement('area')}} همچنان پیوند ایجاد می‌کنند، البته بدون رابطه تعریف‌شده.

## مقادیر

- `alternate`
  - : نشان‌دهنده یک نمایش جایگزین از سند جاری است. برای {{htmlelement('link')}}، {{htmlelement('a')}} و {{htmlelement('area')}} معتبر است و معنی آن به مقادیر ویژگی‌های دیگر بستگی دارد.
    - همراه با کلیدواژه [`stylesheet`](#stylesheet) در یک `<link>`، یک [stylesheet جایگزین](/en-US/docs/Web/HTML/Reference/Attributes/rel/alternate_stylesheet) ایجاد می‌کند.

      ```html
      <!-- یک stylesheet پایدار -->
      <link rel="stylesheet" href="default.css" />
      <!-- stylesheet‌های جایگزین -->
      <link
        rel="alternate stylesheet"
        href="highcontrast.css"
        title="High contrast" />
      ```

    - همراه با ویژگی [`hreflang`](/en-US/docs/Web/HTML/Reference/Elements/link#hreflang) که با زبان سند متفاوت است، نشان‌دهنده یک ترجمه است.
    - همراه با مقدار `"application/rss+xml"` یا `"application/atom+xml"` برای ویژگی [`type`](/en-US/docs/Web/HTML/Reference/Elements/link#type)، یک پیوند به یک فید syndication ایجاد می‌کند.

      ```html
      <link
        rel="alternate"
        type="application/atom+xml"
        href="posts.xml"
        title="Blog" />
      ```

    - در غیر این صورت، یک پیوند به یک نمایش جایگزین از سند جاری ایجاد می‌کند که ماهیت آن توسط ویژگی‌های [`hreflang`](/en-US/docs/Web/HTML/Reference/Elements/link#hreflang) و [`type`](/en-US/docs/Web/HTML/Reference/Elements/link#type) مشخص می‌شود.
      - اگر `hreflang` همراه با `alternate` داده شود و مقدار `hreflang` با زبان سند جاری متفاوت باشد، نشان می‌دهد که سند ارجاع‌شده یک ترجمه است.
      - اگر `type` همراه با `alternate` داده شود، نشان می‌دهد که سند ارجاع‌شده یک قالب جایگزین (مانند PDF) است.
      - ویژگی‌های `hreflang` و `type` می‌توانند هر دو همراه با `alternate` داده شوند.

      ```html
      <link
        rel="alternate"
        href="/fr/html/print"
        hreflang="fr"
        type="text/html"
        media="print"
        title="French HTML (for printing)" />
      <link
        rel="alternate"
        href="/fr/pdf"
        hreflang="fr"
        type="application/pdf"
        title="French PDF" />
      ```

- `author`
  - : نشان می‌دهد که سند ارجاع‌شده اطلاعات بیشتری درباره نویسنده سند یا مقاله جاری ارائه می‌دهد. برای عناصر {{htmlelement('link')}}، {{htmlelement('a')}} و {{htmlelement('area')}} کاربرد دارد.

    در {{htmlelement('a')}} و {{htmlelement('area')}}، نشان می‌دهد که سند پیوندشده (یا `mailto:`) اطلاعاتی درباره نویسنده نزدیک‌ترین عنصر جد {{htmlelement('article')}} (در صورت وجود) یا در غیر این صورت کل سند ارائه می‌دهد.

    در {{htmlelement('link')}}، نشان‌دهنده نویسنده کل سند است.

    > [!NOTE]
    > به دلایل تاریخی، مقدار منسوخ `rev="made"` معادل `rel="author"` در نظر گرفته می‌شود.

- `bookmark`
  - : به عنوان مقدار `rel` برای `element`های `<a>` و `<area>` کاربرد دارد. اگر نزدیک‌ترین `ancestor` از نوع `<article>` وجود داشته باشد، یک `permalink` به آن می‌دهد. اگر چنین `ancestor`ای نباشد، `permalink` مربوط به بخشی را می‌دهد که `element` لینک‌دهنده بیشترین ارتباط را با آن دارد.

- `canonical`
  - : برای `<link>` معتبر است؛ `URL` ترجیحی سند فعلی را تعریف می‌کند و به موتورهای جستجو در کاهش محتوای تکراری کمک می‌کند.

- `compression-dictionary` (آزمایشی)
  - : برای `<link>` معتبر است؛ یک `compression dictionary` تعریف می‌کند که می‌تواند برای فشرده‌سازی دانلودهای آینده منابع این سایت استفاده شود تا حجم این منابع نسبت به فشرده‌سازی استاندارد کمتر شود.

- `dns-prefetch`
  - : هم برای `element` `<link>` در `<body>` و هم در `<head>` کاربرد دارد. به مرورگر می‌گوید که از قبل `DNS resolution` را برای `origin` منبع هدف انجام دهد. این کار برای منابعی که کاربر احتمالاً به آن‌ها نیاز خواهد داشت مفید است؛ تأخیر را کاهش می‌دهد و در نتیجه وقتی کاربر به منابع دسترسی پیدا می‌کند، عملکرد بهتری خواهد داشت، چون مرورگر از قبل `DNS resolution` را برای `origin` منبع مشخص‌شده انجام داده است. به [dns-prefetch](/en-US/docs/Web/Performance/Guides/dns-prefetch) در [resource hints](https://w3c.github.io/resource-hints/) مراجعه کنید.

- `external`
  - : برای `<form>`، `<a>` و `<area>` کاربرد دارد و نشان می‌دهد سند ارجاع‌داده‌شده بخشی از سایت فعلی نیست. می‌توان آن را با `attribute selector`ها استفاده کرد تا لینک‌های خارجی طوری استایل بگیرند که به کاربر نشان دهند از سایت فعلی خارج خواهد شد.

- `expect` (آزمایشی)
  - : به صفحه اجازه می‌دهد تا زمانی که بخش‌های ضروری سند `parse` نشده‌اند، [render-blocked](/en-US/docs/Glossary/Render_blocking) بماند تا رندر آن یکنواخت باشد. توجه داشته باشید که `render-blocking` فقط زمانی رخ می‌دهد که با `attribute` [`blocking="render"`](/en-US/docs/Web/HTML/Reference/Elements/link#blocking) همراه باشد.

    > **نکته:** برای اطلاعات بیشتر درباره کاربرد آن، به [Stabilizing page state to make cross-document transitions consistent](/en-US/docs/Web/API/View_Transition_API/Using#stabilizing_page_state_to_make_cross-document_transitions_consistent) مراجعه کنید.

- `help`
  - : برای `<form>`، `<link>`، `<a>` و `<area>` کاربرد دارد. کلیدواژه `help` نشان می‌دهد محتوای لینک‌شده راهنمای حساس به زمینه (context-sensitive help) ارائه می‌دهد؛ اطلاعاتی برای والد (parent) `element` تعریف‌کننده پیوند و فرزندان آن. وقتی در `<link>` استفاده شود، راهنما برای کل سند است. وقتی همراه با `<a>` و `<area>` استفاده شود و مرورگر از آن پشتیبانی کند، `cursor` پیش‌فرض به‌جای `pointer` مقدار `help` خواهد گرفت.

- `icon`
  - : با `<link>` معتبر است. منبع لینک‌شده نماد (icon) سند فعلی را در رابط کاربری نمایش می‌دهد.

    رایج‌ترین استفاده از مقدار `icon` برای favicon است:

    ```html
    <link rel="icon" href="favicon.ico" />
    ```

    اگر چند `<link rel="icon">` وجود داشته باشد، مرورگر از `attribute`های [`media`](/en-US/docs/Web/HTML/Reference/Elements/link#media)، [`type`](/en-US/docs/Web/HTML/Reference/Elements/link#type) و [`sizes`](/en-US/docs/Web/HTML/Reference/Elements/link#sizes) برای انتخاب مناسب‌ترین آیکون استفاده می‌کند. اگر چند آیکون به یک اندازه مناسب باشند، آخرین آن‌ها انتخاب می‌شود. اگر بعداً مشخص شود که مناسب‌ترین آیکون در واقع نامناسب است (مثلاً به این دلیل که از فرمت پشتیبانی‌نشده استفاده می‌کند)، مرورگر به سراغ مناسب‌ترین آیکون بعدی می‌رود و همین‌طور ادامه می‌دهد.

    > **نکته:** `attribute` [`crossorigin`](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin) برای `rel="icon"` در مرورگرهای مبتنی بر Chromium پشتیبانی نمی‌شود. به [issue باز Chromium](https://crbug.com/1121645) مراجعه کنید.

> [!NOTE]
> iOS اپل، برخلاف سایر مرورگرهای موبایل، از این نوع لینک و attribute «sizes» برای انتخاب آیکون صفحه وب برای Web Clip یا placeholder راه‌اندازی استفاده نمی‌کند. در عوض، به ترتیب از [`apple-touch-icon`](https://developer.apple.com/library/archive/documentation/AppleApplications/Reference/SafariWebContent/ConfiguringWebApplications/ConfiguringWebApplications.html#//apple_ref/doc/uid/TP40002051-CH3-SW4) و [`apple-touch-startup-image`](https://developer.apple.com/library/archive/documentation/AppleApplications/Reference/SafariWebContent/ConfiguringWebApplications/ConfiguringWebApplications.html#//apple_ref/doc/uid/TP40002051-CH3-SW6) استفاده می‌کند که استاندارد نیستند.

> [!NOTE]
> نوع لینک `shortcut` اغلب قبل از `icon` دیده می‌شود، اما این نوع لینک غیراستاندارد است، نادیده گرفته می‌شود و **توسعه‌دهندگان وب دیگر نباید از آن استفاده کنند**.

- `license`
  - : مقدار `license` روی عناصر `<a>`، `<area>`، `<form>` و `<link>` معتبر است و نشان می‌دهد که لینک به سندی مربوط به اطلاعات مجوز اشاره می‌کند؛ یعنی محتوای اصلی سند جاری تحت پوشش مجوز کپی‌رایتی است که در سند مرجع توضیح داده شده است. اگر این لینک داخل عنصر `<head>` نباشد، استاندارد بین لینکی که به بخش خاصی از سند اشاره می‌کند و لینکی که به کل سند مربوط است تفاوتی قائل نمی‌شود. فقط داده‌های موجود در صفحه می‌توانند این را مشخص کنند.

    ```html
    <link rel="license" href="#license" />
    ```

    > [!NOTE]
    > اگرچه `copyright` به عنوان مترادف شناخته می‌شود، اما نادرست است و باید از آن اجتناب کرد.

- `manifest`
  - : [Web app manifest](/en-US/docs/Web/Progressive_web_apps/Manifest). برای دریافت از دامنه‌های دیگر (cross-origin) به استفاده از پروتکل CORS نیاز دارد.
- `modulepreload`
  - : برای بهبود کارایی مفید است و به عنصر `<link>` در هر جای سند مربوط می‌شود. تنظیم `rel="modulepreload"` به مرورگر می‌گوید که اسکریپت (و وابستگی‌های آن) را از قبل دریافت کند و در module map سند برای ارزیابی بعدی ذخیره کند. لینک‌های `modulepreload` می‌توانند اطمینان دهند که دریافت شبکه با ماژول آماده (اما ارزیابی‌نشده) در module map انجام می‌شود، قبل از اینکه واقعاً به آن نیاز باشد. همچنین به [`modulepreload`](/en-US/docs/Web/HTML/Reference/Attributes/rel/modulepreload) مراجعه کنید.
- `next`
  - : مربوط به عناصر `<form>`، `<link>`، `<a>` و `<area>` است. مقدار `next` نشان می‌دهد که سند جاری بخشی از یک سری است و سند بعدی در این سری، سند مرجع است. وقتی در یک `<link>` قرار می‌گیرد، مرورگرها ممکن است فرض کنند که آن سند بعدی دریافت خواهد شد و آن را به عنوان یک راهنمای منبع (resource hint) در نظر بگیرند.
- `nofollow`
  - : مربوط به عناصر `<form>`، `<a>` و `<area>` است. کلمه کلیدی `nofollow` به خزنده‌های موتور جستجو می‌گوید که رابطه لینک را نادیده بگیرند. رابطه `nofollow` ممکن است نشان دهد که مالک سند جاری، سند مرجع را تأیید نمی‌کند. این رابطه اغلب توسط بهینه‌سازان موتور جستجو (SEO) استفاده می‌شود که وانمود می‌کنند لینک‌فارم‌هایشان صفحات اسپم نیستند.
- `noopener`
  - : مربوط به عناصر `<form>`، `<a>` و `<area>` است. این مقدار یک بافت مرور سطح بالا (top-level browsing context) ایجاد می‌کند که بافت کمکی (auxiliary) نیست، اگر لینک در ابتدا یکی از این‌ها را ایجاد می‌کرد (یعنی مقدار مناسب attribute `target` را داشته باشد). به عبارت دیگر، باعث می‌شود لینک طوری رفتار کند که انگار [`window.opener`](/en-US/docs/Web/API/Window/opener) برابر null است و `target="_parent"` تنظیم شده است.

    این برعکس [`opener`](#opener) است.

- `noreferrer`
  - : مربوط به element های `<form>`، `<a>` و `<area>` است. قرار دادن این مقدار باعث می‌شود مرجع (referrer) ناشناخته بماند (هیچ هدر `Referer` ارسال نمی‌شود) و یک browsing context سطح بالا به‌گونه‌ای ایجاد می‌کند که انگار `noopener` نیز تنظیم شده است.
- `opener`
  - : اگر hyperlink در غیر این صورت یک browsing context سطح بالا ایجاد کند که یک browsing context کمکی (auxiliary) نباشد (یعنی مقدار attribute `target` برابر `"_blank"` باشد)، این مقدار یک browsing context کمکی می‌سازد. در واقع، این مقدار نقطه‌ی مقابل [noopener](#noopener) است.
- `pingback`
  - : آدرس سرور pingback را می‌دهد که pingback های مربوط به سند فعلی را مدیریت می‌کند. به [مشخصات Pingback](https://www.hixie.ch/specs/pingback/pingback) مراجعه کنید.
- `preconnect`
  - : به browser اشاره می‌کند که پیشاپیش اتصالی به وب‌سایت لینک‌شده برقرار کند، بدون اینکه اطلاعات خصوصی فاش شود یا محتوایی دانلود گردد؛ به این ترتیب، وقتی لینک دنبال شود، محتوای مرتبط سریع‌تر دریافت می‌شود.
- `prefetch`
  - : مشخص می‌کند که user agent باید منبع هدف را به‌صورت پیشگیرانه واکشی (fetch) و در حافظه نهان (cache) نگه دارد، زیرا احتمالاً برای ناوبری بعدی لازم خواهد بود. برای اطلاعات بیشتر به prefetch مراجعه کنید.
- `preload`
  - : مشخص می‌کند که user agent باید منبع هدف را برای ناوبری فعلی، بر اساس مقصد احتمالی که توسط attribute [`as`](/en-US/docs/Web/HTML/Reference/Elements/link#as) تعیین شده (و اولویت مرتبط با آن مقصد)، از قبل واکشی و در حافظه نگه دارد. صفحه مربوط به مقدار [`preload`](/en-US/docs/Web/HTML/Reference/Attributes/rel/preload) را ببینید.
- `prerender` — Deprecated, Non-standard
  - : مشخص می‌کند که user agent باید منبع هدف را از قبل واکشی و به‌گونه‌ای پردازش کند که در آینده پاسخ سریع‌تری ارائه دهد، مثلاً با واکشی زیرمنابع (subresources) یا انجام بخشی از رندر. این قابلیت با [Speculation Rules API](/en-US/docs/Web/API/Speculation_Rules_API) جایگزین شده است.
- `prev`
  - : مشابه کلمه کلیدی [`next`](#next)، مربوط به element های `<form>`، `<link>`، `<a>` و `<area>` است. مقدار `prev` نشان می‌دهد که سند فعلی بخشی از یک سری است و لینک به سند قبلی در آن سری اشاره می‌کند.

    توجه: مترادف `previous` نادرست است و نباید استفاده شود.
- `privacy-policy`
  - : برای element های `<a>`، `<area>` و `<link>` معتبر است. مقدار `privacy-policy` نشان می‌دهد که سند ارجاع‌داده‌شده، خط‌مشی حریم خصوصی (Privacy Policy) است که شیوه‌های جمع‌آوری و استفاده از داده‌های سند فعلی را توصیف می‌کند.
- `search`
  - : مربوط به element های `<form>`، `<link>`، `<a>` و `<area>` است. کلمه کلیدی `search` نشان می‌دهد که hyperlink به سندی اشاره می‌کند که رابط آن به‌طور خاص برای جستجو در سند فعلی، سایت و منابع مرتبط طراحی شده است و لینکی به منبعی فراهم می‌کند که می‌توان از آن برای جستجو استفاده کرد.

    اگر attribute [`type`](/en-US/docs/Web/HTML/Reference/Elements/link#type) برابر با `application/opensearchdescription+xml` باشد، منبع مورد نظر یک افزونه [OpenSearch](/en-US/docs/Web/XML/Guides/OpenSearch) است که می‌توان آن را به‌راحتی به رابط Firefox اضافه کرد.
- `stylesheet`
  - : برای element `<link>` معتبر است و یک منبع خارجی را به عنوان stylesheet وارد می‌کند. اگر stylesheet از نوع `text/css` باشد (که مقدار پیش‌فرض است)، نیازی به attribute [`type`](/en-US/docs/Web/HTML/Reference/Elements/link#type) نیست. اگر نوع آن `text/css` نباشد، بهتر است نوع صریحاً اعلام شود.

    اگرچه این attribute لینک را به عنوان stylesheet تعریف می‌کند، تعامل آن با سایر attribute ها و سایر کلمات کلیدی مهم در مقدار rel تعیین می‌کند که آیا stylesheet دانلود و/یا استفاده شود.

هنگامی که با کلیدواژهٔ [`alternate`](#alternate) استفاده شود، یک استایل‌شیت جایگزین را تعریف می‌کند. در این حالت، یک [`title`](/en-US/docs/Web/HTML/Reference/Elements/link#title) غیرخالی قرار دهید.

اگر رسانه (media) با مقدار ویژگی [`media`](/en-US/docs/Web/HTML/Reference/Elements/link#media) مطابقت نداشته باشد، استایل‌شیت خارجی استفاده یا حتی دانلود نمی‌شود.

برای دریافت بین‌مبدئی (cross-origin)، استفاده از پروتکل CORS الزامی است.

- `tag`
  - : برای عناصر `<a>` و `<area>` معتبر است. این مقدار یک برچسب (tag) را مشخص می‌کند که با آدرس داده‌شده شناسایی می‌شود و به سند فعلی اعمال می‌شود. مقدار `tag` یعنی پیوند به سندی اشاره دارد که برچسب اعمال‌شده به همین سند را توصیف می‌کند. این نوع پیوند برای برچسب‌های داخل ابر برچسب (tag cloud) در نظر گرفته نشده است؛ چون آن برچسب‌ها به گروهی از صفحات اعمال می‌شوند، در حالی که مقدار `tag` در ویژگی `rel` برای یک سند واحد است.

- `terms-of-service`
  - : مقدار `terms-of-service` برای عناصر `<a>`، `<area>` و `<link>` معتبر است و نشان می‌دهد سند ارجاع‌داده‌شده «شرایط استفاده از خدمات» (Terms of Service) است؛ یعنی توافقات بین ارائه‌دهندهٔ سند فعلی و کاربرانی که می‌خواهند از آن استفاده کنند.

### مقادیر غیراستاندارد

- [`apple-touch-icon`](https://developer.apple.com/library/archive/documentation/AppleApplications/Reference/SafariWebContent/ConfiguringWebApplications/ConfiguringWebApplications.html#//apple_ref/doc/uid/TP40002051-CH3-SW4)
  - : آیکون برنامهٔ وب را در دستگاه‌های iOS مشخص می‌کند.

## مشخصات

## سازگاری مرورگر

## جستارهای وابسته

- `HTMLLinkElement.relList`
- `HTMLAnchorElement.relList`
- `HTMLAreaElement.relList`