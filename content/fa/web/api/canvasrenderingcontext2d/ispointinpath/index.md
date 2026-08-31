---
title: "CanvasRenderingContext2D: isPointInPath() method"
short-title: isPointInPath()
slug: Web/API/CanvasRenderingContext2D/isPointInPath
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.isPointInPath
---

{{APIRef("Canvas API")}}

متد **`CanvasRenderingContext2D.isPointInPath()`** در Canvas 2D API گزارش می‌دهد که آیا نقطهٔ مشخص‌شده در مسیر (path) فعلی قرار دارد یا خیر.

## نحو (Syntax)

```js-nolint
isPointInPath(x, y)
isPointInPath(x, y, fillRule)
isPointInPath(path, x, y)
isPointInPath(path, x, y, fillRule)
```

### پارامترها

- `x`
  - : مختصات نقطه بر روی محور x که بررسی می‌شود. این مقدار تحت تأثیر تبدیل (transformation) فعلی بافت (context) قرار نمی‌گیرد.
- `y`
  - : مختصات نقطه بر روی محور y که بررسی می‌شود. این مقدار تحت تأثیر تبدیل فعلی بافت قرار نمی‌گیرد.
- `fillRule`
  - : الگوریتمی که تعیین می‌کند نقطه داخل یا خارج مسیر باشد. مقادیر ممکن:
    - `nonzero`
      - : [قانون پیچش غیرصفر](https://en.wikipedia.org/wiki/Nonzero-rule). قانون پیش‌فرض.
    - `evenodd`
      - : [قانون پیچش زوج-فرد](https://en.wikipedia.org/wiki/Even%E2%80%93odd_rule).

- `path`
  - : یک مسیر از نوع {{domxref("Path2D")}} که باید نقطه در برابر آن بررسی شود. اگر مشخص نشود، مسیر فعلی استفاده می‌شود.

### مقدار بازگشتی

یک مقدار بولی که اگر نقطهٔ مشخص‌شده در مسیر فعلی یا مسیر مشخص‌شده قرار داشته باشد `true` است و در غیر این صورت `false`.

## مثال‌ها

### بررسی نقطه در مسیر فعلی

این مثال از متد `isPointInPath()` برای بررسی اینکه آیا نقطه‌ای داخل مسیر فعلی است استفاده می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
<p>در مسیر: <code id="result">false</code></p>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
const result = document.getElementById("result");

ctx.rect(10, 10, 100, 100);
ctx.fill();
result.innerText = ctx.isPointInPath(30, 70);
```

#### نتیجه

{{ EmbedLiveSample('Checking_a_point_in_the_current_path', 700, 220) }}

### بررسی نقطه در مسیر مشخص‌شده

هر بار که ماوس را حرکت می‌دهید، این مثال بررسی می‌کند که آیا مکان‌نما درون یک مسیر دایره‌ای `Path2D` قرار دارد یا خیر. اگر بله، دایره سبز می‌شود و در غیر این صورت قرمز می‌ماند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// ساخت دایره
const circle = new Path2D();
circle.arc(150, 75, 50, 0, 2 * Math.PI);
ctx.fillStyle = "red";
ctx.fill(circle);

// گوش دادن به حرکت ماوس
canvas.addEventListener("mousemove", (event) => {
  // بررسی اینکه آیا نقطه داخل دایره است
  const isPointInPath = ctx.isPointInPath(circle, event.offsetX, event.offsetY);
  ctx.fillStyle = isPointInPath ? "green" : "red";

  // رسم دایره
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  ctx.fill(circle);
});
```

#### نتیجه

{{ EmbedLiveSample('Checking_a_point_in_the_specified_path', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

### نکته ویژه Gecko

- پیش از Gecko 7.0 (Firefox 7.0 / Thunderbird 7.0 / SeaMonkey 2.4)، این متد به اشتباه مختصات نقطه‌ای را که بررسی می‌شد، پیش از مقایسه با مسیر، در ماتریس تبدیل فعلی ضرب نمی‌کرد. اکنون این متد حتی اگر بافت چرخیده، مقیاس‌شده یا به شکل دیگری تبدیل شده باشد، به درستی کار می‌کند.

## همچنین ببینید

- رابط تعریف‌کننده این متد: {{domxref("CanvasRenderingContext2D")}}