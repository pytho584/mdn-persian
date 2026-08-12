---
title: <a> HTML anchor element
source: https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/a
translated_by: n8n + AI
---

# \<a> HTML anchor element

الان که این متن را می‌خوانی، یعنی داری با عنصر `<a>` سروکار داری. این عنصر HTML که به آن anchor (لنگر) هم می‌گویند، با استفاده از صفت `href` یک لینک (hypertext link) به مقصدهای مختلف می‌سازد: صفحات وب، فایل‌ها، آدرس ایمیل، جای مشخصی در همان صفحه، یا هر چیزی که یک URL بتواند به آن اشاره کند.

محتوایی که داخل هر `<a>` می‌نویسید باید نشان بدهد که لینک به کجا می‌رود. اگر صفت `href` وجود داشته باشد، وقتی روی عنصر `<a>` فوکوس دارید و دکمه Enter را می‌زنید، لینک فعال می‌شود.

```html
<p>می‌توانید با مایکل از این راه‌ها تماس بگیرید:</p>

<ul>
  <li><a href="https://example.com">وب‌سایت</a></li>
  <li><a href="mailto:m.bluth@example.com">ایمیل</a></li>
  <li><a href="tel:+123456789">تلفن</a></li>
</ul>
```

```css
li {
  margin-bottom: 0.5rem;
}
```

### صفت‌ها (Attributes)

این عنصر شامل تمام [صفت‌های سراسری (global attributes)](../../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/) است.

* `attributionsrc` \{{deprecated\_inline\}} \{{non-standard\_inline\}}
  *   : مشخص می‌کند که مرورگر باید هدر `{{httpheader("Attribution-Reporting-Eligible")}}` را ارسال کند. در سمت سرور، این هدر برای فعال‌سازی ارسال هدر `{{httpheader("Attribution-Reporting-Register-Source")}}` در پاسخ استفاده می‌شود و یک منبع انتساب (attribution source) مبتنی بر ناوبری ثبت می‌کند. (برای اطلاعات بیشتر به [Attribution Reporting API](../../../../../../../en-US/docs/Web/API/Attribution_Reporting_API/) مراجعه کنید.)

      وقتی کاربر روی لینک کلیک می‌کند، مرورگر داده‌های مربوط به این منبع انتساب را (که در هدر پاسخ `{{httpheader("Attribution-Reporting-Register-Source")}}` مشخص شده) ذخیره می‌کند. دو حالت برای این صفت وجود دارد:

      * حالت Boolean: فقط نام `attributionsrc` را بنویسید. یعنی هدر `{{httpheader("Attribution-Reporting-Eligible")}}` به همان سروری فرستاده می‌شود که صفت `href` به آن اشاره می‌کند. این برای وقتی مناسب است که ثبت منبع انتساب را در همان سرور انجام می‌دهید.
      *   مقدار شامل یک یا چند URL: برای مثال:

          ```html
          attributionsrc="https://a.example/register-source
          https://b.example/register-source"
          ```

          این حالت مفید است وقتی منبع درخواست‌شده روی سروری نیست که شما کنترل می‌کنید، یا فقط می‌خواهید ثبت منبع انتساب را روی سرور دیگری انجام دهید. در این حالت، یک یا چند URL را به عنوان مقدار `attributionsrc` مشخص می‌کنید. وقتی درخواست منبع انجام می‌شود، هدر `{{httpheader("Attribution-Reporting-Eligible")}}` علاوه بر سرور مبدأ، به URL(های) مشخص‌شده در `attributionsrc` هم فرستاده می‌شود. آن URLها می‌توانند با هدر `{{httpheader("Attribution-Reporting-Register-Source")}}` پاسخ دهند و ثبت را کامل کنند.

          > \[!NOTE] مشخص کردن چندین URL یعنی می‌توان چند منبع انتساب را روی یک ویژگی ثبت کرد. مثلاً ممکن است چند کمپین مختلف داشته باشید که می‌خواهید موفقیت هرکدام را اندازه بگیرید و گزارش‌های متفاوتی روی داده‌های مختلف تولید کنید.

      عناصر `<a>` فقط می‌توانند به عنوان منبع (source) استفاده شوند، نه به عنوان trigger.
* `download`
  * : باعث می‌شود مرورگر با URL لینک‌شده مثل یک فایل دانلودی رفتار کند. می‌تواند بدون مقدار یا با یک `filename` استفاده شود:
    * بدون مقدار: مرورگر یک نام و پسوند فایل پیشنهاد می‌دهد که از منابع مختلف می‌آید:
      * هدر HTTP `{{HTTPHeader("Content-Disposition")}}`
      * آخرین بخش مسیر URL (path) در [()](../../../../../../../en-US/docs/Web/API/URL/pathname/)
      * نوع رسانه (media type) (از هدر `{{HTTPHeader("Content-Type")}}`، شروع یک [`data:` URL](../../../../../../../en-US/docs/Web/URI/Reference/Schemes/data/)، یا `{{domxref("Blob.type")}}` برای یک [`blob:` URL](../../../../../../../en-US/docs/Web/URI/Reference/Schemes/blob/))
*   `filename`: تعریف یک مقدار برای آن، آن مقدار را به‌عنوان نام فایل پیشنهاد می‌دهد. کاراکترهای `/` و `\` به زیرخط (`_`) تبدیل می‌شوند. سیستم‌های فایل ممکن است کاراکترهای دیگری را در نام فایل ممنوع کنند، بنابراین مرورگرها در صورت لزوم نام پیشنهادی را تنظیم می‌کنند.

    > \[!NOTE]
    >
    > * `download` فقط برای [URLهای هم‌ریشه](../../../../../../../en-US/docs/Web/Security/Defenses/Same-origin_policy/) یا طرح‌های `blob:` و `data:` کار می‌کند.
    > * نحوه برخورد مرورگرها با دانلودها بسته به مرورگر، تنظیمات کاربر و عوامل دیگر متفاوت است. ممکن است قبل از شروع دانلود از کاربر تأیید گرفته شود، یا فایل به‌طور خودکار ذخیره شود، یا در یک برنامه خارجی یا خود مرورگر باز شود.
    > * اگر هدر `Content-Disposition` اطلاعاتی متفاوت از ویژگی `download` داشته باشد، رفتار نهایی ممکن است متفاوت باشد:
    >   * اگر هدر یک `filename` مشخص کند، آن نام بر نام فایل مشخص‌شده در ویژگی `download` اولویت دارد.
    >   * اگر هدر disposition را `inline` تعیین کند، کروم و فایرفاکس به ویژگی `download` اولویت داده و آن را به‌عنوان یک دانلود در نظر می‌گیرند. نسخه‌های قدیمی فایرفاکس (قبل از ۸۲) به هدر اولویت می‌دادند و محتوا را به‌صورت درون‌خطی نمایش می‌دادند.
* `href`
  *   : نشانی اینترنتی (URL) که لینک به آن اشاره می‌کند. لینک‌ها محدود به URLهای مبتنی بر HTTP نیستند – می‌توانند از هر طرح URL که مرورگرها پشتیبانی می‌کنند استفاده کنند:

      * شماره تلفن با URLهای `tel:`
      * آدرس ایمیل با URLهای `mailto:`
      * پیامک با URLهای `sms:`
      * کد اجرایی با [URLهای `javascript:`](../../../../../../../en-US/docs/Web/URI/Reference/Schemes/javascript/)
      * اگرچه مرورگرهای وب ممکن است از طرح‌های URL دیگر پشتیبانی نکنند، وب‌سایت‌ها می‌توانند با [`registerProtocolHandler()`](../../../../../../../en-US/docs/Web/API/Navigator/registerProtocolHandler/) این کار را انجام دهند.

      علاوه بر این، ویژگی‌های URL دیگری می‌توانند بخش‌های خاصی از منبع را مشخص کنند، از جمله:

      * بخش‌های یک صفحه با قطعات سند (document fragments)
      * بخش‌های متنی خاص با [قطعات متن](../../../../../../../en-US/docs/Web/URI/Reference/Fragment/Text_fragments/)
      * قطعات فایل‌های رسانه‌ای با قطعات رسانه
* `hreflang`
  * : به زبان انسانیِ URL مقصد اشاره می‌کند. عملکرد داخلی ندارد. مقادیر مجاز همان مقادیر [attribute سراسری `lang`](../../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/lang/) هستند.
* `interestfor`
  * : عنصر `<a>` را به‌عنوان **interest invoker** تعریف می‌کند. مقدار آن `id` عنصر هدف است. وقتی روی عنصر invoker علاقه نشان داده شود یا از بین برود (مثلاً با هاور کردن/برداشتن هاور یا فوکوس/از فوکوس خارج شدن)، عنصر هدف به نحوی تحت تأثیر قرار می‌گیرد (معمولاً نمایش یا مخفی می‌شود). برای جزئیات و مثال‌های بیشتر، [استفاده از interest invokerها](../../../../../../../en-US/docs/Web/API/Popover_API/Using_interest_invokers/) را ببینید.
* `ping`
  * : فهرستی از URLها که با فاصله جدا شده‌اند. وقتی لینک دنبال شود، مرورگر درخواست‌های `POST` با بدنهٔ `PING` به آن URLها ارسال می‌کند. معمولاً برای ردیابی استفاده می‌شود.
* `referrerpolicy`
  * : مشخص می‌کند هنگام دنبال کردن لینک، چه مقدار از [referrer](../../../../../../../en-US/docs/Web/HTTP/Reference/Headers/Referer/) ارسال شود.
    * `no-referrer`: هدر `Referer` ارسال نخواهد شد.
    * `no-referrer-when-downgrade`: هدر `Referer` به originهایی که TLS (HTTPS) ندارند ارسال نمی‌شود.
    * `origin`: referrer ارسالی به origin صفحهٔ ارجاع‌دهنده محدود می‌شود: یعنی [scheme](../../../../../../../en-US/docs/Learn_web_development/Howto/Web_mechanics/What_is_a_URL/)، host و port آن.
    * `origin-when-cross-origin`: referrer ارسالی به دیگر originها به scheme، host و port محدود می‌شود. ناوبری‌ها (navigations) روی همان origin همچنان مسیر (path) را شامل می‌شوند.
    * `same-origin`: برای same origin یک referrer ارسال می‌شود، اما درخواست‌های cross-origin هیچ اطلاعات referrer ندارند.
    * `strict-origin`: فقط زمانی که سطح امنیت پروتکل یکسان باشد (HTTPS→HTTPS)، origin سند را به عنوان referrer ارسال کن، اما به مقصد کم‌امنیت‌تر (HTTPS→HTTP) ارسال نکن.
    * `strict-origin-when-cross-origin` (پیش‌فرض): برای درخواست same-origin، URL کامل ارسال کن؛ وقتی سطح امنیت پروتکل یکسان است (HTTPS→HTTPS) فقط origin ارسال کن؛ و به مقصد کم‌امنیت‌تر (HTTPS→HTTP) هیچ هدری ارسال نکن.
    * `unsafe-url`: referrer شامل origin و مسیر (path) خواهد بود (اما [fragment](../../../../../../../en-US/docs/Web/API/HTMLAnchorElement/hash/)، [password](../../../../../../../en-US/docs/Web/API/HTMLAnchorElement/password/) یا [username](../../../../../../../en-US/docs/Web/API/HTMLAnchorElement/username/) را شامل نمی‌شود). **این مقدار ناامن است**، چون origin و path را از منابع محافظت‌شده با TLS به originهای ناامن درز می‌دهد.
* [`rel`](../../../../../../../en-US/docs/Web/HTML/Reference/Attributes/rel/)
  * : رابطهٔ URL مقصد را به صورت نوع‌های لینک (link types) که با فاصله جدا شده‌اند مشخص می‌کند.
* `target`
  * : تعیین می‌کند URL مقصد کجا نمایش داده شود؛ به عنوان نامی برای یک _browsing context_ (تب، پنجره یا `<iframe>`). کلمات کلیدی زیر معنای خاصی برای محل بارگذاری URL دارند:
    * `_self`: همان browsing context فعلی. (پیش‌فرض)
    * `_blank`: معمولاً یک تب جدید، اما کاربران می‌توانند مرورگر را طوری پیکربندی کنند که به جای آن یک پنجرهٔ جدید باز کند.
    * `_parent`: browsing context والدِ context فعلی. اگر والدی نباشد، مانند `_self` عمل می‌کند.
    * `_top`: بالاترین browsing context. به بیان دقیق‌تر، یعنی «بالاترین» context که جدِ context فعلی است. اگر جدی وجود نداشته باشد، مانند `_self` عمل می‌کند.
    * `_unfencedTop`: به [fenced frames](../../../../../../../en-US/docs/Web/API/Fenced_frame_API/) جاسازی‌شده اجازه می‌دهد تا frame سطح بالا را ناوبری کنند (یعنی برخلاف سایر مقصدهای رزروشده، از ریشهٔ fenced frame عبور کنند). توجه داشته باشید که اگر این مقدار خارج از context فنس‌شده استفاده شود، ناوبری همچنان موفق خواهد بود، اما مانند یک کلمهٔ کلیدی رزروشده رفتار نخواهد کرد.

> \[!NOTE] تنظیم `target="_blank"` روی عناصر `<a>` به‌طور ضمنی همان رفتار `rel` را دارد که تنظیم [`rel="noopener"`](../../../../../../../en-US/docs/Web/HTML/Reference/Attributes/rel/noopener/) ارائه می‌دهد؛ یعنی `window.opener` را تنظیم نمی‌کند.

* `type`
  * : به فرمت URL مقصد با استفاده از \{{Glossary("MIME type")\}} اشاره می‌کند. عملکرد داخلی ندارد.

#### ویژگی‌های منسوخ‌شده (Deprecated attributes)

* `charset` \{{Deprecated\_Inline\}}
  *   : به \{{Glossary("character encoding")\}} (رمزگذاری کاراکتر) URL مقصد اشاره می‌کرد.

      > **نکته:** این ویژگی منسوخ شده و **نویسندگان نباید از آن استفاده کنند**. به جای آن از هدر HTTP \{{HTTPHeader("Content-Type")\}} در URL مقصد استفاده کنید.
* `coords` \{{Deprecated\_Inline\}}
  * : همراه با [ویژگی `shape`](index.md#shape) استفاده می‌شد. یک فهرست مختصات که با کاما جدا شده‌اند.
* `name` \{{Deprecated\_Inline\}}
  *   : برای تعریف یک موقعیت هدف در یک صفحه لازم بود. در HTML 4.01، `id` و `name` هر دو می‌توانستند روی `<a>` استفاده شوند، به شرطی که مقدار یکسانی داشتند.

      > **نکته:** به جای آن از ویژگی سراسری [`id`](../../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/id/) استفاده کنید.
* `rev` \{{Deprecated\_Inline\}}
  * : یک لینک معکوس را مشخص می‌کرد؛ برعکس [ویژگی `rel`](index.md#rel). به دلیل ایجاد سردرگمی زیاد منسوخ شد.
* `shape` \{{Deprecated\_Inline\}}
  *   : شکل ناحیه‌ی هایپرلینک در یک نقشه تصویری (image map).

      > **نکته:** برای نقشه‌های تصویری از عنصر \{{HTMLElement("area")\}} استفاده کنید.

### دسترسی‌پذیری (Accessibility)

#### متن لینک قوی (Strong link text)

**محتوای داخل یک لینک باید مشخص کند که لینک به کجا می‌رود**، حتی خارج از زمینه.

**متن لینک ضعیف و غیرقابل دسترس**

یک اشتباه رایج این است که فقط کلمات "اینجا کلیک کنید" یا "اینجا" را لینک کنیم:

```html
<p>برای آشنایی بیشتر با محصولات ما <a href="/products">اینجا</a> کلیک کنید.</p>
```

**نتیجه**

\{{EmbedLiveSample('Inaccessible, weak link text', '100%', '50')\}}

**متن لینک قوی و دسترس‌پذیر**

خوشبختانه این مشکل به راحتی قابل حل است و حتی از نسخهٔ غیرقابل دسترس کوتاه‌تر است!

```html
<p>بیشتر دربارهٔ <a href="/products">محصولات ما</a> بدانید.</p>
```

**نتیجه**

\{{EmbedLiveSample('Accessible, strong link text', '100%', '50')\}}

نرم‌افزارهای کمکی میانبرهایی برای فهرست کردن همهٔ لینک‌های یک صفحه دارند. با این حال، متن لینک قوی به نفع همهٔ کاربران است – میانبر «فهرست همه لینک‌ها» تقلیدی از نحوهٔ مرور سریع صفحات توسط کاربران بینا است.

#### رویدادهای onclick

از عناصر لنگر (anchor) اغلب به عنوان دکمه‌های تقلبی استفاده می‌شود، با تنظیم `href` روی `#` یا [`javascript:void(0)`](../../../../../../../en-US/docs/Web/URI/Reference/Schemes/javascript/) برای جلوگیری از بارگذاری مجدد صفحه، و سپس گوش دادن به رویدادهای `click`.

این مقادیر جعلی `href` باعث رفتار غیرمنتظره هنگام کپی/کشیدن لینک‌ها، باز کردن لینک در تب/پنجره جدید، بوکمارک کردن، یا وقتی جاوااسکریپت در حال بارگذاری است، خطا دارد یا غیرفعال است، می‌شوند. همچنین معانی نادرستی را به فناوری‌های کمکی مانند screen reader منتقل می‌کنند.

به جای آن از یک \{{HTMLElement("button")\}} استفاده کنید. به طور کلی، **شما فقط باید از یک هایپرلینک برای ناوبری به یک URL واقعی استفاده کنید**.

#### لینک‌های خارجی و لینک به منابع غیر HTML

لینک‌هایی که از طریق `target="_blank"` در یک تب/پنجره جدید باز می‌شوند، یا لینک‌هایی که به یک فایل دانلودی اشاره دارند، باید نشان دهند که پس از کلیک چه اتفاقی می‌افتد.

افرادی که مشکل بینایی دارند، با فناوری screen reader کار می‌کنند، یا مشکلات شناختی دارند، ممکن است با باز شدن ناگهانی یک تب یا پنجره جدید سردرگم شوند. نرم‌افزارهای قدیمی screen reader ممکن است اصلاً این رفتار را اعلام نکنند.

**لینکی که در یک تب/پنجره جدید باز می‌شود**

```html
<a target="_blank" href="https://www.wikipedia.org">
  ویکی‌پدیا (در تب جدید باز می‌شود)
</a>
```

**نتیجه**

\{{EmbedLiveSample('Link that opens a new tab/window')\}}

**لینک به یک منبع غیر HTML**

اگر از یک آیکون برای نشان دادن رفتار لینک استفاده می‌شود، مطمئن شوید که یک [`alt` attribute](../../../../../../../en-US/docs/Web/HTML/Reference/Elements/img/#alt) (ویژگی alt) برای توصیف هدف آن وجود دارد. در صورت نبود آیکون، محتوای ویژگی `alt` همچنان رفتار لینک را منتقل خواهد کرد.

```html
<p>
  <a href="https://www.wikipedia.org/" target="_blank">
    Wikipedia
    <img src="new-tab.svg" width="14" alt="(Opens in new tab)" />
  </a>
  <br />
  <a href="2017-annual-report.ppt">
    2017 annual report
    <img src="powerpoint.svg" width="14" alt="(PowerPoint file)" />
  </a>
</p>
<p>
  <a href="https://www.wikipedia.org/" target="_blank">
    Wikipedia
    <img src="missing-icon.svg" width="14" alt="(Opens in new tab)" />
  </a>
  <br />
  <a href="2017-annual-report.ppt">
    2017 annual report
    <img src="missing-icon.svg" width="14" alt="(PowerPoint file)" />
  </a>
</p>
```

**نتیجه**

* [WebAIM: Links and Hypertext - Hypertext Links](https://webaim.org/techniques/hypertext/hypertext_links)
* [MDN / Understanding WCAG, Guideline 3.2](../../../../../../../en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Understandable/#guideline_3.2_%E2%80%94_predictable_make_web_pages_appear_and_operate_in_predictable_ways)
* [G200: Opening new windows and tabs from a link only when necessary](https://www.w3.org/TR/WCAG20-TECHS/G200.html)
* [G201: Giving users advanced warning when opening a new window](https://www.w3.org/TR/WCAG20-TECHS/G201.html)

#### لینک‌های پرش

یک **لینک پرش (Skip link)** پیوندی است که در ابتدای محتوای عنصر body قرار می‌گیرد و به شروع محتوای اصلی صفحه اشاره می‌کند. معمولاً CSS این لینک را تا وقتی فوکس نگیرد، خارج از دید پنهان می‌کند.

```html
<body>
  <a href="#content" class="skip-link">Skip to main content</a>

  <header>…</header>

  <!-- The skip link jumps to here -->
  <main id="content"></main>
</body>
```

```css
.skip-link {
  position: absolute;
  top: -3em;
  background: white;
}
.skip-link:focus {
  top: 0;
}
```

**نتیجه**

لینک‌های پرش به کاربران صفحه‌کلید اجازه می‌دهند از محتوای تکراری در چندین صفحه، مثل ناوبری هدر، عبور کنند.

این لینک‌ها به‌ویژه برای افرادی مفیدند که با کمک فناوری‌های کمکی مانند کنترل سوییچی، فرمان صوتی، یا چوب دهانی/عصای سر حرکت می‌کنند؛ جایی که عبور از پیوندهای تکراری می‌تواند خسته‌کننده باشد.

* [WebAIM: "Skip Navigation" Links](https://webaim.org/techniques/skipnav/)
* [How-to: Use Skip Navigation links](https://www.a11yproject.com/posts/skip-nav-links/)
* [MDN / Understanding WCAG, Guideline 2.4 explanations](../../../../../../../en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Operable/#guideline_2.4_%E2%80%94_navigable_provide_ways_to_help_users_navigate_find_content_and_determine_where_they_are)
* [Understanding Success Criterion 2.4.1](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-skip.html)

#### اندازه و نزدیکی

**اندازه**

المان‌های تعاملی، مانند لینک‌ها، باید ناحیه‌ای به اندازه کافی بزرگ در اختیار بگذارند تا فعال کردنشان آسان باشد. این کار به طیف گسترده‌ای از افراد کمک می‌کند، از جمله افرادی که مشکلات کنترل حرکتی دارند و افرادی که از ورودی‌های دقیق مثل تاچ‌اسکرین استفاده می‌کنند. حداقل اندازه پیشنهادی ۴۴×۴۴ پیکسل CSS است.

لینک‌های صرفاً متنی در محتوای متنی از این الزام معاف هستند، اما همچنان بهتر است مطمئن شوید بخش کافی از متن لینک می‌شود تا به راحتی قابل فعال‌سازی باشد.

* [Understanding Success Criterion 2.5.5: Target Size](https://www.w3.org/WAI/WCAG21/Understanding/target-size.html)
* [Target Size and 2.5.5](https://adrianroselli.com/2019/06/target-size-and-2-5-5.html)
* [Quick test: Large touch targets](https://www.a11yproject.com/posts/large-touch-targets/)

**نزدیکی**

المان‌های تعاملی، مانند لینک‌ها، که از نظر بصری نزدیک به هم قرار دارند، باید با فاصله از هم جدا شوند. این فاصله‌گذاری به افرادی که مشکلات کنترل حرکتی دارند کمک می‌کند، زیرا در غیر این صورت ممکن است به طور تصادفی محتوای تعاملی اشتباهی را فعال کنند.

این فاصله را می‌توان با استفاده از ویژگی‌های CSS مثل `margin` ایجاد کرد.

* [Hand tremors and the giant-button-problem](https://axesslab.com/hand-tremors/)

### مثال‌ها

#### لینک به یک URL مطلق

**HTML**

```html
<a href="https://www.mozilla.com">Mozilla</a>
```

**نتیجه**

#### پیوند به URLهای نسبی

**HTML**

```html
<a href="//example.com">Scheme-relative URL</a>
<a href="/en-US/docs/Web/HTML">Origin-relative URL</a>
<a href="p">Directory-relative URL</a>
<a href="./p">Directory-relative URL</a>
<a href="../p">Parent-directory-relative URL</a>
```

```css
a {
  display: block;
  margin-bottom: 0.5em;
}
```

**نتیجه**

#### پیوند به یک element در همان صفحه

```html
<!-- <a> element links to the section below -->
<p><a href="#Section_further_down">Jump to the heading below</a></p>

<!-- Heading to link to -->
<h2 id="Section_further_down">Section further down</h2>
```

**نتیجه**

> \[!NOTE] می‌توانید از `href="#top"` یا fragment خالی (`href="#"`) برای پیوند به بالای صفحه‌ی جاری استفاده کنید؛ [طبق تعریف در مشخصات HTML](https://html.spec.whatwg.org/multipage/browsing-the-web.html#scroll-to-the-fragment-identifier).

#### پیوند به یک نشانی ایمیل

برای ساخت لینک‌هایی که برنامه‌ی ایمیل کاربر را باز می‌کنند تا پیام جدیدی ارسال کنند، از اسکیم `mailto:` استفاده کنید:

```html
<a href="mailto:nowhere@mozilla.org">Send email to nowhere</a>
```

**نتیجه**

برای جزئیات مربوط به URLهای `mailto:`، مانند افزودن موضوع (subject) یا بدنه (body)، به [لینک‌های ایمیل](../../../../../../../en-US/docs/Learn_web_development/Core/Structuring_content/Creating_links/#email_links) یا RFC 6068 مراجعه کنید.

#### پیوند به شماره تلفن

```html
<a href="tel:+49.157.0156">+49 157 0156</a>
<a href="tel:+1(800)555-0123">(800) 555-0123</a>
```

**نتیجه**

رفتار لینک `tel:` بسته به قابلیت‌های دستگاه متفاوت است:

* دستگاه‌های سلولی به‌صورت خودکار شماره را شماره‌گیری می‌کنند.
* بیشتر سیستم‌عامل‌ها برنامه‌هایی برای تماس دارند، مانند Skype یا FaceTime.
* وب‌سایت‌ها می‌توانند با `registerProtocolHandler` تماس برقرار کنند، مانند `web.skype.com`.
* رفتارهای دیگر شامل ذخیره‌ی شماره در مخاطبین یا ارسال شماره به دستگاه دیگر است.

برای آشنایی با نحو (syntax)، ویژگی‌های اضافی و جزئیات دیگر درباره‌ی اسکیم URL `tel:`، به RFC 3966 مراجعه کنید.

#### استفاده از download attribute برای ذخیره‌ی `<canvas>` به صورت PNG

برای ذخیره‌ی محتوای یک `<canvas>` به عنوان تصویر، می‌توانید لینکی بسازید که `href` آن، داده‌ی canvas به صورت URL از نوع `data:` (ساخته‌شده با JavaScript) باشد و `download` attribute نام فایل PNG دانلودی را مشخص کند:

**مثال برنامه‌ی نقاشی با لینک ذخیره**

**HTML**

```html
<p>
  Paint by holding down the mouse button and moving it.
  <a href="" download="my_painting.png">Download my painting</a>
</p>

<canvas width="300" height="300"></canvas>
```

**CSS**

```css
html {
  font-family: sans-serif;
}
canvas {
  background: white;
  border: 1px dashed;
}
a {
  display: inline-block;
  background: #6699cc;
  color: white;
  padding: 5px 10px;
}
```

**JavaScript**

```js
const canvas = document.querySelector("canvas");
const c = canvas.getContext("2d");
c.fillStyle = "hotpink";
let isDrawing;

function draw(x, y) {
  if (isDrawing) {
    c.beginPath();
    c.arc(x, y, 10, 0, Math.PI * 2);
    c.closePath();
    c.fill();
  }
}

canvas.addEventListener("mousemove", (event) =>
  draw(event.offsetX, event.offsetY),
);
canvas.addEventListener("mousedown", () => (isDrawing = true));
canvas.addEventListener("mouseup", () => (isDrawing = false));

document
  .querySelector("a")
  .addEventListener(
    "click",
    (event) => (event.target.href = canvas.toDataURL()),
  );
```

**نتیجه**

### امنیت و حریم خصوصی

المان‌های `<a>` می‌توانند پیامدهایی برای امنیت و حریم خصوصی کاربران داشته باشند. برای اطلاعات بیشتر به [هدر `Referer`: نگرانی‌های حریم خصوصی و امنیت](../../../../../../../en-US/docs/Web/Privacy/Guides/Referer_header:_privacy_and_security_concerns/) مراجعه کنید.

### خلاصه فنی

استفاده از `target="_blank"` بدون `rel="noreferrer"` و `rel="noopener"` باعث می‌شود وب‌سایت در معرض حملات سوءاستفاده از API `window.opener` قرار گیرد. البته توجه داشته باشید که در نسخه‌های جدیدتر مرورگرها، تنظیم `target="_blank"` به طور ضمنی همان محافظتی را فراهم می‌کند که `rel="noopener"` ارائه می‌دهد. برای جزئیات بیشتر به [browser compatibility](index.md#browser_compatibility) مراجعه کنید.

```markdown
<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">Content categories</a>
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a>,
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">phrasing content</a>,
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#interactive_content">interactive content</a>, palpable content.
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#transparent_content_model">Transparent</a>، به این استثنا که هیچ نواده‌ای نمی‌تواند
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#interactive_content">interactive content</a> یا یک
        <code>&lt;a&gt;</code> element باشد، و هیچ نواده‌ای نمی‌تواند یک
        <a href="/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex">tabindex</a> attribute تعیین‌شده داشته باشد.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچ؛ هم تگ شروع و هم تگ پایان اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        هر element که <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">flow content</a> را می‌پذیرد، اما نه
        <code>&lt;a&gt;</code> element های دیگر.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        هنگامی که <code>href</code> attribute وجود داشته باشد:
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/link_role"><code>link</code></a>، در غیر این صورت
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role"><code>generic</code></a>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>
        <p>هنگامی که <code>href</code> attribute وجود داشته باشد:</p>
        <ul>
          <li><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role"><code>button</code></a></li>
          <li><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role"><code>checkbox</code></a></li>
          <li><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role"><code>menuitem</code></a></li>
          <li><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role"><code>menuitemcheckbox</code></a></li>
          <li><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role"><code>menuitemradio</code></a></li>
          <li><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role"><code>option</code></a></li>
          <li><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radio_role"><code>radio</code></a></li>
          <li><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/switch_role"><code>switch</code></a></li>
          <li><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role"><code>tab</code></a></li>
          <li><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treeitem_role"><code>treeitem</code></a></li>
        </ul>
        <p>هنگامی که <code>href</code> attribute وجود نداشته باشد:</p>
        <ul>
          <li>هر نقشی</li>
        </ul>
      </td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td><a href="https://developer.mozilla.org/en-US/docs/Web/API/HTMLAnchorElement"><code>HTMLAnchorElement</code></a></td>
    </tr>
  </tbody>
</table>

## مشخصات

## سازگاری مرورگر

## همچنین ببینید
```

* `<link>` مشابه `<a>` است، اما برای ابرپیوندهای فراداده‌ای که برای کاربران نامرئی هستند.
* `:link` یک شبه‌کلاس CSS است که عناصر `<a>` دارای URL در ویژگی `href` را که کاربر هنوز از آن بازدید نکرده، مطابقت می‌دهد.
* `:visited` یک شبه‌کلاس CSS است که عناصر `<a>` دارای URL در ویژگی `href` را که کاربر قبلاً از آن بازدید کرده، مطابقت می‌دهد.
* `:any-link` یک شبه‌کلاس CSS است که عناصر `<a>` دارای ویژگی `href` را مطابقت می‌دهد.
* [Text fragments](../../../../../../../en-US/docs/Web/URI/Reference/Fragment/Text_fragments/) دستوراتی هستند که توسط user-agent به URLها اضافه می‌شوند و به نویسندگان محتوا امکان می‌دهند بدون نیاز به ID، به متن خاصی در یک صفحه لینک بدهند.
