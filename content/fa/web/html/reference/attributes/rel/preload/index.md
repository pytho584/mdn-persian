---
title: "rel=\"preload\" HTML attribute value"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/rel/preload"
translated_by: "n8n + AI"
---

مقدار `preload` برای ویژگی `rel` در عنصر {{htmlelement("link")}} به شما امکان می‌دهد تا درخواست‌های fetch را در بخش {{htmlelement("head")}} HTML اعلام کنید. این کار مشخص می‌کند که چه منابعی را به‌زودی نیاز خواهید داشت و می‌خواهید بارگذاری آن‌ها را در مراحل اولیه چرخهٔ عمر صفحه شروع کنید، پیش از آنکه موتور اصلی رندر مرورگر شروع به کار کند. این کار باعث می‌شود منابع زودتر در دسترس باشند و احتمال مسدود کردن رندر صفحه کاهش یابد، که بهبود عملکرد را به همراه دارد. اگرچه نام این مقدار شامل واژهٔ _load_ است، اما اسکریپت را بارگذاری و اجرا نمی‌کند؛ بلکه فقط زمان‌بندی می‌کند که با اولویت بالاتر دانلود و در حافظهٔ نهان ذخیره شود.

## اصول اولیه

معمولاً از `<link>` برای بارگذاری یک فایل CSS برای استایل‌دهی به صفحه استفاده می‌کنید:

```html
<link rel="stylesheet" href="styles/main.css" />
```

اما در اینجا، از مقدار `preload` برای `rel` استفاده می‌کنیم که `<link>` را به یک پیش‌بارگذار (preloader) برای هر منبع مورد نظر تبدیل می‌کند. همچنین باید موارد زیر را مشخص کنید:

- مسیر منبع در ویژگی [`href`](/en-US/docs/Web/HTML/Reference/Elements/link#href)
- نوع منبع در ویژگی [`as`](/en-US/docs/Web/HTML/Reference/Elements/link#as)

یک مثال می‌تواند به این شکل باشد (منبع [JS and CSS example source](https://github.com/mdn/html-examples/tree/main/link-rel-preload/js-and-css) و [نمایش زنده](https://mdn.github.io/html-examples/link-rel-preload/js-and-css/)):

```html
<head>
  <meta charset="utf-8" />
  <title>JS and CSS preload example</title>

  <link rel="preload" href="style.css" as="style" />
  <link rel="preload" href="main.js" as="script" />

  <link rel="stylesheet" href="style.css" />
</head>

<body>
  <h1>bouncing balls</h1>
  <canvas></canvas>

  <script src="main.js" defer></script>
</body>
```

در اینجا فایل‌های CSS و JavaScript خود را از قبل بارگذاری می‌کنیم تا به‌محض نیاز برای رندر صفحه در مراحل بعدی، در دسترس باشند. این مثال ساده است، زیرا مرورگر احتمالاً عناصر `<link rel="stylesheet">` و `<script>` را در همان بخش HTML که preloadها قرار دارند کشف می‌کند. اما مزایا زمانی بسیار واضح‌تر می‌شوند که منابع دیرتر کشف شوند و حجم بیشتری داشته باشند. برای مثال:

- منابعی که از داخل CSS به آن‌ها اشاره شده است، مانند فونت‌ها یا تصاویر.
- منابعی که JavaScript می‌تواند درخواست کند، مانند اسکریپت‌های وارداتی.

`preload` مزایای دیگری نیز دارد. استفاده از `as` برای مشخص کردن نوع محتوای پیش‌بارگذاری‌شده به مرورگر اجازه می‌دهد:

- آن را در حافظهٔ نهان برای درخواست‌های آینده ذخیره کند و در صورت مناسب بودن، منبع را دوباره استفاده کند.
- خط‌مشی امنیت محتوای ([CSP](/en-US/docs/Web/HTTP/Guides/CSP)) مناسب را برای منبع اعمال کند.
- هدر درخواست {{HTTPHeader("Accept")}} صحیح را برای آن تنظیم کند.

### چه نوع محتوایی را می‌توان پیش‌بارگذاری کرد؟

انواع محتوای زیادی را می‌توان پیش‌بارگذاری کرد. مقادیر ممکن برای ویژگی `as` عبارتند از:

- `fetch`: منبعی که توسط درخواست fetch یا XHR قابل دسترسی است، مانند ArrayBuffer، باینری WebAssembly یا فایل JSON.
- `font`: فایل فونت.
- `image`: فایل تصویر.
- `script`: فایل JavaScript.
- `style`: برگه‌ی سبک CSS.
- `track`: فایل WebVTT.

> [!NOTE]
> پیش‌بارگذاری `font` و `fetch` نیاز به تنظیم ویژگی `crossorigin` دارد؛ در بخش [CORS-enabled fetches](#cors-enabled_fetches) در زیر ببینید.

> [!NOTE]
> جزئیات بیشتر دربارهٔ این مقادیر و ویژگی‌های وب که انتظار می‌رود توسط آن‌ها مصرف شوند، در مشخصات HTML آمده است — [Link type "preload"](https://html.spec.whatwg.org/multipage/links.html#link-type-preload). همچنین توجه داشته باشید که فهرست کامل مقادیری که ویژگی `as` می‌تواند بگیرد، توسط مشخصات HTML کنترل می‌شود — [Link type "preload" destinations](https://html.spec.whatwg.org/multipage/links.html#preload-destination).

## شامل کردن یک نوع MIME

المان‌های `<link>` می‌توانند یک attribute به نام [`type`](/en-US/docs/Web/HTML/Reference/Elements/link#type) دریافت کنند که شامل MIME type منبع مورد اشاره است. این ویژگی به‌ویژه هنگام preload کردن منابع مفید است – مرورگر از مقدار attribute `type` استفاده می‌کند تا ببیند آیا از آن منبع پشتیبانی می‌کند یا نه. اگر پشتیبانی کند، آن را دانلود می‌کند و در غیر این‌صورت نادیده می‌گیرد.

```html
<head>
  <meta charset="utf-8" />
  <title>Image preload example</title>

  <link rel="preload" href="flower.avif" as="image" type="image/avif" />
</head>
<body>
  <picture>
    <source src="flower.avif" type="image/avif" />
    <source src="flower.webp" type="image/webp" />
    <img src="flower.jpg" />
  </picture>
</body>
```

کد مثال بالا باعث می‌شود تصویر `image/avif` فقط در مرورگرهایی که از آن پشتیبانی می‌کنند preload شود – و برای کاربرانی که مرورگرشان `image/avif` را پشتیبانی می‌کند، همان تصویر `image/avif` استفاده شود (چون اولین عنصر `<source>` است). این کار باعث می‌شود دانلود تصویر برای کاربرانی که مرورگرشان `image/avif` را پشتیبانی می‌کند، احتمالاً سبک‌تر باشد.

توجه کنید که اگر مرورگر کاربران هم از `image/avif` و هم از `image/webp` پشتیبانی کند، و در آن کد یک المان `<link rel="preload" href="flower.webp" as="image" type="image/webp">` نیز اضافه شود، آنگاه هر دو تصویر `image/avif` و `image/webp` preload می‌شوند – حتی اگر فقط یکی از آنها واقعاً استفاده شود.

بنابراین، تعیین preload برای چند نوع از یک منبع توصیه نمی‌شود. بهترین روش این است که فقط نوعی را preload کنید که احتمالاً اکثر کاربران از آن استفاده خواهند کرد. به همین دلیل کد مثال بالا preload برای تصویر `image/webp` را مشخص نکرده است.

با این حال، نبود preload مانع از استفاده کاربرانی که به `image/webp` نیاز دارند نمی‌شود: برای کاربرانی که مرورگرشان از `image/avif` پشتیبانی نمی‌کند اما از `image/webp` پشتیبانی می‌کند، کد مثال بالا همچنان باعث می‌شود از تصویر `image/webp` استفاده شود – اما بدون اینکه آن را برای اکثر کاربران دیگر به‌طور غیرضروری preload کند.

## واکشی با CORS

هنگام preload کردن منابعی که با [CORS](/en-US/docs/Web/HTTP/Guides/CORS) واکشی می‌شوند (مثلاً [`fetch()`](/en-US/docs/Web/API/Window/fetch)، [`XMLHttpRequest`](/en-US/docs/Web/API/XMLHttpRequest) یا [فونت‌ها](/en-US/docs/Web/CSS/Reference/At-rules/@font-face))، باید دقت ویژه‌ای به تنظیم attribute [`crossorigin`](/en-US/docs/Web/HTML/Reference/Elements/link#crossorigin) روی المان [`<link>`](/en-US/docs/Web/HTML/Reference/Elements/link) داشت. این attribute باید به‌گونه‌ای تنظیم شود که با حالت CORS و credentials منبع مطابقت داشته باشد، حتی اگر واکشی cross-origin نباشد.

همان‌طور که در بالا اشاره شد، یک مورد جالب که این موضوع در آن صدق می‌کند، فایل‌های فونت هستند. به دلایل مختلف، این فایل‌ها باید با استفاده از CORS در حالت anonymous واکشی شوند (به [نیازمندی‌های واکشی فونت](https://drafts.csswg.org/css-fonts/#font-fetching-requirements) مراجعه کنید).

این مورد را به عنوان مثال در نظر بگیرید. می‌توانید [کد کامل مثال را در GitHub](https://github.com/mdn/html-examples/tree/main/link-rel-preload/fonts) ببینید ([نسخه زنده](https://mdn.github.io/html-examples/link-rel-preload/fonts/)):

```html
<head>
  <meta charset="utf-8" />
  <title>Web font example</title>

  <link
    rel="preload"
    href="fonts/cicle_fina-webfont.woff2"
    as="font"
    type="font/woff2"
    crossorigin />
  <link
    rel="preload"
    href="fonts/zantroke-webfont.woff2"
    as="font"
    type="font/woff2"
    crossorigin />

  <link href="style.css" rel="stylesheet" />
</head>
<body>
  …
</body>
```

نه تنها در attributeهای `type` راهنمای MIME type را ارائه داده‌ایم، بلکه attribute `crossorigin` را نیز تنظیم کرده‌ایم تا مطمئن شویم حالت CORS مربوط به preload با درخواست نهایی فونت همخوانی دارد.

## گنجاندن media

یکی از ویژگی‌های خوب عناصر `<link>` این است که می‌توانند attribute های [`media`](/en-US/docs/Web/HTML/Reference/Elements/link#media) را بپذیرند. این attribute ها می‌توانند [media types](/en-US/docs/Web/CSS/Reference/At-rules/@media#media_types) یا [media queries](/en-US/docs/Web/CSS/Guides/Media_queries/Using) کامل باشند و به شما امکان می‌دهند پیش‌بارگذاری واکنش‌گرا (responsive preloading) انجام دهید.

بیایید یک مثال را بررسی کنیم (مشاهده در GitHub — [source code](https://github.com/mdn/html-examples/tree/main/link-rel-preload/media)، [live example](https://mdn.github.io/html-examples/link-rel-preload/media/)):

```html
<head>
  <meta charset="utf-8" />
  <title>Responsive preload example</title>

  <link
    rel="preload"
    href="bg-image-narrow.png"
    as="image"
    media="(width <= 600px)" />
  <link
    rel="preload"
    href="bg-image-wide.png"
    as="image"
    media="(width > 600px)" />

  <link rel="stylesheet" href="main.css" />
</head>
<body>
  <header>
    <h1>My site</h1>
  </header>

  <script>
    const mediaQueryList = window.matchMedia("(width <= 600px)");
    const header = document.querySelector("header");

    if (mediaQueryList.matches) {
      header.style.backgroundImage = 'url("bg-image-narrow.png")';
    } else {
      header.style.backgroundImage = 'url("bg-image-wide.png")';
    }
  </script>
</body>
```

ما attribute های `media` را روی عناصر `<link>` قرار می‌دهیم تا اگر کاربر viewport باریکی داشت، تصویر باریک پیش‌بارگذاری شود و اگر viewport پهن داشت، تصویر پهن بارگذاری شود. برای این کار از `Window.matchMedia` / `MediaQueryList` استفاده می‌کنیم (برای اطلاعات بیشتر به [Testing media queries](/en-US/docs/Web/CSS/Guides/Media_queries/Testing) مراجعه کنید).

این تکنیک برای سایر انواع منابع نیز کاربرد دارد. برای مثال، وقتی با فونت‌ها استفاده شود، پیش‌بارگذاری باعث می‌شود فونت در زمان رندر در دسترس باشد و احتمال نمایش متن بدون استایل (FOUT) کاهش پیدا کند.

این کار لزومی ندارد به تصاویر یا حتی فایل‌های هم‌نوع محدود شود — بزرگ فکر کنید! مثلاً اگر کاربر صفحه‌نمایش باریکی دارد که پهنای باند و CPU احتمالاً محدودتر هستند، می‌توانید یک نمودار SVG ساده‌شده را پیش‌بارگذاری و نمایش دهید، یا اگر منابع کاربر بیشتر است، یک تکه کد JavaScript پیچیده را پیش‌بارگذاری کنید و بعداً از آن برای رندر یک مدل تعاملی سه‌بعدی استفاده کنید.

## اسکریپت‌نویسی و پیش‌بارگذاری‌ها

> [!NOTE]
> اگر با [JavaScript modules](/en-US/docs/Web/JavaScript/Guide/Modules) کار می‌کنید، به‌جای آن از [`<link rel="modulepreload">`](/en-US/docs/Web/HTML/Reference/Attributes/rel/modulepreload) استفاده کنید.

نکته خوب دیگر درباره این پیش‌بارگذاری‌ها این است که می‌توانید آن‌ها را با اسکریپت اجرا کنید.
برای مثال، در اینجا یک instance از `HTMLLinkElement` می‌سازیم و سپس آن را به DOM متصل می‌کنیم:

```js
const preloadLink = document.createElement("link");
preloadLink.href = "myscript.js";
preloadLink.rel = "preload";
preloadLink.as = "script";
document.head.appendChild(preloadLink);
```

این یعنی مرورگر فایل `myscript.js` را پیش‌بارگذاری می‌کند اما هنوز از آن استفاده نمی‌کند. برای استفاده از آن می‌توانید این کار را انجام دهید:

```js
const preloadedScript = document.createElement("script");
preloadedScript.src = "myscript.js";
document.body.appendChild(preloadedScript);
```

این کار وقتی مفید است که بخواهید یک اسکریپت را پیش‌بارگذاری کنید اما اجرای آن را تا زمانی که دقیقاً به آن نیاز دارید به تأخیر بیندازید.

## مشخصات فنی

## سازگاری با مرورگرها

## همچنین ببینید

- [Speculative loading](/en-US/docs/Web/Performance/Guides/Speculative_loading) برای مقایسه `<link rel="preload">` با سایر ویژگی‌های مشابه بهبود عملکرد.
- [Preload: What Is It Good For?](https://www.smashingmagazine.com/2016/02/preload-what-is-it-good-for/) نوشتهٔ Yoav Weiss