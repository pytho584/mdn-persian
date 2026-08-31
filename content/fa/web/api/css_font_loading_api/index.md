---
title: CSS Font Loading API
slug: Web/API/CSS_Font_Loading_API
page-type: web-api-overview
browser-compat: api.FontFace
---

{{DefaultAPISidebar("CSS Font Loading API")}}{{AvailableInWorkers}}

**CSS Font Loading API** رویدادها و رابط‌هایی برای بارگذاری پویای منابع فونت فراهم می‌کند.

## مفاهیم و کاربرد

شیوه‌نامه‌های CSS به نویسندگان امکان استفاده از فونت‌های سفارشی را می‌دهند؛ با تعیین فونت‌هایی که باید با استفاده از قاعده {{cssxref("@font-face")}} بارگیری شوند، و اعمال آن‌ها به عناصر با ویژگی {{cssxref("font-family")}}. نقطه‌ای که در آن فونت بارگیری می‌شود توسط عامل کاربر (user agent) کنترل می‌شود. بیشتر عامل‌ها فقط زمانی که فونت برای اولین بار نیاز شود، آن را واکشی و بارگذاری می‌کنند که می‌تواند باعث تأخیر قابل توجهی شود.

CSS Font Loading API این مشکل را با این امکان که نویسندگان بتوانند زمان واکشی و بارگذاری یک چهره فونت (font face) و همچنین زمان اضافه شدن آن به مجموعه چهره‌های فونت متعلق به سند یا worker را کنترل و ردیابی کنند، برطرف می‌کند. افزودن یک چهره فونت به مجموعه چهره‌های فونت سند یا worker باعث می‌شود که عامل کاربر در صورت نیاز به‌طور خودکار منبع فونت مرتبط را واکشی و بارگذاری کند. یک چهره فونت یا قبل از اضافه شدن به مجموعه چهره‌های فونت یا بعد از آن می‌تواند بارگذاری شود، اما _باید_ قبل از استفاده برای ترسیم به مجموعه اضافه شود.

چهره‌های فونت در اشیای {{domxref('FontFace')}} تعریف می‌شوند که یک منبع فونت باینری یا URL و سایر ویژگی‌های فونت را تقریباً به همان روشی که قاعده CSS {{cssxref("@font-face")}} مشخص می‌کند. اشیای `FontFace` با استفاده از {{domxref("Document.fonts")}} و {{domxref("WorkerGlobalScope.fonts")}} به ترتیب به مجموعه {{domxref('FontFaceSet')}} سند یا worker اضافه می‌شوند. نویسندگان می‌توانند بارگیری فونت‌ها را با استفاده از `FontFace` یا `FontFaceSet` آغاز کنند و تکمیل بارگذاری را زیر نظر داشته باشند. `FontFaceSet` همچنین می‌تواند برای تعیین زمان بارگذاری تمام فونت‌های مورد نیاز یک صفحه و تکمیل طرح‌بندی سند استفاده شود.

ویژگی {{domxref('FontFace.status')}} وضعیت بارگذاری چهره فونت را نشان می‌دهد: `unloaded` (بارگیری نشده)، `loading` (در حال بارگیری)، `loaded` (بارگیری شده) یا `failed` (ناموفق). این وضعیت در ابتدا `unloaded` است. هنگامی که فایل در حال بارگیری است یا داده‌های فونت در حال پردازش هستند، روی `loading` تنظیم می‌شود و اگر تعریف فونت نامعتبر باشد یا داده‌های فونت قابل بارگیری نباشند، روی `failed` تنظیم می‌شود. وقتی داده‌های چهره فونت با موفقیت (در صورت نیاز) واکشی و بارگیری شدند، وضعیت روی `loaded` تنظیم می‌شود.

### تعریف یک چهره فونت

چهره‌های فونت با استفاده از [سازنده `FontFace`](/en-US/docs/Web/API/FontFace/FontFace) ایجاد می‌شوند که پارامترهای زیر را می‌گیرد: خانواده فونت، منبع فونت و توصیف‌گرهای اختیاری. قالب و دستور زبان این آرگومان‌ها با تعریف معادل {{cssxref("@font-face")}} یکسان است.

منبع فونت می‌تواند یا داده‌های باینری در یک [`ArrayBuffer`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer) باشد یا یک منبع فونت در یک URL. یک تعریف معمولی از چهره فونت با استفاده از منبع URL ممکن است مانند زیر باشد. توجه داشته باشید که تابع `url()` برای منابع فونت URL ضروری است.

```js
const font = new FontFace("my-font", 'url("my-font.woff")', {
  style: "italic",
  weight: "400",
  stretch: "condensed",
});
```

> [!NOTE]
> مانند `@font-face`، برخی از توصیف‌گرها نشان‌دهنده داده‌های مورد انتظار در داده‌های فونت هستند و برای تطبیق فونت استفاده می‌شوند، در حالی که برخی دیگر در واقع ویژگی‌های چهره فونت تولید شده را تنظیم/تعریف می‌کنند.
> برای مثال، تنظیم `style` به "italic" نشان می‌دهد که فایل حاوی فونت‌های ایتالیک است؛ این به عهده نویسنده است که فایلی را مشخص کند که این موضوع برای آن صادق باشد.

چهره‌های فونت با _منبع باینری_ به‌طور خودکار بارگیری می‌شوند اگر تعریف فونت معتبر باشد و داده‌های فونت قابل بارگیری باشند — {{domxref('FontFace.status')}} در صورت موفقیت روی `loaded` و در غیر این صورت روی `failed` تنظیم می‌شود.
چهره‌های فونت با منبع URL اعتبارسنجی می‌شوند اما به‌طور خودکار بارگیری نمی‌شوند — اگر تعریف چهره فونت معتبر باشد {{domxref('FontFace.status')}} روی `unloaded` و در غیر این صورت روی `failed` تنظیم می‌شود.

### افزودن فونت به یک سند یا worker

چهره‌های فونت معمولاً به {{domxref('FontFaceSet')}} سند یا worker اضافه می‌شوند تا به عامل کاربر اجازه دهند در صورت نیاز به‌طور خودکار فونت را بارگیری کند، و _باید_ اضافه شوند تا فونت برای رندر کردن متن استفاده شود.

کد زیر نشان می‌دهد که یک چهره فونت به سند اضافه می‌شود.

```js
// تعریف یک FontFace
const font = new FontFace("my-font", 'url("my-font.woff")', {
  style: "italic",
  weight: "400",
  stretch: "condensed",
});

// اضافه کردن به document.fonts (FontFaceSet)
document.fonts.add(font);
```

### بارگذاری یک فونت

یک چهره فونت را می‌توان به صورت دستی با فراخوانی {{domxref('FontFace.load()')}} یا با فراخوانی {{domxref('FontFaceSet.load()')}} در صورتی که چهره فونت به `FontFaceSet` اضافه شده باشد، بارگیری کرد. توجه داشته باشید که تلاش برای بارگیری یک فونت از قبل بارگیری شده تأثیری ندارد.

کد زیر نحوه تعریف یک چهره فونت، اضافه کردن آن به فونت‌های سند و سپس شروع بارگیری فونت را نشان می‌دهد.

```js
// تعریف یک FontFace
const font = new FontFace("my-font", 'url("my-font.woff")');

// اضافه کردن به document.fonts (FontFaceSet)
document.fonts.add(font);

// بارگیری فونت
font.load();

// منتظر ماندن تا همه فونت‌ها بارگیری شوند
document.fonts.ready.then(() => {
  // استفاده از فونت برای رندر متن (مثلاً در یک canvas)
});
```

توجه داشته باشید که `font.load()` یک promise برمی‌گرداند، بنابراین می‌توانستیم با زنجیره کردن `then` بعد از آن، تکمیل بارگیری فونت را مدیریت کنیم. استفاده از [`document.fonts.ready`](/en-US/docs/Web/API/FontFaceSet/ready) در برخی موارد می‌تواند بهتر باشد، زیرا فقط زمانی فراخوانی می‌شود که تمام فونت‌های موجود در سند تعیین تکلیف شده و طرح‌بندی کامل شده است.

## رابط‌ها

- {{domxref('FontFace')}}
  - : نشان‌دهنده یک چهره فونت قابل استفاده واحد است.
- {{domxref('FontFaceSet')}}
  - : یک رابط برای بارگیری چهره‌های فونت و بررسی وضعیت بارگیری آن‌ها.
- {{domxref('FontFaceSetLoadEvent')}}
  - : هر زمان که یک {{domxref("FontFaceSet")}} بارگیری می‌کند، شلیک می‌شود.

## مثال‌ها

### بارگذاری اولیه فونت

این یک مثال بسیار ساده است که نشان می‌دهد یک فونت از Google Fonts بارگیری شده و برای کشیدن متن روی یک canvas استفاده می‌شود. مثال همچنین `status` را بلافاصله پس از ایجاد و پس از بارگیری ثبت می‌کند.

#### HTML

این کد یک canvas برای کشیدن و یک textarea برای ثبت (log) تعریف می‌کند.

```html
<canvas id="js-canvas"></canvas>
<textarea id="log" rows="3" cols="100"></textarea>
```

#### JavaScript

ابتدا عنصری که قرار است در آن ثبت کنیم و canvas که برای رندر متن با فونت بارگیری شده استفاده می‌شود را دریافت می‌کنیم.

```js
const log = document.getElementById("log");

const canvas = document.getElementById("js-canvas");
canvas.width = 650;
canvas.height = 75;
```

سپس یک `FontFace` تعریف می‌کنیم که منبع URL آن یک فونت Google است و آن را به `document.fonts` اضافه می‌کنیم. سپس وضعیت فونت را ثبت می‌کنیم که باید `unloaded` باشد.

```js
const bitterFontFace = new FontFace(
  "FontFamily Bitter",
  'url("https://fonts.gstatic.com/s/bitter/v7/HEpP8tJXlWaYHimsnXgfCOvvDin1pK8aKteLpeZ5c0A.woff2")',
);
document.fonts.add(bitterFontFace);
log.textContent += `Bitter font: ${bitterFontFace.status}\n`; // > Bitter font: unloaded
```

سپس متد {{domxref('FontFace.load()')}} را برای بارگیری چهره فونت فراخوانی می‌کنیم و منتظر promise برگشتی می‌مانیم. وقتی promise حل شد، وضعیت بارگیری شده (که باید `loaded` باشد) را ثبت می‌کنیم و متن را با فونت بارگیری شده روی canvas می‌کشیم.

```js
bitterFontFace.load().then(
  () => {
    log.textContent += `Bitter font: ${bitterFontFace.status}\n`; // > Bitter font: loaded

    const ctx = canvas.getContext("2d");
    ctx.font = '36px "FontFamily Bitter"';
    ctx.fillText("Bitter font loaded", 20, 50);
  },
  (err) => {
    console.error(err);
  },
);
```

توجه داشته باشید که می‌توانستیم روی promise برگشتی توسط ویژگی {{domxref('FontFace.loaded')}} یا روی {{domxref('FontFaceSet.ready')}} نیز منتظر بمانیم.

#### نتیجه

نتیجه در زیر نشان داده شده است. باید نام فونت کشیده شده روی canvas را با فونت بارگیری شده و یک log نشان‌دهنده وضعیت بارگیری قبل و بعد از بارگیری نشان دهد.

{{ EmbedLiveSample('Basic font loading', 700, 180) }}

### بارگذاری فونت با رویدادها

این مثال مشابه مثال قبلی است، با این تفاوت که از {{domxref('FontFaceSet.load()')}} برای بارگیری فونت استفاده می‌کند. همچنین نحوه گوش دادن به رویدادهای بارگیری فونت را نشان می‌دهد.

#### HTML

```html
<canvas id="js-canvas"></canvas>
<textarea id="log" rows="25" cols="100"></textarea>
```

#### JavaScript

کد زیر یک بافت canvas برای کشیدن متن تعریف می‌کند، یک چهره فونت تعریف می‌کند و آن را به مجموعه چهره‌های فونت سند اضافه می‌کند.

```js
const log = document.getElementById("log");

const canvas = document.getElementById("js-canvas");
canvas.width = 650;
canvas.height = 75;
const ctx = canvas.getContext("2d");

const oxygenFontFace = new FontFace(
  "FontFamily Oxygen",
  'url("https://fonts.gstatic.com/s/oxygen/v5/qBSyz106i5ud7wkBU-FrPevvDin1pK8aKteLpeZ5c0A.woff2")',
);
document.fonts.add(oxygenFontFace);
log.textContent += `Oxygen status: ${oxygenFontFace.status}\n`;
```

سپس از `load()` روی مجموعه چهره‌های فونت برای بارگیری فونت استفاده می‌کنیم و مشخص می‌کنیم کدام یک از فونت‌ها بارگیری شود. این متد یک {{jsxref("Promise")}} برمی‌گرداند. اگر promise حل شود، از فونت برای کشیدن متن استفاده می‌کنیم. اگر رد شود، خطا ثبت می‌شود.

```js
document.fonts.load("36px FontFamily Oxygen").then(
  (fonts) => {
    log.textContent += `Bitter font: ${fonts}\n`; // > Oxygen font: loaded
    log.textContent += `Bitter font: ${oxygenFontFace.status}\n`; // > Oxygen font: loaded
    ctx.font = '36px "FontFamily Oxygen"';
    ctx.fillText("Oxygen font loaded", 20, 50);
  },
  (err) => {
    console.error(err);
  },
);
```

به جای انتظار برای یک promise، می‌توانیم از رویدادها برای ردیابی عملیات بارگیری فونت استفاده کنیم. کد زیر به رویدادهای `loading` و `loadingerror` گوش می‌دهد و تعداد چهره‌های فونت را برای هر مورد ثبت می‌کند. در شنونده رویداد `loadingdone`، علاوه بر این، از میان چهره‌های فونت عبور کرده و نام خانواده‌ها را ثبت می‌کنیم.

```js
document.fonts.addEventListener("loading", (event) => {
  log.textContent += `loading_event: ${event.fontfaces.length}\n`;
});
document.fonts.addEventListener("loadingerror", (event) => {
  log.textContent += `loadingerror_event: ${event.fontfaces.length}\n`;
});
document.fonts.addEventListener("loadingdone", (event) => {
  log.textContent += `loadingdone_event: ${event.fontfaces.length}\n`;
  event.fontfaces.forEach((value) => {
    log.textContent += `  fontface: ${value.family}\n`;
  });
});
```

آخرین بخش کد نحوه نظارت بر تکمیل بارگیری فونت را با استفاده از promise برگشتی توسط {{domxref('FontFaceSet.ready')}} نشان می‌دهد. برخلاف مکانیزم‌های دیگر، این زمانی برمی‌گردد که تمام فونت‌های تعریف شده در سند بارگیری شده و طرح‌بندی کامل شده است.

وقتی promise حل شد، از میان مقادیر موجود در چهره‌های فونت سند عبور می‌کنیم.

```js
document.fonts.ready.then(() => {
  log.textContent += `\nFontFaces in document: ${document.fonts.size}.\n`;

  for (const fontFace of document.fonts.values()) {
    log.textContent += "FontFace:\n";
    for (const property in fontFace) {
      log.textContent += `  ${property}: ${fontFace[property]}\n`;
    }
  }
});
```

#### نتیجه

خروجی زیر متن کشیده شده با فونت «Oxygen» را نشان می‌دهد. همچنین ثبت از رویدادها و زمانی که promise برگشتی توسط `document.fonts.ready` حل می‌شود را نشان می‌دهد.

{{ EmbedLiveSample('Font loading with events', 700, 520) }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}