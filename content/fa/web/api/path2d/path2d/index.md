---
title: "Path2D: Path2D() constructor"
short-title: Path2D()
slug: Web/API/Path2D/Path2D
page-type: web-api-constructor
browser-compat: api.Path2D.Path2D
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

سازندهٔ `Path2D()` یک شیء `Path2D` جدید برمی‌گرداند. به‌صورت اختیاری می‌توان یک مسیر دیگر را به‌عنوان آرگومان به آن داد، که در این صورت یک کپی ساخته می‌شود. همچنین می‌توان رشته‌ای شامل داده‌های [مسیر SVG](/en-US/docs/Web/SVG/Tutorials/SVG_from_scratch/Paths) به آن داد تا مسیر جدید از روی آن توصیف ساخته شود.

## سینتکس

```js-nolint
new Path2D()
new Path2D(path)
new Path2D(d)
```

### پارامترها

- `path` {{optional_inline}}
  - : اگر این سازنده با یک شیء `Path2D` دیگر فراخوانده شود، یک کپی از آرگومان `path` ساخته می‌شود.
- `d` {{optional_inline}}
  - : اگر با رشته‌ای حاوی داده‌های [مسیر SVG](/en-US/docs/Web/SVG/Tutorials/SVG_from_scratch/Paths) فراخوانده شود، یک مسیر جدید از روی آن توصیف ساخته می‌شود.

## مثال‌ها

### ایجاد و کپی کردن مسیرها

این مثال یک مسیر `Path2D` را ایجاد و کپی می‌کند. ابتدا `path1` یک مسیر مستطیلی است. سپس `path1` را در `path2` کپی می‌کنیم و یک دایره به آن اضافه می‌کنیم. در نهایت، `path2` را خط‌کشی می‌کنیم که هم مستطیل و هم دایره را شامل می‌شود. توجه کنید که `path1` بدون تغییر باقی می‌ماند، حتی اگر هرگز آن را روی بوم (canvas) رسم نکنیم. تنها هدف آن نشان دادن این است که چگونه می‌توانید با تکیه بر مسیرهای موجود، یک مسیر پیچیده بسازید.

```html hidden
<canvas id="canvas"></canvas>
```

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

const path1 = new Path2D();
path1.rect(10, 10, 100, 100);

const path2 = new Path2D(path1);
path2.moveTo(220, 60);
path2.arc(170, 60, 50, 0, 2 * Math.PI);

ctx.stroke(path2);
```

{{ EmbedLiveSample('Creating_and_copying_paths', 700, 180) }}

### استفاده از مسیرهای SVG

این مثال با استفاده از [داده‌های مسیر SVG](/en-US/docs/Web/SVG/Tutorials/SVG_from_scratch/Paths) یک مسیر `Path2D` ایجاد می‌کند. مسیر به نقطهٔ (`M10 10`) حرکت می‌کند؛ سپس ۸۰ واحد به سمت راست (`h 80`)، ۸۰ واحد به پایین (`v 80`)، ۸۰ واحد به سمت چپ (`h -80`) حرکت کرده و در نهایت به نقطهٔ شروع بازمی‌گردد (`Z`).

```html hidden
<canvas id="canvas"></canvas>
```

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

const p = new Path2D("M10 10 h 80 v 80 h -80 Z");
ctx.fill(p);
```

{{ EmbedLiveSample('Using_SVG_paths', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Path2D")}}، واسطی که این سازنده به آن تعلق دارد.