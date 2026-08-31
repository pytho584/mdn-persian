---
title: "Transformations"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Transformations"
translated_by: "n8n + AI"
---

---
title: Transformations
slug: Web/API/Canvas_API/Tutorial/Transformations
page-type: guide
---

{{DefaultAPISidebar("Canvas API")}} {{PreviousNext("Web/API/Canvas_API/Tutorial/Using_images", "Web/API/Canvas_API/Tutorial/Compositing")}}

پیش‌تر در این آموزش با [شبکهٔ canvas](/en-US/docs/Web/API/Canvas_API/Tutorial/Drawing_shapes) و **فضای مختصات** آشنا شدیم. تاکنون فقط از شبکهٔ پیش‌فرض استفاده کرده و اندازهٔ کلی canvas را متناسب با نیاز خود تغییر می‌دادیم. با استفاده از تبدیل‌ها (transformations) راه‌های قدرتمندتری برای انتقال مبدأ به موقعیت دیگر، چرخاندن شبکه و حتی مقیاس‌دهی آن وجود دارد.

## ذخیره و بازیابی حالت

پیش از بررسی روش‌های تبدیل، به دو روش دیگر نگاه می‌کنیم که به محض شروع به ترسیم نقشه‌های پیچیده‌تر، ضروری می‌شوند.

- {{domxref("CanvasRenderingContext2D.save", "save()")}}
  - : کل حالت canvas را ذخیره می‌کند.
- {{domxref("CanvasRenderingContext2D.restore", "restore()")}}
  - : آخرین حالت ذخیره‌شدهٔ canvas را بازیابی می‌کند.

حالت‌های Canvas در یک پشته (stack) ذخیره می‌شوند. هر بار که متد `save()` فراخوانی می‌شود، حالت فعلی ترسیم به پشته اضافه می‌شود. یک حالت ترسیم شامل موارد زیر است:

- تبدیل‌هایی که اعمال شده‌اند (یعنی `translate`، `rotate` و `scale` – به زیر مراجعه کنید).
- مقادیر فعلی ویژگی‌های زیر:
  - {{domxref("CanvasRenderingContext2D.strokeStyle", "strokeStyle")}}
  - {{domxref("CanvasRenderingContext2D.fillStyle", "fillStyle")}}
  - {{domxref("CanvasRenderingContext2D.globalAlpha", "globalAlpha")}}
  - {{domxref("CanvasRenderingContext2D.lineWidth", "lineWidth")}}
  - {{domxref("CanvasRenderingContext2D.lineCap", "lineCap")}}
  - {{domxref("CanvasRenderingContext2D.lineJoin", "lineJoin")}}
  - {{domxref("CanvasRenderingContext2D.miterLimit", "miterLimit")}}
  - {{domxref("CanvasRenderingContext2D.lineDashOffset", "lineDashOffset")}}
  - {{domxref("CanvasRenderingContext2D.shadowOffsetX", "shadowOffsetX")}}
  - {{domxref("CanvasRenderingContext2D.shadowOffsetY", "shadowOffsetY")}}
  - {{domxref("CanvasRenderingContext2D.shadowBlur", "shadowBlur")}}
  - {{domxref("CanvasRenderingContext2D.shadowColor", "shadowColor")}}
  - {{domxref("CanvasRenderingContext2D.globalCompositeOperation", "globalCompositeOperation")}}
  - {{domxref("CanvasRenderingContext2D.font", "font")}}
  - {{domxref("CanvasRenderingContext2D.textAlign", "textAlign")}}
  - {{domxref("CanvasRenderingContext2D.textBaseline", "textBaseline")}}
  - {{domxref("CanvasRenderingContext2D.direction", "direction")}}
  - {{domxref("CanvasRenderingContext2D.imageSmoothingEnabled", "imageSmoothingEnabled")}}.
- [مسیر برش (clipping path)](/en-US/docs/Web/API/Canvas_API/Tutorial/Compositing#clipping_paths) فعلی، که در بخش بعدی خواهیم دید.

می‌توانید هر چند بار که می‌خواهید متد `save()` را فراخوانی کنید. هر بار که متد `restore()` فراخوانی می‌شود، آخرین حالت ذخیره‌شده از پشته خارج شده و تمام تنظیمات ذخیره‌شده بازیابی می‌شوند.

### یک مثال از ذخیره و بازیابی حالت canvas

```js
function draw() {
  const ctx = document.getElementById("canvas").getContext("2d");

  ctx.fillRect(0, 0, 150, 150); // یک مستطیل سیاه با تنظیمات پیش‌فرض رسم کنید
  ctx.save(); // حالت پیش‌فرض اصلی را ذخیره کنید

  ctx.fillStyle = "#0099ff"; // تغییراتی در تنظیمات ذخیره‌شده اعمال کنید
  ctx.fillRect(15, 15, 120, 120); // یک مستطیل آبی با تنظیمات جدید رسم کنید
  ctx.save(); // حالت فعلی را ذخیره کنید

  ctx.fillStyle = "white"; // تغییراتی در تنظیمات ذخیره‌شده اعمال کنید
  ctx.globalAlpha = 0.5;
  ctx.fillRect(30, 30, 90, 90); // یک مستطیل ۵۰٪ سفید با جدیدترین تنظیمات رسم کنید

  ctx.restore(); // به حالت قبلی بازگردید
  ctx.fillRect(45, 45, 60, 60); // یک مستطیل با تنظیمات آبی بازیابی‌شده رسم کنید

  ctx.restore(); // به حالت اصلی بازگردید
  ctx.fillRect(60, 60, 30, 30); // یک مستطیل با تنظیمات سیاه بازیابی‌شده رسم کنید
}
```

```html hidden
<canvas id="canvas" width="150" height="150"></canvas>
```

```js hidden
draw();
```

اولین مرحله رسم یک مستطیل بزرگ با تنظیمات پیش‌فرض است. سپس این حالت را ذخیره کرده و رنگ پر کردن را تغییر می‌دهیم. سپس مستطیل دوم کوچک‌تر آبی را رسم کرده و حالت را ذخیره می‌کنیم. دوباره برخی تنظیمات رسم را تغییر داده و سومین مستطیل نیمه‌شفاف سفید را رسم می‌کنیم.

تا اینجا بسیار شبیه به کارهایی است که در بخش‌های قبلی انجام دادیم. اما هنگامی که اولین دستور `restore()` را فراخوانی می‌کنیم، بالاترین حالت رسم از پشته حذف شده و تنظیمات بازیابی می‌شوند. اگر حالت را با `save()` ذخیره نکرده بودیم، برای بازگشت به حالت قبلی باید رنگ پر کردن و شفافیت را به‌صورت دستی تغییر می‌دادیم. این کار برای دو ویژگی آسان است، اما اگر ویژگی‌های بیشتری داشته باشیم، کد ما خیلی سریع طولانی می‌شود.

هنگامی که دستور `restore()` دوم فراخوانی می‌شود، حالت اصلی (حالتی که قبل از اولین فراخوانی `save` تنظیم کرده بودیم) بازیابی شده و آخرین مستطیل دوباره به رنگ سیاه رسم می‌شود.

{{EmbedLiveSample("A_save_and_restore_canvas_state_example", "", "160")}}

## انتقال (Translate)

اولین روش از روش‌های تبدیل که بررسی می‌کنیم `translate()` است. این روش برای جابه‌جایی canvas و مبدأ آن به نقطه‌ای متفاوت در شبکه استفاده می‌شود.

- {{domxref("CanvasRenderingContext2D.translate", "translate(x, y)")}}
  - : Canvas و مبدأ آن را روی شبکه جابه‌جا می‌کند. `x` فاصلهٔ افقی و `y` فاصلهٔ عمودی جابه‌جایی را مشخص می‌کند.

![Canvas از نقطهٔ مبدأ خود روی شبکه به اندازهٔ 'x' واحد به صورت افقی و 'y' واحد به صورت عمودی به پایین و راست منتقل (یا ترجمه) می‌شود.](canvas_grid_translate.png)

توصیه می‌شود قبل از انجام هر تبدیل، حالت canvas را ذخیره کنید. در بیشتر موارد، فراخوانی متد `restore` آسان‌تر از انجام یک انتقال معکوس برای بازگشت به حالت اولیه است. همچنین اگر درون یک حلقه در حال انتقال هستید و حالت canvas را ذخیره و بازیابی نمی‌کنید، ممکن است قسمتی از رسم خود را از دست بدهید، زیرا خارج از لبهٔ canvas رسم شده است.

### یک مثال از `translate`

این مثال برخی از مزایای انتقال مبدأ canvas را نشان می‌دهد. بدون متد `translate()`، همهٔ مستطیل‌ها در یک موقعیت (0,0) رسم می‌شدند. متد `translate()` همچنین به ما این آزادی را می‌دهد که مستطیل را در هر جایی از canvas قرار دهیم بدون اینکه نیاز به تنظیم دستی مختصات در تابع `fillRect()` داشته باشیم. این کار درک و استفاده از آن را کمی آسان‌تر می‌کند.

در تابع `draw()`، تابع `fillRect()` را نه بار با استفاده از دو حلقه `for` فراخوانی می‌کنیم. در هر حلقه، canvas انتقال داده می‌شود، مستطیل رسم می‌شود و canvas به حالت اولیه خود بازگردانده می‌شود. توجه کنید که فراخوانی `fillRect()` هر بار از مختصات یکسانی استفاده می‌کند و برای تنظیم موقعیت رسم به `translate()` وابسته است.

```js
function draw() {
  const ctx = document.getElementById("canvas").getContext("2d");
  for (let i = 0; i < 3; i++) {
    for (let j = 0; j < 3; j++) {
      ctx.save();
      ctx.fillStyle = `rgb(${51 * i} ${255 - 51 * i} 255)`;
      ctx.translate(10 + j * 50, 10 + i * 50);
      ctx.fillRect(0, 0, 25, 25);
      ctx.restore();
    }
  }
}
```

```html hidden
<canvas id="canvas" width="150" height="150"></canvas>
```

```js hidden
draw();
```

{{EmbedLiveSample("A_translate_example", "", "160")}}

## چرخش (Rotate)

دومین روش تبدیل `rotate()` است. از آن برای چرخاندن canvas حول مبدأ فعلی استفاده می‌کنیم.

- {{domxref("CanvasRenderingContext2D.rotate", "rotate(angle)")}}
  - : Canvas را حول مبدأ فعلی به اندازهٔ `angle` رادیان در جهت عقربه‌های ساعت می‌چرخاند.

![نقطهٔ مبدأ پیش‌فرض در بالا سمت چپ است، ۰ درجه افقی و به سمت راست است. نقطهٔ چرخش از نقطهٔ مبدأ شروع شده و در جهت عقربه‌های ساعت می‌چرخد.](canvas_grid_rotate.png)

نقطهٔ مرکز چرخش همواره مبدأ canvas است. برای تغییر نقطهٔ مرکز، باید با استفاده از متد `translate()` canvas را جابه‌جا کنیم.

### یک مثال از `rotate`

در این مثال، از متد `rotate()` برای چرخاندن یک مستطیل ابتدا از مبدأ canvas و سپس از مرکز خود مستطیل با کمک `translate()` استفاده می‌کنیم.

> [!NOTE]
> زاویه‌ها بر حسب رادیان هستند، نه درجه. برای تبدیل، از این فرمول استفاده می‌کنیم: `radians = (Math.PI/180)*degrees`.

```js
function draw() {
  const ctx = document.getElementById("canvas").getContext("2d");

  // مستطیل‌های سمت چپ، چرخش از مبدأ canvas
  ctx.save();
  // مستطیل آبی
  ctx.fillStyle = "#0095DD";
  ctx.fillRect(30, 30, 100, 100);
  ctx.rotate((Math.PI / 180) * 25);
  // مستطیل خاکستری
  ctx.fillStyle = "#4D4E53";
  ctx.fillRect(30, 30, 100, 100);
  ctx.restore();

  // مستطیل‌های سمت راست، چرخش از مرکز مستطیل
  // رسم مستطیل آبی
  ctx.fillStyle = "#0095DD";
  ctx.fillRect(150, 30, 100, 100);

  ctx.translate(200, 80); // انتقال به مرکز مستطیل
  // x = x + 0.5 * width
  // y = y + 0.5 * height
  ctx.rotate((Math.PI / 180) * 25); // چرخش
  ctx.translate(-200, -80); // انتقال به عقب

  // رسم مستطیل خاکستری
  ctx.fillStyle = "#4D4E53";
  ctx.fillRect(150, 30, 100, 100);
}
```

برای چرخاندن مستطیل حول مرکز خود، canvas را به مرکز مستطیل منتقل می‌کنیم، سپس canvas را می‌چرخانیم، دوباره canvas را به 0,0 برمی‌گردانیم و سپس مستطیل را رسم می‌کنیم.

```html hidden
<canvas id="canvas" width="300" height="200"></canvas>
```

```js hidden
draw();
```

{{EmbedLiveSample("A_rotate_example", "", "220")}}

## مقیاس‌دهی (Scale)

روش تبدیل بعدی مقیاس‌دهی است. از آن برای افزایش یا کاهش واحدها در شبکهٔ canvas خود استفاده می‌کنیم. این می‌تواند برای رسم اشکال و بیت‌مپ‌های کوچک‌شده یا بزرگ‌شده استفاده شود.

- {{domxref("CanvasRenderingContext2D.scale", "scale(x, y)")}}
  - : واحدهای canvas را به صورت افقی به اندازهٔ x و به صورت عمودی به اندازهٔ y مقیاس می‌کند. هر دو پارامتر اعداد حقیقی هستند. مقادیر کوچک‌تر از 1.0 اندازهٔ واحد را کاهش می‌دهند و مقادیر بالای 1.0 اندازهٔ واحد را افزایش می‌دهند. مقادیر 1.0 واحدها را به همان اندازه نگه می‌دارند.

با استفاده از اعداد منفی می‌توانید بازتاب محور (axis mirroring) انجام دهید (مثلاً با استفاده از `translate(0,canvas.height); scale(1,-1);` سیستم مختصات دکارتی معروف را خواهید داشت که مبدأ آن در گوشهٔ پایین سمت چپ است).

به طور پیش‌فرض، یک واحد در canvas دقیقاً یک پیکسل است. اگر مثلاً ضریب مقیاس 0.5 را اعمال کنیم، واحد حاصل 0.5 پیکسل می‌شود و بنابراین اشکال با نصف اندازه رسم می‌شوند. به همین ترتیب، تنظیم ضریب مقیاس به 2.0 اندازهٔ واحد را افزایش می‌دهد و یک واحد اکنون دو پیکسل می‌شود. این باعث می‌شود اشکال دو برابر بزرگتر رسم شوند.

### یک مثال از `scale`

در این مثال آخر، اشکالی را با ضرایب مقیاس مختلف رسم می‌کنیم.

```js
function draw() {
  const ctx = document.getElementById("canvas").getContext("2d");

  // رسم یک مستطیل ساده، اما با مقیاس‌دهی
  ctx.save();
  ctx.scale(10, 3);
  ctx.fillRect(1, 10, 10, 10);
  ctx.restore();

  // بازتاب افقی
  ctx.scale(-1, 1);
  ctx.font = "48px serif";
  ctx.fillText("MDN", -135, 120);
}
```

```html hidden
<canvas id="canvas" width="150" height="150"></canvas>
```

```js hidden
draw();
```

{{EmbedLiveSample("A_scale_example", "", "160")}}

## تبدیل‌ها (Transforms)

در نهایت، روش‌های تبدیل زیر امکان تغییرات مستقیم در ماتریس تبدیل را فراهم می‌کنند.

- {{domxref("CanvasRenderingContext2D.transform", "transform(a, b, c, d, e, f)")}}
  - : ماتریس تبدیل فعلی را در ماتریس توصیف‌شده توسط آرگومان‌هایش ضرب می‌کند. ماتریس تبدیل به صورت زیر است:

    <!-- prettier-ignore-start -->

    <math display="block">
      <semantics><mrow><mo>[</mo><mtable columnalign="center center center" rowspacing="0.5ex"><mtr><mtd><mi>a</mi></mtd><mtd><mi>c</mi></mtd><mtd><mi>e</mi></mtd></mtr><mtr><mtd><mi>b</mi></mtd><mtd><mi>d</mi></mtd><mtd><mi>f</mi></mtd></mtr><mtr><mtd><mn>0</mn></mtd><mtd><mn>0</mn></mtd><mtd><mn>1</mn></mtd></mtr></mtable><mo>]</mo></mrow><annotation encoding="TeX">\left[ \begin{array}{ccc} a & c & e \\ b & d & f \\ 0 & 0 & 1 \end{array} \right]</annotation></semantics>
    </math>
    <!-- prettier-ignore-end -->

    اگر هر یک از آرگومان‌ها [`Infinity`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Infinity) باشد، ماتریس تبدیل باید به‌جای پرتاب استثنا توسط متد، به‌عنوان نامتناهی علامت‌گذاری شود.

پارامترهای این تابع عبارتند از:

- `a` (`m11`)
  - : مقیاس افقی.
- `b` (`m12`)
  - : کج‌سازی افقی (horizontal skewing).
- `c` (`m21`)
  - : کج‌سازی عمودی (vertical skewing).
- `d` (`m22`)
  - : مقیاس عمودی.
- `e` (`dx`)
  - : جابه‌جایی افقی.
- `f` (`dy`)
  - : جابه‌جایی عمودی.
- {{domxref("CanvasRenderingContext2D.setTransform", "setTransform(a, b, c, d, e, f)")}}
  - : تبدیل فعلی را به ماتریس همانی بازنشانی می‌کند و سپس متد `transform()` را با همان آرگومان‌ها فراخوانی می‌کند. این کار اساساً تبدیل فعلی را لغو کرده و سپس تبدیل مشخص‌شده را در یک مرحله تنظیم می‌کند.
- {{domxref("CanvasRenderingContext2D.resetTransform", "resetTransform()")}}
  - : تبدیل فعلی را به ماتریس همانی بازنشانی می‌کند. این معادل فراخوانی `ctx.setTransform(1, 0, 0, 1, 0, 0);` است.

### مثال برای `transform` و `setTransform`

```js
function draw() {
  const ctx = document.getElementById("canvas").getContext("2d");

  const sin = Math.sin(Math.PI / 6);
  const cos = Math.cos(Math.PI / 6);
  ctx.translate(100, 100);
  let c = 0;
  for (let i = 0; i <= 12; i++) {
    c = Math.floor((255 / 12) * i);
    ctx.fillStyle = `rgb(${c} ${c} ${c})`;
    ctx.fillRect(0, 0, 100, 10);
    ctx.transform(cos, sin, -sin, cos, 0, 0);
  }

  ctx.setTransform(-1, 0, 0, 1, 100, 100);
  ctx.fillStyle = "rgb(255 128 255 / 50%)";
  ctx.fillRect(0, 50, 100, 100);
}
```

```html hidden
<canvas id="canvas" width="200" height="250"></canvas>
```

```js hidden
draw();
```

{{EmbedLiveSample("Example_for_transform_and_setTransform", "", "260")}}

{{PreviousNext("Web/API/Canvas_API/Tutorial/Using_images", "Web/API/Canvas_API/Tutorial/Compositing")}}