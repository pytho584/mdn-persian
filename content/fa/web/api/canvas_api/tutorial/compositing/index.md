---
title: "ترکیب و برش (Compositing and clipping)"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Compositing"
translated_by: "n8n + AI"
---

---
title: Compositing and clipping
slug: Web/API/Canvas_API/Tutorial/Compositing
page-type: guide
---

{{DefaultAPISidebar("Canvas API")}} {{PreviousNext("Web/API/Canvas_API/Tutorial/Transformations", "Web/API/Canvas_API/Tutorial/Basic_animations")}}

در تمام [مثال‌های قبلی](/en-US/docs/Web/API/Canvas_API/Tutorial/Transformations)، اشکال همیشه یکی روی دیگری رسم می‌شدند. این برای بیشتر موقعیت‌ها کاملاً کافی است، اما ترتیب ساخت اشکال ترکیبی را محدود می‌کند. با این حال، می‌توانیم این رفتار را با تنظیم ویژگی `globalCompositeOperation` تغییر دهیم. علاوه بر این، ویژگی `clip` به ما امکان می‌دهد بخش‌های ناخواسته اشکال را پنهان کنیم.

## `globalCompositeOperation`

ما نه تنها می‌توانیم اشکال جدید را پشت اشکال موجود رسم کنیم، بلکه می‌توانیم از آن برای پوشاندن بخش‌هایی خاص، پاک کردن بخش‌هایی از بوم (محدود به مستطیل‌ها مانند روش {{domxref("CanvasRenderingContext2D.clearRect", "clearRect()")}} نیست) و موارد دیگر استفاده کنیم.

- {{domxref("CanvasRenderingContext2D.globalCompositeOperation", "globalCompositeOperation = type")}}
  - : این نوع عملیات ترکیب را هنگام رسم اشکال جدید تنظیم می‌کند، که type رشته‌ای است که یکی از دوازده عملیات ترکیب را مشخص می‌کند.

## مسیرهای برش (Clipping paths)

مسیر برش مانند یک شکل عادی بوم است اما به عنوان یک ماسک برای پنهان کردن بخش‌های ناخواسته اشکال عمل می‌کند. این در تصویر زیر نشان داده شده است. شکل ستاره قرمز مسیر برش ما است. هر چیزی که خارج از این مسیر باشد روی بوم رسم نمی‌شود.

![یک بوم با یک ستاره که با رنگ قرمز دور آن خط کشیده شده است. داخل ستاره شفاف است، همانطور که مربع‌های شبکه داخل ستاره به وضوح قابل مشاهده هستند در حالی که مربع‌های شبکه خارج از ستاره تار هستند.](canvas_clipping_path.png)

اگر مسیرهای برش را با ویژگی `globalCompositeOperation` که در بالا دیدیم مقایسه کنیم، دو حالت ترکیب را می‌بینیم که تقریباً همان اثر را در `source-in` و `source-atop` به دست می‌آورند. مهم‌ترین تفاوت‌های بین آن‌ها این است که مسیرهای برش هرگز واقعاً روی بوم رسم نمی‌شوند و مسیر برش هرگز با افزودن اشکال جدید تحت تأثیر قرار نمی‌گیرد. این امر مسیرهای برش را برای رسم چندین شکل در یک منطقه محدود ایده‌آل می‌کند.

در فصل درباره [رسم اشکال](/en-US/docs/Web/API/Canvas_API/Tutorial/Drawing_shapes) من فقط به روش‌های `stroke()` و `fill()` اشاره کردم، اما روش سومی也存在 که می‌توانیم با مسیرها استفاده کنیم، به نام `clip()`.

- {{domxref("CanvasRenderingContext2D.clip", "clip()")}}
  - : مسیر در حال ساخت را به مسیر برش فعلی تبدیل می‌کند.

شما از `clip()` به جای `closePath()` برای بستن یک مسیر و تبدیل آن به مسیر برش استفاده می‌کنید، به جای خط کشیدن یا پر کردن مسیر.

به طور پیش‌فرض، عنصر {{HTMLElement("canvas")}} دارای یک مسیر برش است که دقیقاً به اندازه خود بوم است. به عبارت دیگر، هیچ برشی رخ نمی‌دهد.

### یک مثال `clip`

در این مثال، از یک مسیر برش دایره‌ای برای محدود کردن رسم مجموعه‌ای از ستاره‌های تصادفی به یک منطقه خاص استفاده می‌کنیم.

```js
function draw() {
  const ctx = document.getElementById("canvas").getContext("2d");
  ctx.fillRect(0, 0, 150, 150);
  ctx.translate(75, 75);

  // Create a circular clipping path
  ctx.beginPath();
  ctx.arc(0, 0, 60, 0, Math.PI * 2, true);
  ctx.clip();

  // Draw background
  const linGrad = ctx.createLinearGradient(0, -75, 0, 75);
  linGrad.addColorStop(0, "#232256");
  linGrad.addColorStop(1, "#143778");

  ctx.fillStyle = linGrad;
  ctx.fillRect(-75, -75, 150, 150);

  generateStars(ctx);
}

function generateStars(ctx) {
  for (let j = 1; j < 50; j++) {
    ctx.save();
    ctx.fillStyle = "white";
    ctx.translate(
      75 - Math.floor(Math.random() * 150),
      75 - Math.floor(Math.random() * 150),
    );
    drawStar(ctx, Math.floor(Math.random() * 4) + 2);
    ctx.restore();
  }
}

function drawStar(ctx, r) {
  ctx.save();
  ctx.beginPath();
  ctx.moveTo(r, 0);
  for (let i = 0; i < 9; i++) {
    ctx.rotate(Math.PI / 5);
    if (i % 2 === 0) {
      ctx.lineTo((r / 0.525731) * 0.200811, 0);
    } else {
      ctx.lineTo(r, 0);
    }
  }
  ctx.closePath();
  ctx.fill();
  ctx.restore();
}
```

```html hidden
<canvas id="canvas" width="150" height="150"></canvas>
```

```js hidden
draw();
```

در چند خط اول کد، یک مستطیل سیاه به اندازه بوم به عنوان پس‌زمینه رسم می‌کنیم، سپس مبدأ را به مرکز منتقل می‌کنیم. در ادامه، مسیر برش دایره‌ای را با رسم یک کمان و فراخوانی `clip()` ایجاد می‌کنیم. مسیرهای برش نیز بخشی از حالت ذخیره‌شده بوم هستند. اگر می‌خواستیم مسیر برش اصلی را حفظ کنیم، می‌توانستیم وضعیت بوم را قبل از ایجاد مسیر جدید ذخیره کنیم.

هر چیزی که پس از ایجاد مسیر برش رسم می‌شود فقط در داخل آن مسیر ظاهر می‌شود. این را می‌توانید به وضوح در گرادیان خطی که بعداً رسم می‌شود ببینید. پس از آن، مجموعه‌ای از ۵۰ ستاره با موقعیت و اندازه تصادفی با استفاده از تابع سفارشی `drawStar()` رسم می‌شود. دوباره، ستاره‌ها فقط در داخل مسیر برش تعریف‌شده ظاهر می‌شوند.

{{EmbedLiveSample("A_clip_example", "", "160")}}

### مسیر برش معکوس

چیزی به نام ماسک برش معکوس وجود ندارد. با این حال، ما می‌توانیم یک ماسک تعریف کنیم که کل بوم را با یک مستطیل پر کند و سوراخی در آن برای قسمت‌هایی که می‌خواهید رد شوید داشته باشد. هنگام [رسم شکل با سوراخ](/en-US/docs/Web/API/Canvas_API/Tutorial/Drawing_shapes#shapes_with_holes)، باید سوراخ را در جهت مخالف شکل بیرونی رسم کنیم. در مثال زیر، یک سوراخ در آسمان ایجاد می‌کنیم.

یک مستطیل جهت رسم ندارد، اما طوری رفتار می‌کند که گویی آن را در جهت عقربه‌های ساعت رسم کرده‌ایم. به طور پیش‌فرض، دستور arc نیز در جهت عقربه‌های ساعت حرکت می‌کند، اما می‌توانیم جهت آن را با آخرین آرگومان تغییر دهیم.

```html hidden
<canvas id="canvas" width="150" height="150"></canvas>
```

```js
function draw() {
  const canvas = document.getElementById("canvas");
  const ctx = canvas.getContext("2d");
  ctx.translate(75, 75);

  // Clipping path
  ctx.beginPath();
  ctx.rect(-75, -75, 150, 150); // Outer rectangle
  ctx.arc(0, 0, 60, 0, Math.PI * 2, true); // Hole anticlockwise
  ctx.clip();

  // Draw background
  const linGrad = ctx.createLinearGradient(0, -75, 0, 75);
  linGrad.addColorStop(0, "#232256");
  linGrad.addColorStop(1, "#143778");

  ctx.fillStyle = linGrad;
  ctx.fillRect(-75, -75, 150, 150);

  generateStars(ctx);
}
```

```js hidden
function generateStars(ctx) {
  for (let j = 1; j < 50; j++) {
    ctx.save();
    ctx.fillStyle = "white";
    ctx.translate(
      75 - Math.floor(Math.random() * 150),
      75 - Math.floor(Math.random() * 150),
    );
    drawStar(ctx, Math.floor(Math.random() * 4) + 2);
    ctx.restore();
  }
}

function drawStar(ctx, r) {
  ctx.save();
  ctx.beginPath();
  ctx.moveTo(r, 0);
  for (let i = 0; i < 9; i++) {
    ctx.rotate(Math.PI / 5);
    if (i % 2 === 0) {
      ctx.lineTo((r / 0.525731) * 0.200811, 0);
    } else {
      ctx.lineTo(r, 0);
    }
  }
  ctx.closePath();
  ctx.fill();
  ctx.restore();
}

draw();
```

{{EmbedLiveSample("Hole_in_rectangle", "", "160")}}

{{PreviousNext("Web/API/Canvas_API/Tutorial/Transformations", "Web/API/Canvas_API/Tutorial/Basic_animations")}}