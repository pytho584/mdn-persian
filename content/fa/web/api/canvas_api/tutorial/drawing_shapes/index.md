---
title: "Drawing shapes with canvas"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Drawing_shapes"
translated_by: "n8n + AI"
---

---
title: Drawing shapes with canvas
slug: Web/API/Canvas_API/Tutorial/Drawing_shapes
page-type: guide
---

{{DefaultAPISidebar("Canvas API")}} {{PreviousNext("Web/API/Canvas_API/Tutorial/Basic_usage", "Web/API/Canvas_API/Tutorial/Applying_styles_and_colors")}}

حالا که [محیط بوم](/en-US/docs/Web/API/Canvas_API/Tutorial/Basic_usage) خود را راه‌اندازی کرده‌ایم، می‌توانیم به جزئیات نحوه رسم روی بوم بپردازیم. در پایان این مقاله، یاد خواهید گرفت که چگونه مستطیل‌ها، مثلث‌ها، خط‌ها، کمان‌ها و منحنی‌ها را رسم کنید و با برخی از شکل‌های پایه آشنا خواهید شد. کار با مسیرها هنگام رسم اشیاء روی بوم ضروری است و خواهیم دید که چگونه می‌توان این کار را انجام داد.

## شبکه

پیش از آنکه بتوانیم رسم را شروع کنیم، باید درباره شبکهٔ بوم یا **فضای مختصات** صحبت کنیم. اسکلت HTML صفحهٔ قبل یک عنصر بوم با عرض ۱۵۰ پیکسل و ارتفاع ۱۵۰ پیکسل داشت.

![Canvas grid with a blue square demonstrating coordinates and axes.](canvas_default_grid.png)

به‌طور معمول، ۱ واحد در شبکه معادل ۱ پیکسل روی بوم است. مبدأ این شبکه در گوشهٔ _بالا سمت چپ_ و در مختصات (0,0) قرار دارد. همهٔ عناصر نسبت به این مبدأ جای‌گذاری می‌شوند. بنابراین موقعیت گوشهٔ بالای سمت چپ مربع آبی، x پیکسل از چپ و y پیکسل از بالا، با مختصات (x,y) مشخص می‌شود. بعداً در این آموزش خواهیم دید که چگونه می‌توان مبدأ را به موقعیت دیگری منتقل کرد، شبکه را چرخاند و حتی مقیاس آن را تغییر داد، اما فعلاً به حالت پیش‌فرض می‌مانیم.

## رسم مستطیل‌ها

برخلاف {{Glossary("SVG")}}، {{HTMLElement("canvas")}} تنها از دو شکل ابتدایی پشتیبانی می‌کند: مستطیل‌ها و مسیرها (فهرستی از نقاط که با خط به هم متصل شده‌اند). همهٔ شکل‌های دیگر باید با ترکیب یک یا چند مسیر ساخته شوند. خوشبختانه، مجموعه‌ای از توابع رسم مسیر در اختیار داریم که ترکیب شکل‌های بسیار پیچیده را ممکن می‌سازند.

اول بیایید مستطیل را بررسی کنیم. سه تابع وجود دارد که روی بوم مستطیل رسم می‌کنند:

- {{domxref("CanvasRenderingContext2D.fillRect", "fillRect(x, y, width, height)")}}
  - : یک مستطیل توپُر رسم می‌کند.
- {{domxref("CanvasRenderingContext2D.strokeRect", "strokeRect(x, y, width, height)")}}
  - : یک حاشیهٔ مستطیلی رسم می‌کند.
- {{domxref("CanvasRenderingContext2D.clearRect", "clearRect(x, y, width, height)")}}
  - : ناحیهٔ مستطیلی مشخص‌شده را پاک می‌کند و آن را کاملاً شفاف می‌سازد.

هر یک از این سه تابع پارامترهای یکسانی می‌گیرند. `x` و `y` موقعیت گوشهٔ بالای سمت چپ مستطیل را روی بوم (نسبت به مبدأ) مشخص می‌کنند. `width` و `height` اندازهٔ مستطیل را تعیین می‌کنند.

در زیر تابع `draw()` از صفحهٔ قبل آورده شده است، اما حالا از این سه تابع استفاده می‌کند.

### مثال شکل مستطیلی

```html hidden
<canvas id="canvas" width="150" height="150"></canvas>
```

```js
function draw() {
  const canvas = document.getElementById("canvas");
  const ctx = canvas.getContext("2d");

  ctx.fillRect(25, 25, 100, 100);
  ctx.clearRect(45, 45, 60, 60);
  ctx.strokeRect(50, 50, 50, 50);
}
```

```js hidden
draw();
```

خروجی این مثال در زیر نشان داده شده است.

{{EmbedLiveSample("Rectangular_shape_example", "", "160")}}

تابع `fillRect()` یک مربع سیاه بزرگ به ضلع ۱۰۰ پیکسل رسم می‌کند. سپس تابع `clearRect()` یک مربع ۶۰×۶۰ پیکسلی را از مرکز پاک می‌کند و در ادامه `strokeRect()` فراخوانی می‌شود تا یک حاشیهٔ مستطیلی ۵۰×۵۰ پیکسلی درون مربع پاک‌شده ایجاد کند (_از نظر مفهومی_ ۵۰×۵۰؛ در واقعیت ۵۲×۵۲ است، همان‌طور که در بخش بعد توضیح داده می‌شود).

در صفحه‌های آینده دو روش جایگزین برای `clearRect()` خواهیم دید و همچنین خواهیم دید که چگونه رنگ و سبک خط (stroke) شکل‌های رندر شده را تغییر دهیم.

برخلاف توابع مسیر که در بخش بعد خواهیم دید، هر سه تابع مستطیل بلافاصله روی بوم رسم می‌کنند.

## لبه‌های تار می‌بینید؟

در مثال مستطیل بالا و در تمام مثال‌های پیش رو، ممکن است متوجه شوید که لبه‌های شکل‌ها نسبت به شکل‌های معادل رسم‌شده با SVG یا CSS تارتر به نظر می‌رسند. این به این دلیل نیست که Canvas API قادر به رسم لبه‌های تیز نیست، بلکه به دلیل نحوه نگاشت شبکهٔ بوم به پیکسل‌های واقعی روی صفحه و همچنین، در برخی موارد، به دلیل نحوه مقیاس‌بندی بوم توسط مرورگر است. اگر مثال بالا به اندازه کافی واضح نیست، بیایید بوم را با استفاده از CSS بزرگ‌تر کنیم:

```html live-sample___seeing_blurry_edges live-sample___seeing_blurry_edges_2 live-sample___seeing_blurry_edges_3
<canvas id="canvas" width="15" height="15"></canvas>
```

```css live-sample___seeing_blurry_edges live-sample___seeing_blurry_edges_2 live-sample___seeing_blurry_edges_3
#canvas {
  width: 300px;
  height: 300px;
}
```

```js live-sample___seeing_blurry_edges live-sample___seeing_blurry_edges_2
function draw() {
  const canvas = document.getElementById("canvas");
  const ctx = canvas.getContext("2d");
  ctx.strokeRect(2, 2, 10, 10);
  ctx.fillRect(7, 7, 1, 1);
}
```

```js hidden live-sample___seeing_blurry_edges live-sample___seeing_blurry_edges_2 live-sample___seeing_blurry_edges_3
draw();
```

{{EmbedLiveSample("Seeing blurry edges", "", "350")}}

در این مثال، بوم را بسیار کوچک (۱۵×۱۵) ایجاد می‌کنیم، اما سپس با CSS آن را تا ۳۰۰×۳۰۰ پیکسل بزرگ می‌کنیم. در نتیجه، هر پیکسل بوم اکنون با یک بلوک ۲۰×۲۰ از پیکسل‌های CSS نمایش داده می‌شود. یک مستطیل خط‌دار از (2,2) تا (12,12) و یک مستطیل توپُر از (7,7) تا (8,8) رسم می‌کنیم. ظاهر آن _واقعاً_ تار است. دلیل این است که مرورگر به‌طور پیش‌فرض هنگام بزرگ‌نمایی تصاویر شطرنجی، از یک الگوریتم هموارسازی برای درون‌یابی پیکسل‌های اضافی استفاده می‌کند. این برای عکس‌ها یا گرافیک‌های بوم با لبه‌های منحنی عالی است، اما برای شکل‌های با لبهٔ صاف چندان مناسب نیست. برای رفع این مشکل، می‌توانیم {{cssxref("image-rendering")}} را روی `pixelated` قرار دهیم:

```css live-sample___seeing_blurry_edges_2 live-sample___seeing_blurry_edges_3
#canvas {
  image-rendering: pixelated;
}
```

{{EmbedLiveSample("Seeing blurry edges 2", "", "350")}}

حالا وقتی مرورگر بوم را مقیاس‌بندی می‌کند، در حد امکان پیکسل‌بندی (pixelation) اصلی را حفظ می‌کند.

> [!NOTE]
> `image-rendering: pixelated` به‌عنوان یک تکنیک حفظ لبه‌های تیز خالی از مشکل نیست. وقتی پیکسل‌های CSS با پیکسل‌های دستگاه هم‌تراز نباشند (اگر {{domxref("Window/devicePixelRatio", "devicePixelRatio")}} عددی صحیح نباشد)، ممکن است برخی پیکسل‌ها بزرگ‌تر از بقیه رسم شوند و ظاهری نایک‌نواخت ایجاد کنند. با این حال، حل این مشکل آسان نیست، زیرا زمانی که پیکسل‌های CSS نتوانند به‌طور دقیق به پیکسل‌های دستگاه نگاشت شوند، پر کردن دقیق پیکسل‌های دستگاه غیرممکن است.

اما حالا مشکل دیگری نمایان می‌شود، مشکلی که در مثال مستطیل اولیه نیز می‌توانید مشاهده کنید: مستطیل خط‌دار نه‌تنها به‌جای ۱ پیکسل، ۲ پیکسل عرض دارد، بلکه به‌جای رنگ سیاه پیش‌فرض، خاکستری به نظر می‌رسد. این به این دلیل است که مختصات‌ها به‌عنوان مرزهای شکل تفسیر می‌شوند.

اگر دوباره به نمودار [شبکه](#the_grid) در بالا نگاه کنید، می‌بینید که مختصاتی مانند `2` یا `12` یک پیکسل را مشخص نمی‌کنند، بلکه لبهٔ بین دو پیکسل را مشخص می‌کنند. در تصویرهای زیر، شبکه نشان‌دهندهٔ شبکهٔ مختصات بوم است. مربع‌های بین خطوط شبکه، پیکسل‌های واقعی روی صفحه هستند. در نخستین تصویر شبکه در زیر، یک مستطیل از (2,1) تا (5,5) پر شده است. کل ناحیهٔ بین آن‌ها (قرمز روشن) روی مرز پیکسل‌ها قرار می‌گیرد، بنابراین مستطیل توپُر حاصل لبه‌های تیزی خواهد داشت.

![Three coordinate grids. The grid lines are actual pixels on the screen. The top left corner of each grid is labeled (0,0). In the first grid, a rectangle from (2,1) to (5,5) is filled in light-red color. In the second grid, (3,1) to (3,5) is joined with a 1-pixel thick royal blue line. The royal-blue line is centered on a grid line, extends from 2.5 to 3.5 on the x access, halfway into the pixels on either side of the graph line, with a light blue background on either side extending from 2 to 4 on the x-access. To avoid the light blue blur extension of the line in the second coordinate grid, the path in, the third coordinate grid is a royal-blue from line (3.5,1) to (3.5,5). The 1 pixel line width ends up completely and precisely filling a single pixel vertical line.](canvas-grid.png)

اگر مسیری از (3,1) تا (3,5) با ضخامت خط `1.0` در نظر بگیرید، به وضعیت تصویر دوم می‌رسید. ناحیهٔ واقعی که باید پر شود (آبی تیره) فقط تا نیمی از پیکسل‌های دو طرف مسیر پیش می‌رود. باید تقریبی از این وضعیت رندر شود، به این معنی که آن پیکسل‌ها فقط به‌طور جزئی سایه می‌خورند و در نتیجه کل ناحیه (آبی روشن و آبی تیره) با رنگی پر می‌شود که تنها نصف تیرگی رنگ واقعی خط است. این دقیقاً همان چیزی است که با خط با عرض `1.0` در فراخوانی `strokeRect()` در مثال مستطیل بالا رخ می‌دهد.

برای رفع این مشکل، باید در ایجاد مسیر بسیار دقیق باشید. با دانستن اینکه یک خط با عرض `1.0` نیم واحد به هر سمت مسیر گسترش می‌یابد، ایجاد مسیر از _مرکز_ پیکسل‌ها به وضعیت تصویر سوم منجر می‌شود—عرض خط `1.0` در نهایت یک خط عمودی تک‌پیکسلی را به‌طور کامل و دقیق پر می‌کند.

> [!NOTE]
> توجه داشته باشید که در مثال خط عمودی، موقعیت Y همچنان به یک موقعیت عدد صحیح روی خط شبکه اشاره می‌کرد—اگر این‌طور نبود، در نقاط انتهایی پیکسل‌هایی با پوشش نصفه می‌دیدیم.

به همین دلیل است که قبلاً گفتیم فراخوانی `strokeRect(50, 50, 50, 50)` در مثال مستطیل _از نظر مفهومی_ ۵۰×۵۰ است، اما در واقعیت ۵۲×۵۲ است. ناحیهٔ واقعی پر شده برای حاشیه از (49.5, 49.5) شروع و به (100.5, 100.5) ختم می‌شود، و به دلیل پیکسل‌های نیمه‌پر، ناحیهٔ واقعاً پر شده از (49,49) تا (101,101) است که ۵۲×۵۲ است و لبه‌ها ۲ پیکسل عرض دارند. برای به دست آوردن یک خط دور توپُر با عرض ۱ پیکسل که دقیقاً ۵۰×۵۰ باشد، باید مستطیل را به اندازهٔ ضخامت خط دور (۱px) _کوچک_ کنید و آن را به اندازهٔ نصف ضخامت (0.5px) جابه‌جا کنید:

```js live-sample___seeing_blurry_edges_3
function draw() {
  const canvas = document.getElementById("canvas");
  const ctx = canvas.getContext("2d");
  ctx.strokeRect(2.5, 2.5, 9, 9);
  ctx.fillRect(7, 7, 1, 1);
}
```

{{EmbedLiveSample("Seeing blurry edges 3", "", "350")}}

برای خطوط با عرض زوج، هر نیمه به تعداد صحیحی پیکسل تبدیل می‌شود، بنابراین مسیری می‌خواهید که بین پیکسل‌ها باشد (یعنی (3,1) تا (3,5))، نه درست از وسط پیکسل‌ها.

هرچند در ابتدای کار با گرافیک دوبعدی مقیاس‌پذیر کمی دشوار است، اما توجه به شبکهٔ پیکسل و موقعیت مسیرها تضمین می‌کند که رسم‌های شما بدون توجه به مقیاس‌بندی یا هر تبدیل دیگری که انجام می‌شود، درست به نظر برسند. یک خط عمودی با عرض 1.0 که در موقعیت صحیح رسم شود، هنگام بزرگ‌نمایی ۲ برابر، به یک خط تیز ۲ پیکسلی تبدیل می‌شود و در موقعیت صحیح ظاهر می‌شود.

این پدیدهٔ پیکسل‌های نیمه‌پر به شکل‌هایی که با شبکهٔ پیکسل هم‌تراز نیستند نیز گسترش می‌یابد. برای مثال، یک مستطیل چرخیده را در نظر بگیرید (در بخش بعد دربارهٔ رسم آن یاد خواهید گرفت). برای دیدن وضعیت با و بدون `image-rendering: pixelated`، دو بوم در کنار هم داریم و بوم سومی که در مقیاس کامل، با خطوط شبکه رسم شده است:

```html hidden live-sample___seeing_blurry_edges_4
<canvas id="canvas1" width="12" height="12"></canvas>
<canvas id="canvas2" width="12" height="12"></canvas>
<canvas id="canvas3" width="240" height="240"></canvas>
```

```css hidden live-sample___seeing_blurry_edges_4
html,
body {
  width: 800px;
  overflow-x: scroll;
}

@media (width < 500px) {
  html,
  body {
    width: 300px;
  }
}

#canvas1,
#canvas2 {
  width: 240px;
  height: 240px;
}
#canvas2 {
  image-rendering: pixelated;
}
```

```js live-sample___seeing_blurry_edges_4
function draw(canvasId) {
  const canvas = document.getElementById(canvasId);
  const ctx = canvas.getContext("2d");
  ctx.beginPath();
  ctx.moveTo(3, 2);
  ctx.lineTo(9, 4.5);
  ctx.lineTo(6.5, 10.5);
  ctx.lineTo(0.5, 8);
  ctx.closePath();
  ctx.fill();
}

function drawFullScale() {
  const canvas = document.getElementById("canvas3");
  const ctx = canvas.getContext("2d");
  ctx.beginPath();
  ctx.moveTo(60, 40);
  ctx.lineTo(180, 90);
  ctx.lineTo(130, 210);
  ctx.lineTo(10, 160);
  ctx.closePath();
  ctx.fill();
  ctx.strokeStyle = "lightgray";
  for (let i = 0; i < 16; i++) {
    ctx.moveTo(i * 20, 0);
    ctx.lineTo(i * 20, 300);
    ctx.moveTo(0, i * 20);
    ctx.lineTo(300, i * 20);
    ctx.stroke();
  }
}
```

```js hidden live-sample___seeing_blurry_edges_4
draw("canvas1");
draw("canvas2");
drawFullScale();
```

{{EmbedLiveSample("Seeing blurry edges 4", "", "350")}}

اگر بزرگ‌کردن تصویر آن را تارتر از حد انتظار نشان دهد، کوچک‌کردن تصویر آن را _تیزتر_ نشان می‌دهد. مثلاً اگر می‌خواهید یک بوم روی صفحه به‌صورت ۳۰۰×۱۵۰ پیکسل دیده شود، می‌توانید آن را با اندازهٔ ۶۰۰×۳۰۰ پیکسل ایجاد کنید و سپس با CSS آن را کوچک کنید. این به‌ویژه در صفحه‌های با DPI بالا (مانند نمایشگرهای رتینا اپل) مفید است، جایی که یک پیکسل CSS با چند پیکسل صفحه نمایش داده می‌شود؛ بنابراین اگر یک بوم ۳۰۰×۱۵۰ پیکسلی را دقیق رنگ‌آمیزی کنید، وضوح پیکسلی یکسانی با دیگر عناصر صفحه نخواهد داشت.

## رسم مسیرها

حالا بیایید مسیرها را بررسی کنیم. مسیر فهرستی از نقاط است که توسط پاره‌خط‌هایی به هم متصل شده‌اند؛ این پاره‌خط‌ها می‌توانند شکل‌های مختلفی داشته باشند، منحنی یا غیرمنحنی، با عرض‌ها و رنگ‌های متفاوت. یک مسیر یا حتی یک زیرمسیر می‌تواند بسته باشد. برای ساخت شکل‌ها با استفاده از مسیرها، چند گام اضافی برمی‌داریم:

1. ابتدا مسیر را ایجاد می‌کنید.
2. سپس از [دستورهای رسم](/en-US/docs/Web/API/CanvasRenderingContext2D#paths) برای رسم درون مسیر استفاده می‌کنید.
3. پس از ایجاد مسیر، می‌توانید آن را خط‌گذاری (stroke) یا پر کنید تا رندر شود.

در اینجا توابعی که برای انجام این مراحل استفاده می‌شوند آورده شده است:

- {{domxref("CanvasRenderingContext2D.beginPath", "beginPath()")}}
  - : یک مسیر جدید ایجاد می‌کند. پس از ایجاد، دستورهای رسم بعدی به سمت این مسیر هدایت شده و برای ساخت مسیر استفاده می‌شوند.
- [روش‌های مسیر](/en-US/docs/Web/API/CanvasRenderingContext2D#paths)
  - : روش‌هایی برای تنظیم مسیرهای مختلف برای اشیاء.
- {{domxref("CanvasRenderingContext2D.closePath", "closePath()")}}
  - : یک خط مستقیم به مسیر اضافه می‌کند که به شروع زیرمسیر جاری می‌رود.
- {{domxref("CanvasRenderingContext2D.stroke", "stroke()")}}
  - : شکل را با خط‌گذاری دور آن رسم می‌کند.
- {{domxref("CanvasRenderingContext2D.fill", "fill()")}}
  - : یک شکل توپُر را با پر کردن ناحیهٔ محتوای مسیر رسم می‌کند.

اولین گام برای ایجاد یک مسیر، فراخوانی `beginPath()` است. در داخل، مسیرها به‌صورت فهرستی از زیرمسیرها (خط‌ها، کمان‌ها و غیره) ذخیره می‌شوند که با هم یک شکل را تشکیل می‌دهند. هر بار که این متد فراخوانی شود، فهرست بازنشانی می‌شود و می‌توانیم رسم شکل‌های جدید را شروع کنیم.

> [!NOTE]
> وقتی مسیر جاری خالی است، مثلاً بلافاصله پس از فراخوانی `beginPath()` یا روی یک بوم تازه ایجاد شده، نخستین دستور ساخت مسیر همیشه به‌عنوان `moveTo()` در نظر گرفته می‌شود، صرف‌نظر از اینکه واقعاً چیست. به همین دلیل، تقریباً همیشه می‌خواهید پس از بازنشانی مسیر، موقعیت شروع خود را به‌طور مشخص تنظیم کنید.

گام دوم، فراخوانی روش‌هایی است که مسیرهای مورد نظر برای رسم را مشخص می‌کنند. به‌زودی آن‌ها را خواهیم دید.

گام سوم و اختیاری، فراخوانی `closePath()` است. این روش تلاش می‌کند شکل را با کشیدن یک خط مستقیم از نقطهٔ جاری به نقطهٔ شروع ببندد. اگر شکل از قبل بسته شده باشد یا فقط یک نقطه در فهرست وجود داشته باشد، این تابع کاری انجام نمی‌دهد.

> [!NOTE]
> وقتی `fill()` را فراخوانی می‌کنید، هر شکل باز به‌طور خودکار بسته می‌شود؛ بنابراین نیازی به فراخوانی `closePath()` ندارید. اما وقتی `stroke()` را فراخوانی می‌کنید این‌طور **نیست**.

### رسم یک مثلث

برای مثال، کد رسم یک مثلث چیزی شبیه به این خواهد بود:

```html hidden
<canvas id="canvas" width="100" height="100"></canvas>
```

```js
function draw() {
  const canvas = document.getElementById("canvas");
  const ctx = canvas.getContext("2d");

  ctx.beginPath();
  ctx.moveTo(75, 50);
  ctx.lineTo(100, 75);
  ctx.lineTo(100, 25);
  ctx.fill();
}
```

```js hidden
draw();
```

نتیجه به این شکل است:

{{EmbedLiveSample("Drawing_a_triangle", "", "110")}}

### جابه‌جایی قلم

یکی از توابع بسیار مفید که در واقع چیزی رسم نمی‌کند اما بخشی از فهرست مسیر توصیف‌شده در بالا می‌شود، تابع `moveTo()` است. احتمالاً بهترین راه برای درک آن این است که آن را مانند برداشتن قلم یا مداد از یک نقطه روی کاغذ و قرار دادن آن روی نقطهٔ بعدی تصور کنید.

- {{domxref("CanvasRenderingContext2D.moveTo", "moveTo(x, y)")}}
  - : قلم را به مختصات مشخص‌شده توسط `x` و `y` حرکت می‌دهد.

وقتی بوم مقداردهی اولیه می‌شود یا `beginPath()` فراخوانی می‌شود، معمولاً می‌خواهید از تابع `moveTo()` برای قرار دادن نقطهٔ شروع در جای دیگری استفاده کنید. همچنین می‌توانیم از `moveTo()` برای رسم مسیرهای بدون اتصال استفاده کنیم. به شکلک صورت خندان زیر نگاه کنید.

برای امتحان کردن این کار، می‌توانید از قطعه‌کد زیر استفاده کنید. کافی است آن را در تابع `draw()` که قبلاً دیدیم قرار دهید.

```html hidden
<canvas id="canvas" width="150" height="150"></canvas>
```

```js
function draw() {
  const canvas = document.getElementById("canvas");
  const ctx = canvas.getContext("2d");

  ctx.beginPath();
  ctx.arc(75, 75, 50, 0, Math.PI * 2, true); // Outer circle
  ctx.moveTo(110, 75);
  ctx.arc(75, 75, 35, 0, Math.PI, false); // Mouth (clockwise)
  ctx.moveTo(65, 65);
  ctx.arc(60, 65, 5, 0, Math.PI * 2, true); // Left eye
  ctx.moveTo(95, 65);
  ctx.arc(90, 65, 5, 0, Math.PI * 2, true); // Right eye
  ctx.stroke();
}
```

```js hidden
draw();
```

نتیجه به این شکل است:

{{EmbedLiveSample("Moving_the_pen", "", "160")}}

اگر می‌خواهید خطوط اتصال را ببینید، می‌توانید خطوطی را که `moveTo()` را فراخوانی می‌کنند حذف کنید.

> [!NOTE]
> برای آشنایی بیشتر با تابع `arc()`، به بخش [کمان‌ها](#arcs) در زیر مراجعه کنید.

### خط‌ها

برای رسم خطوط مستقیم، از روش `lineTo()` استفاده کنید.

- {{domxref("CanvasRenderingContext2D.lineTo", "lineTo(x, y)")}}
  - : خطی از موقعیت رسم فعلی به موقعیت مشخص‌شده توسط `x` و `y` رسم می‌کند.

این روش دو آرگومان `x` و `y` می‌گیرد که مختصات نقطهٔ پایان خط هستند. نقطهٔ شروع به مسیرهای قبلی رسم‌شده بستگی دارد، به این صورت که نقطهٔ پایان مسیر قبلی، نقطهٔ شروع مسیر بعدی است و غیره. نقطهٔ شروع را نیز می‌توان با استفاده از روش `moveTo()` تغییر داد.

مثال زیر دو مثلث رسم می‌کند: یکی توپُر و یکی خط‌دار.

```html hidden
<canvas id="canvas" width="150" height="150"></canvas>
```

```js
function draw() {
  const canvas = document.getElementById("canvas");
  const ctx = canvas.getContext("2d");

  // Filled triangle
  ctx.beginPath();
  ctx.moveTo(25, 25);
  ctx.lineTo(105, 25);
  ctx.lineTo(25, 105);
  ctx.fill();

  // Stroked triangle
  ctx.beginPath();
  ctx.moveTo(125, 125);
  ctx.lineTo(125, 45);
  ctx.lineTo(45, 125);
  ctx.closePath();
  ctx.stroke();
}
```

```js hidden
draw();
```

این کار با فراخوانی `beginPath()` برای شروع یک مسیر شکل جدید آغاز می‌شود. سپس از روش `moveTo()` برای انتقال نقطهٔ شروع به موقعیت مورد نظر استفاده می‌کنیم. در ادامه، دو خط رسم می‌شود که دو ضلع مثلث را تشکیل می‌دهند.

{{EmbedLiveSample("Lines", "", "160")}}

تفاوت بین مثلث توپُر و مثلث خط‌دار را مشاهده خواهید کرد. همان‌طور که در بالا ذکر شد، این به این دلیل است که هنگام پر شدن یک مسیر، شکل‌ها به‌طور خودکار بسته می‌شوند، اما هنگام خط‌گذاری این‌طور نیست. اگر `closePath()` را برای مثلث خط‌دار حذف می‌کردیم، فقط دو خط رسم می‌شد، نه یک مثلث کامل.

### کمان‌ها

برای رسم کمان یا دایره، از روش‌های `arc()` یا `arcTo()` استفاده می‌کنیم.

- {{domxref("CanvasRenderingContext2D.arc", "arc(x, y, radius, startAngle, endAngle, counterclockwise)")}}
  - : کمانی رسم می‌کند که در موقعیت _(x, y)_ با شعاع _r_ مرکز آن قرار دارد و از _startAngle_ شروع و به _endAngle_ ختم می‌شود و در جهت مشخص‌شده توسط _counterclockwise_ حرکت می‌کند (پیش‌فرض در جهت عقربه‌های ساعت است).
- {{domxref("CanvasRenderingContext2D.arcTo", "arcTo(x1, y1, x2, y2, radius)")}}
  - : کمانی را با نقاط کنترل و شعاع داده‌شده رسم می‌کند که با یک خط مستقیم به نقطهٔ قبلی متصل می‌شود.

بیایید نگاه دقیق‌تری به روش `arc` بیندازیم که شش پارامتر می‌گیرد: `x` و `y` مختصات مرکز دایره‌ای هستند که کمان باید روی آن رسم شود. `radius` نیاز به توضیح ندارد. پارامترهای `startAngle` و `endAngle` نقاط شروع و پایان کمان را بر حسب رادیان، در امتداد منحنی دایره تعریف می‌کنند. این زاویه‌ها از محور x اندازه‌گیری می‌شوند. پارامتر `counterclockwise` یک مقدار بولی است که وقتی `true` باشد، کمان در خلاف جهت عقربه‌های ساعت رسم می‌شود؛ در غیر این صورت، کمان در جهت عقربه‌های ساعت رسم می‌شود.

> [!NOTE]
> زاویه‌ها در تابع `arc` بر حسب رادیان اندازه‌گیری می‌شوند، نه درجه. برای تبدیل درجه به رادیان می‌توانید از عبارت جاوااسکریپت زیر استفاده کنید: `radians = (Math.PI/180)*degrees`.

مثال زیر کمی پیچیده‌تر از مثال‌هایی است که در بالا دیدیم. این مثال ۱۲ کمان مختلف با زاویه‌ها و حالت‌های پر شدن متفاوت رسم می‌کند.

دو [حلقهٔ `for`](/en-US/docs/Web/JavaScript/Reference/Statements/for) برای پیمایش سطرها و ستون‌های کمان‌ها هستند. برای هر کمان، با فراخوانی `beginPath()` یک مسیر جدید شروع می‌کنیم. در کد، هر یک از پارامترهای کمان برای خوانایی بیشتر در یک متغیر قرار گرفته است، اما در عمل لزوماً این کار را نمی‌کنید.

مختصات `x` و `y` به اندازه کافی واضح هستند. `radius` و `startAngle` ثابت هستند. `endAngle` در ستون اول از ۱۸۰ درجه (نصف دایره) شروع می‌شود و با گام‌های ۹۰ درجه افزایش می‌یابد و در ستون آخر به یک دایرهٔ کامل می‌رسد.

عبارت مربوط به پارامتر `clockwise` باعث می‌شود سطرهای اول و سوم به‌صورت کمان‌های ساعتگرد و سطرهای دوم و چهارم به‌صورت کمان‌های پادساعتگرد رسم شوند. در نهایت، عبارت `if` باعث می‌شود نیمهٔ بالایی کمان‌ها خط‌دار و نیمهٔ پایینی توپُر باشند.

> [!NOTE]
> این مثال به بوم کمی بزرگ‌تر از سایر مثال‌های این صفحه نیاز دارد: ۱۵۰×۲۰۰ پیکسل.

```html hidden
<canvas id="canvas" width="150" height="200"></canvas>
```

```js
function draw() {
  const canvas = document.getElementById("canvas");
  const ctx = canvas.getContext("2d");

  for (let i = 0; i < 4; i++) {
    for (let j = 0; j < 3; j++) {
      ctx.beginPath();
      const x = 25 + j * 50; // x coordinate
      const y = 25 + i * 50; // y coordinate
      const radius = 20; // Arc radius
      const startAngle = 0; // Starting point on circle
      const endAngle = Math.PI + (Math.PI * j) / 2; // End point on circle
      const counterclockwise = i % 2 !== 0; // clockwise or counterclockwise

      ctx.arc(x, y, radius, startAngle, endAngle, counterclockwise);

      if (i > 1) {
        ctx.fill();
      } else {
        ctx.stroke();
      }
    }
  }
}
```

```js hidden
draw();
```

{{EmbedLiveSample("Arcs", "", "210")}}

### منحنی‌های بزیه و درجه دوم

نوع بعدی مسیرهای موجود، [منحنی‌های بزیه](/en-US/docs/Glossary/Bezier_curve) هستند که در دو نوع مکعبی و درجه دوم موجودند. این منحنی‌ها معمولاً برای رسم شکل‌های ارگانیک پیچیده استفاده می‌شوند.

- {{domxref("CanvasRenderingContext2D.quadraticCurveTo", "quadraticCurveTo(cp1x, cp1y, x, y)")}}
  - : یک منحنی بزیهٔ درجه دوم از موقعیت فعلی قلم تا نقطهٔ پایان مشخص‌شده توسط `x` و `y` رسم می‌کند و از نقطهٔ کنترل مشخص‌شده توسط `cp1x` و `cp1y` استفاده می‌کند.
- {{domxref("CanvasRenderingContext2D.bezierCurveTo", "bezierCurveTo(cp1x, cp1y, cp2x, cp2y, x, y)")}}
  - : یک منحنی بزیهٔ مکعبی از موقعیت فعلی قلم تا نقطهٔ پایان مشخص‌شده توسط `x` و `y`، با استفاده از نقاط کنترل مشخص‌شده توسط (`cp1x`, `cp1y`) و (`cp2x`, `cp2y`) رسم می‌کند.

تفاوت این دو در این است که یک منحنی بزیهٔ درجه دوم یک نقطهٔ شروع و یک نقطهٔ پایان دارد (نقطه‌های آبی) و فقط یک **نقطهٔ کنترل** (که با نقطهٔ قرمز نشان داده شده است)، در حالی که منحنی بزیهٔ مکعبی از دو نقطهٔ کنترل استفاده می‌کند.

![Quadratic and Bezier curve comparison.](canvas_curves.png)

پارامترهای `x` و `y` در هر دوی این روش‌ها مختصات نقطهٔ پایان هستند. `cp1x` و `cp1y` مختصات اولین نقطهٔ کنترل و `cp2x` و `cp2y` مختصات دومین نقطهٔ کنترل هستند.

استفاده از منحنی‌های بزیهٔ درجه دوم و مکعبی می‌تواند کاملاً چالش‌برانگیز باشد، زیرا برخلاف نرم‌افزارهای طراحی برداری مانند Adobe Illustrator، بازخورد بصری مستقیمی از کاری که انجام می‌دهیم نداریم. این موضوع رسم شکل‌های پیچیده را بسیار دشوار می‌کند. در مثال بعدی، چند شکل ارگانیک ساده رسم خواهیم کرد، اما اگر زمان و مهم‌تر از همه، حوصله داشته باشید، می‌توان شکل‌های بسیار پیچیده‌تری نیز ایجاد کرد.

در این مثال‌ها چیز دشواری وجود ندارد. در هر دو مورد، دنباله‌ای از منحنی‌ها رسم می‌شوند که در نهایت به یک شکل کامل منجر می‌شوند.

#### منحنی‌های بزیهٔ درجه دوم

این مثال از چند منحنی بزیهٔ درجه دوم برای رندر کردن یک حباب گفتار استفاده می‌کند.

```html hidden
<canvas id="canvas" width="150" height="150"></canvas>
```

```js
function draw() {
  const canvas = document.getElementById("canvas");
  const ctx = canvas.getContext("2d");

  // Quadratic curves example
  ctx.beginPath();
  ctx.moveTo(75, 25);
  ctx.quadraticCurveTo(25, 25, 25, 62.5);
  ctx.quadraticCurveTo(25, 100, 50, 100);
  ctx.quadraticCurveTo(50, 120, 30, 125);
  ctx.quadraticCurveTo(60, 120, 65, 100);
  ctx.quadraticCurveTo(125, 100, 125, 62.5);
  ctx.quadraticCurveTo(125, 25, 75, 25);
  ctx.stroke();
}
```

```js hidden
draw();
```

{{EmbedLiveSample("Quadratic_Bezier_curves", "", "160")}}

#### منحنی‌های بزیهٔ مکعبی

این مثال با استفاده از منحنی‌های بزیهٔ مکعبی یک قلب رسم می‌کند.

```html hidden
<canvas id="canvas" width="150" height="150"></canvas>
```

```js
function draw() {
  const canvas = document.getElementById("canvas");
  const ctx = canvas.getContext("2d");

  // Cubic curves example
  ctx.beginPath();
  ctx.moveTo(75, 40);
  ctx.bezierCurveTo(75, 37, 70, 25, 50, 25);
  ctx.bezierCurveTo(20, 25, 20, 62.5, 20, 62.5);
  ctx.bezierCurveTo(20, 80, 40, 102, 75, 120);
  ctx.bezierCurveTo(110, 102, 130, 80, 130, 62.5);
  ctx.bezierCurveTo(130, 62.5, 130, 25, 100, 25);
  ctx.bezierCurveTo(85, 25, 75, 37, 75, 40);
  ctx.fill();
}
```

```js hidden
draw();
```

{{EmbedLiveSample("Cubic_Bezier_curves", "", "160")}}

### مستطیل‌ها

علاوه بر سه روشی که در [رسم مستطیل‌ها](#drawing_rectangles) دیدیم و شکل‌های مستطیلی را مستقیماً روی بوم رسم می‌کنند، روش `rect()` نیز وجود دارد که یک مسیر مستطیلی به مسیر باز فعلی اضافه می‌کند.

- {{domxref("CanvasRenderingContext2D.rect", "rect(x, y, width, height)")}}
  - : مستطیلی را رسم می‌کند که گوشهٔ بالای سمت چپ آن توسط (`x`, `y`) مشخص شده و دارای `width` و `height` معین است.

قبل از اجرای این روش، متد `moveTo()` به‌طور خودکار با پارامترهای (x,y) فراخوانی می‌شود. به عبارت دیگر، موقعیت فعلی قلم به‌طور خودکار به مختصات پیش‌فرض بازنشانی می‌شود.

### ترکیب کردن

تاکنون، هر مثال در این صفحه فقط از یک نوع تابع مسیر برای هر شکل استفاده کرده است. با این حال، هیچ محدودیتی برای تعداد یا انواع مسیرهایی که می‌توانید برای ایجاد یک شکل استفاده کنید وجود ندارد. بنابراین در این مثال آخر، بیایید همهٔ توابع مسیر را ترکیب کنیم تا مجموعه‌ای از شخصیت‌های بسیار معروف بازی را بسازیم.

```html hidden
<canvas id="canvas" width="200" height="185"></canvas>
```

```js
function draw() {
  const canvas = document.getElementById("canvas");
  const ctx = canvas.getContext("2d");

  roundedRect(ctx, 12, 12, 184, 168, 15);
  roundedRect(ctx, 19, 19, 170, 154, 9);
  roundedRect(ctx, 53, 53, 49, 33, 10);
  roundedRect(ctx, 53, 119, 49, 16, 6);
  roundedRect(ctx, 135, 53, 49, 33, 10);
  roundedRect(ctx, 135, 119, 25, 49, 10);

  ctx.beginPath();
  ctx.arc(37, 37, 13, Math.PI / 7, -Math.PI / 7, false);
  ctx.lineTo(31, 37);
  ctx.fill();

  for (let i = 0; i < 8; i++) {
    ctx.fillRect(51 + i * 16, 35, 4, 4);
  }

  for (let i = 0; i < 6; i++) {
    ctx.fillRect(115, 51 + i * 16, 4, 4);
  }

  for (let i = 0; i < 8; i++) {
    ctx.fillRect(51 + i * 16, 99, 4, 4);
  }

  ctx.beginPath();
  ctx.moveTo(83, 116);
  ctx.lineTo(83, 102);
  ctx.bezierCurveTo(83, 94, 89, 88, 97, 88);
  ctx.bezierCurveTo(105, 88, 111, 94, 111, 102);
  ctx.lineTo(111, 116);
  ctx.lineTo(106.333, 111.333);
  ctx.lineTo(101.666, 116);
  ctx.lineTo(97, 111.333);
  ctx.lineTo(92.333, 116);
  ctx.lineTo(87.666, 111.333);
  ctx.lineTo(83, 116);
  ctx.fill();

  ctx.fillStyle = "white";
  ctx.beginPath();
  ctx.moveTo(91, 96);
  ctx.bezierCurveTo(88, 96, 87, 99, 87, 101);
  ctx.bezierCurveTo(87, 103, 88, 106, 91, 106);
  ctx.bezierCurveTo(94, 106, 95, 103, 95, 101);
  ctx.bezierCurveTo(95, 99, 94, 96, 91, 96);
  ctx.moveTo(103, 96);
  ctx.bezierCurveTo(100, 96, 99, 99, 99, 101);
  ctx.bezierCurveTo(99, 103, 100, 106, 103, 106);
  ctx.bezierCurveTo(106, 106, 107, 103, 107, 101);
  ctx.bezierCurveTo(107, 99, 106, 96, 103, 96);
  ctx.fill();

  ctx.fillStyle = "black";
  ctx.beginPath();
  ctx.arc(101, 102, 2, 0, Math.PI * 2, true);
  ctx.fill();

  ctx.beginPath();
  ctx.arc(89, 102, 2, 0, Math.PI * 2, true);
  ctx.fill();
}

// A utility function to draw a rectangle with rounded corners.

function roundedRect(ctx, x, y, width, height, radius) {
  ctx.beginPath();
  ctx.moveTo(x, y + radius);
  ctx.arcTo(x, y + height, x + radius, y + height, radius);
  ctx.arcTo(x + width, y + height, x + width, y + height - radius, radius);
  ctx.arcTo(x + width, y, x + width - radius, y, radius);
  ctx.arcTo(x, y, x, y + radius, radius);
  ctx.stroke();
}
```

```js hidden
draw();
```

تصویر حاصل به این شکل است:

{{EmbedLiveSample("Making_combinations", "", "200")}}

ما به جزئیات این مثال نمی‌پردازیم، زیرا در واقع به‌طرز شگفت‌آوری ساده است. مهم‌ترین نکاتی که باید به آن‌ها توجه کنید، استفاده از ویژگی `fillStyle` روی زمینهٔ رسم و استفاده از یک تابع کمکی (در اینجا `roundedRect()`) است. استفاده از توابع کمکی برای بخش‌هایی از رسم که اغلب انجام می‌دهید می‌تواند بسیار مفید باشد و میزان کد مورد نیاز و همچنین پیچیدگی آن را کاهش دهد.

در ادامهٔ این آموزش، دوباره با جزئیات بیشتری به `fillStyle` نگاه خواهیم کرد. در اینجا، تنها کاری که انجام می‌دهیم این است که از آن برای تغییر رنگ پر شدن مسیرها از رنگ پیش‌فرض سیاه به سفید و سپس بازگشت دوباره استفاده می‌کنیم.

### شکل‌های دارای حفره

برای رسم شکلی که در آن حفرهای وجود دارد، باید حفره را در جهت متفاوتی نسبت به شکل بیرونی رسم کنیم. یا شکل بیرونی را ساعتگرد و شکل داخلی را پادساعتگرد رسم می‌کنیم، یا شکل بیرونی را پادساعتگرد و شکل داخلی را ساعتگرد.

```html hidden
<canvas id="canvas" width="150" height="150"></canvas>
```

```js
function draw() {
  const canvas = document.getElementById("canvas");
  const ctx = canvas.getContext("2d");

  ctx.beginPath();

  // Outer shape clockwise ⟳
  ctx.moveTo(0, 0);
  ctx.lineTo(150, 0);
  ctx.lineTo(75, 129.9);

  // Inner shape anticlockwise ↺
  ctx.moveTo(75, 20);
  ctx.lineTo(50, 60);
  ctx.lineTo(100, 60);

  ctx.fill();
}
```

```js hidden
draw();
```

{{EmbedLiveSample("Shapes_with_holes", "", "160")}}

در مثال بالا، مثلث بیرونی ساعتگرد حرکت می‌کند (به گوشهٔ بالا سمت چپ بروید، سپس به گوشهٔ بالا سمت راست خط بکشید و در پایین تمام کنید) و مثلث داخلی پادساعتگرد حرکت می‌کند (به بالا بروید، سپس به گوشهٔ پایین سمت چپ خط بکشید و در پایین سمت راست تمام کنید).

## اشیاء Path2D

همان‌طور که در مثال آخر دیدیم، برای رسم اشیاء روی بوم می‌توان مجموعه‌ای از مسیرها و دستورهای رسم داشت. برای ساده‌سازی کد و بهبود کارایی، شیء {{domxref("Path2D")}} که در نسخه‌های اخیر مرورگرها در دسترس است، به شما امکان می‌دهد این دستورهای رسم را کش یا ضبط کنید. می‌توانید مسیرهای خود را به‌سرعت پخش کنید.

بیایید ببینیم چگونه می‌توان یک شیء `Path2D` ساخت:

- {{domxref("Path2D.Path2D", "Path2D()")}}
  - : سازندهٔ **`Path2D()`** یک شیء `Path2D` تازه نمونه‌سازی‌شده را برمی‌گرداند؛ به‌صورت اختیاری با یک مسیر دیگر به‌عنوان آرگومان (یک کپی ایجاد می‌کند)، یا به‌صورت اختیاری با رشته‌ای شامل داده‌های [مسیر SVG](/en-US/docs/Web/SVG/Tutorials/SVG_from_scratch/Paths).

```js
new Path2D(); // empty path object
new Path2D(path); // copy from another Path2D object
new Path2D(d); // path from SVG path data
```

همهٔ [روش‌های مسیر](/en-US/docs/Web/API/CanvasRenderingContext2D#paths) مانند `moveTo`، `rect`، `arc` یا `quadraticCurveTo` و غیره که در بالا با آن‌ها آشنا شدیم، روی اشیاء `Path2D` در دسترس هستند.

API مربوط به `Path2D` همچنین راهی برای ترکیب مسیرها با استفاده از روش `addPath` اضافه می‌کند. این می‌تواند مفید باشد، مثلاً وقتی می‌خواهید اشیاء را از چند مؤلفه بسازید.

- {{domxref("Path2D.addPath", "Path2D.addPath(path [, transform])")}}
  - : یک مسیر را با یک ماتریس تبدیل اختیاری به مسیر جاری اضافه می‌کند.

### مثال Path2D

در این مثال، یک مستطیل و یک دایره ایجاد می‌کنیم. هر دو به‌عنوان یک شیء `Path2D` ذخیره می‌شوند تا برای استفاده‌های بعدی در دسترس باشند. با API جدید `Path2D`، چندین روش به‌روزرسانی شده‌اند تا به‌صورت اختیاری یک شیء `Path2D` را به‌جای مسیر جاری بپذیرند. در اینجا، `stroke` و `fill` با آرگومان مسیر برای رسم هر دو شیء روی بوم استفاده می‌شوند.

```html hidden
<canvas id="canvas" width="130" height="100"></canvas>
```

```js
function draw() {
  const canvas = document.getElementById("canvas");
  const ctx = canvas.getContext("2d");

  const rectangle = new Path2D();
  rectangle.rect(10, 10, 50, 50);

  const circle = new Path2D();
  circle.arc(100, 35, 25, 0, 2 * Math.PI);

  ctx.stroke(rectangle);
  ctx.fill(circle);
}
```

```js hidden
draw();
```

{{EmbedLiveSample("Path2D_example", "", "110")}}

### استفاده از مسیرهای SVG

یکی دیگر از ویژگی‌های قدرتمند API جدید `Path2D` در بوم، استفاده از [داده‌های مسیر SVG](/en-US/docs/Web/SVG/Tutorials/SVG_from_scratch/Paths) برای مقداردهی اولیهٔ مسیرها روی بوم شماست. این امکان به شما اجازه می‌دهد داده‌های مسیر را جابه‌جا کنید و در هر دو محیط SVG و بوم دوباره از آن‌ها استفاده کنید.

مسیر به نقطهٔ (`M10 10`) می‌رود و سپس ۸۰ واحد به سمت راست حرکت افقی می‌کند (`h 80`)، سپس ۸۰ واحد به پایین (`v 80`)، سپس ۸۰ واحد به سمت چپ (`h -80`) و در نهایت به نقطهٔ شروع بازمی‌گردد (`z`). می‌توانید این مثال را در صفحهٔ [سازندهٔ `Path2D`](/en-US/docs/Web/API/Path2D/Path2D#using_svg_paths) ببینید.

```js
const p = new Path2D("M10 10 h 80 v 80 h -80 Z");
```

{{PreviousNext("Web/API/Canvas_API/Tutorial/Basic_usage", "Web/API/Canvas_API/Tutorial/Applying_styles_and_colors")}}