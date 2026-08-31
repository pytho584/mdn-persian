---
title: "CanvasRenderingContext2D: transform() method"
---

---
title: "CanvasRenderingContext2D: transform() method"
short-title: transform()
slug: Web/API/CanvasRenderingContext2D/transform
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.transform
---

{{APIRef("Canvas API")}}

متد **`CanvasRenderingContext2D.transform()`** در Canvas 2D API، تبدیل فعلی را در ماتریس توصیف‌شده توسط آرگومان‌های این متد ضرب می‌کند. با این کار می‌توانید بافت (context) را مقیاس‌بندی کنید، بچرخانید، انتقال دهید (جابه‌جا کنید) و اریب کنید.

> [!NOTE]
> همچنین به متد {{domxref("CanvasRenderingContext2D.setTransform()", "setTransform()")}} مراجعه کنید که تبدیل فعلی را به ماتریس همانی بازنشانی می‌کند و سپس `transform()` را فراخوانی می‌کند.

## نحو

```js-nolint
transform(a, b, c, d, e, f)
```

ماتریس تبدیل به صورت زیر توصیف می‌شود: <math><semantics><mrow><mo>[</mo><mtable columnalign="center center center" rowspacing="0.5ex"><mtr><mtd><mi>a</mi></mtd><mtd><mi>c</mi></mtd><mtd><mi>e</mi></mtd></mtr><mtr><mtd><mi>b</mi></mtd><mtd><mi>d</mi></mtd><mtd><mi>f</mi></mtd></mtr><mtr><mtd><mn>0</mn></mtd><mtd><mn>0</mn></mtd><mtd><mn>1</mn></mtd></mtr></mtable><mo>]</mo></mrow><annotation encoding="TeX">\left[ \begin{array}{ccc} a & c & e \\ b & d & f \\ 0 & 0 & 1 \end{array} \right]</annotation></semantics></math>.

### پارامترها

- `a` (`m11`)
  - : درایهٔ سطر اول و ستون اول ماتریس.
- `b` (`m12`)
  - : درایهٔ سطر دوم و ستون اول ماتریس.
- `c` (`m21`)
  - : درایهٔ سطر اول و ستون دوم ماتریس.
- `d` (`m22`)
  - : درایهٔ سطر دوم و ستون دوم ماتریس.
- `e` (`m41`)
  - : درایهٔ سطر اول و ستون سوم ماتریس.
- `f` (`m42`)
  - : درایهٔ سطر دوم و ستون سوم ماتریس.

اگر نقطه‌ای در ابتدا مختصات <math><semantics><mrow><mo>(</mo><mi>x</mi><mo>,</mo><mi>y</mi><mo>)</mo></mrow><annotation encoding="TeX">(x, y)</annotation></semantics></math> را داشته باشد، پس از تبدیل مختصات آن به صورت <math><semantics><mrow><mo>(</mo><mi>a</mi><mi>x</mi><mo>+</mo><mi>c</mi><mi>y</mi><mo>+</mo><mi>e</mi><mo>,</mo><mi>b</mi><mi>x</mi><mo>+</mo><mi>d</mi><mi>y</mi><mo>+</mo><mi>f</mi><mo>)</mo></mrow><annotation encoding="TeX">(ax + cy + e, bx + dy + f)</annotation></semantics></math> خواهد بود. یعنی:

- `e` و `f` انتقال افقی و عمودی بافت را کنترل می‌کنند.
- وقتی `b` و `c` برابر `0` باشند، `a` و `d` مقیاس‌بندی افقی و عمودی بافت را کنترل می‌کنند.
- وقتی `a` و `d` برابر `1` باشند، `b` و `c` اریب‌سازی افقی و عمودی بافت را کنترل می‌کنند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### اریب کردن یک شکل

این مثال یک مستطیل را هم به‌صورت عمودی (`.2`) و هم به‌صورت افقی (`.8`) اریب می‌کند. مقیاس‌بندی و انتقال بدون تغییر باقی می‌مانند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.transform(1, 0.2, 0.8, 1, 0, 0);
ctx.fillRect(0, 0, 100, 100);
```

#### نتیجه

{{ EmbedLiveSample('Skewing_a_shape', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابطی که این متد را تعریف می‌کند: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.setTransform()")}}