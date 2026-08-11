---
title: "<link> HTML external resource link element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/link"
translated_by: "n8n + AI"
---

عنصر **`<link>`** در [HTML](/en-US/docs/Web/HTML) برای تعریف رابطه بین سند فعلی و یک منبع خارجی استفاده می‌شود. این عنصر بیشتر برای پیوند به {{Glossary("CSS", "stylesheet")}}‌ها به کار می‌رود، اما برای ایجاد آیکون‌های سایت (اعم از favicon و آیکون‌های صفحه اصلی و اپ‌های موبایل) و موارد دیگر نیز استفاده می‌شود.

برای پیوند یک stylesheet خارجی، یک عنصر `<link>` درون {{HTMLElement("head")}} قرار دهید:

```html
<link href="main.css" rel="stylesheet" />
```

در این مثال، مسیر stylesheet درون ویژگی `href` و یک ویژگی [`rel`](/en-US/docs/Web/HTML/Reference/Attributes/rel) با مقدار `stylesheet` قرار داده شده است. `rel` مخفف «relationship» (رابطه) است و یکی از ویژگی‌های کلیدی عنصر `<link>` محسوب می‌شود — مقدار آن مشخص می‌کند که منبع پیوند داده شده چه رابطه‌ای با سند دارد.

مقادیر رایج دیگری نیز وجود دارند. برای مثال، پیوند به favicon سایت:

```html
<link rel="icon" href="favicon.ico" />
```

مقادیر `rel` دیگری برای آیکون نیز وجود دارند که عمدتاً برای نشان‌دادن انواع خاص آیکون در پلتفرم‌های موبایل استفاده می‌شوند، مانند:

```html
<link
  rel="apple-touch-icon"
  sizes="114x114"
  href="apple-icon-114.png"
  type="image/png" />
```

ویژگی `sizes` اندازه آیکون و `type` نوع MIME منبع پیوندی را مشخص می‌کند. این اطلاعات به مرورگر کمک می‌کند مناسب‌ترین آیکون را انتخاب کند.

همچنین می‌توانید یک نوع یا query رسانه درون ویژگی `media` قرار دهید؛ در این صورت منبع فقط زمانی بارگیری می‌شود که شرط رسانه برقرار باشد. مثال:

```html
<link href="print.css" rel="stylesheet" media="print" />
<link href="mobile.css" rel="stylesheet" media="screen and (width <= 600px)" />
```

برخی ویژگی‌های جدید و جالب در زمینه عملکرد و امنیت نیز به عنصر `<link>` اضافه شده است. به این مثال توجه کنید:

```html
<link
  rel="preload"
  href="myFont.woff2"
  as="font"
  type="font/woff2"
  crossorigin="anonymous" />
```

مقدار `preload` برای `rel` به مرورگر می‌گوید که این منبع را از پیش بارگیری کند (برای جزئیات بیشتر [`rel="preload"`](/en-US/docs/Web/HTML/Reference/Attributes/rel/preload) را ببینید). ویژگی `as` نوع محتوای درخواست‌شده را مشخص می‌کند. ویژگی `crossorigin` نیز مشخص می‌کند که آیا منبع باید با درخواست {{Glossary("CORS")}} دریافت شود یا نه.

سایر نکات استفاده:

- یک عنصر `<link>` می‌تواند درون عنصر {{HTMLElement("head")}} یا {{HTMLElement("body")}} قرار گیرد، بسته به اینکه [نوع link](https://html.spec.whatwg.org/multipage/links.html#body-ok) آن **body-ok** باشد یا نه.
  برای مثال، نوع link به نام `stylesheet` جزو body-ok است، بنابراین `<link rel="stylesheet">` درون body مجاز است.
  با این حال، این کار توصیه نمی‌شود؛ بهتر است عناصر `<link>` را از محتوای body جدا کرده و در `<head>` قرار دهید.
- وقتی از `<link>` برای تعیین favicon سایت استفاده می‌کنید و سایت شما از Content Security Policy (CSP) برای افزایش امنیت بهره می‌برد، این policy روی favicon نیز اعمال می‌شود.
  اگر favicon بارگذاری نمی‌شود، مطمئن شوید که هدر {{HTTPHeader("Content-Security-Policy")}} و دایرکتیو [`img-src`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/img-src) آن دسترسی به favicon را مسدود نکرده است.
- مشخصات HTML و XHTML برای عنصر `<link>` event handlerهایی تعریف کرده‌اند، اما نحوه استفاده از آن‌ها مشخص نیست.
- در XHTML 1.0، {{glossary("void element", "void elements")}} مانند `<link>` نیاز به اسلش انتهایی دارند: `<link />`.
- WebTV از مقدار `next` برای ویژگی `rel` جهت پیش‌بارگذاری صفحه بعدی در یک سری از اسناد پشتیبانی می‌کند.

## Attributes

این عنصر شامل [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- `as`
  - : این attribute زمانی ضروری است که [`rel="preload"`](/en-US/docs/Web/HTML/Reference/Attributes/rel/preload) روی عنصر `<link>` تنظیم شده باشد، و زمانی اختیاری است که [`rel="modulepreload"`](/en-US/docs/Web/HTML/Reference/Attributes/rel/modulepreload) تنظیم شده باشد؛ در غیر این صورت نباید استفاده شود.
    این attribute نوع محتوایی را که توسط `<link>` بارگذاری می‌شود مشخص می‌کند؛ این اطلاعات برای تطبیق درخواست، اعمال [content security policy](/en-US/docs/Web/HTTP/Guides/CSP) صحیح و تنظیم هدر درخواست {{HTTPHeader("Accept")}} مناسب ضروری است.

    علاوه بر این، `rel="preload"` از این attribute به عنوان سیگنالی برای اولویت‌بندی درخواست استفاده می‌کند.
    جدول زیر مقادیر معتبر این attribute و عناصر یا منابعی که به آن‌ها اعمال می‌شود را نشان می‌دهد.

| مقدار `As` | مقدار `Rel` | کاربرد (Applies To) |
| --- | --- | --- |
| `audioworklet` | `modulepreload` | [AudioWorklet modules](/en-US/docs/Web/API/AudioWorklet) |
| `fetch` | `preload` | `fetch`, XHR<br>نکته: این مقدار همچنین به `crossorigin` attribute درون `<link>` نیاز دارد؛ به [CORS-enabled fetches](/en-US/docs/Web/HTML/Reference/Attributes/rel/preload#cors-enabled_fetches) مراجعه کنید. |
| `font` | `preload` | CSS `@font-face`<br>نکته: این مقدار همچنین به `crossorigin` attribute درون `<link>` نیاز دارد؛ به [CORS-enabled fetches](/en-US/docs/Web/HTML/Reference/Attributes/rel/preload#cors-enabled_fetches) مراجعه کنید. |
| `image` | `preload` | element های `<img>` و `<picture>` با attribute های srcset یا imageset، element های SVG `<image>`، قوانین CSS `*-image` |
| `json` | `modulepreload` | فایل JSON مکمل |
| `paintworklet` | `modulepreload` | [PaintWorklet modules](/en-US/docs/Web/API/PaintWorkletGlobalScope) |
| `script` | `preload` یا `modulepreload` | element های `<script>`، Worker `importScripts`، و مقصدهای `modulepreload` |
| `serviceworker` | `modulepreload` | [ServiceWorker modules](/en-US/docs/Web/API/ServiceWorker) |
| `sharedworker` | `modulepreload` | [SharedWorker](/en-US/docs/Web/API/SharedWorker) |
| `style` | `preload` یا `modulepreload` | element های `<link rel=stylesheet>`، CSS `@import` و مقصدهای `modulepreload` |
| `text` | `modulepreload` | فایل متنی ساده مکمل |
| `track` | `preload` | element های `<track>` (WebVTT؛ نوع MIME: `text/vtt`) |
| `worker` | `modulepreload` | [Worker modules](/en-US/docs/Web/API/Worker) |

- `blocking`
  - : این attribute به‌صراحت مشخص می‌کند که برخی عملیات‌ها باید تا برقراری شرایط خاص مسدود بمانند. فقط زمانی باید استفاده شود که attribute ی `rel` حاوی کلمه‌های کلیدی `expect` یا `stylesheet` باشد. با [`rel="expect"`](/en-US/docs/Web/HTML/Reference/Attributes/rel#expect)، یعنی عملیات‌ها تا زمانی که یک گره‌ی خاص از DOM پارس نشده‌اند مسدود می‌مانند. با [`rel="stylesheet"`](/en-US/docs/Web/HTML/Reference/Attributes/rel#stylesheet)، یعنی عملیات‌ها تا زمانی که یک stylesheet خارجی و زیرمنابع حیاتی‌اش دریافت و روی سند اعمال نشده‌اند مسدود می‌شوند. عملیات‌هایی که باید مسدود شوند باید فهرستی از token های `blocking` باشند که با space از هم جدا شده‌اند و در زیر آمده‌اند. در حال حاضر فقط یک token وجود دارد:
    - `render`: رندر کردن محتوا روی صفحه مسدود می‌شود.

    > [!NOTE]
    > فقط element های `link` در `<head>` سند می‌توانند رندر را مسدود کنند. به‌طور پیش‌فرض، یک element با `rel="stylesheet"` در `<head>` وقتی مرورگر هنگام parsing آن را پیدا می‌کند، رندر را مسدود می‌کند. اگر چنین element ی به‌صورت پویا از طریق اسکریپت اضافه شود، باید `blocking = "render"` را نیز تنظیم کنید تا رندر را مسدود کند.

- [`crossorigin`](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin)
  - : این [enumerated](/en-US/docs/Glossary/Enumerated) attribute مشخص می‌کند که هنگام دریافت منبع (resource) آیا باید از CORS استفاده شود یا نه. تصاویری که با CORS فعال بارگذاری می‌شوند را می‌توان بدون _tainted_ شدن در element ی `<canvas>` دوباره استفاده کرد. مقادیر مجاز عبارت‌اند از:
    - `anonymous`
      - : یک درخواست cross-origin (یعنی با هدر HTTP با نام `Origin`) انجام می‌شود، اما هیچ credential ارسال نمی‌شود (یعنی نه cookie، نه گواهی X.509 و نه HTTP Basic authentication). اگر سرور به سایت مبدأ credential ندهد (با تنظیم نکردن هدر HTTP با نام `Access-Control-Allow-Origin`)، منبع tainted می‌شود و استفاده از آن محدود می‌شود.
    - `use-credentials`
      - : یک درخواست cross-origin (یعنی با هدر HTTP با نام `Origin`) همراه با یک credential ارسال می‌شود (یعنی cookie، گواهی، و/یا HTTP Basic authentication انجام می‌شود). اگر سرور به سایت مبدأ credential ندهد (از طریق هدر HTTP با نام `Access-Control-Allow-Credentials`)، منبع _tainted_ می‌شود و استفاده از آن محدود می‌شود.

    اگر attribute وجود نداشته باشد، منبع بدون درخواست CORS دریافت می‌شود (یعنی بدون ارسال هدر HTTP با نام `Origin`) و این باعث می‌شود که نتوان از آن بدون tainted استفاده کرد. اگر مقدار نامعتبر باشد، طوری رفتار می‌شود که انگار کلیدواژه‌ی enumerated **anonymous** استفاده شده است.
    برای اطلاعات بیشتر به [CORS settings attributes](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin) مراجعه کنید.

- `disabled`
  - : فقط برای `rel="stylesheet"`، attribute بولین `disabled` مشخص می‌کند که آیا stylesheet توصیف‌شده باید بارگذاری و روی سند اعمال شود یا نه. اگر `disabled` در HTML هنگام بارگذاری مشخص شده باشد، stylesheet هنگام بارگذاری صفحه بارگذاری نمی‌شود. در عوض، فقط در صورت نیاز بارگذاری می‌شود، یعنی وقتی attribute ی `disabled` به `false` تغییر کند یا حذف شود.

    تنظیم کردن property ی `disabled` در DOM باعث می‌شود که stylesheet از لیست `Document.styleSheets` سند حذف شود.

- [`fetchpriority`](/en-US/docs/Web/HTML/Reference/Attributes/fetchpriority)
  - : نشان‌دهندهٔ اولویت نسبی برای دریافت یک منبع از نوع خاص است. مقادیر مجاز:
    - `high`
      - : منبع را با اولویت بالا نسبت به سایر منابع هم‌نوع دریافت کن.
    - `low`
      - : منبع را با اولویت پایین نسبت به سایر منابع هم‌نوع دریافت کن.
    - `auto`
      - : اولویت خاصی برای دریافت تنظیم نکن. این مقدار پیش‌فرض است. اگر مقداری تنظیم نشود یا نامعتبر باشد، از این استفاده می‌شود.
- `href`
  - : این attribute مشخص‌کنندهٔ {{glossary("URL")}} منبع لینک‌شده است. URL می‌تواند مطلق یا نسبی باشد.
- `hreflang`
  - : این attribute زبان منبع لینک‌شده را مشخص می‌کند. صرفاً جنبهٔ توصیه‌ای دارد. مقادیر باید از تگ‌های زبان BCP 47 معتبر باشند. این attribute را فقط زمانی استفاده کنید که attribute [`href`](/en-US/docs/Web/HTML/Reference/Elements/a#href) وجود داشته باشد.
- `imagesizes`
  - : فقط برای `rel="preload"` و `as="image"` کاربرد دارد. این attribute از نظر syntax و معنا مشابه attribute [`sizes`](/en-US/docs/Web/HTML/Reference/Elements/img#sizes) است و نشان می‌دهد کدام منبع مناسب برای پیش‌بارگذاری (preload) توسط یک `img` element با مقادیر متناظر در `srcset` و `sizes` آن باید استفاده شود.
- `imagesrcset`
  - : فقط برای `rel="preload"` و `as="image"` کاربرد دارد. این attribute از نظر syntax و معنا مشابه attribute [`srcset`](/en-US/docs/Web/HTML/Reference/Elements/img#srcset) است و نشان می‌دهد کدام منبع مناسب برای پیش‌بارگذاری (preload) توسط یک `img` element با مقادیر متناظر در `srcset` و `sizes` آن باید استفاده شود.
- [`integrity`](/en-US/docs/Web/HTML/Reference/Attributes/integrity)
  - : این attribute شامل یک یا چند {{glossary("hash function", "hash")}} از منبع است. برای اطمینان از اینکه محتوای منبع همان چیزی است که توسعه‌دهنده انتظار دارد و در حملات زنجیره تأمین (supply chain attack) با نسخهٔ مخرب جایگزین نشده است، استفاده می‌شود. این attribute فقط زمانی باید مشخص شود که `rel` برابر `stylesheet`، `preload` یا `modulepreload` باشد.  
    به [Subresource Integrity](/en-US/docs/Web/Security/Defenses/Subresource_Integrity) مراجعه کنید.
- `media`
  - : این attribute مشخص می‌کند که منبع لینک‌شده برای چه رسانه‌ای مناسب است. مقدار آن باید یک media type یا [media query](/en-US/docs/Web/CSS/Guides/Media_queries) باشد.  
    این attribute عمدتاً هنگام لینک به stylesheet‌های خارجی مفید است — به user agent اجازه می‌دهد بهترین مورد را برای دستگاه خود انتخاب کند.

- `referrerpolicy`
  - : رشته‌ای (string) که مشخص می‌کند هنگام دریافت منبع از کدام referrer استفاده شود. برای توضیحات دقیق و مثال‌های هر policy، به مستندات هدر `Referrer-Policy` مراجعه کنید.
    - `no-referrer` یعنی هدر `Referer` ارسال نخواهد شد.
    - `no-referrer-when-downgrade` یعنی وقتی به یک origin بدون TLS (HTTPS) ناوبری می‌شود، هیچ هدر `Referer` ارسال نمی‌شود. این رفتار پیش‌فرض user agent است، اگر policy دیگری مشخص نشده باشد.
    - `origin` یعنی referrer برابر با origin صفحه خواهد بود؛ که تقریباً scheme، host و port را شامل می‌شود.
    - `origin-when-cross-origin` یعنی ناوبری به سایر origins فقط به scheme، host و port محدود می‌شود، در حالی که ناوبری در همان origin شامل path نیز خواهد بود.
    - `same-origin` یعنی برای درخواست‌های same-origin، referrer (شامل origin، path و query string) ارسال می‌شود، اما برای درخواست‌های cross-origin هیچ referrer ارسال نمی‌شود.
    - `strict-origin` یعنی فقط origin ارسال می‌شود وقتی سطح امنیت پروتکل یکسان باشد (HTTPS→HTTPS). هیچ referrer به مقصدهای کم‌امنیت‌تر (HTTPS→HTTP) ارسال نمی‌شود. این برای صفحات HTTPS مهم است، چون از نشت اطلاعات referrer به origins ناامن جلوگیری می‌کند.
    - `strict-origin-when-cross-origin` یعنی برای درخواست‌های same-origin، referrer کامل ارسال می‌شود. برای درخواست‌های cross-origin، وقتی پروتکل یکسان است (HTTPS→HTTPS) فقط origin ارسال می‌شود، و وقتی به HTTP downgrade می‌شود هیچ referrer ارسال نمی‌شود. این مقدار پیش‌فرض است که تعادل بین کارایی و حریم خصوصی/امنیت را برای سایت‌های HTTPS برقرار می‌کند.
    - `unsafe-url` یعنی referrer شامل origin و path خواهد بود (اما نه fragment، password یا username). این حالت ناامن است، چون می‌تواند origins و pathها را از منابع محافظت‌شده با TLS به origins ناامن نشت دهد.

- [`rel`](/en-US/docs/Web/HTML/Reference/Attributes/rel)
  - : این attribute رابطه‌ی سند لینک‌شده با سند فعلی را مشخص می‌کند. این attribute باید یک لیست با جداکننده‌ی فاصله از [مقادیر نوع لینک](/en-US/docs/Web/HTML/Reference/Attributes/rel) باشد.
- `sizes`
  - : این attribute اندازه‌ی آیکون‌های رسانه‌های بصری موجود در منبع را تعریف می‌کند.
    فقط زمانی باید وجود داشته باشد که [`rel`](#rel) شامل مقدار `icon` یا یک نوع غیراستاندارد مانند `apple-touch-icon` اپل باشد.
    ممکن است مقادیر زیر را داشته باشد:
    - `any` به این معنی که آیکون می‌تواند به هر اندازه‌ای تغییر مقیاس دهد، چون در قالب برداری مانند `image/svg+xml` است.
    - یک لیست با جداکننده‌ی فاصله از اندازه‌ها، هر یک به فرمت `<width in pixels>x<height in pixels>` یا `<width in pixels>X<height in pixels>`. هر یک از این اندازه‌ها باید در منبع موجود باشد.

    > [!NOTE]
    > اکثر قالب‌های آیکون فقط می‌توانند یک آیکون واحد را ذخیره کنند؛ بنابراین، در بیشتر مواقع، attribute [`sizes`](#sizes) فقط یک ورودی دارد.
    > قالب ICO مایکروسافت و قالب ICNS اپل می‌توانند اندازه‌های متعدد آیکون را در یک فایل ذخیره کنند. ICO پشتیبانی بهتری در مرورگرها دارد، بنابراین اگر پشتیبانی از مرورگرهای مختلف برایتان مهم است، بهتر است از این قالب استفاده کنید.

- `title`
  - : attribute `title` روی عنصر `<link>` معنای ویژه‌ای دارد. وقتی روی `<link rel="stylesheet">` استفاده شود، یک [stylesheet پیش‌فرض یا جایگزین](/en-US/docs/Web/HTML/Reference/Attributes/rel/alternate_stylesheet) را تعریف می‌کند.
- `type`
  - : این attribute برای تعریف نوع محتوایی که به آن لینک داده شده استفاده می‌شود. مقدار attribute باید یک نوع MIME مانند **text/html**، **text/css** و غیره باشد. کاربرد رایج این attribute تعریف نوع stylesheet ارجاع‌داده‌شده (مثل **text/css**) است، اما با توجه به اینکه CSS تنها زبان stylesheet مورد استفاده در وب است، نه تنها امکان حذف `type` وجود دارد، بلکه در حال حاضر به عنوان یک رویه‌ی توصیه‌شده در نظر گرفته می‌شود.
    همچنین در انواع لینک `rel="preload"` استفاده می‌شود تا مطمئن شود مرورگر فقط انواع فایل‌هایی را که پشتیبانی می‌کند دانلود کند.

### ویژگی‌های غیراستاندارد

- `target` (منسوخ)
  - : این attribute نامِ frame یا پنجره‌ای را مشخص می‌کند که رابطه‌ی پیوند تعریف‌شده را دارد، یا محتوای هر منبعِ پیوند داده‌شده را نمایش می‌دهد.

### attribute های منسوخ

- `charset` (منسوخ)
  - : این attribute رمزگذاری کاراکترِ منبعِ پیوند داده‌شده را تعریف می‌کند. مقدار آن یک لیست از مجموعه‌کاراکترهاست که با فاصله یا کاما از هم جدا می‌شوند، همان‌طور که در RFC 2045 تعریف شده است. مقدار پیش‌فرض `iso-8859-1` است.

  > [!NOTE]
  > برای رسیدن به همان اثری که این attribute منسوخ ایجاد می‌کند، از HTTP header به نام `Content-Type` روی منبعِ پیوند داده‌شده استفاده کنید.

- `rev` (منسوخ)
  - : مقدار این attribute رابطه‌ی سندِ فعلی را با سندِ پیوند داده‌شده نشان می‌دهد، همان‌طور که توسط attribute [`href`](#href) تعریف شده است. بنابراین این attribute رابطه‌ی معکوس را نسبت به مقدار attribute `rel` مشخص می‌کند. [مقدارهای نوع پیوند](/en-US/docs/Web/HTML/Reference/Attributes/rel) برای این attribute مشابه مقادیر ممکن برای [`rel`](#rel) هستند.

  > [!NOTE]
  > به‌جای `rev`، باید از attribute [`rel`](#rel) با [مقدار نوع پیوند](/en-US/docs/Web/HTML/Reference/Attributes/rel) مخالف استفاده کنید. مثلاً برای برقراری پیوند معکوسِ `made`، مقدار `author` را مشخص کنید. همچنین این attribute به معنای «revision» نیست و نباید با شماره نسخه استفاده شود، هرچند بسیاری از سایت‌ها به این شکل از آن سوءاستفاده می‌کنند.

## مثال‌ها

### افزودن یک stylesheet

برای افزودن stylesheet به یک صفحه، از سینتکس زیر استفاده کنید:

```html
<link href="style.css" rel="stylesheet" />
```

### ارائه‌ی stylesheet های جایگزین

همچنین می‌توانید [stylesheet های جایگزین](/en-US/docs/Web/HTML/Reference/Attributes/rel/alternate_stylesheet) را مشخص کنید.

کاربر می‌تواند از طریق منوی **View > Page Style** انتخاب کند که کدام stylesheet استفاده شود. این کار به کاربران امکان می‌دهد نسخه‌های مختلفی از یک صفحه را ببینند.

```html
<link href="default.css" rel="stylesheet" title="Default Style" />
<link href="fancy.css" rel="alternate stylesheet" title="Fancy" />
<link href="basic.css" rel="alternate stylesheet" title="Basic" />
```

### ارائه‌ی آیکن‌ها برای کاربردهای مختلف

می‌توانید چند آیکن را در یک صفحه لینک کنید؛ مرورگر با استفاده از مقادیر `rel` و `sizes` به‌عنوان راهنما، بهترین گزینه را برای بافتار خاص خود انتخاب می‌کند.

```html
<!-- iPad Pro با نمایشگر Retina با وضوح بالا: -->
<link
  rel="apple-touch-icon"
  sizes="167x167"
  href="/apple-touch-icon-167x167.png" />
<!-- iPhone با وضوح 3x: -->
<link
  rel="apple-touch-icon"
  sizes="180x180"
  href="/apple-touch-icon-180x180.png" />
<!-- iPad غیر Retina، iPad mini و غیره: -->
<link
  rel="apple-touch-icon"
  sizes="152x152"
  href="/apple-touch-icon-152x152.png" />
<!-- iPhone با وضوح 2x و سایر دستگاه‌ها: -->
<link rel="apple-touch-icon" href="/apple-touch-icon-120x120.png" />
<!-- favicon پایه -->
<link rel="icon" href="/favicon.ico" />
```

برای اطلاعات درباره‌ی اینکه چه مقدار `sizes` برای آیکن‌های اپل انتخاب کنید، به [مستندات اپل درباره‌ی پیکربندی web application ها](https://developer.apple.com/library/archive/documentation/AppleApplications/Reference/SafariWebContent/ConfiguringWebApplications/ConfiguringWebApplications.html#//apple_ref/doc/uid/TP40002051-CH3-SW4) و [راهنمای رابط انسانی اپل](https://developer.apple.com/design/human-interface-guidelines/app-icons#App-icon-sizes) مراجعه کنید. معمولاً کافی است یک تصویر بزرگ مثلاً 192x192 ارائه دهید و اجازه دهید مرورگر در صورت نیاز آن را کوچک کند. اما همان‌طور که راهنمای طراحی اپل توصیه می‌کند، می‌توانید تصاویری با جزئیات متفاوت برای اندازه‌های مختلف ارائه دهید. ارائه‌ی آیکن‌های کوچک‌تر برای وضوح‌های پایین‌تر، پهنای باند را هم ذخیره می‌کند.

ممکن است اصلاً لازم نباشد که element های `<link>` را فراهم کنید. برای مثال، مرورگرها به‌طور خودکار `/favicon.ico` را از ریشه سایت درخواست می‌کنند؛ اپل نیز به‌طور خودکار `/apple-touch-icon-[size].png`، `/apple-touch-icon.png` و موارد مشابه را درخواست می‌کند. با این حال، ارائه لینک‌های صریح از شما در برابر تغییر این قراردادها محافظت می‌کند.

### بارگذاری شرطی منابع با media query ها

می‌توانید یک media type یا query را در داخل attribute «media» قرار دهید؛ در این صورت، این منبع فقط زمانی بارگذاری می‌شود که شرط media برقرار باشد. به عنوان مثال:

```html
<link href="print.css" rel="stylesheet" media="print" />
<link href="mobile.css" rel="stylesheet" media="all" />
<link href="desktop.css" rel="stylesheet" media="screen and (width >= 600px)" />
<link
  href="highres.css"
  rel="stylesheet"
  media="screen and (resolution >= 300dpi)" />
```

### رویدادهای بارگذاری style sheet

می‌توانید با گوش دادن به رویداد `load` روی یک style sheet متوجه شوید که چه زمانی بارگذاری شده است؛ به همین ترتیب، می‌توانید با شنیدن رویداد `error` تشخیص دهید که هنگام پردازش style sheet خطایی رخ داده است:

```html
<link rel="stylesheet" href="mystylesheet.css" id="my-stylesheet" />
```

```js
const stylesheet = document.getElementById("my-stylesheet");

stylesheet.onload = () => {
  // Do something interesting; the sheet has been loaded
};

stylesheet.onerror = () => {
  console.log("An error occurred loading the stylesheet!");
};
```

> [!NOTE]
> رویداد `load` پس از آن‌که style sheet و تمام محتوای import شده‌ی آن بارگذاری و parse شدند، درست قبل از اعمال استایل‌ها به محتوا اجرا می‌شود.

### نمونه‌های Preload

می‌توانید نمونه‌های متعددی از `<link rel="preload">` را در [Preloading content with `rel="preload"`](/en-US/docs/Web/HTML/Reference/Attributes/rel/preload) بیابید.

### مسدود کردن رندر تا دریافت منبع

می‌توانید توکن `render` را در داخل attribute «blocking» قرار دهید؛ در این حالت، رندر صفحه تا زمانی که منبع و زیرمنبع‌های بحرانی آن (critical subresourceها) دریافت و به سند اعمال نشده‌اند، مسدود می‌ماند. به عنوان مثال:

```html
<link blocking="render" rel="stylesheet" href="example.css" crossorigin />
```

## خلاصه فنی

| دسته‌بندی محتوا (Content categories) | Metadata content. در صورت وجود `itemprop`: Flow content و Phrasing content. |
|---|---|
| محتوای مجاز (Permitted content) | هیچ؛ این یک void element است. |
| حذف تگ (Tag omission) | باید تگ شروع داشته باشد و نباید تگ پایانی داشته باشد. |
| والدهای مجاز (Permitted parents) | هر element ای که element های metadata را می‌پذیرد. در صورت وجود `itemprop`: هر element ای که phrasing content را می‌پذیرد. |
| نقش ضمنی ARIA (Implicit ARIA role) | نقش `link` با attribute «href» |
| نقش‌های مجاز ARIA (Permitted ARIA roles) | هیچ `role` ای مجاز نیست. |
| رابط DOM (DOM interface) | `HTMLLinkElement` |

## همچنین ببینید

- هدر HTTP `Link`
- هدر HTTP `Referrer-Policy`