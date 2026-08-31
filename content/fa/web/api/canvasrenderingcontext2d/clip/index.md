---
title: "CanvasRenderingContext2D: clip() method"
short-title: clip()
slug: Web/API/CanvasRenderingContext2D/clip
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.clip
---

{{APIRef("Canvas API")}}

متد
**`CanvasRenderingContext2D.clip()`**
در Canvas 2D API، مسیر فعلی یا مسیر داده‌شده را به ناحیه برش (clipping region) فعلی تبدیل می‌کند. ناحیه برش قبلی، در صورت وجود، با مسیر فعلی یا داده‌شده اشتراک داده می‌شود تا ناحیه برش جدید ایجاد شود.

در تصویر زیر، خط قرمز نشان‌دهنده یک ناحیه برش ستاره‌ای شکل است. فقط بخش‌هایی از الگوی شطرنجی که درون ناحیه برش قرار دارند، رسم می‌شوند.

![ناحیه برش ستاره‌ای شکل](canvas_clipping_path.png)

> [!NOTE]
> توجه داشته باشید که ناحیه برش فقط از اشکالی که به مسیر اضافه شده‌اند ساخته می‌شود. این ناحیه با اشکال اولیه‌ای که مستقیماً روی بوم رسم می‌شوند، مانند {{domxref("CanvasRenderingContext2D.fillRect()","fillRect()")}}، کار نمی‌کند. در عوض، باید از {{domxref("CanvasRenderingContext2D.rect()","rect()")}} برای افزودن یک شکل مستطیلی به مسیر قبل از فراخوانی `clip()` استفاده کنید.

> [!NOTE]
> مسیرهای برش را نمی‌توان مستقیماً بازگردانی کرد. قبل از فراخوانی `clip()` باید وضعیت بوم را با استفاده از {{domxref("CanvasRenderingContext2D/save", "save()")}} ذخیره کنید و پس از اتمام رسم در ناحیه برش‌خورده، آن را با استفاده از {{domxref("CanvasRenderingContext2D/restore", "restore()")}} بازیابی کنید.

## نحو (Syntax)

```js-nolint
clip()
clip(path)
clip(fillRule)
clip(path, fillRule)
```

### پارامترها

- `fillRule`
  - : الگوریتمی که تعیین می‌کند یک نقطه داخل یا خارج ناحیه برش قرار دارد. مقادیر ممکن:
    - `nonzero`
      - : [قانون پیچش غیرصفر](https://en.wikipedia.org/wiki/Nonzero-rule).
        قانون پیش‌فرض.
    - `evenodd`
      - : [قانون پیچش زوج-فرد](https://en.wikipedia.org/wiki/Even%E2%80%93odd_rule).

- `path`
  - : یک مسیر {{domxref("Path2D")}} که به عنوان ناحیه برش استفاده می‌شود.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

### یک ناحیه برش ساده

این مثال از متد `clip()` برای ایجاد یک ناحیه برش بر اساس شکل یک کمان دایره‌ای استفاده می‌کند. سپس دو مستطیل رسم می‌شوند؛ فقط بخش‌هایی که درون ناحیه برش قرار دارند، رندر می‌شوند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

ناحیه برش یک دایره کامل است که مرکز آن در (100, 75) و شعاع آن 50 است.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// ایجاد ناحیه برش دایره‌ای
ctx.beginPath();
ctx.arc(100, 75, 50, 0, Math.PI * 2);
ctx.clip();

// رسم چیزهایی که برش می‌خورند
ctx.fillStyle = "blue";
ctx.fillRect(0, 0, canvas.width, canvas.height);
ctx.fillStyle = "orange";
ctx.fillRect(0, 0, 100, 100);
```

#### نتیجه

{{ EmbedLiveSample('A_simple_clipping_region', 700, 180) }}

### مشخص کردن یک مسیر و fillRule

این مثال دو مستطیل را در یک شیء Path2D ذخیره می‌کند که سپس با استفاده از متد `clip()` به عنوان ناحیه برش فعلی تنظیم می‌شود. قانون `"evenodd"` سوراخی در محل اشتراک مستطیل‌های برش ایجاد می‌کند؛ به طور پیش‌فرض (با قانون `"nonzero"`)، هیچ سوراخی وجود نخواهد داشت.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// ایجاد مسیر برش
let region = new Path2D();
region.rect(80, 10, 20, 130);
region.rect(40, 50, 100, 50);
ctx.clip(region, "evenodd");

// رسم چیزهایی که برش می‌خورند
ctx.fillStyle = "blue";
ctx.fillRect(0, 0, canvas.width, canvas.height);
```

#### نتیجه

{{ EmbedLiveSample('Specifying_a_path_and_a_fillRule', 700, 180) }}

### ایجاد یک ناحیه برش پیچیده

این مثال از دو مسیر، یک دایره و یک مربع، برای ایجاد یک ناحیه برش پیچیده استفاده می‌کند. متد `clip()` دو بار فراخوانی می‌شود؛ ابتدا برای تنظیم ناحیه برش فعلی به دایره با استفاده از یک شیء `Path2D`، و سپس برای اشتراک ناحیه برش دایره‌ای با یک مربع. ناحیه برش نهایی شکلی است که نشان‌دهنده اشتراک دایره و مربع است.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// ایجاد دو مسیر برش
let circlePath = new Path2D();
circlePath.arc(150, 75, 75, 0, 2 * Math.PI);
let squarePath = new Path2D();
squarePath.rect(85, 10, 130, 130);

// تنظیم برش به دایره
ctx.clip(circlePath);
// تنظیم برش به اشتراک دایره و مربع
ctx.clip(squarePath);

// رسم چیزهایی که برش می‌خورند
ctx.fillStyle = "blue";
ctx.fillRect(0, 0, canvas.width, canvas.height);
```

#### نتیجه

{{ EmbedLiveSample('Creating_a_complex_clipping_region', 300, 150) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این متد: {{domxref("CanvasRenderingContext2D")}}