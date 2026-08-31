---
title: "Applying styles and colors"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors"
translated_by: "n8n + AI"
---

---
title: Applying styles and colors
slug: Web/API/Canvas_API/Tutorial/Applying_styles_and_colors
page-type: guide
---

{{DefaultAPISidebar("Canvas API")}} {{PreviousNext("Web/API/Canvas_API/Tutorial/Drawing_shapes", "Web/API/Canvas_API/Tutorial/Drawing_text")}}

در فصل [ترسیم اشکال](/en-US/docs/Web/API/Canvas_API/Tutorial/Drawing_shapes)، ما فقط از سبک‌های پیش‌فرض خط و پر استفاده کردیم. در اینجا گزینه‌های Canvas را که در اختیار داریم بررسی خواهیم کرد تا نقاشی‌های خود را کمی جذاب‌تر کنیم. شما یاد خواهید گرفت که چگونه رنگ‌ها، سبک‌های خط، گرادیان‌ها، الگوها و سایه‌های مختلف را به نقاشی‌های خود اضافه کنید.

> [!NOTE]
> محتوای Canvas برای صفحه‌خوان‌ها قابل دسترسی نیست. اگر Canvas صرفاً تزئینی است، `role="presentation"` را در تگ باز `<canvas>` قرار دهید. در غیر این صورت، متن توصیفی را به عنوان مقدار ویژگی [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) مستقیماً روی خود عنصر canvas قرار دهید یا محتوای جایگزین (fallback) را در بین تگ باز و بسته canvas قرار دهید. محتوای Canvas بخشی از DOM نیست، اما محتوای جایگزین تودرتو بخشی از DOM است.

## رنگ‌ها

تا کنون ما فقط روش‌های مربوط به بافت ترسیم (drawing context) را دیده‌ایم. اگر بخواهیم رنگ را به یک شکل اعمال کنیم، دو ویژگی مهم داریم که می‌توانیم از آن‌ها استفاده کنیم: `fillStyle` و `strokeStyle`.

- {{domxref("CanvasRenderingContext2D.fillStyle", "fillStyle = color")}}
  - : سبک مورد استفاده برای پر کردن اشکال را تنظیم می‌کند.
- {{domxref("CanvasRenderingContext2D.strokeStyle", "strokeStyle = color")}}
  - : سبک خطوط دور اشکال را تنظیم می‌کند.

`color` یک رشته است که یک {{cssxref("&lt;color&gt;")}} سی‌اس‌اس، شیء گرادیان یا شیء الگو را نشان می‌دهد. بعداً به اشیاء گرادیان و الگو خواهیم پرداخت. به‌طور پیش‌فرض، رنگ stroke و fill سیاه است (مقدار رنگ CSS `#000000`).

> [!NOTE]
> وقتی ویژگی `strokeStyle` و/یا `fillStyle` را تنظیم می‌کنید، مقدار جدید به پیش‌فرض برای همه اشکالی که از آن پس ترسیم می‌شوند تبدیل می‌شود. برای هر شکلی که می‌خواهید با رنگ متفاوتی باشد، باید ویژگی `fillStyle` یا `strokeStyle` را دوباره اختصاص دهید.

رشته‌های معتبری که می‌توانید وارد کنید، طبق مشخصات، باید مقادیر {{cssxref("&lt;color&gt;")}} سی‌اس‌اس باشند. هر یک از مثال‌های زیر همان رنگ را توصیف می‌کنند.

```js
// these all set the fillStyle to 'orange'

ctx.fillStyle = "orange";
ctx.fillStyle = "#FFA500";
ctx.fillStyle = "rgb(255 165 0)";
ctx.fillStyle = "rgb(255 165 0 / 100%)";
```

### مثالی از `fillStyle`

در این مثال، دوباره از دو حلقه `for` برای ترسیم یک شبکه از مستطیل‌ها استفاده می‌کنیم که هر کدام رنگ متفاوتی دارند. تصویر حاصل باید چیزی شبیه به اسکرین‌شات باشد. هیچ چیز خارق‌العاده‌ای در اینجا اتفاق نمی‌افتد. ما از دو متغیر `i` و `j` برای تولید یک رنگ RGB یکتا برای هر مربع استفاده می‌کنیم و فقط مقادیر قرمز و سبز را تغییر می‌دهیم. کانال آبی مقدار ثابتی دارد. با تغییر کانال‌ها، می‌توانید انواع پالت‌ها را تولید کنید. با افزایش گام‌ها، می‌توانید به چیزی برسید که شبیه پالت‌های رنگی است که فتوشاپ استفاده می‌کند.

```js
function draw() {
  const ctx = document.getElementById("canvas").getContext("2d");
  for (let i = 0; i < 6; i++) {
    for (let j = 0; j < 6; j++) {
      ctx.fillStyle = `rgb(${Math.floor(255 - 42.5 * i)} ${Math.floor(
        255 - 42.5 * j,
      )} 0)`;
      ctx.fillRect(j * 25, i * 25, 25, 25);
    }
  }
}
```

```html hidden
<canvas id="canvas" width="150" height="150"
  >A 6 by 6 square grid displaying 36 different colors</canvas
>
```

```js hidden
draw();
```

نتیجه به این شکل است:

{{EmbedLiveSample("A_fillStyle_example", "", "160")}}

### مثالی از `strokeStyle`

این مثال مشابه مثال بالا است، اما از ویژگی `strokeStyle` برای تغییر رنگ خطوط دور اشکال استفاده می‌کند. ما از متد `arc()` برای ترسیم دایره‌ها به جای مربع‌ها استفاده می‌کنیم.

```js
function draw() {
  const ctx = document.getElementById("canvas").getContext("2d");
  for (let i = 0; i < 6; i++) {
    for (let j = 0; j < 6; j++) {
      ctx.strokeStyle = `rgb(0 ${Math.floor(255 - 42.5 * i)} ${Math.floor(
        255 - 42.5 * j,
      )})`;
      ctx.beginPath();
      ctx.arc(12.5 + j * 25, 12.5 + i * 25, 10, 0, 2 * Math.PI, true);
      ctx.stroke();
    }
  }
}
```

```html hidden
<canvas id="canvas" width="150" height="150" role="presentation"></canvas>
```

```js hidden
draw();
```

نتیجه به این شکل است:

{{EmbedLiveSample("A_strokeStyle_example", "", "160")}}

## شفافیت

علاوه بر ترسیم اشکال مات روی Canvas، می‌توانیم اشکال نیمه‌شفاف (یا شفاف) نیز ترسیم کنیم. این کار یا با تنظیم ویژگی `globalAlpha` یا با اختصاص یک رنگ نیمه‌شفاف به سبک stroke و/یا fill انجام می‌شود.

- {{domxref("CanvasRenderingContext2D.globalAlpha", "globalAlpha = transparencyValue")}}
  - : مقدار شفافیت مشخص‌شده را برای همه اشکال آینده که روی canvas ترسیم می‌شوند اعمال می‌کند. مقدار باید بین 0.0 (کاملاً شفاف) تا 1.0 (کاملاً مات) باشد. این مقدار به‌طور پیش‌فرض 1.0 (کاملاً مات) است.

ویژگی `globalAlpha` می‌تواند مفید باشد اگر بخواهید تعداد زیادی شکل روی canvas با شفافیت مشابه ترسیم کنید، اما در غیر این صورت معمولاً مفیدتر است که شفافیت را هنگام تنظیم رنگ‌ها روی اشکال جداگانه تنظیم کنید.

از آنجا که ویژگی‌های `strokeStyle` و `fillStyle` مقادیر رنگ rgb سی‌اس‌اس را می‌پذیرند، می‌توانیم از نماد زیر برای اختصاص یک رنگ شفاف به آن‌ها استفاده کنیم.

```js
// Assigning transparent colors to stroke and fill style

ctx.strokeStyle = "rgb(255 0 0 / 50%)";
ctx.fillStyle = "rgb(255 0 0 / 50%)";
```

تابع `rgb()` یک پارامتر اضافی اختیاری دارد. آخرین پارامتر مقدار شفافیت این رنگ خاص را تنظیم می‌کند. محدوده معتبر به صورت درصدی بین `0%` (کاملاً شفاف) و `100%` (کاملاً مات) یا به صورت عددی بین `0.0` (معادل `0%`) و `1.0` (معادل `100%`) مشخص می‌شود.

### مثالی از `globalAlpha`

در این مثال، پس‌زمینه‌ای از چهار مربع با رنگ‌های مختلف ترسیم می‌کنیم. روی این‌ها، مجموعه‌ای از دایره‌های نیمه‌شفاف ترسیم می‌کنیم. ویژگی `globalAlpha` روی `0.2` تنظیم شده است که از آن پس برای همه اشکال استفاده خواهد شد. هر گام در حلقه `for` مجموعه‌ای از دایره‌ها را با شعاع فزاینده ترسیم می‌کند. نتیجه نهایی یک گرادیان شعاعی است. با روی هم قرار دادن دایره‌های بیشتر، عملاً شفافیت دایره‌هایی را که قبلاً ترسیم شده‌اند کاهش می‌دهیم. با افزایش تعداد گام‌ها و در نتیجه ترسیم دایره‌های بیشتر، پس‌زمینه از مرکز تصویر کاملاً محو می‌شود.

```js
function draw() {
  const ctx = document.getElementById("canvas").getContext("2d");
  // draw background
  ctx.fillStyle = "#ffdd00";
  ctx.fillRect(0, 0, 75, 75);
  ctx.fillStyle = "#66cc00";
  ctx.fillRect(75, 0, 75, 75);
  ctx.fillStyle = "#0099ff";
  ctx.fillRect(0, 75, 75, 75);
  ctx.fillStyle = "#ff3300";
  ctx.fillRect(75, 75, 75, 75);
  ctx.fillStyle = "white";

  // set transparency value
  ctx.globalAlpha = 0.2;

  // Draw semi transparent circles
  for (let i = 0; i < 7; i++) {
    ctx.beginPath();
    ctx.arc(75, 75, 10 + 10 * i, 0, Math.PI * 2, true);
    ctx.fill();
  }
}
```

```html hidden
<canvas id="canvas" width="150" height="150" role="presentation"></canvas>
```

```js hidden
draw();
```

{{EmbedLiveSample("A_globalAlpha_example", "", "160")}}

### مثالی با استفاده از `rgb()` با شفافیت alpha

در این مثال دوم، کاری شبیه به مثال بالا انجام می‌دهیم، اما به جای ترسیم دایره‌ها روی هم، مستطیل‌های کوچکی با تیرگی (opacity) فزاینده ترسیم کرده‌ام. استفاده از `rgb()` کنترل و انعطاف‌پذیری بیشتری به شما می‌دهد، زیرا می‌توانیم سبک fill و stroke را به صورت جداگانه تنظیم کنیم.

```js
function draw() {
  const ctx = document.getElementById("canvas").getContext("2d");

  // Draw background
  ctx.fillStyle = "rgb(255 221 0)";
  ctx.fillRect(0, 0, 150, 37.5);
  ctx.fillStyle = "rgb(102 204 0)";
  ctx.fillRect(0, 37.5, 150, 37.5);
  ctx.fillStyle = "rgb(0 153 255)";
  ctx.fillRect(0, 75, 150, 37.5);
  ctx.fillStyle = "rgb(255 51 0)";
  ctx.fillRect(0, 112.5, 150, 37.5);

  // Draw semi transparent rectangles
  for (let i = 0; i < 10; i++) {
    ctx.fillStyle = `rgb(255 255 255 / ${(i + 1) / 10})`;
    for (let j = 0; j < 4; j++) {
      ctx.fillRect(5 + i * 14, 5 + j * 37.5, 14, 27.5);
    }
  }
}
```

```html hidden
<canvas id="canvas" width="150" height="150" role="presentation"></canvas>
```

```js hidden
draw();
```

{{EmbedLiveSample("An_example_using_rgb_with_alpha_transparency", "", "160")}}

## سبک‌های خط

چندین ویژگی وجود دارد که به ما امکان می‌دهد خطوط را سبک‌دهی کنیم.

- {{domxref("CanvasRenderingContext2D.lineWidth", "lineWidth = value")}}
  - : عرض خطوطی را که در آینده ترسیم می‌شوند تنظیم می‌کند.
- {{domxref("CanvasRenderingContext2D.lineCap", "lineCap = type")}}
  - : ظاهر انتهای خطوط را تنظیم می‌کند.
- {{domxref("CanvasRenderingContext2D.lineJoin", "lineJoin = type")}}
  - : ظاهر «گوشه‌هایی» را که خطوط به هم می‌رسند تنظیم می‌کند.
- {{domxref("CanvasRenderingContext2D.miterLimit", "miterLimit = value")}}
  - : محدودیتی برای miter زمانی که دو خط در یک زاویه تیز به هم می‌پیوندند ایجاد می‌کند، تا به شما کنترل دهد که محل اتصال چقدر ضخیم شود.
- {{domxref("CanvasRenderingContext2D.getLineDash", "getLineDash()")}}
  - : آرایه الگوی خط‌چین فعلی را برمی‌گرداند که شامل تعداد زوجی از اعداد غیرمنفی است.
- {{domxref("CanvasRenderingContext2D.setLineDash", "setLineDash(segments)")}}
  - : الگوی خط‌چین فعلی را تنظیم می‌کند.
- {{domxref("CanvasRenderingContext2D.lineDashOffset", "lineDashOffset = value")}}
  - : مشخص می‌کند که یک آرایه خط‌چین روی یک خط از کجا شروع شود.

با مشاهده مثال‌های زیر، درک بهتری از عملکرد این موارد خواهید داشت.

### مثالی از `lineWidth`

این ویژگی ضخامت خط فعلی را تنظیم می‌کند. مقادیر باید اعداد مثبت باشند. به‌طور پیش‌فرض این مقدار روی 1.0 واحد تنظیم شده است.

عرض خط، ضخامت stroke است که در مرکز مسیر مشخص شده قرار دارد. به عبارت دیگر، ناحیه‌ای که ترسیم می‌شود، تا نصف عرض خط در هر دو طرف مسیر گسترش می‌یابد. از آنجا که مختصات Canvas مستقیماً به پیکسل‌ها اشاره نمی‌کنند، باید دقت ویژه‌ای برای به دست آوردن خطوط افقی و عمودی واضح انجام شود.

در مثال زیر، 10 خط مستقیم با عرض‌های خط فزاینده ترسیم شده‌اند. خط سمت چپ 1.0 واحد عرض دارد. با این حال، چپ‌ترین خط و همه خطوط با ضخامت عدد صحیح فرد، به دلیل موقعیت مسیر، واضح به نظر نمی‌رسند.

```js
function draw() {
  const ctx = document.getElementById("canvas").getContext("2d");
  for (let i = 0; i < 10; i++) {
    ctx.lineWidth = 1 + i;
    ctx.beginPath();
    ctx.moveTo(5 + i * 14, 5);
    ctx.lineTo(5 + i * 14, 140);
    ctx.stroke();
  }
}
```

```html hidden
<canvas id="canvas" width="150" height="150" role="presentation"></canvas>
```

```js hidden
draw();
```

{{EmbedLiveSample("A_lineWidth_example", "", "160")}}

> [!NOTE]
> اگر تعجب می‌کنید که چرا خطوط نزدیک لبه به جای سیاه خاکستری به نظر می‌رسند، بخش [دیدن لبه‌های تار؟](/en-US/docs/Web/API/Canvas_API/Tutorial/Drawing_shapes#seeing_blurry_edges) را در فصل قبلی ببینید.

### مثالی از `lineCap`

ویژگی `lineCap` تعیین می‌کند که نقاط انتهایی هر خط چگونه ترسیم شوند. سه مقدار ممکن برای این ویژگی وجود دارد: `butt`، `round` و `square`. به‌طور پیش‌فرض این ویژگی روی `butt` تنظیم شده است:

- `butt`
  - : انتهای خطوط در نقاط انتهایی به صورت مربعی بریده می‌شوند.
- `round`
  - : انتهای خطوط گرد می‌شوند.
- `square`
  - : انتهای خطوط با افزودن یک جعبه با عرض برابر و نصف ارتفاع ضخامت خط، به صورت مربعی بریده می‌شوند.

فقط نقاط شروع و پایان یک