---
title: <script> HTML script element
source: https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/script
translated_by: n8n + AI
---

# \<script> HTML script element

عنصر **`<script>`** در HTML برای جاسازی کد یا داده‌های قابل اجرا استفاده می‌شود. کاربرد اصلی آن، جاسازی یا ارجاع به کد جاوااسکریپت است. همچنین می‌توان از این عنصر با زبان‌های دیگر مانند GLSL (زبان شیدر WebGL) و JSON نیز استفاده کرد.

### ویژگی‌ها

این عنصر شامل [ویژگی‌های سراسری (global attributes)](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes) نیز می‌شود.

* `async`
  *   : برای اسکریپت‌های کلاسیک (classic scripts)، اگر این ویژگی وجود داشته باشد، اسکریپت به‌طور موازی با فرایند تجزیه (parsing) بارگذاری می‌شود و به محض در دسترس بودن اجرا می‌گردد.

      برای [اسکریپت‌های ماژول (module scripts)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules)، اگر ویژگی `async` تعیین شده باشد، خود اسکریپت و تمام وابستگی‌هایش به‌طور موازی با تجزیه بارگذاری می‌شوند و به محض آماده‌شدن اجرا می‌شوند.

      > **هشدار:** این ویژگی برای اسکریپت‌های درون‌خطی (inline) که ویژگی `src` ندارند، نباید استفاده شود، زیرا در این صورت تأثیری نخواهد داشت.

      این ویژگی به حذف **جاوااسکریپت مسدودکننده parser** کمک می‌کند؛ جایی که مرورگر مجبور است قبل از ادامه تجزیه، اسکریپت را بارگذاری و اجرا کند. ویژگی `defer` نیز تأثیر مشابهی دارد.

      اگر `async` همراه با `defer` مشخص شود، عنصر طوری رفتار می‌کند که گویی فقط `async` ذکر شده است.

      این یک ویژگی بولین (boolean) است: وجود ویژگی به معنای `true` و نبود آن به معنای `false` است.

      برای اطلاعات بیشتر درباره پشتیبانی مرورگرها، به [سازگاری مرورگرها](index.md#سازگاری-مرورگرها) مراجعه کنید. همچنین [اسکریپت‌های ناهمگام برای asm.js](https://developer.mozilla.org/en-US/docs/Games/Techniques/Async_scripts) را ببینید.
* `attributionsrc` \{{deprecated\_inline\}} \{{non-standard\_inline\}}
  *   : مشخص می‌کند که مرورگر باید هدر \{{httpheader("Attribution-Reporting-Eligible")\}} را همراه با درخواست اسکریپت ارسال کند. در سمت سرور، این هدر برای فعال‌سازی ارسال هدرهای \{{httpheader("Attribution-Reporting-Register-Source")\}} یا \{{httpheader("Attribution-Reporting-Register-Trigger")\}} در پاسخ استفاده می‌شود تا به ترتیب یک [source attribution](https://developer.mozilla.org/en-US/docs/Web/API/Attribution_Reporting_API/Registering_sources#javascript-based_event_sources) یا [trigger attribution](https://developer.mozilla.org/en-US/docs/Web/API/Attribution_Reporting_API/Registering_triggers#javascript-based_attribution_triggers) مبتنی بر جاوااسکریپت ثبت شود. این که کدام هدر پاسخ باید ارسال شود، به مقدار هدر `Attribution-Reporting-Eligible` که باعث ثبت شده است بستگی دارد.

      > **نکته:** به‌جای آن، می‌توان source یا triggerهای مبتنی بر جاوااسکریپت را با ارسال درخواست \{{domxref("Window/fetch", "fetch()")\}} حاوی گزینه `attributionReporting` (چه مستقیماً روی `fetch()` یا روی یک شیء \{{domxref("Request")\}} که به `fetch()` ارسال می‌شود)، یا با ارسال \{{domxref("XMLHttpRequest")\}} به همراه \{{domxref("XMLHttpRequest.setAttributionReporting", "setAttributionReporting()")\}} روی شیء درخواست ثبت کرد.

      دو نسخه برای این ویژگی وجود دارد:

      * بولین: فقط با ذکر نام `attributionsrc`. در این حالت هدر `Attribution-Reporting-Eligible` به همان سروری که `src` به آن اشاره دارد ارسال می‌شود. این روش زمانی مناسب است که ثبت attribution source یا trigger را در همان سرور انجام می‌دهید. برای ثبت trigger، این ویژگی اختیاری است و در صورت حذف، مقدار رشته‌ای خالی استفاده می‌شود.
      *   مقدار شامل یک یا چند URL، مانند مثال زیر:

          ```html
          <script
            src="myscript.js"
            attributionsrc="https://a.example/register-source https://b.example/register-source"></script>
          ```

این امر در مواردی مفید است که منبع درخواست‌شده روی سروری که کنترل می‌کنید قرار ندارد، یا فقط می‌خواهید ثبت منبع انتساب (attribution source) را روی سرور دیگری مدیریت کنید. در این حالت، می‌توانید یک یا چند URL را به‌عنوان مقدار `attributionsrc` مشخص کنید. وقتی درخواست منبع رخ می‌دهد، هدر `Attribution-Reporting-Eligible` علاوه بر origin منبع، به URL(های) مشخص‌شده در `attributionSrc` ارسال می‌شود. این URLها می‌توانند برای تکمیل ثبت، با هدر `Attribution-Reporting-Register-Source` یا `Attribution-Reporting-Register-Trigger` پاسخ دهند.

> \[!NOTE] مشخص کردن چند URL به این معناست که چند منبع انتساب می‌توانند روی همان ویژگی ثبت شوند. برای مثال، ممکن است کمپین‌های مختلفی داشته باشید که می‌خواهید موفقیت آن‌ها را اندازه بگیرید و این کمپین‌ها گزارش‌های متفاوتی روی داده‌های مختلف تولید می‌کنند.

برای جزئیات بیشتر به [Attribution Reporting API](../../../../../../../en-US/docs/Web/API/Attribution_Reporting_API/) مراجعه کنید.

* `blocking`
  *   : این attribute به‌صراحت مشخص می‌کند که برخی عملیات‌ها باید تا زمان اجرای script مسدود شوند. عملیات‌هایی که باید مسدود شوند، فهرستی از tokenهای مسدودکننده با جداسازی فاصله هستند. در حال حاضر فقط یک token وجود دارد:

      * `render`: رندر کردن محتوا روی صفحه مسدود می‌شود.

      > \[!NOTE] فقط المان‌های `script` که در `<head>` سند هستند می‌توانند رندر را مسدود کنند. اسکریپت‌ها به‌طور پیش‌فرض render-blocking نیستند؛ اگر یک المان `script` شامل `type="module"`، `async` یا `defer` نباشد، به‌جای _rendering_، _parsing_ را مسدود می‌کند. اگر چنین المان `script` ای به‌صورت داینامیک از طریق اسکریپت اضافه شود، باید `blocking = "render"` تنظیم شود تا رندر را مسدود کند.
* [`crossorigin`](../../../../../../../en-US/docs/Web/HTML/Reference/Attributes/crossorigin/)
  * : المان‌های معمولی `script` اطلاعات کمی را به `window.onerror` برای اسکریپت‌هایی که از بررسی‌های استاندارد CORS عبور نمی‌کنند منتقل می‌کنند. برای فعال‌سازی ثبت خطا برای سایت‌هایی که از دامنه‌ای جداگانه برای رسانه‌های استاتیک استفاده می‌کنند، از این attribute استفاده کنید. برای توضیح دقیق‌تر درباره آرگومان‌های معتبر آن، به [CORS settings attributes](../../../../../../../en-US/docs/Web/HTML/Reference/Attributes/crossorigin/) مراجعه کنید.
* `defer`
  *   : این attribute بولی به مرورگر نشان می‌دهد که script قرار است پس از تجزیه سند اجرا شود، اما قبل از رویداد `DOMContentLoaded`.

      اسکریپت‌های دارای attribute `defer` جلوی رخ دادن رویداد `DOMContentLoaded` را می‌گیرند تا زمانی که اسکریپت بارگیری و ارزیابی شود.

      > \[!WARNING] اگر attribute `src` وجود نداشته باشد (یعنی برای اسکریپت‌های داخلی)، این attribute نباید استفاده شود؛ در این صورت هیچ اثری نخواهد داشت.
      >
      > attribute `defer` روی اسکریپت‌های ماژول اثری ندارد — آن‌ها به‌طور پیش‌فرض defer می‌شوند.

      اسکریپت‌های دارای attribute `defer` به ترتیب ظاهر شدن در سند اجرا می‌شوند.

      این attribute امکان حذف **جاوااسکریپت مسدودکننده پارسر** را فراهم می‌کند؛ جایی که مرورگر باید قبل از ادامه تجزیه، اسکریپت‌ها را بارگیری و ارزیابی کند. `async` در این مورد اثری مشابه دارد.

      اگر این attribute همراه با attribute `async` مشخص شده باشد، المان طوری رفتار می‌کند که گویی فقط attribute `async` مشخص شده است.
* [`fetchpriority`](../../../../../../../en-US/docs/Web/HTML/Reference/Attributes/fetchpriority/)
  * : نشان‌دهندهٔ اولویت نسبی هنگام دریافت یک اسکریپت خارجی است. مقادیر مجاز:
    * `high`
      * : اسکریپت خارجی را با اولویت بالا نسبت به سایر اسکریپت‌های خارجی دریافت کن.
    * `low`
      * : اسکریپت خارجی را با اولویت پایین نسبت به سایر اسکریپت‌های خارجی دریافت کن.
    * `auto`
      * : اولویت خاصی برای دریافت تنظیم نمی‌کند. این مقدار پیش‌فرض است. اگر مقداری تنظیم نشود یا مقدار نامعتبر باشد از این مقدار استفاده می‌شود.
* [`integrity`](../../../../../../../en-US/docs/Web/HTML/Reference/Attributes/integrity/)
  * : این ویژگی شامل یک یا چند هش (hash) از اسکریپت است. برای اطمینان از اینکه محتوای اسکریپت همان چیزی است که توسعه‌دهنده انتظار دارد و در یک [حمله به زنجیره تأمین](../../../../../../../en-US/docs/Web/Security/Attacks/Supply_chain_attacks/) با اسکریپت مخرب جایگزین نشده است، استفاده می‌شود. وقتی ویژگی `src` وجود نداشته باشد، این ویژگی نباید مشخص شود. همچنین به [Subresource Integrity](../../../../../../../en-US/docs/Web/Security/Defenses/Subresource_Integrity/) مراجعه کنید.
* `nomodule`
  * : این ویژگی Boolean مشخص می‌کند که اسکریپت در مرورگرهایی که از [ES modules](../../../../../../../en-US/docs/Web/JavaScript/Guide/Modules/) پشتیبانی می‌کنند اجرا نشود. در عمل می‌توان از آن برای ارائه اسکریپت جایگزین (fallback) به مرورگرهای قدیمی‌تر که از کد جاوااسکریپت ماژولار پشتیبانی نمی‌کنند استفاده کرد.
* `nonce`
  * : یک nonce رمزنگاری‌شده (عددی که یک‌بار استفاده می‌شود) برای اجازه دادن به اسکریپت‌ها در [script-src Content-Security-Policy](../../../../../../../en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/script-src/). سرور باید هر بار که خط‌مشی را ارسال می‌کند یک مقدار nonce یکتا تولید کند. بسیار مهم است که nonce‌ای ارائه شود که قابل حدس زدن نباشد؛ در غیر این صورت دور زدن خط‌مشی یک منبع ساده خواهد بود.
* `referrerpolicy`
  * : مشخص می‌کند هنگام دریافت اسکریپت یا منابعی که توسط اسکریپت دریافت می‌شود، کدام [referrer](../../../../../../../en-US/docs/Web/API/Document/referrer/) ارسال شود:
    * `no-referrer`: هدر `Referer` ارسال نخواهد شد.
    * `no-referrer-when-downgrade`: هدر `Referer` به منشأهایی (origin) که TLS (HTTPS) ندارند ارسال نمی‌شود.
    * `origin`: referrer ارسالی به منشأ صفحهٔ مرجع محدود می‌شود: [scheme](../../../../../../../en-US/docs/Learn_web_development/Howto/Web_mechanics/What_is_a_URL/)، host و port آن.
    * `origin-when-cross-origin`: referrer ارسالی به منشأهای دیگر به scheme، host و port محدود می‌شود. ناوبری‌های هم‌منشأ همچنان مسیر (path) را شامل می‌شوند.
    * `same-origin`: برای [هم‌منشأ](../../../../../../../en-US/docs/Web/Security/Same-origin_policy/) referrer ارسال می‌شود، اما درخواست‌های متقاطع (cross-origin) هیچ اطلاعات referrer را شامل نمی‌شوند.
    * `strict-origin`: تنها زمانی origin سند را به عنوان referrer ارسال کن که سطح امنیت پروتکل یکسان بماند (HTTPS→HTTPS)، اما به مقصد کم‌امن‌تر (HTTPS→HTTP) ارسال نکن.
    * `strict-origin-when-cross-origin` (پیش‌فرض): برای درخواست هم‌منشأ URL کامل ارسال کن، فقط زمانی که سطح امنیت پروتکل یکسان است (HTTPS→HTTPS) origin ارسال کن، و به مقصد کم‌امن‌تر (HTTPS→HTTP) هدری ارسال نکن.
    * `unsafe-url`: referrer شامل origin و مسیر (path) خواهد بود (اما نه [fragment](../../../../../../../en-US/docs/Web/API/HTMLAnchorElement/hash/)، [password](../../../../../../../en-US/docs/Web/API/HTMLAnchorElement/password/) یا [username](../../../../../../../en-US/docs/Web/API/HTMLAnchorElement/username/)). **این مقدار ناامن است**، زیرا originها و مسیرها را از منابع محافظت‌شده با TLS به منشأهای ناامن نشت می‌دهد.

> **نکته:**\
> مقدار رشتهٔ خالی (`""`) هم مقدار پیش‌فرض است و هم مقدار بازگشتی (fallback) در صورتی که `referrerpolicy` پشتیبانی نشود. اگر `referrerpolicy` به‌طور صریح روی عنصر `<script>` تعیین نشده باشد، از یک خط‌مشی ارجاع‌دهنده (referrer policy) سطح بالاتر — مثلاً خط‌مشی تنظیم‌شده روی کل سند یا دامنه — پیروی می‌کند. اگر خط‌مشی سطح بالاتری در دسترس نباشد، رشتهٔ خالی معادل `strict-origin-when-cross-origin` در نظر گرفته می‌شود.

* `src`
  * : این صفت (attribute) URI یک اسکریپت خارجی را مشخص می‌کند. می‌توان از آن به‌جای درج مستقیم اسکریپت درون سند استفاده کرد.
* [`type`](../../../../../../../en-US/docs/Web/HTML/Reference/Elements/script/type/)
  * : این صفت نوع اسکریپت درون عنصر را نشان می‌دهد. مقدار آن یکی از موارد زیر است:
    * **صفت تنظیم نشده (پیش‌فرض)، رشتهٔ خالی، یا یک MIME type از نوع JavaScript**
      * : نشان می‌دهد که اسکریپت یک «اسکریپت کلاسیک» (classic script) حاوی کد JavaScript است. توصیه می‌شود اگر اسکریپت به کد JavaScript اشاره دارد، این صفت را حذف کنید و به جای آن یک MIME type مشخص نکنید. MIME typeهای JavaScript در [فهرست انواع رسانهٔ IANA](../../../../../../../en-US/docs/Web/HTTP/Guides/MIME_types/#textjavascript) فهرست شده‌اند.
    * [`importmap`](../../../../../../../en-US/docs/Web/HTML/Reference/Elements/script/type/importmap/)
      * : این مقدار نشان می‌دهد که محتوای عنصر حاوی یک import map است. import map یک شیء JSON است که توسعه‌دهندگان می‌توانند از آن برای کنترل نحوهٔ حل کردن (resolve) مشخص‌کننده‌های ماژول (module specifiers) هنگام وارد کردن [ماژول‌های JavaScript](../../../../../../../en-US/docs/Web/JavaScript/Guide/Modules/#importing_modules_using_import_maps) استفاده کنند.
    * `module`
      * : این مقدار باعث می‌شود کد به‌عنوان یک ماژول JavaScript پردازش شود. پردازش محتوای اسکریپت به تأخیر می‌افتد (deferred). صفت‌های `charset` و `defer` تأثیری ندارند. برای اطلاعات بیشتر دربارهٔ استفاده از `module`، راهنمای [ماژول‌های JavaScript](../../../../../../../en-US/docs/Web/JavaScript/Guide/Modules/) ما را ببینید. برخلاف اسکریپت‌های کلاسیک، اسکریپت‌های ماژول برای دریافت cross-origin نیاز به استفاده از پروتکل CORS دارند.
    * [`speculationrules`](../../../../../../../en-US/docs/Web/HTML/Reference/Elements/script/type/speculationrules/) \{{experimental\_inline\}}
      * : این مقدار نشان می‌دهد که محتوای عنصر حاوی قوانین حدس (speculation rules) است. قوانین حدس به‌صورت یک شیء JSON هستند که مشخص می‌کنند کدام منابع باید توسط مرورگر پیش‌واکشی (prefetch) یا پیش‌رندر (prerender) شوند. این بخشی از \{{domxref("Speculation Rules API", "", "", "nocode")\}} است.
    * **هر مقدار دیگر**
      * : محتوای درون‌ساخته (embedded content) به‌عنوان یک بلوک داده در نظر گرفته می‌شود و توسط مرورگر پردازش نخواهد شد. توسعه‌دهندگان باید از یک MIME type معتبر که از نوع JavaScript نیست برای نشان دادن بلوک داده استفاده کنند. تمام صفت‌های دیگر نادیده گرفته می‌شوند، از جمله صفت `src`.

#### صفت‌های منسوخ (Deprecated)

* `charset` \{{Deprecated\_inline\}}
  * : اگر وجود داشته باشد، مقدار آن باید با `utf-8` مطابقت داشته باشد (به‌صورت case-insensitive در \{{Glossary("ASCII")\}}). نیازی به مشخص کردن صفت `charset` نیست، زیرا اسناد باید از UTF-8 استفاده کنند و عنصر `script` رمزگذاری کاراکتر خود را از سند به ارث می‌برد.
* `language` \{{Deprecated\_inline\}} \{{Non-standard\_Inline\}}
  * : مانند صفت `type`، این صفت زبان اسکریپت‌نویسی مورد استفاده را مشخص می‌کند. اما برخلاف `type`، مقادیر ممکن برای این صفت هرگز استانداردسازی نشده‌اند. بهتر است به جای آن از صفت `type` استفاده شود.

### نکات

اسکریپت‌هایی که صفت‌های [`async`](index.md#async)، [`defer`](index.md#defer) یا `type="module"` ندارند، و همچنین اسکریپت‌های درون‌ساخته (inline) که فاقد `type="module"` هستند، بلافاصله پس از دریافت و اجرا می‌شوند پیش از آنکه مرورگر به تجزیهٔ (parsing) صفحه ادامه دهد.

اسکریپت باید با MIME type از نوع `text/javascript` سرو شود؛ اما مرورگرها سختگیر نیستند و تنها زمانی آن را مسدود میکنند که با یکی از انواع تصویر (`image/*`)، ویدیو (`video/*`)، صدا (`audio/*`) یا `text/csv` سرو شود.\
اگر اسکریپت مسدود شود، رویداد `error` به عنصر ارسال میشود؛ در غیر این صورت رویداد `load` ارسال میشود.

### مثال‌ها

#### استفادهٔ پایه

این مثال نحوهٔ ایمپورت کردن یک اسکریپت خارجی را با استفاده از عنصر `<script>` نشان می‌دهد:

```html
<script src="javascript.js"></script>
```

مثال زیر نحوه قرار دادن یک اسکریپت داخلی (inline) را درون عنصر `<script>` نشان می‌دهد:

```html
<script>
  alert("Hello World!");
</script>
```

#### async و defer

اسکریپت‌هایی که با ویژگی `async` بارگذاری می‌شوند، بدون ایجاد وقفه در رندر صفحه دانلود می‌شوند. اما وقتی دانلود تمام شد، اجرای اسکریپت انجام می‌شود و در این مدت رندر صفحه مسدود می‌ماند. یعنی تا پایان اجرای اسکریپت، بقیه محتوای صفحه پردازش و به کاربر نمایش داده نمی‌شود.

هیچ تضمینی وجود ندارد که اسکریپت‌ها به ترتیب خاصی اجرا شوند. بهتر است از `async` زمانی استفاده کنید که اسکریپت‌های صفحه مستقل از یکدیگر اجرا می‌شوند و به اسکریپت دیگری در صفحه وابسته نیستند.

اسکریپت‌هایی که با ویژگی `defer` بارگذاری می‌شوند، به ترتیب ظاهر شدن در صفحه بارگذاری می‌شوند. آن‌ها تا زمانی که تمام محتوای صفحه بارگذاری نشده اجرا نمی‌شوند. این ویژگی زمانی مفید است که اسکریپت‌های شما به DOM حاضر و آماده وابسته باشند (مثلاً یک یا چند عنصر صفحه را تغییر می‌دهند).

_این تصویر از_ [_مشخصات HTML_](https://html.spec.whatwg.org/images/asyncdefer.svg) _گرفته شده و با برش و کاهش ابعاد، تحت شرایط مجوز_ [_CC BY 4.0_](https://creativecommons.org/licenses/by/4.0/) _استفاده شده است._

برای مثال، اگر عناصر `<script>` زیر را داشته باشیم:

```html
<script async src="js/vendor/jquery.js"></script>
<script async src="js/script2.js"></script>
<script async src="js/script3.js"></script>
```

نمی‌توانید به ترتیب بارگذاری اسکریپت‌ها اطمینان کنید. ممکن است `jquery.js` قبل یا بعد از `script2.js` و `script3.js` بارگذاری شود. در این صورت، هر تابعی در آن اسکریپت‌ها که به `jquery` وابسته باشد خطا ایجاد می‌کند؛ زیرا در زمان اجرای اسکریپت، `jquery` تعریف نشده است.

از `async` باید زمانی استفاده کنید که گروهی از اسکریپت‌های پس‌زمینه را برای بارگذاری دارید و می‌خواهید هرچه سریع‌تر در دسترس قرار بگیرند. مثلاً فرض کنید فایل‌های داده بازی دارید که هنگام شروع بازی به آن‌ها نیاز می‌شود، اما فعلاً فقط می‌خواهید بخش معرفی، عنوان‌ها و لابی بازی را نشان دهید و نمی‌خواهید این بخش‌ها توسط بارگذاری اسکریپت مسدود شوند.

اسکریپت‌هایی که با ویژگی `defer` بارگذاری می‌شوند (به مثال زیر مراجعه کنید)، به ترتیب ظاهر شدن در صفحه اجرا می‌شوند و به محض دانلود اسکریپت و محتوا اجرا می‌شوند:

```html
<script defer src="js/vendor/jquery.js"></script>
<script defer src="js/script2.js"></script>
<script defer src="js/script3.js"></script>
```

در مثال دوم، می‌توانیم مطمئن باشیم که `jquery.js` قبل از `script2.js` و `script3.js` و همچنین `script2.js` قبل از `script3.js` بارگذاری می‌شود. این اسکریپت‌ها تا زمانی که تمام محتوای صفحه بارگذاری نشده اجرا نمی‌شوند. این ویژگی زمانی مفید است که اسکریپت‌های شما به DOM آماده وابسته باشند (مثلاً یک یا چند عنصر صفحه را تغییر می‌دهند).

برای جمع‌بندی:

* صفت‌های `async` و `defer` هر دو به مرورگر می‌گویند که اسکریپت‌ها را در یک thread جداگانه دانلود کند، در حالی که بقیهٔ صفحه (DOM و...) در حال دانلود است؛ بنابراین بارگذاری صفحه در فرایند دریافت فایل مسدود نمی‌شود.
* اسکریپت‌هایی که صفت `async` دارند، به محض اتمام دانلود اجرا می‌شوند. این کار باعث مسدود شدن صفحه می‌شود و ترتیب اجرای مشخصی را تضمین نمی‌کند.
* اسکریپت‌هایی که صفت `defer` دارند، به ترتیبی که در صفحه قرار گرفته‌اند بارگذاری می‌شوند و فقط بعد از اتمام بارگذاری همه‌چیز اجرا می‌شوند.
* اگر اسکریپت‌های شما باید فوراً اجرا شوند و وابستگی ندارند، از `async` استفاده کنید.
* اگر اسکریپت‌های شما باید منتظر پارس شدن بمانند و به اسکریپت‌های دیگر و/یا DOM وابسته هستند، آن‌ها را با `defer` بارگذاری کنید و عناصر `<script>` مربوطه را به ترتیبی که می‌خواهید مرورگر اجرا کند در صفحه قرار دهید.

#### Module fallback

مرورگرهایی که از مقدار `module` برای صفت [`type`](../../../../../../../en-US/docs/Web/HTML/Reference/Elements/script/type/) پشتیبانی می‌کنند، هر اسکریپتی که صفت `nomodule` داشته باشد را نادیده می‌گیرند. این به شما امکان می‌دهد از اسکریپت‌های ماژول استفاده کنید و در عین حال اسکریپت‌های fallback (بازگشتی) با نشان `nomodule` برای مرورگرهایی که پشتیبانی نمی‌کنند فراهم کنید.

```html
<script type="module" src="main.js"></script>
<script nomodule src="fallback.js"></script>
```

#### وارد کردن ماژول‌ها با importmap

هنگامی که ماژول‌ها را در اسکریپت‌ها وارد می‌کنید، اگر از قابلیت [`type=importmap`](../../../../../../../en-US/docs/Web/HTML/Reference/Elements/script/type/importmap/) استفاده نکنید، هر ماژول باید با یک مشخص‌کنندهٔ ماژول (module specifier) وارد شود که یا یک URL مطلق است یا یک URL نسبی. در مثال زیر، اولین مشخص‌کنندهٔ ماژول یک URL مطلق است، در حالی که دومی (`"./shapes/square.js"`) نسبت به URL پایهٔ سند تفسیر می‌شود.

```js
import { name as circleName } from "https://example.com/shapes/circle.js";
import { name as squareName, draw } from "./shapes/square.js";
```

یک نقشهٔ import به شما امکان می‌دهد یک نگاشت (mapping) ارائه دهید که در صورت تطابق، می‌تواند متن موجود در مشخص‌کنندهٔ ماژول را جایگزین کند. نقشهٔ import زیر کلیدهای `circle` و `square` را تعریف می‌کند که می‌توانند به عنوان نام مستعار برای مشخص‌کننده‌های ماژول نشان‌داده‌شده در بالا استفاده شوند.

```html
<script type="importmap">
  {
    "imports": {
      "circle": "https://example.com/shapes/circle.js",
      "square": "./shapes/square.js"
    }
  }
</script>
```

این به ما اجازه می‌دهد ماژول‌ها را با استفاده از نام‌هایی که در مشخص‌کنندهٔ ماژول آمده‌اند وارد کنیم (به جای URLهای مطلق یا نسبی).

```js
import { name as circleName } from "circle";
import { name as squareName, draw } from "square";
```

برای مثال‌های بیشتر دربارهٔ کارهایی که می‌توانید با import map انجام دهید، بخش [Importing modules using import maps](../../../../../../../en-US/docs/Web/JavaScript/Guide/Modules/#importing_modules_using_import_maps) را در راهنمای ماژول‌های JavaScript ببینید.

#### تعبیهٔ داده در HTML

شما همچنین می‌توانید از عنصر `<script>` برای تعبیهٔ داده در HTML با رندر سمت سرور استفاده کنید، به شرطی که یک MIME type معتبر غیر-JavaScript را در صفت `type` مشخص کنید.

```html
<!-- تولید شده توسط سرور -->
<script id="data" type="application/json">
  {
    "userId": 1234,
    "userName": "Maria Cruz",
    "memberSince": "2000-01-01T00:00:00.000Z"
  }
</script>

<!-- استاتیک -->
<script>
  const userInfo = JSON.parse(document.getElementById("data").text);
  console.log("User information: %o", userInfo);
</script>
```

#### مسدود کردن رندر تا زمان دریافت و اجرای اسکریپت

می‌توانید توکن `render` را در داخل صفت `blocking` قرار دهید؛ رندر صفحه تا زمانی که اسکریپت دریافت و اجرا شود مسدود خواهد ماند. در مثال زیر، رندر را روی یک اسکریپت async مسدود می‌کنیم، به طوری که اسکریپت پارسینگ را مسدود نمی‌کند اما تضمین می‌شود که قبل از شروع رندر ارزیابی شده باشد.

```html
<script blocking="render" async src="async-script.js"></script>
```

| ویژگی                                                                                          | توضیحات                                                                                                                                                                                                                                                                                                                                      |
| ---------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [دسته‌بندی محتوا](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories) | [Metadata content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#metadata_content)، [Flow content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، [Phrasing content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) |
| محتوای مجاز                                                                                    | اسکریپت پویا مانند `text/javascript`                                                                                                                                                                                                                                                                                                         |
| عدم ذکر برچسب                                                                                  | هیچ‌کدام؛ برچسب شروع و پایان هر دو اجباری هستند                                                                                                                                                                                                                                                                                              |
| والدین مجاز                                                                                    | هر عنصری که محتوای متادیتا (metadata content) یا محتوای عبارتی (phrasing content) را بپذیرد                                                                                                                                                                                                                                                  |
| نقش ARIA ضمنی                                                                                  | [نقش متناظری ندارد](https://w3c.github.io/html-aria/#dfn-no-corresponding-role)                                                                                                                                                                                                                                                              |
| نقش‌های ARIA مجاز                                                                              | هیچ `role` مجاز نیست                                                                                                                                                                                                                                                                                                                         |
| رابط DOM                                                                                       | `HTMLScriptElement`                                                                                                                                                                                                                                                                                                                          |

### مشخصات

### سازگاری با مرورگرها

### همچنین ببینید

* `document.currentScript`
* [مقاله‌ی Flavio Copes درباره‌ی بارگذاری کارآمد JavaScript و توضیح تفاوت‌های بین `async` و `defer`](https://thevalleyofcode.com/javascript-async-defer/)
* [راهنمای ماژول‌های JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules)
