---
title: "CanvasRenderingContext2D: beginPath() method"
short-title: beginPath()
slug: Web/API/CanvasRenderingContext2D/beginPath
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.beginPath
---

{{APIRef("Canvas API")}}

متد
**`CanvasRenderingContext2D.beginPath()`**
در API Canvas 2D با خالی کردن فهرست زیرمسیرها (sub-paths)، یک مسیر جدید را شروع می‌کند. زمانی که می‌خواهید یک مسیر جدید ایجاد کنید، این متد را فراخوانی کنید.

> [!NOTE]
> برای ایجاد یک زیرمسیر جدید، یعنی زیرمسیری که با وضعیت فعلی بوم (canvas) مطابقت دارد، می‌توانید از {{domxref("CanvasRenderingContext2D.moveTo()")}} استفاده کنید.

## نحو (Syntax)

```js-nolint
beginPath()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### ایجاد مسیرهای مجزا

این مثال دو مسیر ایجاد می‌کند که هر کدام شامل یک خط هستند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

متد `beginPath()` قبل از شروع هر خط فراخوانی می‌شود تا بتوان خطوط را با رنگ‌های مختلف رسم کرد.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// مسیر اول
ctx.beginPath();
ctx.strokeStyle = "blue";
ctx.moveTo(20, 20);
ctx.lineTo(200, 20);
ctx.stroke();

// مسیر دوم
ctx.beginPath();
ctx.strokeStyle = "green";
ctx.moveTo(20, 20);
ctx.lineTo(120, 120);
ctx.stroke();
```

#### نتیجه

{{ EmbedLiveSample('Creating_distinct_paths', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- interfrace تعریف‌کننده این متد: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.closePath()")}}