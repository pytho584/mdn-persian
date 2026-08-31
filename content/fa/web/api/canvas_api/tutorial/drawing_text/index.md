---
title: "Drawing text"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Drawing_text"
translated_by: "n8n + AI"
---

---
title: Drawing text
slug: Web/API/Canvas_API/Tutorial/Drawing_text
page-type: guide
---

{{DefaultAPISidebar("Canvas API")}} {{PreviousNext("Web/API/Canvas_API/Tutorial/Applying_styles_and_colors", "Web/API/Canvas_API/Tutorial/Using_images")}}

پس از اینکه در فصل قبل دیدیم چگونه [استایل‌ها و رنگ‌ها را اعمال کنیم](/fa/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors)، اکنون به نحوه رسم متن روی بوم (canvas) می‌پردازیم.

## رسم متن

زمینه رندر بوم دو روش برای نمایش متن ارائه می‌دهد:

- {{domxref("CanvasRenderingContext2D.fillText", "fillText(text, x, y [, maxWidth])")}}
  - : یک متن داده شده را در موقعیت (x,y) داده شده پر می‌کند. به صورت اختیاری با حداکثر عرض برای رسم.
- {{domxref("CanvasRenderingContext2D.strokeText", "strokeText(text, x, y [, maxWidth])")}}
  - : یک متن داده شده را در موقعیت (x,y) داده شده رسم می‌کند (فقط خط دور). به صورت اختیاری با حداکثر عرض برای رسم.

### یک مثال از `fillText`

متن با استفاده از `fillStyle` جاری پر می‌شود.

```js
function draw() {
  const ctx = document.getElementById("canvas").getContext("2d");
  ctx.font = "48px serif";
  ctx.fillText("Hello world", 10, 50);
}
```

```html hidden
<canvas id="canvas" width="300" height="100"></canvas>
```

```js hidden
draw();
```

{{EmbedLiveSample("A_fillText_example", 310, 110)}}

### یک مثال از `strokeText`

متن با استفاده از `strokeStyle` جاری رسم می‌شود (خط دور).

```js
function draw() {
  const ctx = document.getElementById("canvas").getContext("2d");
  ctx.font = "48px serif";
  ctx.strokeText("Hello world", 10, 50);
}
```

```html hidden
<canvas id="canvas" width="300" height="100"></canvas>
```

```js hidden
draw();
```

{{EmbedLiveSample("A_strokeText_example", 310, 110)}}

## استایل‌دهی به متن

در مثال‌های بالا قبلاً از ویژگی `font` برای بزرگ‌تر کردن متن نسبت به اندازه پیش‌فرض استفاده کرده‌ایم. چند ویژگی دیگر وجود دارد که به شما امکان می‌دهد نحوه نمایش متن روی بوم را تنظیم کنید:

- {{domxref("CanvasRenderingContext2D.font", "font = value")}}
  - : سبک متن فعلی هنگام رسم متن. این رشته از همان syntax ویژگی [CSS](/fa/docs/Web/CSS) {{cssxref("font")}} استفاده می‌کند. فونت پیش‌فرض 10px sans-serif است.
- {{domxref("CanvasRenderingContext2D.textAlign", "textAlign = value")}}
  - : تنظیم تراز متن. مقادیر ممکن: `start`, `end`, `left`, `right` یا `center`. مقدار پیش‌فرض `start` است.
- {{domxref("CanvasRenderingContext2D.textBaseline", "textBaseline = value")}}
  - : تنظیم تراز خط پایه. مقادیر ممکن: `top`, `hanging`, `middle`, `alphabetic`, `ideographic`, `bottom`. مقدار پیش‌فرض `alphabetic` است.
- {{domxref("CanvasRenderingContext2D.direction", "direction = value")}}
  - : جهت‌گیری. مقادیر ممکن: `ltr`, `rtl`, `inherit`. مقدار پیش‌فرض `inherit` است.

اگر قبلاً با CSS کار کرده باشید، این ویژگی‌ها ممکن است برای شما آشنا باشند.

نمودار زیر از [مشخصات HTML](https://html.spec.whatwg.org/multipage/canvas.html#text-styles) خطوط پایه مختلف پشتیبانی‌شده توسط ویژگی `textBaseline` را نشان می‌دهد.

![خط پایه em-over تقریباً در بالای حروف یک فونت قرار دارد، خط پایه hanging جایی است که برخی حروف مانند आ لنگر می‌خورند، خط پایه middle نصف راه بین خطوط پایه em-over و em-under است، خط پایه alphabetic جایی است که کاراکترهایی مانند Á, ÿ, f, و Ω لنگر می‌خورند، خط پایه ideographic-under جایی است که حروفی مانند 私 و 達 لنگر می‌خورند، و خط پایه em-under تقریباً در پایین حروف یک فونت قرار دارد. بالا و پایین جعبه مرزی می‌توانند از این خطوط پایه دور باشند، به دلیل حروفی که بسیار فراتر از خطوط پایه em-over و em-under گسترش می‌یابند.](baselines.png)

### یک مثال از `textBaseline`

این مثال مقادیر مختلف ویژگی `textBaseline` را نشان می‌دهد. برای اطلاعات بیشتر و مثال‌های دقیق به صفحه [`CanvasRenderingContext2D.textBaseline`](/fa/docs/Web/API/CanvasRenderingContext2D/textBaseline) مراجعه کنید.

```html hidden live-sample___textBaseline
<canvas id="canvas" width="400" height="100"></canvas>
```

```js live-sample___textBaseline
function draw() {
  const ctx = document.getElementById("canvas").getContext("2d");
  ctx.font = "48px serif";

  ctx.textBaseline = "hanging";
  ctx.strokeText("hanging", 10, 50);

  ctx.textBaseline = "middle";
  ctx.strokeText("middle", 250, 50);

  ctx.beginPath();
  ctx.moveTo(10, 50);
  ctx.lineTo(300, 50);
  ctx.stroke();
}
```

```js hidden live-sample___textBaseline
draw();
```

{{EmbedLiveSample('textBaseline', 310, 110)}}

## اندازه‌گیری پیشرفته متن

در صورت نیاز به اطلاعات دقیق‌تر درباره متن، روش زیر به شما امکان اندازه‌گیری آن را می‌دهد.

- {{domxref("CanvasRenderingContext2D.measureText", "measureText()")}}
  - : یک شی {{domxref("TextMetrics")}} شامل عرض (به پیکسل) که متن مشخص شده در سبک متن فعلی رسم خواهد شد، برمی‌گرداند.

قطعه کد زیر نحوه اندازه‌گیری یک متن و دریافت عرض آن را نشان می‌دهد.

```js
function draw() {
  const ctx = document.getElementById("canvas").getContext("2d");
  const text = ctx.measureText("foo"); // TextMetrics object
  text.width; // 16;
}
```

## ملاحظات دسترسی‌پذیری

عنصر `<canvas>` فقط یک نقشه بیت (bitmap) است و اطلاعاتی درباره اشیاء رسم شده ارائه نمی‌دهد. متنی که روی بوم نوشته می‌شود می‌تواند باعث مشکلات خوانایی برای کاربرانی شود که از بزرگنمایی صفحه استفاده می‌کنند. پیکسل‌های داخل یک عنصر canvas مقیاس‌پذیر نیستند و با بزرگنمایی تار می‌شوند. این به دلیل این است که آنها یک بردار نیستند، بلکه مجموعه‌ای از پیکسل‌ها به شکل حروف هستند. هنگام بزرگنمایی روی آن، پیکسل‌ها بزرگتر می‌شوند.

محتوای Canvas مانند HTML معنایی در معرض ابزارهای دسترسی‌پذیری قرار نمی‌گیرد. به طور کلی، باید از استفاده از canvas در یک وب‌سایت یا برنامه قابل دسترس خودداری کنید. یک جایگزین استفاده از عناصر HTML یا SVG به جای canvas است.

{{PreviousNext("Web/API/Canvas_API/Tutorial/Applying_styles_and_colors", "Web/API/Canvas_API/Tutorial/Using_images")}}