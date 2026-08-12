---
title: <a> HTML anchor element
source: https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/a
translated_by: n8n + AI
---

# \<a> HTML anchor element

The **`<a>`** HTML element (یا عنصر «انکر» (anchor))، با `href`، یک پیوند (hyperlink) به صفحات وب، فایل‌ها، آدرس‌های ایمیل، مکان‌هایی در همان صفحه، یا هر چیزی که یک URL بتواند به آن اشاره کند، ایجاد می‌کند.

محتوای داخل هر `<a>` باید مقصد پیوند را نشان دهد. اگر صفت `href` وجود داشته باشد، فشردن کلید Enter هنگام فوکوس روی عنصر `<a>` آن را فعال می‌کند.

```html
<p>You can reach Michael at:</p>

<ul>
  <li><a href="https://example.com">Website</a></li>
  <li><a href="mailto:m.bluth@example.com">Email</a></li>
  <li><a href="tel:+123456789">Phone</a></li>
</ul>
```

```css
li {
  margin-bottom: 0.5rem;
}
```

### Attributes

این عنصر دارای صفات [global attributes](../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/) نیز هست.

* `attributionsrc` (deprecated) (non-standard)
  *   : مشخص می‌کند که می‌خواهید مرورگر هدر Attribution-Reporting-Eligible را ارسال کند. در سمت سرور از این برای تحریک ارسال هدر Attribution-Reporting-Register-Source در پاسخ، جهت ثبت یک navigation-based attribution source استفاده می‌شود.

      مرورگر داده‌های منبع مرتبط با navigation-based attribution source را (همان‌طور که در هدر پاسخ Attribution-Reporting-Register-Source ارائه شده) هنگامی که کاربر روی لینک کلیک می‌کند ذخیره می‌کند. برای جزئیات بیشتر به Attribution Reporting API مراجعه کنید.

      دو نسخه از این صفت وجود دارد که می‌توانید تنظیم کنید:

      * بولی، یعنی تنها نام `attributionsrc`. این مشخص می‌کند که می‌خواهید هدر Attribution-Reporting-Eligible به همان سروری که `href` به آن اشاره می‌کند ارسال شود. این زمانی مناسب است که ثبت منبع attribution را در همان سرور اداره می‌کنید.
      *   مقدار شامل یک یا چند URL، برای مثال:

          ```html
          attributionsrc="https://a.example/register-source
          https://b.example/register-source"
          ```

          این در مواردی مفید است که منبع درخواست روی سروری نباشد که شما کنترلش را دارید، یا می‌خواهید ثبت منبع attribution را روی سرور متفاوتی انجام دهید. در این حالت می‌توانید یک یا چند URL را به عنوان مقدار `attributionsrc` مشخص کنید. وقتی درخواست منبع رخ می‌دهد، هدر Attribution-Reporting-Eligible به URLهای مشخص‌شده در `attributionsrc` علاوه بر مبدأ (origin) منبع ارسال می‌شود. این URLها سپس می‌توانند با هدر Attribution-Reporting-Register-Source پاسخ دهند تا ثبت کامل شود.

          > \[!NOTE] مشخص کردن چند URL به این معنی است که چندین منبع attribution می‌توانند روی یک ویژگی ثبت شوند. برای مثال ممکن است کمپین‌های مختلفی داشته باشید که می‌خواهید موفقیت آن‌ها را اندازه‌گیری کنید و گزارش‌های متفاوتی روی داده‌های مختلف تولید کنید.

      عناصر `<a>` نمی‌توانند به عنوان attribution triggers استفاده شوند، فقط به عنوان منابع (sources).
* `download`
  * : باعث می‌شود مرورگر URL پیوند داده‌شده را به‌عنوان یک دانلود در نظر بگیرد. می‌تواند با یا بدون مقدار `filename` استفاده شود:
    * بدون مقدار، مرورگر یک نام‌فایل/پسوند پیشنهادی تولید می‌کند، که از منابع مختلف گرفته می‌شود:
      * هدر Content-Disposition
      * بخش نهایی در مسیر (path) URL
      * MIME type (media type) (از هدر Content-Type، ابتدای یک `data:` URL، یا `Blob.type` برای یک `blob:` URL)
* `filename`: تعیین یک مقدار آن را به‌عنوان نام فایل پیشنهاد می‌دهد. کاراکترهای `/` و `\` به خط زیرین (`_`) تبدیل می‌شوند. سیستم‌فایل‌ها ممکن است برخی کاراکترهای دیگر را در نام فایل ممنوع کنند، بنابراین مرورگرها در صورت لزوم نام پیشنهادی را تنظیم خواهند کرد.

> \[!NOTE]
>
> * `download` تنها برای [same-origin URLs](../../../../../../en-US/docs/Web/Security/Defenses/Same-origin_policy/) یا schemeهای `blob:` و `data:` کار می‌کند.
> * نحوه رفتار مرورگرها با دانلودها بسته به مرورگر، تنظیمات کاربر و عوامل دیگر متفاوت است. ممکن است قبل از شروع دانلود از کاربر پرسیده شود، یا فایل به‌طور خودکار ذخیره شود، یا به‌طور خودکار باز شود، یا در یک برنامه خارجی یا خود مرورگر نمایش داده شود.
> * اگر هدر `Content-Disposition` اطلاعات متفاوتی نسبت به صفت `download` داشته باشد، رفتار حاصل ممکن است متفاوت باشد:
>   * اگر هدر یک `filename` مشخص کند، نسبت به نام فایل مشخص‌شده در صفت `download` اولویت دارد.
>   * اگر هدر یک disposition برابر `inline` مشخص کند، Chrome و Firefox به صفت اولویت می‌دهند و آن را به‌عنوان دانلود در نظر می‌گیرند. نسخه‌های قدیمی Firefox (قبل از 82) به هدر اولویت می‌دهند و محتوا را به‌صورت inline نمایش می‌دهند.

* `href`
  *   : آدرسی (URL) که هایپرلینک به آن اشاره می‌کند. پیوندها محدود به آدرس‌های مبتنی بر HTTP نیستند — آن‌ها می‌توانند از هر scheme آدرس‌دهی‌ای که توسط مرورگرها پشتیبانی می‌شود استفاده کنند:

      * شماره تلفن‌ها با آدرس‌های `tel:`
      * نشانی‌های ایمیل با آدرس‌های `mailto:`
      * پیامک‌ها با آدرس‌های `sms:`
      * کد اجرایی با [`javascript:` URLs](../../../../../../en-US/docs/Web/URI/Reference/Schemes/javascript/)
      * در حالی که مرورگرهای وب ممکن است schemeهای دیگر را پشتیبانی نکنند، وب‌سایت‌ها می‌توانند با [`registerProtocolHandler()`](../../../../../../en-US/docs/Web/API/Navigator/registerProtocolHandler/) آن‌ها را ثبت کنند

      علاوه بر این، ویژگی‌های دیگر URL می‌توانند بخش‌های مشخصی از منبع را مشخص کنند، از جمله:

      * بخش‌های یک صفحه با fragmentهای سند
      * بخش‌های مشخصی از متن با [text fragments](../../../../../../en-US/docs/Web/URI/Reference/Fragment/Text_fragments/)
      * قطعاتی از فایل‌های رسانه‌ای با media fragments
* `hreflang`
  * : اشاره‌ای به زبان انسانی (human language) آدرس لینک‌شده. عملکرد داخلی (built-in) ندارد. مقادیر مجاز همان مقادیر [the global `lang` attribute](../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/lang/) هستند.
* `interestfor` \{{experimental\_inline\}} \{{non-standard\_inline\}}
  * : عنصر `<a>` را به‌عنوان یک **فراخوانِ علاقه** (interest invoker) تعریف می‌کند. مقدار آن `id` عنصر هدف است که هنگام نمایش یا از دست رفتن علاقه روی عنصر فراخوان (مثلاً هنگام قرارگیری/برداشتن اشاره‌گر یا فوکوس/بلور) به نوعی تحت تأثیر قرار می‌گیرد (معمولاً نشان‌دادن یا پنهان‌سازی). برای اطلاعات و مثال‌های بیشتر به [Using interest invokers](../../../../../../en-US/docs/Web/API/Popover_API/Using_interest_invokers/) مراجعه کنید.
* `ping`
  * : یک لیست آدرس URL جداشده با فاصله. وقتی لینک دنبال می‌شود، مرورگر درخواست‌های \{{HTTPMethod("POST")\}} با بدنه `PING` به آن آدرس‌ها ارسال می‌کند. معمولاً برای ردیابی (tracking) استفاده می‌شود.
* `referrerpolicy`
  * : چه مقداری از [referrer](../../../../../../en-US/docs/Web/HTTP/Reference/Headers/Referer/) هنگام دنبال کردن لینک ارسال شود.
    * `no-referrer`: هدر \{{HTTPHeader("Referer")\}} ارسال نخواهد شد.
    * `no-referrer-when-downgrade`: هدر \{{HTTPHeader("Referer")\}} به \{{Glossary("origin")\}}هایی که از \{{Glossary("TLS")\}} (\{{Glossary("HTTPS")\}}) برخوردار نیستند ارسال نمی‌شود.
    * `origin`: ریفرر ارسال‌شده به منشأ (origin) صفحه ارجاع محدود خواهد شد: [scheme](../../../../../../en-US/docs/Learn_web_development/Howto/Web_mechanics/What_is_a_URL/)، \{{Glossary("host")\}} و \{{Glossary("port")\}}.
    * `origin-when-cross-origin`: ریفرری که به مبادی (origins) دیگر ارسال می‌شود به scheme، host و port محدود خواهد شد. ناوبری‌ها روی همان origin همچنان مسیر (path) را شامل خواهند شد.
    * `same-origin`: برای سیاست همان‌منشأ (Same-origin policy) ریفرر ارسال خواهد شد، اما درخواست‌های بین‌منشأ (cross-origin) هیچ اطلاعات ریفرری نخواهند داشت.
    * `strict-origin`: تنها منشأ سند به‌عنوان ریفرر ارسال می‌شود هنگامی که سطح امنیت پروتکل ثابت بماند (HTTPS→HTTPS)، اما به مقصد کم‌امنیت‌تر (HTTPS→HTTP) ارسال نخواهد شد.
    * `strict-origin-when-cross-origin` (default): هنگام انجام درخواست همان‌منشأ URL کامل ارسال می‌شود، فقط منشأ هنگام ثابت ماندن سطح امنیت پروتکل ارسال می‌شود (HTTPS→HTTPS)، و به مقصد کم‌امنیت‌تر (HTTPS→HTTP) هیچ هدر ارسال نمی‌شود.
    * `unsafe-url`: ریفرر شامل منشأ و مسیر (path) خواهد بود (اما نه [fragment](../../../../../../en-US/docs/Web/API/HTMLAnchorElement/hash/)، [password](../../../../../../en-US/docs/Web/API/HTMLAnchorElement/password/)، یا [username](../../../../../../en-US/docs/Web/API/HTMLAnchorElement/username/)). این مقدار **ناامن** است، زیرا منشأها و مسیرها از منابع محافظت‌شده با TLS را به منشأهای ناامن نشت می‌دهد.
* [`rel`](../../../../../../en-US/docs/Web/HTML/Reference/Attributes/rel/)
  * : رابطه (relationship) URL لینک‌شده به‌صورت نوع‌های لینک جداشده با فاصله.
* `target`
  *   : کجا آدرس لینک‌شده نمایش داده شود، به‌صورت نام یک زمینه مرور (browsing context) (یک تب، پنجره، یا \{{HTMLElement("iframe")\}}). کلیدواژه‌های زیر معانی ویژه‌ای برای محل بارگذاری URL دارند:

      * `_self`: زمینه مرور فعلی. (پیش‌فرض)
      * `_blank`: معمولاً یک تب جدید، اما کاربران می‌توانند مرورگرها را طوری تنظیم کنند که به‌جای آن پنجره جدید باز شود.
      * `_parent`: زمینه مرور والد (parent) زمینه فعلی. اگر والد وجود نداشته باشد، مانند `_self` رفتار می‌کند.
      * `_top`: بالاترین زمینه مرور. به‌طور مشخص، این به "بالاترین" زمینه‌ای که جد (ancestor) زمینه فعلی است اشاره دارد. اگر جدی وجود نداشته باشد، مانند `_self` رفتار می‌کند.
      * `_unfencedTop`: به فریم‌های جاسازی‌شده [fenced frames](../../../../../../en-US/docs/Web/API/Fenced_frame_API/) اجازه می‌دهد تا به فریم سطح بالا ناوبری کنند (یعنی عبور فراتر از ریشه fenced frame، برخلاف سایر مقاصد رزرو‌شده). توجه داشته باشید که اگر این مقدار خارج از زمینه fenced frame استفاده شود، ناوبری هنوز موفق خواهد شد، اما مانند یک کلیدواژه رزروشده عمل نخواهد کرد.

      > \[!NOTE] تنظیم `target="_blank"` روی عناصر `<a>` به‌طور ضمنی همان رفتار `rel` را مانند تنظیم [`rel="noopener"`](../../../../../../en-US/docs/Web/HTML/Reference/Attributes/rel/noopener/) فراهم می‌کند که باعث نمی‌شود `window.opener` تنظیم شود.
* `type`
  * : اشاره‌ای به فرمت URL پیوند داده‌شده با نوع MIME (MIME type). هیچ عملکرد داخلی‌ای ندارد.

#### Deprecated attributes

* `charset`
  * : نشان‌دهندهٔ رمزگذاری نویسه (character encoding)ِ URL پیوند داده‌شده بود.

> \[!NOTE] این خصوصیت منسوخ شده و **نباید توسط نویسندگان استفاده شود**. به‌جای آن از هدر HTTP `Content-Type` در URL پیوند داده‌شده استفاده کنید.

* `coords`
  * : با `shape` استفاده می‌شد. فهرستی جداشده با کاما از مختصات.
* `name`
  * : برای تعریف یک مکان هدف ممکن در یک صفحه الزامی بود. در HTML 4.01، `id` و `name` می‌توانستند هر دو روی `<a>` استفاده شوند، به شرطی که مقدارهای یکسانی داشته باشند.

> \[!NOTE] به‌جای آن از صفات سراسری `id` استفاده کنید.

* `rev`
  * : یک لینک معکوس را مشخص می‌کرد؛ مخالف `rel`. به‌دلیل ایجاد ابهام زیاد منسوخ شد.
* `shape`
  * : شکل ناحیهٔ لینک در یک نقشهٔ تصویر را تعیین می‌کرد.

> \[!NOTE] به‌جای آن از عنصر `area` برای نقشه‌های تصویری استفاده کنید.

### Accessibility

#### Strong link text

**محتوای داخل یک لینک باید نشان دهد که لینک به کجا می‌رود، حتی خارج از زمینه.**

**Inaccessible, weak link text**

یک اشتباه متداول این است که تنها کلمات "click here" یا "here" لینک شوند:

```html
<p>Learn more about our products <a href="/products">here</a>.</p>
```

**Result**

**Accessible, strong link text**

خوشبختانه این را می‌توان به‌راحتی اصلاح کرد، و در واقع کوتاه‌تر از نسخهٔ غیرقابل‌دسترس است!

```html
<p>Learn more <a href="/products">about our products</a>.</p>
```

**Result**

نرم‌افزارهای کمکی میانبرهایی برای فهرست کردن همهٔ لینک‌های یک صفحه دارند. با این حال، متن قوی لینک به همهٔ کاربران سود می‌رساند — میانبر «فهرست همهٔ لینک‌ها» نحوهٔ اسکن سریع صفحات توسط کاربران بینا را شبیه‌سازی می‌کند.

#### onclick events

عناصر لینک اغلب به‌عنوان دکمه‌های جعلی سوءاستفاده می‌شوند با قرار دادن `href` روی `#` یا `javascript:void(0)` تا از تازه‌سازی صفحه جلوگیری شود، سپس به رویدادهای `click` آن‌ها گوش داده می‌شود.

این مقادیر دروغین `href` هنگام کپی/کشیدن لینک‌ها، باز کردن لینک‌ها در تب/پنجرهٔ جدید، نشان‌گذاری (bookmarking)، یا زمانی که JavaScript در حال بارگذاری است، خطا دارد، یا غیرفعال است، رفتار غیرمنتظره‌ای ایجاد می‌کنند. آن‌ها همچنین معانی نادرستی را به فنّاوری‌های کمکی مانند صفحه‌خوان‌ها منتقل می‌کنند.

به‌جای آن از عنصر `button` استفاده کنید. به‌طور کلی، **فقط برای ناوبری به یک URL واقعی باید از هایپرلینک استفاده شود**.

#### External links and linking to non-HTML resources

لینک‌هایی که با `target="_blank"` در تب/پنجرهٔ جدید باز می‌شوند، یا لینک‌هایی که به یک فایل دانلود اشاره می‌کنند باید مشخص کنند که هنگام دنبال کردن لینک چه اتفاقی خواهد افتاد.

افرادی که اختلالات بینایی دارند، با کمک فناوری‌های صفحه‌خوان ناوبری می‌کنند، یا مشکلات شناختی دارند ممکن است وقتی تب، پنجره، یا برنامه‌ای به‌طور غیرمنتظره باز می‌شود سردرگم شوند. نرم‌افزارهای قدیمی صفحه‌خوان ممکن است حتی این رفتار را اعلام نکنند.

**Link that opens a new tab/window**

```html
<a target="_blank" href="https://www.wikipedia.org">
  Wikipedia (opens in new tab)
</a>
```

**Result**

**Link to a non-HTML resource**

اگر از یک نماد برای نشان دادن رفتار لینک استفاده می‌کنید، مطمئن شوید که دارای صفت `alt` برای توصیف هدف آن باشد. در صورت گم شدن نماد، محتوای صفت `alt` هنوز رفتار لینک را منتقل خواهد کرد.

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

**Result**

* [WebAIM: Links and Hypertext - Hypertext Links](https://webaim.org/techniques/hypertext/hypertext_links)
* [MDN / Understanding WCAG, Guideline 3.2](../../../../../../en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Understandable/#guideline_3.2_%E2%80%94_predictable_make_web_pages_appear_and_operate_in_predictable_ways)
* [G200: Opening new windows and tabs from a link only when necessary](https://www.w3.org/TR/WCAG20-TECHS/G200.html)
* [G201: Giving users advanced warning when opening a new window](https://www.w3.org/TR/WCAG20-TECHS/G201.html)

#### Skip links

یک لینکِ پرش (skip link) لینکی است که در اولین قسمت ممکن از محتوای قرار می‌گیرد و به ابتدای محتوای اصلی صفحه اشاره می‌کند. معمولاً با CSS لینکِ پرش را طوری مخفی می‌کنند که خارج از صفحه قرار داشته باشد تا وقتی فوکوس می‌گیرد قابل مشاهده شود.

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

**Result**

لینک‌های پرش به کاربران صفحه‌کلید اجازه می‌دهند تا از محتوایی که در چند صفحه تکرار می‌شود (مثلاً ناوبری هدر) عبور کنند و مستقیماً به محتوا برسند.

لینک‌های پرش به‌ویژه برای افرادی مفیدند که با فناوری کمکی (assistive technology) مانند کنترل سوئیچ، فرمان صوتی، یا چوبک‌های هدایت دهان (mouth sticks/head wands) جابه‌جا می‌شوند، جایی که حرکت از میان لینک‌های تکراری ممکن است پرزحمت باشد.

* [WebAIM: "Skip Navigation" Links](https://webaim.org/techniques/skipnav/)
* [How-to: Use Skip Navigation links](https://www.a11yproject.com/posts/skip-nav-links/)
* [MDN / Understanding WCAG, Guideline 2.4 explanations](../../../../../../en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Operable/#guideline_2.4_%E2%80%94_navigable_provide_ways_to_help_users_navigate_find_content_and_determine_where_they_are)
* [Understanding Success Criterion 2.4.1](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-skip.html)

#### Size and proximity

**Size**

عناصر تعاملی، مانند لینک‌ها، باید یک ناحیه به‌اندازه کافی بزرگ فراهم کنند تا فعال‌سازی آن‌ها آسان باشد. این امر به انواع افراد کمک می‌کند، از جمله کسانی که مشکلات کنترل حرکتی دارند و کسانی که از ورودی‌های نامطمئن مانند صفحه‌نمایش لمسی استفاده می‌کنند. حداقل اندازه 44×44 CSS pixels توصیه می‌شود.

لینک‌های متنی درون متن (text-only links) از این الزام معاف هستند، اما همچنان ایده خوبی است که مطمئن شوید مقدار کافی از متن لینک‌شده است تا به‌راحتی فعال شود.

* [Understanding Success Criterion 2.5.5: Target Size](https://www.w3.org/WAI/WCAG21/Understanding/target-size.html)
* [Target Size and 2.5.5](https://adrianroselli.com/2019/06/target-size-and-2-5-5.html)
* [Quick test: Large touch targets](https://www.a11yproject.com/posts/large-touch-targets/)

**Proximity**

عناصر تعاملی مانند لینک‌ها که در نزدیکی بصری هم قرار دارند باید فاصله‌ای بینشان وجود داشته باشد. فاصله‌گذاری به افرادی با مشکلات کنترل حرکتی کمک می‌کند، کسانی که در غیر این صورت ممکن است به‌طور تصادفی محتوای تعاملی اشتباه را فعال کنند.

فاصله‌گذاری می‌تواند با استفاده از خصوصیات CSS مانند margin ایجاد شود.

* [Hand tremors and the giant-button-problem](https://axesslab.com/hand-tremors/)

### Examples

#### Linking to an absolute URL

**HTML**

```html
<a href="https://www.mozilla.com">Mozilla</a>
```

**Result**

#### پیوند دادن به آدرس‌های نسبی

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

#### پیوند دادن به یک المان در همان صفحه

```html
<!-- <a> element links to the section below -->
<p><a href="#Section_further_down">Jump to the heading below</a></p>

<!-- Heading to link to -->
<h2 id="Section_further_down">Section further down</h2>
```

> \[!NOTE] می‌توانید از `href="#top"` یا فرگمنت خالی (`href="#"`) برای پیوند دادن به بالای صفحه جاری استفاده کنید، همان‌طور که در مشخصات HTML تعریف شده است.

#### پیوند دادن به آدرس ایمیل

برای ساختن پیوندهایی که برنامه ایمیل کاربر را باز می‌کنند تا پیام جدیدی ارسال کند، از اسکیم `mailto:` استفاده کنید:

```html
<a href="mailto:nowhere@mozilla.org">Send email to nowhere</a>
```

برای جزئیات دربارهٔ آدرس‌های `mailto:`، مانند افزودن subject یا body، بخش Email links را ببینید یا RFC 6068 را مطالعه کنید.

#### پیوند دادن به شماره‌های تلفن

```html
<a href="tel:+49.157.0156">+49 157 0156</a>
<a href="tel:+1(800)555-0123">(800) 555-0123</a>
```

رفتار لینک‌های `tel:` با توجه به قابلیت‌های دستگاه متفاوت است:

* دستگاه‌های سلولی شماره را به‌طور خودکار شماره‌گیری می‌کنند.
* اکثر سیستم‌عامل‌ها برنامه‌هایی دارند که می‌توانند تماس برقرار کنند، مانند Skype یا FaceTime.
* وب‌سایت‌ها می‌توانند تماس تلفنی را با متدی مانند `registerProtocolHandler` ثبت کنند، مانند `web.skype.com`.
* رفتارهای دیگر شامل ذخیره شماره در مخاطبین یا ارسال شماره به دستگاه دیگری است.

برای نحو و ویژگی‌ها و جزئیات بیشتر دربارهٔ اسکیم URL `tel:`، RFC 3966 را ببینید.

#### استفاده از ویژگی download برای ذخیرهٔ یک به‌صورت PNG

برای ذخیرهٔ محتوای یک عنصر `canvas` به‌عنوان تصویر، می‌توانید لینکی بسازید که `href` آن دادهٔ کانواس به‌صورت یک URL با اسکیم `data:` باشد که توسط JavaScript ایجاد شده است و ویژگی `download` نام فایل دانلودی PNG را تعیین می‌کند.

**Example painting app with save link**

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

### امنیت و حریم خصوصی

عنصرهای `<a>` می‌توانند برای امنیت و حریم خصوصی کاربران پیامدهایی داشته باشند. برای اطلاعات بیشتر به Referer header: privacy and security concerns مراجعه کنید.

استفاده از `target="_blank"` بدون [`rel="noreferrer"`](../../../../../../en-US/docs/Web/HTML/Reference/Attributes/rel/noreferrer/) و [`rel="noopener"`](../../../../../../en-US/docs/Web/HTML/Reference/Attributes/rel/noopener/) باعث می‌شود وب‌سایت در برابر حملات بهره‌برداری از API `window.opener` آسیب‌پذیر شود، اگرچه توجه داشته باشید که در نسخه‌های جدیدتر مرورگرها تنظیم `target="_blank"` به‌طور ضمنی همان حفاظت مربوط به تنظیم `rel="noopener"` را فراهم می‌کند. برای جزئیات بیشتر به [browser compatibility](a.md#browser_compatibility) مراجعه کنید.

### خلاصهٔ فنی

| [Content categories](../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/) | [Flow content](../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/#flow_content), [phrasing content](../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/#phrasing_content), [interactive content](../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/#interactive_content)، palpable content.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| -------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| محتوای مجاز                                                                            | [Transparent](../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/#transparent_content_model)، به این استثنا که هیچ فرزندی نباید [interactive content](../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/#interactive_content) یا یک `<a>` element باشد، و هیچ فرزندی نباید صفت مشخص‌شده [tabindex](../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/tabindex/) را داشته باشد.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| حذف تگ                                                                                 | هیچ‌یک، هر دو تگ آغازین و پایانی الزامی هستند.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| والدین مجاز                                                                            | هر عنصری که [flow content](../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/#flow_content) را می‌پذیرد، اما نه عناصر دیگر `<a>`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| نقش ARIA ضمنی                                                                          | [`link`](../../../../../../en-US/docs/Web/Accessibility/ARIA/Reference/Roles/link_role/) زمانی که صفت `href` موجود باشد، در غیر این صورت [`generic`](../../../../../../en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role/)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| نقش‌های ARIA مجاز                                                                      | <p>زمانی که صفت <code>href</code> موجود است:</p><ul><li><a href="../../../../../../en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role/"><code>button</code></a></li><li><a href="../../../../../../en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role/"><code>checkbox</code></a></li><li><a href="../../../../../../en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role/"><code>menuitem</code></a></li><li><a href="../../../../../../en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role/"><code>menuitemcheckbox</code></a></li><li><a href="../../../../../../en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role/"><code>menuitemradio</code></a></li><li><a href="../../../../../../en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role/"><code>option</code></a></li><li><a href="../../../../../../en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radio_role/"><code>radio</code></a></li><li><a href="../../../../../../en-US/docs/Web/Accessibility/ARIA/Reference/Roles/switch_role/"><code>switch</code></a></li><li><a href="../../../../../../en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role/"><code>tab</code></a></li><li><a href="../../../../../../en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treeitem_role/"><code>treeitem</code></a></li></ul><p>زمانی که صفت <code>href</code> موجود نیست:</p><ul><li>هرکدام</li></ul> |
| واسط DOM                                                                               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |

### Specifications

### Browser compatibility

### See also

* `<link>` مشابه `<a>` است، اما برای پیوندهای متاداده (metadata) که برای کاربران نامرئی هستند.
* `:link` یک شبه‌کلاس CSS است که با عناصر `<a>` که URL در صفت `href` دارند و هنوز توسط کاربر بازدید نشده‌اند، مطابقت دارد.
* `:visited` یک شبه‌کلاس CSS است که با عناصر `<a>` که URL در صفت `href` دارند و در گذشته توسط کاربر بازدید شده‌اند، مطابقت دارد.
* `:any-link` یک شبه‌کلاس CSS است که با عناصر `<a>` که صفت `href` دارند، مطابقت دارد.
* [Text fragments](../../../../../../en-US/docs/Web/URI/Reference/Fragment/Text_fragments/) are user-agent instructions added to URLs that allow content authors to link to specific text on a page, without IDs being required.
