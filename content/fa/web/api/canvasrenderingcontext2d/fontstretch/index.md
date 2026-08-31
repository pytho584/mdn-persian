---
title: "CanvasRenderingContext2D: fontStretch property"
short-title: fontStretch
slug: Web/API/CanvasRenderingContext2D/fontStretch
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.fontStretch
---

{{APIRef("Canvas API")}}

ویژگی **`CanvasRenderingContext2D.fontStretch`** از [Canvas API](/en-US/docs/Web/API/Canvas_API) مشخص می‌کند که هنگام ترسیم متن، قلم چگونه می‌تواند پهن‌تر یا فشرده‌تر شود.

این ویژگی معادل ویژگی CSS {{cssxref("font-stretch")}} در هنگام استفاده با کلیدواژه‌ها است (مقادیر درصدی پشتیبانی نمی‌شوند).

## مقدار

مقدار کشیدگی قلم به‌صورت یک رشته. این مقدار یکی از این‌هاست: `ultra-condensed`، `extra-condensed`، `condensed`، `semi-condensed`، `normal` (پیش‌فرض)، `semi-expanded`، `expanded`، `extra-expanded`، `ultra-expanded`.

از این ویژگی می‌توان برای خواندن یا تنظیم مقدار کشیدگی قلم استفاده کرد.

## مثال‌ها

در این مثال، متن «Hello World» را با تک‌تک مقادیر پشتیبانی‌شدهٔ ویژگی `fontStretch` نمایش می‌دهیم. همچنین مقدار کشیدگی در هر حالت با خواندن همان ویژگی نمایش داده می‌شود.

### HTML

```html
<canvas id="canvas" width="700" height="310"></canvas>
```

### JavaScript

ابتدا بوم (canvas) تعریف‌شده در فایل HTML را دریافت می‌کنیم و از آن برای به‌دست آوردن `CanvasRenderingContext2D` استفاده می‌کنیم که بعداً برای رسم متن به کار می‌رود.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
```

مرحلهٔ بعدی در این مثال، بارگذاری یک قلم متغیر (variable font) است که می‌توان آن را در محور عرض تغییر داد. این کار ضروری است زیرا `fontStretch` فقط می‌تواند قلمی را کشیده کند که اطلاعاتی دربارهٔ نحوهٔ ترسیم گلیف‌ها هنگام کشیدگی داشته باشد؛ در غیر این صورت، متن با نزدیک‌ترین مقدار کشیدگی موجود برای آن قلم رسم می‌شود که معمولاً عرض عادی است.

در اینجا از [`FontFace`](/en-US/docs/Web/API/FontFace) برای تعریف یک چهرهٔ قلم (font face) برای فونت Google [Inconsolata](https://fonts.google.com/specimen/Inconsolata/tester) استفاده می‌کنیم؛ فونتی که عرض‌های ۵۰٪ تا ۲۰۰٪ را پشتیبانی می‌کند (و به ما امکان می‌دهد مقادیر `fontStretch` از `ultra-condensed` تا `ultra-expanded` را نشان دهیم). سپس این قلم را به [`FontFaceSet`](/en-US/docs/Web/API/FontFaceSet) سند ([`document.fonts`](/en-US/docs/Web/API/Document/fonts)) اضافه می‌کنیم تا برای رسم قابل استفاده باشد.

```js
const fontFile = new FontFace(
  "Inconsolata",
  'url("https://fonts.gstatic.com/s/inconsolata/v31/QlddNThLqRwH-OJ1UHjlKENVzlm-WkL3GZQmAwPyya15.woff2") format("woff2")',
  { stretch: "50% 200%" },
);

document.fonts.add(fontFile);
```

کد زیر سپس [`FontFaceSet.load()`](/en-US/docs/Web/API/FontFaceSet/load) را برای دریافت و بارگذاری فونت Google فراخوانی می‌کند. توجه داشته باشید که این فراخوانی اندازهٔ قلم مورد نیاز را تعیین می‌کند و یک promise برمی‌گرداند که وقتی قلم بارگذاری شد، حل می‌شود.

سپس چهرهٔ قلم دانلودشده را به context نسبت می‌دهیم و از context برای رسم متن روی بوم در هر یک از سطوح کشیدگی کلیدواژه‌ای استفاده می‌کنیم. توجه داشته باشید که در اینجا نیز اندازهٔ قلم مورد نظر مشخص شده است (این اندازه لزوماً نباید با اندازهٔ قلم بارگذاری‌شده یکسان باشد).

```js
document.fonts.load("30px Inconsolata").then(
  () => {
    ctx.font = "30px 'Inconsolata'";
    // Default (normal)
    ctx.fillText(`Hello world (default: ${ctx.fontStretch})`, 5, 20);

    ctx.fontStretch = "ultra-condensed";
    ctx.fillText(`Hello world (${ctx.fontStretch})`, 5, 50);

    ctx.fontStretch = "extra-condensed";
    ctx.fillText(`Hello world (${ctx.fontStretch})`, 5, 80);

    ctx.fontStretch = "condensed";
    ctx.fillText(`Hello world (${ctx.fontStretch})`, 5, 110);

    ctx.fontStretch = "semi-condensed";
    ctx.fillText(`Hello world (${ctx.fontStretch})`, 5, 140);

    ctx.fontStretch = "extra-condensed";
    ctx.fillText(`Hello world (${ctx.fontStretch})`, 5, 170);

    ctx.fontStretch = "semi-expanded";
    ctx.fillText(`Hello world (${ctx.fontStretch})`, 5, 200);

    ctx.fontStretch = "expanded";
    ctx.fillText(`Hello world (${ctx.fontStretch})`, 5, 230);

    ctx.fontStretch = "extra-expanded";
    ctx.fillText(`Hello world (${ctx.fontStretch})`, 5, 260);

    ctx.fontStretch = "ultra-expanded";
    ctx.fillText(`Hello world (${ctx.fontStretch})`, 5, 290);
  },
  (err) => {
    console.error(err);
  },
);
```

### نتیجه

{{ EmbedLiveSample('Examples', 700, 300) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}