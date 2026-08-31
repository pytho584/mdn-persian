---
title: Using the CSS Painting API
slug: Web/API/CSS_Painting_API/Guide
page-type: guide
---

{{DefaultAPISidebar("CSS Painting API")}}

[CSS Paint API](/en-US/docs/Web/API/CSS_Painting_API) برای این طراحی شده است که به توسعه‌دهندگان امکان دهد تصاویر را به‌صورت برنامه‌نویسی تعریف کنند و سپس از آن‌ها در هر جایی که یک تصویر CSS قابل استفاده است، مانند {{cssxref("background-image")}}، {{cssxref("border-image")}}، {{cssxref("mask-image")}} و غیره، استفاده کنند.

برای ایجاد برنامه‌نویسی یک تصویر که توسط استایل‌شیت CSS استفاده می‌شود، باید چند مرحله را طی کنیم:

1. تعریف یک paint worklet با استفاده از تابع {{domxref('PaintWorkletGlobalScope.registerPaint', 'registerPaint()')}}
2. ثبت کردن worklet
3. استفاده از تابع CSS {{cssxref('image/paint', 'paint()')}}

برای شرح بیشتر این مراحل، با ایجاد یک پس‌زمینه نیمه‌رنگ‌شده شروع می‌کنیم، مانند این سربرگ:

![متنی با عنوان 'My Cool Header' با یک بلوک تصویر پس‌زمینه زرد یکدست در دو سوم پایین سمت چپ سربرگ](mycoolheader.png)

> [!NOTE]
> برای یک نمونه کار کامل به [CSS Painting API Example](https://mdn.github.io/dom-examples/css-painting/) مراجعه کنید و همچنین [کد منبع](https://github.com/mdn/dom-examples/tree/main/css-painting).

## پینت ورک‌لت CSS

در یک فایل اسکریپت خارجی، از تابع {{domxref('PaintWorkletGlobalScope.registerPaint', 'registerPaint()')}} برای نام‌گذاری [CSS Paint worklet](/en-US/docs/Web/API/Worklet) خود استفاده می‌کنیم. این تابع دو پارامتر می‌گیرد. پارامتر اول نامی است که به worklet می‌دهیم — این همان نامی است که در CSS خود به عنوان پارامتر تابع `paint()` استفاده خواهیم کرد، زمانی که بخواهیم این استایل را روی یک عنصر اعمال کنیم. پارامتر دوم کلاسی است که همه کارها را انجام می‌دهد؛ این کلاس گزینه‌های زمینه را تعریف می‌کند و مشخص می‌کند چه چیزی روی بوم دوبعدی ترسیم شود که تصویر ما خواهد بود.

```js
registerPaint(
  "header-highlight",
  class {
    /*
     * define if alpha transparency is allowed alpha
     * is set to true by default. If set to false, all
     * colors used on the canvas will be fully opaque
     */
    static get contextOptions() {
      return { alpha: true };
    }

    /*
     * ctx is the 2D drawing context
     * a subset of the HTML Canvas API.
     */
    paint(ctx) {
      ctx.fillStyle = "hsl(55 90% 60% / 100%)";
      ctx.fillRect(0, 15, 200, 20); /* order: x, y, w, h */
    }
  },
);
```

در این مثال کلاسی، ما یک گزینه زمینه را با تابع `contextOptions()` تعریف کرده‌ایم: یک شیء برمی‌گردانیم که بیان می‌کند شفافیت آلفا مجاز است.

سپس از تابع `paint()` برای نقاشی روی بوم استفاده کرده‌ایم.

تابع `paint()` می‌تواند سه آرگومان بگیرد. در اینجا یک آرگومان ارائه داده‌ایم: زمینه رندر (که بعداً بیشتر به آن می‌پردازیم)، که معمولاً با نام متغیر `ctx` به آن اشاره می‌شود. زمینه رندر دوبعدی زیرمجموعه‌ای از [HTML Canvas API](/en-US/docs/Web/API/Canvas_API) است؛ نسخه‌ای که در اختیار Houdini قرار می‌گیرد (به نام `PaintRenderingContext2D`) زیرمجموعه دیگری است که شامل بیشتر ویژگی‌های موجود در Canvas API کامل است، به‌جز [APIهای](https://drafts.css-houdini.org/css-paint-api-1/#2d-rendering-context) `CanvasImageData`، `CanvasUserInterface`، `CanvasText` و `CanvasTextDrawingStyles`.

ما {{domxref('CanvasRenderingContext2D.fillStyle', 'fillStyle')}} را برابر با `hsl(55 90% 60% / 100%)` تعریف می‌کنیم که سایه‌ای از زرد است و سپس `fillRect()` را برای ایجاد یک مستطیل با آن رنگ فراخوانی می‌کنیم. پارامترهای {{domxref('CanvasRenderingContext2D.fillRect', 'fillRect()')}} به ترتیب عبارتند از: مبدأ محور x، مبدأ محور y، عرض و ارتفاع. `fillRect(0, 15, 200, 20)` منجر به ایجاد یک مستطیل به عرض ۲۰۰ واحد و ارتفاع ۲۰ واحد می‌شود که ۰ واحد از چپ و ۱۵ واحد از بالای جعبه محتوا قرار گرفته است.

ما می‌توانیم از ویژگی‌های CSS {{cssxref("background-size")}} و {{cssxref("background-position")}} برای تغییر اندازه یا جابه‌جایی این تصویر پس‌زمینه استفاده کنیم، اما این اندازه و مکان پیش‌فرض جعبه زردی است که در paint worklet خود ایجاد کرده‌ایم.

ما سعی کردیم مثال را ساده نگه داریم. برای گزینه‌های بیشتر، به مستندات {{HTMLElement("canvas")}} مراجعه کنید. همچنین کمی پیچیدگی را در ادامه این آموزش اضافه می‌کنیم.

## ثبت کردن ورک‌لت

برای استفاده از paint worklet، باید آن را با استفاده از {{domxref('Worklet.addModule', 'addModule()')}} ثبت کنیم و در CSS خود شامل کنیم و مطمئن شویم که انتخابگر CSS با یک گره DOM در HTML ما مطابقت دارد.

راه‌اندازی و طراحی paint worklet ما در اسکریپت خارجی نشان داده‌شده در بالا انجام شد. باید آن {{domxref('worklet')}} را از اسکریپت اصلی خود ثبت کنیم.

```js
CSS.paintWorklet.addModule("nameOfPaintWorkletFile.js");
```

این کار را می‌توان با استفاده از متد `addModule()` پینت ورک‌لت در یک `<script>` در HTML اصلی یا در یک فایل جاوااسکریپت خارجی که به سند لینک شده است، انجام داد.

## استفاده از پینت ورک‌لت

در مثال ما، پینت ورک‌لت در کنار فایل اسکریپت اصلی ذخیره شده است. برای استفاده از آن، ابتدا آن را ثبت می‌کنیم:

```js
CSS.paintWorklet.addModule("header-highlight.js");
```

### ارجاع به پینت ورک‌لت در CSS

هنگامی که یک پینت ورک‌لت ثبت‌شده داشته باشیم، می‌توانیم از آن در CSS استفاده کنیم. تابع CSS `paint()` را مانند هر نوع `<image>` دیگری به کار ببرید، با استفاده از همان شناسه متنی که در تابع `registerPaint()` پینت ورک‌لت استفاده کرده‌ایم.

```css
.fancy {
  background-image: paint(header-highlight);
}
```

### کنار هم قرار دادن

سپس می‌توانیم کلاس `fancy` را به هر عنصری در صفحه اضافه کنیم تا یک جعبه زرد به عنوان پس‌زمینه داشته باشیم:

```html
<h1 class="fancy">My Cool Header</h1>
```

مثال زیر در [مرورگرهایی که از CSS Painting API پشتیبانی می‌کنند](/en-US/docs/Web/API/CSS/paintWorklet_static#browser_compatibility) مانند تصویر بالا به نظر می‌رسد.

{{EmbedGHLiveSample("dom-examples/css-painting/half-highlight-fixed-size/", 120, 120)}}

اگرچه نمی‌توانید با اسکریپت ورک‌لت بازی کنید، می‌توانید `background-size` و `background-position` را تغییر دهید تا اندازه و مکان تصویر پس‌زمینه تغییر کند.

## PaintSize

در مثال بالا، یک جعبه ۲۰×۲۰۰ واحد ایجاد کردیم که ۱۵ واحد از بالای عنصر رنگ شده است؛ این مقدار صرف‌نظر از اندازه عنصر ثابت است. اگر متن کوچک باشد، جعبه زرد مانند یک زیرخط بزرگ به نظر می‌رسد. اگر متن بزرگ باشد، ممکن است جعبه مانند یک نوار بالای سه حرف اول به نظر برسد. بهتر بود اگر تصویر پس‌زمینه نسبت به اندازه عنصر باشد — می‌توانیم از ویژگی `paintSize` عنصر استفاده کنیم تا مطمئن شویم تصویر پس‌زمینه متناسب با اندازه جعبه مدل عنصر است.

![پس‌زمینه ۵۰٪ ارتفاع و ۶۰٪ عرض عنصر است](mycoolheadersized.png)

در تصویر بالا، پس‌زمینه متناسب با اندازه عنصر است. مثال سوم دارای `width: 50%` بر روی عنصر سطح بلوک است که عنصر را باریک‌تر و در نتیجه تصویر پس‌زمینه را باریک‌تر می‌کند.

### پینت ورک‌لت

کدی که این کار را انجام می‌دهد به این صورت است:

```js
registerPaint(
  "header-highlight",
  class {
    static get contextOptions() {
      return { alpha: true };
    }

    /*
     * ctx is the 2D drawing context
     * size is the paintSize, the dimensions (height and width) of the box being painted
     */
    paint(ctx, size) {
      ctx.fillStyle = "hsl(55 90% 60% / 100%)";
      ctx.fillRect(0, size.height / 3, size.width * 0.4, size.height * 0.6);
    }
  },
);
```

این مثال کد دو تفاوت با مثال اول ما دارد:

1. ما یک آرگومان دوم اضافه کرده‌ایم که اندازه نقاشی است.
2. ابعاد و موقعیت مستطیل خود را به‌جای مقادیر مطلق، نسبت به اندازه جعبه عنصر تغییر داده‌ایم.

می‌توانیم پارامتر دوم را به تابع `paint()` منتقل کنیم تا از طریق ویژگی‌های `.width` و `.height` به عرض و ارتفاع عنصر دسترسی داشته باشیم.

اکنون سربرگ ما یک برجسته‌سازی دارد که با توجه به اندازه آن تغییر می‌کند.

### استفاده از پینت ورک‌لت

#### HTML

```html
<h1 class="fancy">Largest Header</h1>
<h6 class="fancy">Smallest Header</h6>
<h3 class="fancy half">50% width header</h3>
```

#### CSS

اگرچه نمی‌توانید با اسکریپت ورک‌لت بازی کنید، می‌توانید `font-size` و `width` عنصر را تغییر دهید تا اندازه تصویر پس‌زمینه تغییر کند.

```css
.fancy {
  background-image: paint(header-highlight);
}
.half {
  width: 50%;
}
```

#### JavaScript

```js
CSS.paintWorklet.addModule("header-highlight.js");
```

#### نتیجه

در [مرورگرهایی که از CSS Paint API پشتیبانی می‌کنند](/en-US/docs/Web/API/CSS/paintWorklet_static#browser_compatibility)، عناصر موجود در مثال زیر باید پس‌زمینه‌های زرد متناسب با اندازه فونت خود دریافت کنند.

{{EmbedGHLiveSample("dom-examples/css-painting/half-highlight-paintsize", 200, 200)}}

## ویژگی‌های سفارشی

علاوه بر دسترسی به اندازه عنصر، ورک‌لت می‌تواند به ویژگی‌های سفارشی CSS و ویژگی‌های معمول CSS نیز دسترسی داشته باشد.

```js
registerPaint(
  "cssPaintFunctionName",
  class {
    static get inputProperties() {
      return ["PropertyName1", "--customPropertyName2"];
    }
    static get inputArguments() {
      return ["<color>"];
    }
    static get contextOptions() {
      return { alpha: true };
    }

    paint(drawingContext, elementSize, styleMap) {
      // Paint code goes here.
    }
  },
);
```

سه پارامتر تابع `paint()` شامل زمینه ترسیم، اندازه نقاشی و ویژگی‌ها است. برای دسترسی به ویژگی‌ها، متد استاتیک `inputProperties()` را وارد می‌کنیم که دسترسی زنده به ویژگی‌های CSS، از جمله ویژگی‌های معمول و [ویژگی‌های سفارشی](/en-US/docs/Web/CSS/Guides/Cascading_variables) را فراهم می‌کند و یک {{jsxref("Array", "آرایه", "", 1)}} از نام ویژگی‌ها برمی‌گرداند. در بخش آخر به [`inputArguments`](#passing_parameters) نگاهی خواهیم انداخت.

بیایید یک لیست از موارد با تصویر پس‌زمینه ایجاد کنیم که بین سه رنگ و سه عرض مختلف چرخش می‌کند.

![عرض و رنگ تصویر پس‌زمینه بر اساس ویژگی‌های سفارشی تغییر می‌کند](boxbg.png)

برای این کار، دو ویژگی سفارشی CSS تعریف می‌کنیم: `--box-color` و `--width-subtractor`.

### پینت ورک‌لت

در ورک‌لت خود، می‌توانیم به این ویژگی‌های سفارشی ارجاع دهیم.

```js
registerPaint(
  "boxbg",
  class {
    static get contextOptions() {
      return { alpha: true };
    }

    /*
     * use this function to retrieve any custom properties (or regular properties, such as 'height')
     * defined for the element, return them in the specified array
     */
    static get inputProperties() {
      return ["--box-color", "--width-subtractor"];
    }

    paint(ctx, size, props) {
      /*
       * ctx -> drawing context
       * size -> paintSize: width and height
       * props -> properties: get() method
       */
      ctx.fillStyle = props.get("--box-color");
      ctx.fillRect(
        0,
        size.height / 3,
        size.width * 0.4 - props.get("--width-subtractor"),
        size.height * 0.6,
      );
    }
  },
);
```

ما از متد `inputProperties()` در کلاس `registerPaint()` استفاده کردیم تا مقادیر دو ویژگی سفارشی تعیین‌شده روی عنصری که `boxbg` به آن اعمال شده است را بگیریم و سپس از آن‌ها در تابع `paint()` استفاده کنیم. متد `inputProperties()` می‌تواند همه ویژگی‌های تأثیرگذار بر عنصر را برگرداند، نه فقط ویژگی‌های سفارشی را.

### استفاده از پینت ورک‌لت

#### HTML

```html
<ul>
  <li>item 1</li>
  <li>item 2</li>
  <li>item 3</li>
  <li>item 4</li>
  <li>item 5</li>
  <li>item 6</li>
  <li>item 7</li>
  <li>item 8</li>
  <li>item 9</li>
  <li>item 10</li>
  <li>item 11</li>
  <li>item 12</li>
  <li>item 13</li>
  <li>item 14</li>
  <li>item 15</li>
  <li>item 16</li>
  <li>item 17</li>
  <li>item</li>
</ul>
```

#### CSS

در CSS خود، ویژگی‌های سفارشی `--box-color` و `--width-subtractor` را تعریف می‌کنیم.

```css
li {
  background-image: paint(boxbg);
  --box-color: hsl(55 90% 60% / 100%);
}

li:nth-of-type(3n) {
  --box-color: hsl(155 90% 60% / 100%);
  --width-subtractor: 20;
}

li:nth-of-type(3n + 1) {
  --box-color: hsl(255 90% 60% / 100%);
  --width-subtractor: 40;
}
```

#### JavaScript

در `<script>` خود ورک‌لت را ثبت می‌کنیم:

```js
CSS.paintWorklet.addModule("boxbg.js");
```

#### نتیجه

اگرچه نمی‌توانید با اسکریپت ورک‌لت بازی کنید، می‌توانید مقادیر ویژگی سفارشی را در DevTools تغییر دهید تا رنگ‌ها و عرض تصویر پس‌زمینه تغییر کند.

{{EmbedGHLiveSample("dom-examples/css-painting/custom-properties/", '100%', 400)}}

## افزودن پیچیدگی

مثال‌های بالا شاید چندان هیجان‌انگیز به نظر نرسند، زیرا می‌توانید آن‌ها را به چند روش مختلف با ویژگی‌های CSS موجود بازآفرینی