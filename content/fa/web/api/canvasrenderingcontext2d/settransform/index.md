---
title: "CanvasRenderingContext2D: setTransform() method"
short-title: setTransform()
slug: Web/API/CanvasRenderingContext2D/setTransform
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.setTransform
---

{{APIRef("Canvas API")}}

متد **`CanvasRenderingContext2D.setTransform()`** در Canvas 2D API، تبدیل فعلی را به ماتریس همانندی (identity matrix) بازنشانی (بازنویسی) می‌کند و سپس تبدیلی را که توسط آرگومان‌های این متد توصیف شده اعمال می‌کند. این به شما امکان می‌دهد بافت (context) را مقیاس‌بندی، چرخش، انتقال (جابه‌جایی) و اریب کنید.

> [!NOTE]
> همچنین به متد {{domxref("CanvasRenderingContext2D.transform()", "transform()")}} مراجعه کنید؛ به‌جای بازنویسی ماتریس تبدیل فعلی، آن را در یک ماتریس داده‌شده ضرب می‌کند.

## نحو

```js-nolint
setTransform(a, b, c, d, e, f)
setTransform(matrix)
```

ماتریس تبدیل به این شکل توصیف می‌شود: <math><semantics><mrow><mo>[</mo><mtable columnalign="center center center" rowspacing="0.5ex"><mtr><mtd><mi>a</mi></mtd><mtd><mi>c</mi></mtd><mtd><mi>e</mi></mtd></mtr><mtr><mtd><mi>b</mi></mtd><mtd><mi>d</mi></mtd><mtd><mi>f</mi></mtd></mtr><mtr><mtd><mn>0</mn></mtd><mtd><mn>0</mn></mtd><mtd><mn>1</mn></mtd></mtr></mtable><mo>]</mo></mrow><annotation encoding="TeX">\left[ \begin{array}{ccc} a & c & e \\ b & d & f \\ 0 & 0 & 1 \end{array} \right]</annotation></semantics></math>.

این ماتریس تبدیل در سمت چپ بردار ستونی که نمایانگر هر نقطه‌ای است که روی بوم (canvas) رسم می‌شود ضرب می‌شود تا مختصات نهایی مورد استفاده روی بوم تولید شود.

### پارامترها

`setTransform()` دو نوع پارامتر می‌پذیرد. نوع قدیمی‌تر شامل چند پارامتر است که مؤلفه‌های جداگانه ماتریس تبدیل را برای تنظیم مشخص می‌کنند:

- `a` (`m11`)
  - : خانه‌ی سطر اول و ستون اول ماتریس.
- `b` (`m12`)
  - : خانه‌ی سطر دوم و ستون اول ماتریس.
- `c` (`m21`)
  - : خانه‌ی سطر اول و ستون دوم ماتریس.
- `d` (`m22`)
  - : خانه‌ی سطر دوم و ستون دوم ماتریس.
- `e` (`m41`)
  - : خانه‌ی سطر اول و ستون سوم ماتریس.
- `f` (`m42`)
  - : خانه‌ی سطر دوم و ستون سوم ماتریس.

به‌عنوان جایگزین، می‌توانید یک پارامتر واحد که یک شیء حاوی مقادیر بالا به‌عنوان ویژگی است را ارسال کنید. نام پارامترها کلیدهای ویژگی هستند و اگر هر دو نام مترادف وجود داشته باشند (مثلاً `m11` و `a`)، باید مقدار عددی یکسانی داشته باشند، در غیر این صورت یک {{jsxref("TypeError")}} پرتاب می‌شود. استفاده از فرم شیء اجازه می‌دهد برخی پارامترها حذف شوند — `a` و `d` به‌طور پیش‌فرض `1` و بقیه به‌طور پیش‌فرض `0` هستند.

اگر یک نقطه در ابتدا مختصات <math><semantics><mrow><mo>(</mo><mi>x</mi><mo>,</mo><mi>y</mi><mo>)</mo></mrow><annotation encoding="TeX">(x, y)</annotation></semantics></math> داشته باشد، پس از تبدیل مختصات آن <math><semantics><mrow><mo>(</mo><mi>a</mi><mi>x</mi><mo>+</mo><mi>c</mi><mi>y</mi><mo>+</mo><mi>e</mi><mo>,</mo><mi>b</mi><mi>x</mi><mo>+</mo><mi>d</mi><mi>y</mi><mo>+</mo><mi>f</mi><mo>)</mo></mrow><annotation encoding="TeX">(ax + cy + e, bx + dy + f)</annotation></semantics></math> خواهد بود. این یعنی:

- `e` و `f` انتقال افقی و عمودی بافت را کنترل می‌کنند.
- وقتی `b` و `c` صفر باشند، `a` و `d` مقیاس‌بندی افقی و عمودی بافت را کنترل می‌کنند.
- وقتی `a` و `d` برابر ۱ باشند، `b` و `c` اریب‌شدن افقی و عمودی بافت را کنترل می‌کنند.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

### اریب کردن یک شکل

این مثال یک مستطیل را هم به‌صورت عمودی (`.2`) و هم به‌صورت افقی (`.8`) اریب می‌کند. مقیاس‌بندی و انتقال بدون تغییر می‌مانند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.setTransform(1, 0.2, 0.8, 1, 0, 0);
ctx.fillRect(0, 0, 100, 100);
```

#### نتیجه

{{ EmbedLiveSample('Skewing_a_shape', 700, 180) }}

### دریافت و ارسال یک شیء DOMMatrix

در مثال زیر، دو عنصر {{htmlelement("canvas")}} داریم. با استفاده از نوع اول `setTransform()` یک تبدیل روی بافت عنصر اول اعمال می‌کنیم و یک مربع روی آن رسم می‌کنیم، سپس ماتریس را با استفاده از {{domxref("CanvasRenderingContext2D.getTransform()")}} از آن دریافت می‌کنیم.

سپس ماتریس دریافت‌شده را مستقیماً با ارسال شیء `DOMMatrix` به `setTransform()` (یعنی نوع دوم) روی بافت عنصر دوم اعمال می‌کنیم و یک دایره روی آن رسم می‌کنیم.

#### HTML

```html
<!-- First canvas (ctx1) -->
<canvas width="240"></canvas>
<!-- Second canvas (ctx2) -->
<canvas width="240"></canvas>
```

#### CSS

```css
canvas {
  border: 1px solid black;
}
```

#### JavaScript

```js
const canvases = document.querySelectorAll("canvas");
const ctx1 = canvases[0].getContext("2d");
const ctx2 = canvases[1].getContext("2d");

ctx1.setTransform(1, 0.2, 0.8, 1, 0, 0);
ctx1.fillRect(25, 25, 50, 50);

let storedTransform = ctx1.getTransform();
console.log(storedTransform);

ctx2.setTransform(storedTransform);
ctx2.beginPath();
ctx2.arc(50, 50, 50, 0, 2 * Math.PI);
ctx2.fill();
```

#### نتیجه

{{ EmbedLiveSample('Retrieving_and_passing_a_DOMMatrix_object', "100%", 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این متد: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.transform()")}}