---
title: "CanvasRenderingContext2D: fillRect() method"
short-title: fillRect()
slug: Web/API/CanvasRenderingContext2D/fillRect
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.fillRect
---

{{APIRef("Canvas API")}}

متد **`CanvasRenderingContext2D.fillRect()`** در Canvas 2D API یک مستطیل رسم می‌کند که بر اساس {{domxref("CanvasRenderingContext2D.fillStyle", "fillStyle")}} کنونی پر می‌شود.

این متد مستقیماً روی بوم (canvas) رسم می‌کند و مسیر فعلی را تغییر نمی‌دهد؛ بنابراین هر فراخوانی بعدی {{domxref("CanvasRenderingContext2D.fill()", "fill()")}} یا {{domxref("CanvasRenderingContext2D.stroke()", "stroke()")}} هیچ تأثیری روی آن نخواهد داشت.

## نحو

```js-nolint
fillRect(x, y, width, height)
```

متد `fillRect()` یک مستطیل توپر رسم می‌کند که نقطه شروع آن در `(x, y)` است و اندازه آن با `width` و `height` مشخص می‌شود. سبک پر کردن با توجه به ویژگی `fillStyle` فعلی تعیین می‌شود.

### پارامترها

- `x`
  - : مختصات محور x نقطه شروع مستطیل.
- `y`
  - : مختصات محور y نقطه شروع مستطیل.
- `width`
  - : عرض مستطیل. مقادیر مثبت به سمت راست و مقادیر منفی به سمت چپ هستند.
- `height`
  - : ارتفاع مستطیل. مقادیر مثبت به سمت پایین و مقادیر منفی به سمت بالا هستند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### یک مستطیل توپر ساده

این مثال با استفاده از متد `fillRect()` یک مستطیل توپر سبز رسم می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### جاوااسکریپت

گوشه بالا-چپ مستطیل در نقطه (20, 10) قرار دارد. عرض آن ۱۵۰ و ارتفاع آن ۱۰۰ است.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
ctx.fillStyle = "green";
ctx.fillRect(20, 10, 150, 100);
```

#### نتیجه

{{ EmbedLiveSample('A_simple_filled_rectangle', 700, 180) }}

### پر کردن کل بوم

این قطعه‌کد کل بوم را با یک مستطیل پر می‌کند. این کار اغلب برای ایجاد پس‌زمینه‌ای مفید است که بتوان بعداً چیزهای دیگری را روی آن رسم کرد. برای این کار، ابعاد مستطیل را برابر با ویژگی‌های `width` و `height` عنصر {{HtmlElement("canvas")}} قرار می‌دهیم.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
ctx.fillRect(0, 0, canvas.width, canvas.height);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- رابطی که این متد را تعریف می‌کند: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.fillStyle")}}
- {{domxref("CanvasRenderingContext2D.clearRect()")}}
- {{domxref("CanvasRenderingContext2D.strokeRect()")}}