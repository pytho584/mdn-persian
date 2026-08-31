---
title: "CanvasRenderingContext2D: fill() method"
short-title: fill()
slug: Web/API/CanvasRenderingContext2D/fill
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.fill
---

{{APIRef("Canvas API")}}

متد
**`CanvasRenderingContext2D.fill()`**
از Canvas 2D API، مسیر جاری یا داده شده را با
{{domxref("CanvasRenderingContext2D.fillStyle", "fillStyle")}}
جاری پر می‌کند.

## نحو

```js-nolint
fill()
fill(path)
fill(fillRule)
fill(path, fillRule)
```

### پارامترها

- `fillRule`
  - : الگوریتمی که تعیین می‌کند یک نقطه داخل یا خارج ناحیه پر شدن است.
    مقادیر ممکن:
    - `nonzero`
      - : قاعده [non-zero winding rule](https://en.wikipedia.org/wiki/Nonzero-rule).
        قاعده پیش‌فرض.
    - `evenodd`
      - : قاعده [even-odd winding rule](https://en.wikipedia.org/wiki/Even%E2%80%93odd_rule).

- `path`
  - : یک مسیر {{domxref("Path2D")}} برای پر کردن.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### پر کردن یک مستطیل

این مثال یک مستطیل را با استفاده از متد `fill()` پر می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
ctx.rect(10, 10, 150, 100);
ctx.fill();
```

#### نتیجه

{{ EmbedLiveSample('Filling_a_rectangle', 700, 180) }}

### تعیین یک مسیر و یک fillRule

این مثال چند خط متقاطع را در یک شیء Path2D ذخیره می‌کند. سپس متد `fill()` برای رندر کردن شیء روی بوم به کار می‌رود. با استفاده از قانون `"evenodd"` یک حفره در مرکز شیء پرنشده باقی می‌ماند؛ به طور پیش‌فرض (با قانون `"nonzero"`) آن حفره نیز پر می‌شد.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// Create path
let region = new Path2D();
region.moveTo(30, 90);
region.lineTo(110, 20);
region.lineTo(240, 130);
region.lineTo(60, 130);
region.lineTo(190, 20);
region.lineTo(270, 90);
region.closePath();

// Fill path
ctx.fillStyle = "green";
ctx.fill(region, "evenodd");
```

#### نتیجه

{{ EmbedLiveSample('Specifying_a_path_and_a_fillRule', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این متد: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.fillStyle")}}