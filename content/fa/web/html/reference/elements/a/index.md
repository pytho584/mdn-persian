---
title: "<a> HTML anchor element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/a"
translated_by: "n8n + AI"
---

The **`<a>`** [HTML](/en-US/docs/Web/HTML) element (or _anchor_ element)، با [attribute `href`](#href)، یک هایپرلینک به صفحات وب، فایل‌ها، آدرس‌های ایمیل، مکان‌هایی در همان صفحه یا هر چیزی که یک URL بتواند به آن ارجاع دهد، ایجاد می‌کند.

محتوای داخل هر `<a>` باید مقصد لینک را نشان دهد. اگر attribute `href` موجود باشد، فشردن کلید Enter در زمانی که عنصر `<a>` فوکوس شده باشد، آن را فعال می‌کند.

```html interactive-example
<p>You can reach Michael at:</p>

<ul>
  <li><a href="https://example.com">Website</a></li>
  <li><a href="mailto:m.bluth@example.com">Email</a></li>
  <li><a href="tel:+123456789">Phone</a></li>
</ul>
```

```css interactive-example
li {
  margin-bottom: 0.5rem;
}
```

## Attributes

This element's attributes include the [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes).

- `attributionsrc` deprecated non-standard
  - : مشخص می‌کند که می‌خواهید مرورگر هدر `Attribution-Reporting-Eligible` را ارسال کند. در سمت سرور این هدر برای آغاز ارسال هدر `Attribution-Reporting-Register-Source` در پاسخ استفاده می‌شود تا یک منبع attribution مبتنی بر navigation ثبت شود.

    مرورگر داده‌های منبع مرتبط با منبع attribution مبتنی بر navigation را (همان‌طور که در هدر پاسخ `Attribution-Reporting-Register-Source` ارائه شده) هنگامی که کاربر روی لینک کلیک می‌کند ذخیره می‌کند. برای جزئیات بیشتر به Attribution Reporting API مراجعه کنید.

    دو نسخه از این attribute وجود دارد که می‌توانید تنظیم کنید:
    - بولی، یعنی فقط نام `attributionsrc`. این مشخص می‌کند که می‌خواهید هدر `Attribution-Reporting-Eligible` به همان سروری که `href` به آن اشاره می‌کند ارسال شود. این وقتی مناسب است که ثبت منبع attribution را در همان سرور مدیریت می‌کنید.
    - مقداری که شامل یک یا چند URL است، برای مثال:

      ```html
      attributionsrc="https://a.example/register-source
      https://b.example/register-source"
      ```

      این حالت زمانی مفید است که منبع درخواست‌شده روی سروری که کنترلش را دارید نباشد، یا می‌خواهید ثبت منبع attribution را در سرور دیگری انجام دهید. در این حالت می‌توانید یک یا چند URL را به‌عنوان مقدار `attributionsrc` مشخص کنید. وقتی درخواست منبع رخ دهد، هدر `Attribution-Reporting-Eligible` علاوه بر مبدأ منبع، به URLهای مشخص‌شده در `attributionsrc` نیز ارسال خواهد شد. این URLها سپس می‌توانند با ارسال هدر `Attribution-Reporting-Register-Source` به تکمیل ثبت کمک کنند.

      > [!NOTE]
      > مشخص‌کردن چند URL به این معنی است که می‌توان منابع attribution متعددی را برای یک ویژگی ثبت کرد. برای مثال ممکن است کمپین‌های مختلفی داشته باشید که می‌خواهید موفقیتشان را اندازه‌گیری کنید و این شامل تولید گزارش‌های متفاوت بر اساس داده‌های مختلف می‌شود.

    عناصر `<a>` نمی‌توانند به‌عنوان attribution triggers استفاده شوند، فقط به‌عنوان sources قابل استفاده‌اند.

- `download`
  - : باعث می‌شود مرورگر URL لینک‌شده را به‌عنوان یک دانلود در نظر بگیرد. می‌توان از آن با یا بدون مقدار `filename` استفاده کرد:
    - بدون مقدار، مرورگر یک نام/پسوند فایل را پیشنهاد می‌دهد که از منابع مختلف تولید می‌شود:
      - هدر HTTP `Content-Disposition`
      - بخش نهایی در مسیر URL (`pathname`)
      - نوع MIME (از هدر HTTP `Content-Type`، ابتدای یک `data:` URL، یا `Blob.type` برای یک `blob:` URL)

- `filename`: تعیین یک مقدار به عنوان نام فایل پیشنهاد می‌شود. کاراکترهای `/` و `\` به آندرلاین (`_`) تبدیل می‌شوند. سامانهٔ فایل‌ها ممکن است برخی کاراکترهای دیگر را در نام فایل ممنوع کند، پس مرورگرها در صورت نیاز نام پیشنهادی را تنظیم می‌کنند.

> [!NOTE]
>
> - `download` فقط برای [same-origin URLs](/en-US/docs/Web/Security/Defenses/Same-origin_policy) یا schemeهای `blob:` و `data:` کار می‌کند.
> - نحوهٔ رفتار مرورگرها هنگام دانلود بسته به مرورگر، تنظیمات کاربر و عوامل دیگر متفاوت است. ممکن است قبل از شروع دانلود از کاربر پرسیده شود، یا فایل به‌صورت خودکار ذخیره شود، یا مستقیماً باز شود — یا در یک برنامهٔ خارجی یا در خود مرورگر.
> - اگر هدر `Content-Disposition` اطلاعات متفاوتی نسبت به صفت `download` داشته باشد، رفتار حاصل ممکن است متفاوت باشد:
>   - اگر هدر یک `filename` مشخص کند، بر نام تعیین‌شده در صفت `download` ارجحیت دارد.
>   - اگر هدر یک disposition با مقدار `inline` مشخص کند، Chrome و Firefox صفت را اولویت می‌دهند و آن را به‌عنوان دانلود در نظر می‌گیرند. نسخه‌های قدیمی Firefox (قبل از 82) هدر را ارجح می‌دانستند و محتوا را به‌صورت inline نمایش می‌دادند.

- `href`
  - : URL که لینک به آن اشاره می‌کند. لینک‌ها محدود به URLهای مبتنی بر HTTP نیستند — آن‌ها می‌توانند از هر scheme آدرسی که مرورگرها پشتیبانی می‌کنند استفاده کنند:
    - شماره‌های تلفن با URLهای `tel:`
    - آدرس‌های ایمیل با URLهای `mailto:`
    - پیامک‌ها با URLهای `sms:`
    - کد اجرایی با [`javascript:` URLs](/en-US/docs/Web/URI/Reference/Schemes/javascript)
    - در حالی که مرورگرهای وب ممکن است سایر schemeها را پشتیبانی نکنند، وب‌سایت‌ها می‌توانند با استفاده از [`registerProtocolHandler()`](/en-US/docs/Web/API/Navigator/registerProtocolHandler) آنها را ثبت کنند

    علاوه بر این، ویژگی‌های دیگر URL می‌توانند بخش‌های خاصی از منبع را مشخص کنند، از جمله:
    - بخش‌هایی از یک صفحه با فرگمنت‌های سند (document fragments)
    - بخش‌های خاصی از متن با [text fragments](/en-US/docs/Web/URI/Reference/Fragment/Text_fragments)
    - قطعاتی از فایل‌های رسانه‌ای با media fragments

- `hreflang`
  - : نشانه‌ای از زبان انسانی (human language)ِ URL لینک‌شده. عملکرد داخلی خاصی ندارد. مقادیر مجاز همان مقادیر صِفت سراسری [`lang`](/en-US/docs/Web/HTML/Reference/Global_attributes/lang) هستند.
- `interestfor`
  - : عنصر `<a>` را به‌عنوان یک **interest invoker** تعریف می‌کند. مقدار این صفت، `id` عنصر هدف است؛ عنصری که هنگام نمایش یا از دست رفتن «interest» روی عنصر فراخواننده (مثلاً با hover/unhover یا focus/blur) به شکلی تحت تأثیر قرار می‌گیرد (معمولاً نشان داده یا پنهان می‌شود). برای جزئیات و مثال‌ها، بخش Using interest invokers را ببینید.
- `ping`
  - : فهرستی از URLها جداشده با فاصله. وقتی لینک دنبال می‌شود، مرورگر درخواست‌های POST با بدنه `PING` به آن URLها ارسال می‌کند. معمولاً برای ردیابی استفاده می‌شود.
- `referrerpolicy`
  - : میزان اطلاعاتِ referrer که هنگام دنبال کردن لینک ارسال می‌شود.
    - `no-referrer`: هدر Referer ارسال نخواهد شد.
    - `no-referrer-when-downgrade`: هدر Referer به originهایی که از TLS (HTTPS) استفاده نمی‌کنند ارسال نخواهد شد.
    - `origin`: ارجاع ارسالی به origin صفحه ارجاع‌دهنده محدود می‌شود: scheme، host و port آن.
    - `origin-when-cross-origin`: ارجاعی که به originهای دیگر فرستاده می‌شود به scheme، host و port محدود خواهد شد. ناوبری‌ها روی همان origin همچنان شامل مسیر (path) خواهند بود.
    - `same-origin`: برای same origin ارجاع ارسال می‌شود، اما درخواست‌های cross-origin هیچ اطلاعات referrer نخواهند داشت.
    - `strict-origin`: فقط origin سند به‌عنوان referrer ارسال می‌شود وقتی سطح امنیت پروتکل ثابت بماند (HTTPS→HTTPS)، و به مقصدِ کمتر امن (HTTPS→HTTP) ارسال نخواهد شد.
    - `strict-origin-when-cross-origin` (پیش‌فرض): هنگام درخواست same-origin یک URL کامل ارسال می‌شود، هنگام ماندن سطح امنیت پروتکل فقط origin ارسال می‌شود (HTTPS→HTTPS)، و به مقصدِ کمتر امن (HTTPS→HTTP) هیچ هدر ارسال نمی‌شود.
    - `unsafe-url`: referrer شامل origin و مسیر (path) خواهد بود (ولی شامل fragment، password یا username نمی‌شود). این مقدار ناامن است؛ زیرا originها و مسیرها را از منابع محافظت‌شده با TLS به مقصدهای ناامن لو می‌دهد.

- [`rel`](/en-US/docs/Web/HTML/Reference/Attributes/rel)
  - : رابطه‌ی URL لینک‌شده به‌صورت لیستی از link typeها جداشده با فاصله.
- `target`
  - : مکان نمایش URL لینک‌شده، به‌عنوان نام یک browsing context (یک تب، پنجره، یا `iframe`). کلیدواژه‌های زیر معانی ویژه‌ای برای محل بارگذاری URL دارند:
    - `_self`: browsing context فعلی. (پیش‌فرض)
    - `_blank`: معمولاً یک تب جدید، اما کاربران می‌توانند مرورگر را طوری تنظیم کنند که به‌جای تب، پنجرهٔ جدید باز کند.
    - `_parent`: browsing context والدِ کنونی. اگر والد وجود نداشته باشد، مانند `_self` رفتار می‌کند.
    - `_top`: بالاترین browsing context؛ به‌عبارت دیگر «بالا‌ترین» کانتکستی که جد (ancestor) کانتکست فعلی است. اگر جدی وجود نداشته باشد، مانند `_self` رفتار می‌کند.
    - `_unfencedTop`: امکان می‌دهد فریم‌های محصور (fenced frames) جاسازی‌شده به فریم سطح بالا ناوبری کنند (یعنی عبور فراتر از ریشهٔ fenced frame، برخلاف مقصدهای رزروشدهٔ دیگر). توجه داشته باشید که اگر این مقدار خارج از زمینهٔ fenced frame استفاده شود، ناوبری همچنان موفق خواهد بود، اما مانند یک کلیدواژهٔ رزروشده عمل نخواهد کرد.

    > [!NOTE]
    > قرار دادن `target="_blank"` روی عناصر `<a>` به‌طور ضمنی همان رفتار `rel` مربوط به [`rel="noopener"`](/en-US/docs/Web/HTML/Reference/Attributes/rel/noopener) را فراهم می‌کند که باعث نمی‌شود `window.opener` تنظیم شود.

- `type`
  - : اشاره به فرمت URL مرتبط دارد، با MIME type. هیچ عملکرد داخلی خاصی ارائه نمی‌دهد.

### Deprecated attributes

- `charset` 
  - : به character encoding آدرس اشاره می‌کرد.

    > [!NOTE]
    > این صفت منسوخ شده و نباید توسط نویسندگان استفاده شود. از هدر HTTP Content-Type در سرور برای تعیین encoding استفاده کنید.

- `coords` 
  - : همراه با صفت `shape` استفاده می‌شد. فهرستی جداشده با کاما از مختصات است.
- `name` 
  - : برای تعریف یک موقعیت هدف احتمالی در صفحه ضروری بود. در HTML 4.01، می‌شد از هر دو `id` و `name` روی `<a>` استفاده کرد مشروط بر اینکه مقادیرشان یکسان باشد.

    > [!NOTE]
    > به جای آن از صفت سراسری `id` استفاده کنید.

- `rev` 
  - : لینک معکوس را مشخص می‌کرد؛ مخالف صفت `rel`. به‌خاطر ایجاد سردرگمی منسوخ شد.
- `shape` 
  - : شکل ناحیهٔ هایپرلینک در یک image map را تعیین می‌کرد.

    > [!NOTE]
    > به‌جای آن از عنصر `area` برای نقشه‌های تصویر استفاده کنید.

## Accessibility

### Strong link text

محتوای داخل لینک باید نشان دهد لینک به کجا می‌رود، حتی زمانی که خارج از زمینه قرار گرفته باشد.

#### Inaccessible, weak link text

خطای رایج این است که تنها روی کلماتی مثل "click here" یا "here" لینک زده شود:

```html example-bad
<p>Learn more about our products <a href="/products">here</a>.</p>
```

##### Result

#### Accessible, strong link text

خوشبختانه این مشکل به‌راحتی قابل حل است و در واقع نسخهٔ درست اغلب کوتاه‌تر هم هست:

```html example-good
<p>Learn more <a href="/products">about our products</a>.</p>
```

##### Result

نرم‌افزارهای کمکی میانبری برای فهرست کردن همهٔ لینک‌های صفحه دارند. با این حال، متن قوی لینک به همهٔ کاربران کمک می‌کند — میانبر «فهرست همهٔ لینک‌ها» رفتار اسکن سریع صفحه توسط کاربران بینا را شبیه‌سازی می‌کند.

### onclick events

عنصرهای anchor اغلب به‌عنوان دکمه‌های جعلی سوءاستفاده می‌شوند با تنظیم `href` روی `#` یا `javascript:void(0)` تا از بازنشانی صفحه جلوگیری شود، و سپس به رویداد `click` آنها گوش می‌دهند.

این مقادیر تقلبی `href` هنگام کپی/کشیدن لینک، باز کردن در تب/پنجرهٔ جدید، بوکمارک کردن، یا زمانی که JavaScript در حال بارگذاری است، خطا می‌دهد یا غیرفعال است، باعث رفتار غیرمنتظره می‌شوند. همچنین معانی نادرستی به فناوری‌های کمکی مانند screen readerها منتقل می‌کنند.

به جای آن از `button` استفاده کنید. به طور کلی، باید فقط از hyperlink برای ناوبری به یک URL واقعی استفاده شود.

### External links and linking to non-HTML resources

لینک‌هایی که با `target="_blank"` در تب/پنجرهٔ جدید باز می‌شوند، یا لینک‌هایی که به فایل دانلود اشاره می‌کنند، باید نشان دهند هنگام دنبال کردن لینک چه اتفاقی می‌افتد.

افرادی که مشکلات بینایی دارند، با کمک screen readerها ناوبری می‌کنند، یا مسائل شناختی دارند ممکن است با باز شدن ناگهانی تب، پنجره یا برنامهٔ جدید سردرگم شوند. نرم‌افزارهای قدیمی صفحه‌خوان ممکن است حتی این رفتار را اعلام نکنند.

#### Link that opens a new tab/window

```html
<a target="_blank" href="https://www.wikipedia.org">
  Wikipedia (opens in new tab)
</a>
```

##### Result

#### Link to a non-HTML resource

اگر از یک آیکن برای نشان دادن رفتار لینک استفاده می‌کنید، مطمئن شوید که آن آیکن یک صفت `alt` دارد تا هدفش را توصیف کند. اگر آیکن نمایش داده نشود، محتوای `alt` همچنان رفتار لینک را منتقل خواهد کرد.

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

##### نتیجه

- [WebAIM: Links and Hypertext - Hypertext Links](https://webaim.org/techniques/hypertext/hypertext_links)
- [MDN / Understanding WCAG, Guideline 3.2](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Understandable#guideline_3.2_—_predictable_make_web_pages_appear_and_operate_in_predictable_ways)
- [G200: Opening new windows and tabs from a link only when necessary](https://www.w3.org/TR/WCAG20-TECHS/G200.html)
- [G201: Giving users advanced warning when opening a new window](https://www.w3.org/TR/WCAG20-TECHS/G201.html)

### Skip links

یک پیوند پرش (skip link) پیوندی است که در اولین بخش ممکن از محتوای عنصر body قرار می‌گیرد و به شروع محتوای اصلی صفحه اشاره می‌کند. معمولاً با CSS پیوند پرش خارج از صفحه پنهان می‌شود تا زمانی که فوکوس پیدا کند قابل مشاهده شود.

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

#### نتیجه

پیوندهای پرش به کاربران کیبورد اجازه می‌دهند از محتوای تکراری در صفحات متعدد عبور کنند و مستقیماً به بخش‌های مهم مانند ناوبری هدر بپرند.

پیوندهای پرش برای افرادی که با فناوری کمکی مانند کنترل سوئیچ، فرمان صوتی، یا ابزارهایی مانند mouth sticks/head wands ناوبری می‌کنند بسیار مفیدند، زیرا حرکت از میان لینک‌های تکراری می‌تواند زمان‌بر یا دشوار باشد.

- [WebAIM: "Skip Navigation" Links](https://webaim.org/techniques/skipnav/)
- [How-to: Use Skip Navigation links](https://www.a11yproject.com/posts/skip-nav-links/)
- [MDN / Understanding WCAG, Guideline 2.4 explanations](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Operable#guideline_2.4_%e2%80%94_navigable_provide_ways_to_help_users_navigate_find_content_and_determine_where_they_are)
- [Understanding Success Criterion 2.4.1](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-skip.html)

### اندازه و فاصله

#### اندازه

عناصر تعاملی، مثل لینک‌ها، باید ناحیه‌ای به اندازه کافی بزرگ فراهم کنند تا فعال‌سازی آن‌ها آسان باشد. این امر به گروه‌های مختلفی از افراد کمک می‌کند، از جمله کسانی که مشکلات کنترل حرکتی دارند یا از ورودی‌های کم‌دقت مثل صفحه‌لمس استفاده می‌کنند. حداقل اندازهٔ پیشنهادی 44×44 CSS pixels است.

لینک‌های متنی در متن معمولی (text-only links) از این الزام مستثنا هستند، اما باز هم بهتر است مطمئن شوید متن کافی لینک شده تا فعال‌سازی آن آسان باشد.

- [Understanding Success Criterion 2.5.5: Target Size](https://www.w3.org/WAI/WCAG21/Understanding/target-size.html)
- [Target Size and 2.5.5](https://adrianroselli.com/2019/06/target-size-and-2-5-5.html)
- [Quick test: Large touch targets](https://www.a11yproject.com/posts/large-touch-targets/)

#### فاصله

عناصر تعاملی که در نزدیکی بصری یکدیگر قرار دارند باید با فاصله‌ای از هم جدا شوند. فاصله‌گذاری به افرادی که مشکلات کنترل حرکتی دارند کمک می‌کند تا به اشتباه آیتمِ نادرست را فعال نکنند.

فاصله می‌تواند با استفاده از ویژگی‌های CSS مانند margin ایجاد شود.

- [Hand tremors and the giant-button-problem](https://axesslab.com/hand-tremors/)

## Examples

### Linking to an absolute URL

#### HTML

```html
<a href="https://www.mozilla.com">Mozilla</a>
```

#### نتیجه

### Linking to relative URLs

#### HTML

```html
<a href="//example.com">Scheme-relative URL</a>
<a href="/en-US/docs/Web/HTML">Origin-relative URL</a>
<a href="p">Directory-relative URL</a>
<a href="./p">Directory-relative URL</a>
<a href="../p">Parent-directory-relative URL</a>
```

```css hidden
a {
  display: block;
  margin-bottom: 0.5em;
}
```

#### Result


### Linking to an element on the same page

```html
<!-- <a> element links to the section below -->
<p><a href="#Section_further_down">Jump to the heading below</a></p>

<!-- Heading to link to -->
<h2 id="Section_further_down">Section further down</h2>
```

#### Result


> [!NOTE]
> می‌توانید از `href="#top"` یا fragment خالی (`href="#"`) برای لینک دادن به بالای صفحهٔ جاری استفاده کنید، همان‌طور که در مشخصهٔ HTML تعریف شده است: https://html.spec.whatwg.org/multipage/browsing-the-web.html#scroll-to-the-fragment-identifier.

### Linking to an email address

برای ساختن لینک‌هایی که برنامهٔ ایمیل کاربر را باز می‌کنند تا پیام جدیدی ارسال کند، از scheme `mailto:` استفاده کنید:

```html
<a href="mailto:nowhere@mozilla.org">Send email to nowhere</a>
```

#### Result


برای جزئیات دربارهٔ URLهای `mailto:`، مثل اضافه کردن subject یا body، به بخش Email links در آموزش ساختاردهی محتوا مراجعه کنید یا RFC 6068.

### Linking to telephone numbers

```html
<a href="tel:+49.157.0156">+49 157 0156</a>
<a href="tel:+1(800)555-0123">(800) 555-0123</a>
```

#### Result


رفتار لینک‌های `tel:` بسته به قابلیت‌های دستگاه متفاوت است:

- دستگاه‌های تلفن همراه شماره را به‌طور خودکار شماره‌گیری می‌کنند.
- اکثر سیستم‌عامل‌ها برنامه‌هایی برای برقراری تماس دارند، مثل Skype یا FaceTime.
- وب‌سایت‌ها می‌توانند با استفاده از registerProtocolHandler، مانند `web.skype.com`، تماس تلفنی راه‌اندازی کنند.
- رفتارهای دیگر شامل ذخیرهٔ شماره در دفترچهٔ مخاطبین یا ارسال شماره به دستگاه دیگری است.

برای نحو، قابلیت‌های اضافی و جزئیات دیگر دربارهٔ scheme `tel:` به RFC 3966 مراجعه کنید.

### Using the download attribute to save a <canvas> as a PNG

برای ذخیرهٔ محتوای عنصر <canvas> به‌عنوان یک تصویر، می‌توانید یک لینک بسازید که مقدار `href` آن دادهٔ canvas به‌صورت یک URL از نوع `data:` باشد (توسط JavaScript ساخته شده) و صفت `download` نام فایل PNG دانلودشده را مشخص کند.

#### Example painting app with save link

##### HTML

```html
<p>
  Paint by holding down the mouse button and moving it.
  <a href="" download="my_painting.png">Download my painting</a>
</p>

<canvas width="300" height="300"></canvas>
```

##### CSS

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

##### JavaScript

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

##### Result


## Security and privacy

عناصر `<a>` می‌توانند تأثیراتی بر امنیت و حریم خصوصی کاربران داشته باشند. برای اطلاعات بیشتر به Referer header: privacy and security concerns مراجعه کنید.

استفاده از `target="_blank"` بدون [`rel="noreferrer"`](/en-US/docs/Web/HTML/Reference/Attributes/rel/noreferrer) و [`rel="noopener"`](/en-US/docs/Web/HTML/Reference/Attributes/rel/noopener) وب‌سایت را در معرض حملات سوءاستفاده از API `window.opener` قرار می‌دهد. توجه داشته باشید که در نسخه‌های جدیدتر مرورگرها، تنظیم `target="_blank"` به‌صورت ضمنی همان محافظتِ `rel="noopener"` را فراهم می‌کند. برای جزئیات بیشتر به [browser compatibility](#browser_compatibility) مراجعه کنید.

## خلاصهٔ فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories"
          >Content categories</a
        >
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >Flow content</a
        >,
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >phrasing content</a
        >,
        <a
          href="/en-US/docs/Web/HTML/Guides/Content_categories#interactive_content"
          >interactive content</a
        >، palpable content.
      </td>
    </tr>
    <tr>
      <th scope="row">Permitted content</th>
      <td>
        <a
          href="/en-US/docs/Web/HTML/Guides/Content_categories#transparent_content_model"
          >Transparent</a
        >، به‌استثنای این‌که هیچ فرزندی نباید
        <a
          href="/en-US/docs/Web/HTML/Guides/Content_categories#interactive_content"
          >interactive content</a
        > یا یک عنصر
        <code>&lt;a&gt;</code> باشد، و هیچ فرزندی نباید صفت مشخص‌شده
        <a
          href="/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex"
          >tabindex</a
        > را داشته باشد.
      </td>
    </tr>
    <tr>
      <th scope="row">Tag omission</th>
      <td>ندارد؛ هم تگ شروع و هم تگ پایان اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">Permitted parents</th>
      <td>
        هر عنصری که <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >flow content</a
        > را می‌پذیرد، اما دیگر عناصر <code>&lt;a&gt;</code> را نه.
      </td>
    </tr>
    <tr>
      <th scope="row">Implicit ARIA role</th>
      <td>
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/link_role"><code>link</code></a> زمانی که صفت <code>href</code> حضور دارد، در غیر این صورت
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role"><code>generic</code></a>
      </td>
    </tr>
    <tr>
      <th scope="row">Permitted ARIA roles</th>
      <td>
        <p>وقتی صفت <code>href</code> حضور دارد:</p>
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
        <p>وقتی صفت <code>href</code> حضور ندارد:</p>
        <ul>
          <li>هر نقش</li>
        </ul>
      </td>
    </tr>
    <tr>
      <th scope="row">DOM interface</th>
      <td>HTMLAnchorElement</td>
    </tr>
  </tbody>
</table>

## Specifications

## Browser compatibility

## See also

- `<link>` مشابه `<a>` است، ولی برای پیوندهای متادیتا که برای کاربران نامرئی هستند استفاده می‌شود.
- `:link` یک شبه‌کلاس (pseudo-class) در CSS است که با عناصر `<a>` که در صفت `href` یک URL دارند و کاربر هنوز آن را بازدید نکرده است، مطابقت می‌کند.
- `:visited` یک شبه‌کلاس (pseudo-class) در CSS است که با عناصر `<a>` که در صفت `href` یک URL دارند و کاربر قبلاً آن را بازدید کرده است، مطابقت می‌کند.
- `:any-link` یک شبه‌کلاس (pseudo-class) در CSS است که با عناصر `<a>` که صفت `href` دارند مطابقت می‌کند.
- [Text fragments](/en-US/docs/Web/URI/Reference/Fragment/Text_fragments) دستورات user-agent هستند که به URLها اضافه می‌شوند و به نویسندگان محتوا اجازه می‌دهند بدون نیاز به داشتن ID، به متن خاصی در صفحه لینک دهند.