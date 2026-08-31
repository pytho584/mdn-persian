---
title: "CanvasRenderingContext2D: lang property"
---

---
title: "CanvasRenderingContext2D: lang property"
short-title: lang
slug: Web/API/CanvasRenderingContext2D/lang
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.lang
---

{{APIRef("Canvas API")}}

ویژگی **`CanvasRenderingContext2D.lang`** از Canvas 2D API، زبانِ بافت ترسیم canvas را دریافت یا تنظیم می‌کند.

## مقدار

ویژگی `lang` می‌تواند یکی از مقادیر رشته‌ای زیر را بگیرد:

- یک {{glossary("BCP 47 language tag")}} که زبان بافت canvas را نشان می‌دهد.
- رشتهٔ `inherit`، که در این حالت زبان از ویژگی [`lang`](/en-US/docs/Web/HTML/Reference/Global_attributes/lang) عنصرِ مبدأ {{HTMLElement("canvas")}} یا نزدیک‌ترین جدِ در دسترس که `lang` صریح تنظیم شده است به ارث برده می‌شود.
- یک رشتهٔ خالی (`""`) که می‌توان آن را تنظیم کرد تا مشخص شود بافت canvas زبانی ندارد.

مقدار پیش‌فرض `inherit` است.

## توضیحات

گاهی لازم است برای یک بافت رندر canvas زبانی تعیین کنید تا بداند ویژگی‌های وابسته به زبان را چگونه رندر کند؛ برای مثال، در برخی قلم‌ها، برخی نویسه‌ها در زبان‌های مختلف به شکل متفاوتی رندر می‌شوند.

یک بافت canvas روی‌صفحه (`CanvasRenderingContext2D`) همیشه با یک عنصر `<canvas>` مشخص مرتبط است؛ بنابراین هر زمان که با آن محتوایی رندر می‌کنید، می‌تواند زبان را از مقدار ویژگی `lang` عنصر `<canvas>` به دست آورد.

با این حال، یک بافت canvas خارج از صفحه ({{domxref("OffscreenCanvasRenderingContext2D")}}) محتوای خود را پیش از آنکه با یک عنصر `<canvas>` مرتبط شود رندر می‌کند؛ بنابراین نمی‌تواند زبان رندر را از ویژگی `lang` عنصر `<canvas>` به دست آورد.

ویژگی `lang` این مشکل را برطرف می‌کند و به شما امکان می‌دهد زبانی را مستقیماً روی یک بافت رندر canvas تنظیم کنید؛ چه از canvas روی‌صفحه استفاده کنید و چه از canvas خارج از صفحه.

### مقدار `inherit`

وقتی مقدار `inherit` استفاده شود، زبان بافت canvas از ویژگی [`lang`](/en-US/docs/Web/HTML/Reference/Global_attributes/lang) نزدیک‌ترین منبع HTML در دسترس به ارث برده می‌شود:

- در مورد یک بافت روی‌صفحه، یا یک بافت خارج از صفحه که از یک بافت روی‌صفحه منتقل شده است، این منبع، عنصر مبدأ {{HTMLElement("canvas")}} خواهد بود، به شرط آنکه ویژگی `lang` معتبری روی آن تنظیم شده باشد.
- اگر ویژگی `lang` روی عنصر `<canvas>` مرتبط موجود نباشد (که ممکن است برای یک بافت روی‌صفحه یا خارج از صفحه رخ دهد)، این منبع، نزدیک‌ترین جد در دسترس با `lang` صریح خواهد بود که معمولاً ریشهٔ سند است.

به دلیل محدودیت‌های فنی، مقدار `inherit` برای canvasهای روی‌صفحه و خارج از صفحه رفتار متفاوتی دارد:

- برای canvasهای روی‌صفحه، مقدار `lang` بافت هنگام نخستین ایجاد شیء `CanvasRenderingContext2D` مرتبط به ارث برده می‌شود و اگر ویژگی `lang` canvas مرتبط به‌روزرسانی شود (چه مستقیم و چه از طریق ارث‌بری)، به‌صورت پویا به‌روزرسانی می‌شود.
- برای canvasهای خارج از صفحه، مقدار `lang` هنگام نخستین ایجاد شیء `OffscreenCanvasRenderingContext2D` مرتبط «به‌صورت یک snapshot» به ارث برده می‌شود؛ به‌روزرسانی‌های بعدی ویژگی `lang` که بافت خارج از صفحه مقدار خود را از آن به ارث برده است، ویژگی `lang` آن را تغییر نمی‌دهند.

  به همین دلیل، زبان یک canvas خارج از صفحه تنها با تنظیم صریح مقدار `lang` آن قابل تغییر است.

## مثال‌ها

### کاربرد پایه

```js
const canvasElem = document.querySelector("canvas");
const ctx = canvasElem.getContext("2d");

// Get context language; returns "inherit" by default
console.log(ctx.lang);

// Set context language
ctx.lang = "en";
// Logs "en"
console.log(ctx.lang);
```

### نمایش پشتیبانی از محلی‌سازی بافت canvas

در این مثال، یک رشتهٔ متنی را با قلمی خاص که لیگاتورهای وابسته به زبان دارد، روی یک بافت canvas دوبعدی رندر می‌کنیم. زبان بافت canvas را قابل تنظیم می‌کنیم تا بتوانید تفاوت رندر را ببینید.

#### HTML

HTML شامل یک عنصر {{htmlelement("select")}} است که به شما امکان می‌دهد زبانی را انتخاب کنید — `en` (انگلیسی) یا `tr` (ترکی) — و یک عنصر {{htmlelement("canvas")}} که متن روی آن رندر شود.

```html live-example___canvas-l10n
<p>
  <label for="lang">Choose language:</label>
  <select id="lang" name="lang">
    <option>en</option>
    <option>tr</option>
  </select>
</p>
<canvas></canvas>
```

#### جاوااسکریپت

در بخش جاوااسکریپت، ابتدا ارجاع‌هایی به عنصر `<canvas>`، به `CanvasRenderingContext2D` آن و به عنصر `<select>` می‌گیریم؛ سپس قلم وابسته به زبان را با استفاده از [CSS Font Loading API](/en-US/docs/Web/API/CSS_Font_Loading_API) بارگذاری می‌کنیم. پس از بارگذاری قلم، تابع `init()` را اجرا می‌کنیم. این تابع، تابع دیگری به نام `drawText()` تعریف می‌کند که با استفاده از قلم بارگذاری‌شده متنی را روی بافت canvas می‌کشد، یک [`change`](/en-US/docs/Web/API/HTMLElement/change_event) [event listener](/en-US/docs/Web/API/EventTarget/addEventListener) به عنصر `<select>` اضافه می‌کند و سپس `drawText()` را فراخوانی می‌کند تا متن هنگام نخستین بارگذاری صفحه بلافاصله روی canvas کشیده شود.

```js live-example___canvas-l10n
const canvasElem = document.querySelector("canvas");
const ctx = canvasElem.getContext("2d");

const selectElem = document.querySelector("select");

const latoMediumFontFace = new FontFace(
  // Lato-Medium is a font with language specific ligatures
  "Lato-Medium",
  'url("https://mdn.github.io/shared-assets/fonts/Lato-Medium.ttf")',
);

latoMediumFontFace.load().then((font) => {
  document.fonts.add(font);
  init();
});

function init() {
  function drawText() {
    ctx.clearRect(0, 0, canvasElem.width, canvasElem.height);
    ctx.font = "30px Lato-Medium";
    ctx.color = "black";
    ctx.fillText("finish crafting", 50, 100);
  }

  selectElem.addEventListener("change", () => {
    document.documentElement.lang = selectElem.value;
    drawText();
  });

  drawText();
}
```

وقتی مقدار `<select>` تغییر می‌کند، تابع مدیریت رویداد `change` اجرا می‌شود که:

- مقدار ویژگی [`lang`](/en-US/docs/Web/HTML/Reference/Global_attributes/lang) عنصر `<html>` را برابر با مقدار عنصر `<select>` قرار می‌دهد و عملاً زبان سند را تغییر می‌دهد.
- تابع `drawText()` را اجرا می‌کند. ویژگی `CanvasRenderingContext2D.lang` به‌طور پیش‌فرض روی `inherit` تنظیم است؛ بنابراین بافت canvas زبان سند را به ارث می‌برد.

#### نتیجه

مثال به صورت زیر رندر می‌شود:

{{ EmbedLiveSample('canvas-l10n', "100%", 220) }}

با استفاده از عنصر `<select>` زبان سند را تغییر دهید. وقتی زبان روی انگلیسی تنظیم شود، قلم با لیگاتور «fi» رندر می‌شود. با این حال، وقتی روی ترکی تنظیم شود، قلم بدون لیگاتور «fi» رندر می‌شود، زیرا آن locale شامل این لیگاتور نیست.

### پشتیبانی زبانی برای canvasهای خارج از صفحه

این مثال مشابه مثال قبلی است، با این تفاوت که قلم روی یک {{domxref("OffscreenCanvasRenderingContext2D")}} رندر می‌شود و سپس bitmap حاصل برای نمایش به `<canvas>` روی‌صفحه منتقل می‌شود.

علاوه بر این، از آنجا که زبانِ به‌ارث‌برده‌شدهٔ یک canvas خارج از صفحه فقط یک بار تنظیم می‌شود و اگر مقدار ویژگی `lang` ارث‌برده‌شده تغییر کند به‌صورت پویا به‌روزرسانی نمی‌شود، در عوض ویژگی `lang` را به‌صورت صریح روی `OffscreenCanvasRenderingContext2D` تنظیم می‌کنیم.

#### HTML

```html live-example___offscreen-l10n
<p>
  <label for="lang">Choose language:</label>
  <select id="lang" name="lang">
    <option>en</option>
    <option>tr</option>
  </select>
</p>
<canvas></canvas>
```

#### جاوااسکریپت

جاوااسکریپت این مثال همانند مثال قبلی کار می‌کند، با این تفاوت‌ها:

- بافت canvas روی‌صفحه به‌صورت یک {{domxref("ImageBitmapRenderingContext")}} تعریف شده است.
- یک `OffscreenCanvasRenderingContext2D` جدید تعریف می‌کنیم تا متن روی آن کشیده شود؛ نتیجه را با استفاده از {{domxref("OffscreenCanvas.transferToImageBitmap", "transferToImageBitmap()")}} به یک bitmap منتقل می‌کنیم و سپس آن را با استفاده از {{domxref("ImageBitmapRenderingContext.transferFromImageBitmap", "transferFromImageBitmap()")}} روی `<canvas>` رندر می‌کنیم.
- وقتی مقدار `<select>` تغییر می‌کند، به‌جای تغییر مقدار ویژگی `lang` عنصر `<html>`، ویژگی `lang` را مستقیماً روی `OffscreenCanvasRenderingContext2D` به‌روزرسانی می‌کنیم.

```js live-example___offscreen-l10n
const canvasElem = document.querySelector("canvas");
const ctx = canvasElem.getContext("bitmaprenderer");

const offscreen = new OffscreenCanvas(canvasElem.width, canvasElem.height);
const offscreenCtx = offscreen.getContext("2d");

const selectElem = document.querySelector("select");

const latoMediumFontFace = new FontFace(
  // Lato-Medium is a font with language specific ligatures.
  "Lato-Medium",
  'url("https://mdn.github.io/shared-assets/fonts/Lato-Medium.ttf")',
);

latoMediumFontFace.load().then((font) => {
  document.fonts.add(font);
  init();
});

function init() {
  function drawText() {
    offscreenCtx.clearRect(0, 0, canvasElem.width, canvasElem.height);
    offscreenCtx.lang = selectElem.value;
    offscreenCtx.font = "30px Lato-Medium";
    offscreenCtx.color = "black";
    offscreenCtx.fillText("finish crafting", 50, 100);

    const bitmap = offscreen.transferToImageBitmap();
    ctx.transferFromImageBitmap(bitmap);
  }

  selectElem.addEventListener("change", () => {
    drawText();
  });

  drawText();
}
```

#### نتیجه

مثال به صورت زیر رندر می‌شود:

{{ EmbedLiveSample('offscreen-l10n', "100%", 220) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## جستارهای وابسته

- {{domxref("CanvasRenderingContext2D")}}
- [Canvas Localization Support](https://blogs.igalia.com/schenney/canvas-localization-support/) از Igalia (۲۰۲۵)