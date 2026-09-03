---
title: "Path2D: addPath() method"
---

---
title: "Path2D: addPath() method"
short-title: addPath()
slug: Web/API/Path2D/addPath
page-type: web-api-instance-method
browser-compat: api.Path2D.addPath
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

متد **`Path2D.addPath()`** در Canvas 2D API یک شیء {{domxref("Path2D")}} را به یک شیء `Path2D` دیگر اضافه می‌کند.

## سینتکس

```js-nolint
addPath(path)
addPath(path, transform)
```

### پارامترها

- `path`
  - : مسیر {{domxref("Path2D")}} که باید اضافه شود.
- `transform` {{optional_inline}}
  - : یک {{domxref("DOMMatrix")}} که به‌عنوان ماتریس تبدیل برای مسیر اضافه‌شده استفاده می‌شود. (از نظر فنی، شیئی که همان ویژگی‌های یک شیء `DOMMatrix` را دارد.)

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### افزودن مسیر به یک مسیر موجود

این مثال یک مسیر را به مسیر دیگری اضافه می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

ابتدا، دو شیء جداگانه از {{domxref("Path2D")}} می‌سازیم که هرکدام شامل یک مستطیل ایجادشده با استفاده از متد {{domxref("CanvasRenderingContext2D.rect()", "rect()")}} است. سپس با استفاده از {{Domxref("DOMMatrix.DOMMatrix", "DOMMatrix()")}} یک ماتریس می‌سازیم. سپس با استفاده از `addPath()`، مسیر دوم را به مسیر اول اضافه می‌کنیم و ماتریس را نیز برای جابه‌جایی مسیر دوم به سمت راست اعمال می‌کنیم. در پایان، مسیر اول (که اکنون هر دو مستطیل را شامل می‌شود) را با استفاده از {{domxref("CanvasRenderingContext2D.fill()", "fill()")}} رسم می‌کنیم.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// Create first path and add a rectangle
let p1 = new Path2D();
p1.rect(0, 0, 100, 150);

// Create second path and add a rectangle
let p2 = new Path2D();
p2.rect(0, 0, 100, 75);

// Create transformation matrix that moves 200 points to the right
let m = new DOMMatrix();
m.a = 1;
m.b = 0;
m.c = 0;
m.d = 1;
m.e = 200;
m.f = 0;

// Add second path to the first path
p1.addPath(p2, m);

// Draw the first path
ctx.fill(p1);
```

#### نتیجه

{{ EmbedLiveSample('Adding_a_path_to_an_existing_path', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده‌ی این متد: {{domxref("Path2D")}}