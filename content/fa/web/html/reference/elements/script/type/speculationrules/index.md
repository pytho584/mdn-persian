---
title: "<script type=\"speculationrules\"> HTML attribute value"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/script/type/speculationrules"
translated_by: "n8n + AI"
---

```markdown
# مقدار ویژگی HTML `<script type="speculationrules">`

مقدار **`speculationrules`** برای ویژگی [`type`](/en-US/docs/Web/HTML/Reference/Elements/script/type) عنصر `<script>` نشان می‌دهد که بدنهٔ این عنصر شامل speculation rules است.

speculation rules به صورت یک ساختار JSON هستند که تعیین می‌کنند چه منابعی باید توسط مرورگر prefetch یا prerender شوند. این قابلیت بخشی از [Speculation Rules API](/en-US/docs/Web/API/Speculation_Rules_API) است.

> **توجه:**
> می‌توان speculation rules را در فایل‌های متنی خارجی که توسط هدر HTTP [`Speculation-Rules`](/en-US/docs/Web/HTTP/Reference/Headers/Speculation-Rules) ارجاع داده می‌شوند تعریف کرد؛ با استفاده از همان [نمایش JSON](#speculation_rules_json_representation) که در ادامه آمده است. تعیین هدر HTTP زمانی مفید است که توسعه‌دهندگان نتوانند مستقیماً سند را تغییر دهند.

## نحو

```html
<script type="speculationrules">
  // JSON object defining rules
</script>
```

> **توجه:**
> ویژگی‌های `src`، `async`، `nomodule`، `defer`، `crossorigin`، `integrity` و `referrerpolicy` نباید مشخص شوند.

## استثناها

- `TypeError`
  - : تعریف speculation rules یک شیء JSON معتبر نیست.

## توضیحات

یک عنصر `<script type="speculationrules">` باید یک ساختار JSON معتبر داشته باشد که قوانین را تعریف می‌کند. مثال‌های زیر، قوانین جداگانه prefetch و prerender را نشان می‌دهند:

```html
<script type="speculationrules">
  {
    "prefetch": [
      {
        "urls": ["next.html", "next2.html"],
        "requires": ["anonymous-client-ip-when-cross-origin"],
        "referrer_policy": "no-referrer"
      }
    ]
  }
</script>
```

```html
<script type="speculationrules">
  {
    "prerender": [
      {
        "where": { "href_matches": "/next" },
        "eagerness": "eager"
      }
    ]
  }
</script>
```

### نمایش JSON مربوط به speculation rules

ساختار JSON شامل یک یا چند فیلد در سطح بالاست که هر کدام یک action را برای تعریف قوانین نشان می‌دهد. در حال حاضر actionهای پشتیبانی‌شده عبارتند از:

- `"prefetch"` (اختیاری، آزمایشی)
  - : قوانینی برای ناوبری‌های احتمالی آینده که باید بدنهٔ پاسخ سند مربوطه‌شان دانلود شود؛ این کار منجر به بهبود قابل توجه عملکرد هنگام ناوبری به آن مستندات می‌شود. توجه کنید که هیچ‌کدام از زیرمنابع (subresources) ارجاع‌شده توسط صفحه دانلود نمی‌شوند.
- `"prerender"` (اختیاری، آزمایشی)
  - : قوانینی برای ناوبری‌های احتمالی آینده که مستندات مربوطه‌شان باید به‌طور کامل دانلود، رندر و در یک تب نامرئی بارگذاری شوند. این شامل بارگذاری همه زیرمنابع، اجرای تمام JavaScript، و حتی بارگذاری زیرمنابع و واکشی داده‌هایی است که توسط JavaScript شروع شده‌اند. وقتی به آن مستندات ناوبری شود، ناوبری‌ها آنی خواهند بود و بهبود عملکرد قابل توجهی ایجاد می‌کنند.

> **توجه:**
> برای جزئیات کامل درباره نحوه استفاده مؤثر از prefetch و prerender، به صفحه اصلی [Speculation Rules API](/en-US/docs/Web/API/Speculation_Rules_API) مراجعه کنید.

هر فیلد action شامل یک آرایه است که به نوبه خود حاوی یک یا چند شیء است. هر شیء یک قانون واحد را تعریف می‌کند که مجموعه‌ای از URLها و پارامترهای مرتبط را مشخص می‌کند.

هر شیء می‌تواند ویژگی‌های زیر را داشته باشد:

- `"source"` (آزمایشی)
  - : رشته‌ای که منبع URLهایی را که قانون برای آن‌ها اعمال می‌شود نشان می‌دهد. این ویژگی اختیاری است چون مقدار آن همیشه از ویژگی‌های دیگر قابل استنباط است.
```

- `"document"`
      - : مشخص می‌کند که URLها از لینک‌های ناوبری سند مرتبط (مطابق تعریف در عناصر `<a>` و `<area>`) تطبیق داده می‌شوند، بر اساس شرایطی که توسط کلید `"where"` توصیف شده است. توجه داشته باشید که وجود کلید `"where"` به معنای `"source": "document"` است، بنابراین اختیاری است.
    - `"list"`
      - : مشخص می‌کند که URLها از یک لیست، که در کلید `"urls"` مشخص شده است، می‌آیند. توجه داشته باشید که وجود کلید `"urls"` به معنای `"source": "list"` است، بنابراین اختیاری است.

- `"urls"`
  - : آرایه‌ای از رشته‌ها که لیستی از URLها را برای اعمال قانون مشخص می‌کند. این URLها می‌توانند مطلق یا نسبی باشند. URLهای نسبی نسبت به base URL سند (اگر درون سند) یا نسبت به URL منبع خارجی (اگر به صورت خارجی واکشی شود) تفسیر می‌شوند. `"urls"` و `"where"` نمی‌توانند همزمان در یک قانون تنظیم شوند.

- `"where"`
  - : شیءای که شرایطی را نشان می‌دهد که قانون با URLهای موجود در سند مرتبط تطبیق داده می‌شود. به عبارت دیگر، شیء `"where"` یک تست را نشان می‌دهد که روی هر لینک در صفحه انجام می‌شود تا ببیند آیا قانون speculation روی آن اعمال می‌شود یا خیر. `"where"` و `"urls"` نمی‌توانند همزمان در یک قانون تنظیم شوند.

    این شیء می‌تواند دقیقاً یکی از ویژگی‌های زیر را داشته باشد:
    - `"href_matches"`
      - : رشته‌ای حاوی یک الگوی URL، یا آرایه‌ای حاوی چندین رشته الگوی URL که از syntax استاندارد [URL Pattern API](/en-US/docs/Web/API/URL_Pattern_API) پیروی می‌کنند. لینک‌هایی در سند که URL آنها با الگو(ها) مطابقت داشته باشد، قانون روی آنها اعمال می‌شود.
    - `"relative_to"`
      - : در مورد شرط `"href_matches"`، این مشخص می‌کند که آن شرط نسبت به چه چیزی تطبیق داده شود. این دقیقاً به همان روش کلید سطح قانون `"relative_to"` کار می‌کند، با این تفاوت که فقط روی یک شرط `"href_matches"` درون کلید `"where"` تأثیر می‌گذارد.
    - `"selector_matches"`
      - : رشته‌ای حاوی یک [CSS selector](/en-US/docs/Web/CSS/Guides/Selectors)، یا آرایه‌ای حاوی چندین CSS selector. لینک‌هایی در سند که توسط آن selectorها تطبیق داده شوند، قانون روی آنها اعمال می‌شود.
    - `"and"`
      - : آرایه‌ای حاوی یک یا چند شیء که شرایطی را شامل می‌شوند (`"href_matches"`, `"selector_matches"`, `"and"`, `"not"`, یا `"or"`)، که همه آنها باید مطابقت داشته باشند تا قانون روی آنها اعمال شود.
    - `"not"`
      - : شیءای حاوی یک شرط (`"href_matches"`, `"selector_matches"`, `"and"`, `"not"`, یا `"or"`) که اگر مطابقت داشته باشد، قانون روی آن اعمال _نمی‌شود_. تمام لینک‌هایی که با شرط مطابقت _ندارند_، قانون روی آنها اعمال می‌شود.
    - `"or"`
      - : آرایه‌ای حاوی یک یا چند شیء که شرایطی را شامل می‌شوند (`"href_matches"`, `"selector_matches"`, `"and"`, `"not"`, یا `"or"`)، که هر کدام از آنها می‌تواند مطابقت داشته باشد تا قانون روی آنها اعمال شود.

    شرایط `"where"` می‌توانند چندین سطح تودرتو شوند تا شرایط پیچیده‌ای ایجاد کنند، یا می‌توانید آنها را به قوانین جداگانه تقسیم کنید تا ساده بمانند. برای توضیحات بیشتر و چندین مثال از استفاده، به [مثال‌های where](#where_syntax_examples) مراجعه کنید.

- `"eagerness"` (تجربی)
  - رشت‌ای که به مرورگر اشاره می‌کند با چه اشتیاقی (eagerness) لینک‌های هدف را `prefetch` یا `prerender` کند تا تعادل میان مزایای عملکرد و هزینه منابع برقرار شود. مقادیر ممکن عبارتند از:
    - `"immediate"`
      - : نویسنده معتقد است که احتمال کلیک روی لینک بسیار زیاد است و/یا دریافت سند ممکن است زمان قابل توجهی نیاز داشته باشد. `prefetch`/`prerender` باید در اسرع وقت شروع شود، تنها با در نظر گرفتن عواملی مانند تنظیمات کاربر و محدودیت منابع.
    - `"eager"`
      - : نویسنده می‌خواهد تعداد زیادی از ناوبری‌ها را در اسرع وقت `prefetch`/`prerender` کند. `prefetch`/`prerender` باید با هر نشانه‌ای مبنی بر احتمال کلیک روی لینک شروع شود. مثلاً کاربر می‌تواند مکان‌نمای ماوس را به سمت لینک حرکت دهد، برای لحظه‌ای روی آن `hover`/`focus` کند، یا با لینک در جای برجسته‌ای از صفحه، اسکرول را متوقف کند.
    - `"moderate"`
      - : نویسنده به دنبال تعادل بین `eager` و `conservative` است. `prefetch`/`prerender` باید زمانی شروع شود که نشانه معقولی وجود داشته باشد که کاربر در آینده نزدیک روی لینک کلیک خواهد کرد. مثلاً کاربر لینک را به viewport اسکرول کرده و برای مدتی روی آن `hover`/`focus` کند.
    - `"conservative"`
      - : نویسنده می‌خواهد با هزینه نسبتاً کمی از منابع، از بارگذاری پیش‌بینی‌شده (speculative loading) بهره‌مند شود. `prefetch`/`prerender` باید تنها زمانی شروع شود که کاربر در حال کلیک کردن روی لینک است، مثلاً در رویدادهای [`mousedown`](/en-US/docs/Web/API/Element/mousedown_event) یا [`pointerdown`](/en-US/docs/Web/API/Element/pointerdown_event).

    اگر `"eagerness"` به طور صریح مشخص نشود، قوانین لیست (`"urls"`) به طور پیش‌فرض `immediate` و قوانین سند (`"where"`) به طور پیش‌فرض `conservative` هستند. مرورگر این اشاره را همراه با heuristics خود در نظر می‌گیرد، بنابراین ممکن است لینکی را انتخاب کند که نویسنده اشتیاق کمتری به آن داده است، اگر آن نامزد با اشتیاق کمتر انتخاب بهتری محسوب شود.

- `"expects_no_vary_search"` (تجربی)
  - رشت‌ای که به مرورگر اشاره می‌کند چه مقدار هدر [`No-Vary-Search`](/en-US/docs/Web/HTTP/Reference/Headers/No-Vary-Search) روی پاسخ‌های اسنادی که درخواست `prefetch`/`prerender` برای آنها دریافت می‌کند، تنظیم خواهد شد. مرورگر می‌تواند از این برای تعیین از پیش (ahead of time) استفاده کند که آیا منتظر ماندن برای تکمیل یک `prefetch`/`prerender` موجود مفیدتر است یا شروع یک درخواست `fetch` جدید در صورت تطابق قانون speculation. برای توضیح بیشتر درباره نحوه استفاده از این ویژگی، به [مثال `"expects_no_vary_search"`](#expects_no_vary_search_example) مراجعه کنید.

- `"referrer_policy"` (تجربی)
  - رشت‌ای که نمایانگر یک خط‌مشی referrer خاص برای استفاده هنگام درخواست URLهای مشخص‌شده در قانون است — مقادیر ممکن را در [`Referrer-Policy`](/en-US/docs/Web/HTTP/Reference/Headers/Referrer-Policy) ببینید. هدف این است که صفحه مرجع (referring page) بتواند یک خط‌مشی سخت‌گیرانه‌تر را به طور خاص برای درخواست speculative تنظیم کند نسبت به خط‌مشی که صفحه از قبل دارد (چه به صورت پیش‌فرض، چه با استفاده از `Referrer-Policy`).

    > [!NOTE]
    > یک `prefetch` بین‌سایتی (cross-site) نیازمند خط‌مشی referrer است که حداقل به اندازه مقدار پیش‌فرض `"strict-origin-when-cross-origin"` سخت‌گیرانه باشد — یعنی `"strict-origin-when-cross-origin"`، `"same-origin"`، `"strict-origin"` یا `"no-referrer"`. یک خط‌مشی سست‌تر که در قوانین speculation تنظیم شده باشد، خط‌مشی سخت‌گیرانه‌تر صفحه مرجع را لغو می‌کند، تا زمانی که همچنان برای حالت بین‌سایتی به اندازه کافی سخت‌گیرانه باشد.

    > [!NOTE]
    > در مورد قوانین سند (document rules)، خط‌مشی referrer مشخص‌شده در لینک تطبیق‌یافته (مثلاً با استفاده از attribute [`referrerpolicy`](/en-US/docs/Web/HTML/Reference/Elements/a#referrerpolicy)) استفاده خواهد شد، مگر اینکه قانون یک خط‌مشی را مشخص کند که آن را لغو کند.

- `"relative_to"` {{experimental_inline}}
  - : رشته‌ای که مشخص می‌کند آدرس‌های URL که با قانون تطبیق داده می‌شوند، نسبت به چه چیزی ارزیابی شوند. مقادیر ممکن:
    - `"document"`
      - : آدرس‌ها باید نسبت به سندی که قوانین پیش‌بینی (speculation rules) روی آن تنظیم شده‌اند، تطبیق داده شوند.
    - `"ruleset"`
      - : آدرس‌ها باید نسبت به فایلی که قوانین در آن مشخص شده‌اند، تطبیق داده شوند. این مقدار پیش‌فرض است.

    این تنظیم کلید فقط برای قوانینی که در یک فایل خارجی (با استفاده از هدر {{httpheader("Speculation-Rules")}} تعریف شده‌اند، معنا دارد. وقتی قوانین در همان سندی که برای آن تنظیم شده‌اند (یعنی درون یک عنصر `<script>` درون‌خطی) مشخص شوند، تفاوتی ایجاد نمی‌کند.

- `"requires"` {{experimental_inline}}
  - : آرایه‌ای از رشته‌ها که نشان‌دهنده قابلیت‌های مرورگر در حال تحلیل قانون است. این قابلیت‌ها باید در دسترس باشند تا قانون روی آدرس‌های مشخص شده اعمال شود.

    > [!WARNING]
    > در مرورگرهایی که نمی‌توانند یک نیاز مشخص را برآورده کنند، پیش‌بارگیری‌ها (prefetch) به‌طور خودکار شکست می‌خورند، حتی اگر از [API قوانین پیش‌بینی (Speculation Rules API)](/en-US/docs/Web/API/Speculation_Rules_API) پشتیبانی کنند.

    مقادیر ممکن:
    - `"anonymous-client-ip-when-cross-origin"`
      - : (فقط مربوط به prefetch) مشخص می‌کند که قانون فقط در صورتی اعمال شود که user agent بتواند از نمایش آدرس IP سرویس‌گیرنده به سرور مبدأ جلوگیری کند، در صورت ارسال درخواست prefetch بین‌دامنه‌ای. نحوه دقیق این کار به جزئیات پیاده‌سازی مرورگر بستگی دارد. مثال:
        - پیاده‌سازی کروم از یک پروکسی متعلق به گوگل برای مخفی کردن IP استفاده می‌کند، بنابراین به‌طور پیش‌فرض فقط برای مراجعه‌کنندگان تحت کنترل گوگل کار می‌کند (چون در این صورت، ارسال آدرس‌های مقصد به گوگل نشت حریم خصوصی اضافی نیست). در سایت‌های غیر متعلق به گوگل، قوانینی که شامل این مقدار هستند فقط برای کاربرانی که «پیش‌بارگیری پیشرفته» (Enhanced preloading) را در `chrome://settings/preloading` فعال کرده‌اند، اعمال می‌شوند.
        - مرورگرهای مبتنی بر کروم دیگر باید راه‌حل‌های خود را ارائه دهند. آزمایش کامل در تمام مرورگرهای هدف توصیه می‌شود.
        - پیاده‌سازی آینده سافاری ممکن است از چیزی شبیه [iCloud Private Relay](https://support.apple.com/en-us/102602) استفاده کند.
        - پیاده‌سازی آینده فایرفاکس ممکن است از محصول [Mozilla VPN](https://www.mozilla.org/en-US/products/vpn/) استفاده کند.

- `"tag"` {{experimental_inline}}
  - : رشته‌ای برای شناسایی یک قانون یا مجموعه قوانین. این مقدار در هدر درخواست {{HTTPHeader("Sec-Speculation-Tags")}} برای هر پیش‌بینی تحت پوشش آن قانون قرار می‌گیرد.

- `"target_hint"` {{experimental_inline}}
  - : رشته‌ای که نشان می‌دهد صفحه انتظار دارد محتوای پیش‌رندر (prerendered) در کجا فعال شود.
    این دستور برای پیش‌بینی‌های prefetch پشتیبانی نمی‌شود.
    مقادیر مجاز:
    - `"target_hint": "_blank"`
      - : محتوای پیش‌رندر را در یک صفحه جدید باز کن.
    - `"target_hint": "_self"`
      - : محتوای پیش‌رندر را در همان صفحه فعلی باز کن.
        این مقدار پیش‌فرض است، اگر مشخص نشود.

> [!NOTE]
> از آنجایی که قوانین پیش‌بینی از یک عنصر `<script>` استفاده می‌کنند، باید به‌طور صریح در دستور [`Content-Security-Policy`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy) [`script-src`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/script-src) مجاز شوند، اگر سایت آن را شامل می‌شود. این کار با افزودن مقدار `"inline-speculation-rules"` به همراه یک منبع hash یا nonce انجام می‌شود.

## مثال‌ها

### پیش‌بارگیری و پیش‌رندر در یک مجموعه قانون

مثال‌های پایه‌ای که در بخش توضیحات نشان داده شدند، شامل قوانین پیش‌بینی جداگانه برای prefetch و prerender بودند. می‌توان هر دو را در یک مجموعه قانون تعریف کرد:

```html
<script type="speculationrules">
  {
    "prefetch": [
      {
        "urls": ["next.html", "next2.html"],
        "requires": ["anonymous-client-ip-when-cross-origin"],
        "referrer_policy": "no-referrer"
      }
    ],
    "prerender": [
      {
        "where": { "selector_matches": ".product-link" },
        "eagerness": "eager"
      }
    ]
  }
</script>
```

> [!NOTE]
> این قطعه‌کد نمونه‌ای از یک قانون فهرستی (`"urls"`) و یک قانون مبتنی بر سند (`"where"`) را نشان می‌دهد.

### چند مجموعه قانون

در یک فایل HTML می‌توان چندین مجموعه قانون را نیز گنجاند:

```html
<script type="speculationrules">
  {
    "prefetch": [
      {
        "urls": ["next.html", "next2.html"],
        "requires": ["anonymous-client-ip-when-cross-origin"],
        "referrer_policy": "no-referrer"
      }
    ]
  }
</script>
<script type="speculationrules">
  {
    "prerender": [
      {
        "where": { "selector_matches": ".product-link" },
        "eagerness": "eager"
      }
    ]
  }
</script>
```

همچنین می‌توان چندین قانون را در یک مجموعه نتیجه واحد قرار داد:

```html
<script type="speculationrules">
  {
    "prerender": [
      {
        "urls": ["one.html"]
      },
      {
        "urls": ["two.html"]
      }
    ]
  }
</script>
```

### درج پویای قانون

مثال زیر قابلیت پشتیبانی از speculation rules را تشخیص می‌دهد (feature detection) و در صورت پشتیبانی، یک قانون prerender را به‌صورت پویا از طریق JavaScript اضافه می‌کند:

```js
if (
  HTMLScriptElement.supports &&
  HTMLScriptElement.supports("speculationrules")
) {
  const specScript = document.createElement("script");
  specScript.type = "speculationrules";
  const specRules = {
    prerender: [
      {
        urls: ["/next.html"],
      },
    ],
  };
  specScript.textContent = JSON.stringify(specRules);
  console.log("added speculation rules to: next.html");
  document.body.append(specScript);
}
```

### نمونه‌هایی از ساختار `where`

یک قانون مبتنی بر سند دارای خاصیت `"where"` است؛ این خاصیت شیئی است که معیارهایی را تعریف می‌کند و مشخص می‌کند کدام لینک‌های داخل سند مطابقت داده شوند. به بیان دیگر، شیء `"where"` یک آزمون است که روی تک‌تک لینک‌های صفحه اجرا می‌شود تا مشخص شود آیا قانون speculation روی آن لینک اعمال می‌شود یا نه.

ساده‌ترین نسخه، فقط با یک الگوی URL یا یک انتخابگر CSS مطابقت می‌کند:

```json
{ "where": { "href_matches": "/next" } }
```

```json
{ "where": { "selector_matches": ".important-link" } }
```

`"href_matches"` و `"selector_matches"` را می‌توان به‌صورت آرایه‌ای از مقادیر نیز تنظیم کرد؛ به این ترتیب چند الگوی URL یا چند انتخابگر CSS به‌طور هم‌زمان قابل تطبیق هستند:

```json
{ "where": { "href_matches": ["/next", "/profile"] } }
```

```json
{ "where": { "selector_matches": [".important-link", "#unique-link"] } }
```

الگوهای URL و انتخابگرها می‌توانند حاوی کاراکتر wildcard (`*`) باشند و بدین ترتیب یک مقدار می‌تواند با چند URL مطابقت کند. برای مثال، شیء زیر می‌تواند با `user/`، `user/settings`، `user/stats` و غیره مطابقت کند.

```json
{ "where": { "href_matches": "/user/*" } }
```

پارامترهای جستجو (یا query stringها) را نیز می‌توان در `href_matches` هدف قرار داد. برای مثال، شیء زیر با همه URLهای هم‌خاستگاه (same-origin) که دارای پارامتر جستجوی `category` باشند (به‌عنوان پارامتر اول یا پارامتری بعدی) مطابقت می‌کند:

```json
{ "where": { "href_matches": "/*\\?*(^|&)category=*" } }
```

هر شرطی را می‌توان با قرار دادن آن در داخل یک شرط `"not"` نفی کرد. یعنی وقتی شرط برقرار باشد، قانون speculation روی لینک _اعمال نمی‌شود_، اما وقتی شرط برقرار نباشد، قانون _اعمال می‌شود_. مثال زیر باعث می‌شود همه لینک‌هایی که با الگوی URL `/logout` _مطابقت ندارند_، قانون روی آن‌ها اعمال شود، اما لینک‌هایی که با `/logout` مطابقت دارند، این‌طور نباشند:

```json
{ "where": { "not": { "href_matches": "/logout" } } }
```

#### ترکیب چند شرط `"where"` با `"and"` یا `"or"`

چند شرط را می‌توان در داخل شرایط `"and"` یا `"or"` ترکیب کرد. این شرایط یک آرایه از چند شرط را دریافت می‌کنند؛ در `"and"` همه شروط و در `"or"` هرکدام از شروط باید برقرار باشند تا قانون speculation روی لینک اعمال شود. با استفاده از `"and"` یا `"or"` می‌توان شرایط را در چند سطح تودرتو قرار داد؛ هیچ محدودیت مشخصی برای عمق تودرتو وجود ندارد.

مفید است که شیء `"where"` را معادل یک دستور `if` در نظر بگیریم. بنابراین

```plain
{ and: [A, B, { or: [C, { not: D }] }] }
```

معادل این است:

```plain
if (A && B && (C || !D)) {
  apply speculation rule
}
```

در مثال کاملی که در ادامه می‌بینید، همهٔ صفحات هم‌ریشه (same-origin) برای پیش‌واکشی (prefetching) علامت‌گذاری شده‌اند، به جز صفحاتی که می‌دانیم مشکل‌ساز هستند: صفحهٔ `/logout` و هر لینکی که کلاس `.no-prerender` دارد.

```html
<script type="speculationrules">
  {
    "prefetch": [
      {
        "where": {
          "and": [
            { "href_matches": "/*" },
            { "not": { "href_matches": "/logout" } },
            { "not": { "selector_matches": ".no-prerender" } }
          ]
        }
      }
    ]
  }
</script>
```

> [!NOTE]
> الگوی `where` بالا شامل لینک‌های cross-site نمی‌شود؛ این لینک‌ها برای پیش‌واکشی پشتیبانی می‌شوند (به شرطی که کاربر برای مقصد کوکی تنظیم نکرده باشد، تا از ردیابی جلوگیری شود) اما برای پیش‌رندر (prerendering) پشتیبانی نمی‌شوند.

### مثال `"relative_to"`

برای مجموعه‌قوانینی که به‌صورت خارجی دریافت می‌شوند (یعنی از طریق هدر پاسخ `Speculation-Rules`)، به‌طور پیش‌فرض URLهای موجود در list rules و الگوهای URL در document rules نسبت به URL فایل متنی بیرونی که شامل قوانین است، تجزیه می‌شوند. اگر بخواهید URLهای یک list rule نسبت به URL پایهٔ سند تجزیه شوند، از `"relative_to"` به این شکل استفاده کنید:

```json
{
  "urls": ["/home", "/about"],
  "relative_to": "document"
}
```

برای document rules می‌توان `"relative_to"` را مستقیماً با `"href_matches"` جفت کرد؛ در این حالت، URL پایهٔ سند فقط برای الگوهای همان شرط خاص استفاده می‌شود:

```json
{
  "where": {
    "or": [
      { "href_matches": "/home", "relative_to": "document" },
      { "href_matches": "/about" }
    ]
  }
}
```

در مثال بالا، تنها `"href_matches"` اول نسبت به URL پایهٔ سند تطبیق داده می‌شود.

`relative_to` عمدتاً در شرایطی کاربرد دارد که فایل JSON قوانین Speculation با سندی که می‌خواهید قوانین را روی آن اعمال کنید در یک origin نیست:

1. اگر سند در `https://example.com/some/subpage.html` و قوانین در `https://example.com/resources/rules.json` باشد، در این صورت `/home` همیشه به `https://example.com/home` تبدیل می‌شود، چه `relative_to` برابر `document` باشد چه `ruleset`.

2. اگر سند در `https://example.com/some/subpage.html` و قوانین در `https://other.example/resources/rules.json` قرار داشته باشند (مثلاً روی یک origin شخص ثالث یا بدون کوکی)، آنگاه:
   - `"relative_to": "document"` باعث می‌شود `/home` به `https://example.com/home` تبدیل شود.
   - `"relative_to": "ruleset"` باعث می‌شود `/home` به `https://other.example/home` تبدیل شود.

   این معمول‌ترین مورد استفادهٔ `"relative_to"` است.

3. یک مورد استفادهٔ دیگر (البته نادرتر) وقتی است که URLها را به شکل `home` مشخص کرده‌اید نه `/home`. اگر سند در `https://example.com/some/subpage.html` و قوانین در `https://example.com/resources/rules.json` باشد، آنگاه:
   - `"relative_to": "document"` باعث می‌شود `home` به `https://example.com/some/home` تبدیل شود.
   - `"relative_to": "ruleset"` باعث می‌شود `home` به `https://example.com/resources/home` تبدیل شود.

### مثال `"expects_no_vary_search"`

مورد صفحهٔ فهرست کاربران `/users` را در نظر بگیرید که پارامتر `id` به آن اضافه می‌شود تا اطلاعات یک کاربر خاص نمایش داده شود، مثلاً `/users?id=345`. اینکه آیا این URL برای اهداف کش‌کردن باید یکسان در نظر گرفته شود یا نه، به رفتار برنامه بستگی دارد:

1. اگر این پارامتر باعث بارگذاری یک صفحهٔ کاملاً جدید شامل اطلاعات کاربر مشخص‌شده باشد، آنگاه URL باید جداگانه کش شود.
2. اگر این پارامتر فقط کاربر مشخص‌شده را در همان صفحه برجسته کند و شاید یک پنل کشویی با داده‌های او نمایش دهد، آنگاه برای اهداف کش‌کردن باید همان URL در نظر گرفته شود. این کار می‌تواند بهبود عملکرد در بارگذاری صفحات کاربر را به همراه داشته باشد و می‌توان از طریق هدر `No-Vary-Search` با مقدار `params=("id")` به آن رسید.

این موضوع چه تأثیری روی قوانین speculation دارد؟ کد زیر را در نظر بگیرید:

```html
<script type="speculationrules">
  {
    "prefetch": [
      {
        "urls": ["/users"]
      }
    ]
  }
</script>
<a href="/users?id=345">User Bob</a>
```

در این سناریو چه اتفاقی می‌افتد اگر کاربر به سمت `/users?id=345` حرکت کند، در حالی که هدرهای prefetch مربوط به `/users` هنوز دریافت نشده‌اند؟ در این لحظه، مرورگر نمی‌داند مقدار `No-Vary-Search` چیست یا اصلاً وجود دارد یا نه. اگر `No-Vary-Search` تنظیم نشده باشد و رفتار برنامه شبیه گزینه‌ی ۱ (در بالا) باشد، prefetch بیهوده خواهد بود و مرورگر مجبور می‌شود صفحه‌ی جداگانه‌ی `/users?id=345` را از اول دریافت کند.

برای حل این مشکل، می‌توانیم یک hint (راهنما) درباره‌ی آنچه نویسنده‌ی صفحه انتظار دارد که مقدار `No-Vary-Search` باشد، ارائه دهیم. یک قانون speculation می‌تواند فیلد `"expects_no_vary_search"` داشته باشد که شامل نمایش رشته‌ای از مقدار هدر مورد انتظار است:

```html
<script type="speculationrules">
  {
    "prefetch": [
      {
        "urls": ["/users"],
        "expects_no_vary_search": "params=(\"id\")"
      }
    ]
  }
</script>
<a href="/users?id=345">User Bob</a>
```

این نشان می‌دهد که انتظار داریم سرور گزینه‌ی ۲ (که در بالا توضیح داده شد) را تولید کند. اگر یک navigation (ناوبری) در حالی شروع شود که یک prefetch از `/users` در جریان است، این به مرورگر اطلاع می‌دهد که منتظر ماندن برای prefetch مناسب است، به جای اینکه بلافاصله درخواست دیگری برای `/users?id=345` شروع کند.

قوانین document rule (قوانین سند) نیز می‌توانند همراه با `"expects_no_vary_search"` استفاده شوند، بسته به الگوی مورد استفاده. مثلاً در این حالت:

```html
<script type="speculationrules">
  {
    "prefetch": [
      {
        { "where": { "href_matches": "/users?id=*" } },
        "expects_no_vary_search": "params=(\"id\")"
      }
    ]
  }
</script>
<a href="/users?id=012">User Bill</a>
<a href="/users?id=345">User Bob</a>
<a href="/users?id=678">User Ben</a>
```

اگر روی یک لینک هاور (hover) شود، مرورگر prefetch آن لینک خاص را شروع می‌کند.

اگر کاربر قبل از اتمام prefetch، روی لینک دیگری هاور کند، الگوی `expects_no_vary_search` به مرورگر می‌گوید که نیازی به لغو prefetch فعلی نیست، زیرا تمام URLهای `/users` با پارامترهای `id` مختلف، در این زمینه (و برای اهداف caching) عملاً به یک صفحه اشاره می‌کنند.

> [!WARNING]
> هنگام استفاده از prerender با `No-Vary-Search` باید دقت بیشتری داشت، زیرا ممکن است صفحه ابتدا با پارامترهای URL متفاوت prerender شود. `No-Vary-Search` برای پارامترهای URLای استفاده می‌شود که منبع یکسانی را از سرور تحویل می‌دهند، اما توسط کلاینت به دلایل مختلف (رندر سمت کلاینت، پارامترهای UTM برای اندازه‌گیری analytics و ...) استفاده می‌شوند. از آنجا که prerender اولیه ممکن است برای پارامترهای URL متفاوت باشد، هر کدی که به آن پارامترها وابسته است باید تنها پس از فعال‌سازی prerender (prerender activation) اجرا شود.

چندین پارامتر را می‌توان در یک آرایه‌ی space-separated (جدا شده با فاصله) ارائه داد:

```html
<script type="speculationrules">
  {
    "prefetch": [
      {
        { "where": { "href_matches": "/users?id=*" } },
        "expects_no_vary_search": "params=(\"id\" \"order\" \"lang\")"
      }
    ]
  }
</script>
```

> [!NOTE]
> از آنجایی که این یک [structured field](https://www.rfc-editor.org/info/rfc8941/) (فیلد ساختاریافته) است، پارامترها باید به صورت رشته‌های جدا شده با فاصله و نقل‌قول‌دار (quoted strings) باشند — همانطور که در بالا نشان داده شده — و نه با کاما جدا شوند، که توسعه‌دهندگان ممکن است بیشتر به آن عادت داشته باشند.

### مثال `eagerness`

مجموعه قوانین document rule زیر نشان می‌دهد که چگونه می‌توان از `eagerness` برای اشاره به میزان اشتیاق (eagerness) مرورگر برای prerender کردن هر دسته از لینک‌های منطبق استفاده کرد.

```html
<script type="speculationrules">
  {
    "prerender": [
      {
        "where": { "href_matches": "/*" },
        "eagerness": "conservative"
      },
      {
        "where": { "selector_matches": ".product-link" },
        "eagerness": "eager"
      }
    ]
  }
</script>
```

در اینجا اشاره می‌کنیم که:
- لینک‌های عمومی (`/*`) با eagerness محافظه‌کارانه (conservative) prerender شوند.
- لینک‌های با کلاس `product-link` با eagerness مشتاقانه (eager) prerender شوند.

همه لینک‌های هم‌سایت (same-site) داخل سند باید به‌صورت محافظه‌کارانه (conservatively) prerender شوند — یعنی زمانی که کاربر شروع به فعال کردنشان می‌کند.

هر لینک محصول (در اینجا آن‌هایی که کلاس `product-link.` دارند) باید به‌صورت eager prerender شود — یعنی اگر کاربر هرگونه حرکتی به سمت ناوبری به آن‌ها انجام دهد.

> [!NOTE]
> تأثیر تنظیمات eagerness برای قوانین لیست (list rules) کمتر مفید است. به‌طور پیش‌فرض، URLهای قوانین لیست به‌محض parse شدن قوانین، prefetch/prerender می‌شوند که همان چیزی است که انتظار می‌رود — این قوانین برای فهرست کردن صریح URLهای اولویت‌دار طراحی شده‌اند که می‌خواهید هرچه زودتر در دسترس باشند. به همین دلیل، `eager` در پیاده‌سازی‌های فعلی همان اثر `immediate` را دارد. تنظیمات eagerness پایین‌تر برای زمانی است که لینک‌ها تعامل داشته باشند و برای این موارد احتمالاً از قوانین سند (document rules) برای پیدا کردن آن‌ها در صفحه استفاده می‌کنید.

### مثال `tag`

یک `tag` می‌تواند در سطح بالایی قرار گیرد تا کل مجموعه قوانین را مشخص کند:

```html
<script type="speculationrules">
  {
    "tag": "my-rules",
    "prerender": [
      {
        "where": { "href_matches": "/*" },
        "eagerness": "conservative"
      }
    ]
  }
</script>
```

یا برای شناسایی قوانین جداگانه:

```html
<script type="speculationrules">
  {
    "prefetch": [
      "tag": "my-prefetch-rule",
      "urls": ["next.html"]
    ],
    "prerender": [
      "tag": "my-prerender-rule",
      "urls": ["next2.html"]
    ],
  }
</script>
```

### مثال `target_hint`

یک `target_hint` می‌تواند برای مشخص کردن پنجره‌ی هدف (target window) که در آن prerenderهای منطبق باز می‌شوند، استفاده شود:

```html
<script type="speculationrules">
  {
    "tag": "my-rules",
    "prerender": [
      {
        "eagerness": "eager",
        "target_hint": "_blank",
        "urls": ["page2.html"]
      }
    ]
  }
</script>
```

قوانین بالا اجازه می‌دهند که لینک‌های زیر در هدف‌های مناسب به‌درستی prerender شوند:

```html
<a href="page1.html">Open link in this window</a>
<a target="_blank" href="page2.html">Open link in new window</a>
```

`target_hint` فقط برای قوانین لیست (list rules) که از `urls` استفاده می‌کنند لازم است. برای قوانین سند (document rules) که از `where` استفاده می‌کنند نیازی نیست، زیرا هدف از طریق ویژگی `target` عنصر `<a>` قابل تشخیص است.