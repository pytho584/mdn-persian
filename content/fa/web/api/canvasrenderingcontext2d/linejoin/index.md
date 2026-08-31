---
title: "CanvasRenderingContext2D: lineJoin property"
short-title: lineJoin
slug: Web/API/CanvasRenderingContext2D/lineJoin
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.lineJoin
---

{{APIRef("Canvas API")}}

ویژگی **`CanvasRenderingContext2D.lineJoin`** در Canvas 2D API شکلی را تعیین می‌کند که برای اتصال دو پاره‌خط در نقطه‌ای که به هم می‌رسند استفاده می‌شود.

این ویژگی در هر جایی که دو بخش متصل به هم هم‌جهت باشند اثری ندارد، زیرا در این حالت ناحیهٔ اتصال اضافه نمی‌شود. همچنین بخش‌های تباهیده (degenerate) با طول صفر (یعنی جایی که همهٔ نقاط پایانی و نقاط کنترلی دقیقاً در یک موقعیت قرار دارند) نادیده گرفته می‌شوند.

> [!NOTE]
> خطوط را می‌توان با روش‌های
> {{domxref("CanvasRenderingContext2D.stroke()", "stroke()")}}،
> {{domxref("CanvasRenderingContext2D.strokeRect()", "strokeRect()")}} و
> {{domxref("CanvasRenderingContext2D.strokeText()", "strokeText()")}} رسم کرد.

## مقدار

برای این ویژگی سه مقدار ممکن وجود دارد: `"round"`، `"bevel"` و `"miter"`. مقدار پیش‌فرض `"miter"` است.

![سه خط زیگزاگی افقی با مقادیر round، bevel و miter، به ترتیب از بالا به پایین.](canvas_linejoin.png)

- `"round"`
  - : گوشه‌های یک شکل را با پر کردن یک بخش اضافی از دایره که مرکز آن در نقطهٔ مشترک بخش‌های متصل است، گرد می‌کند. شعاع این گوشه‌های گرد برابر با پهنای خط است.
- `"bevel"`
  - : یک ناحیهٔ مثلثی اضافی بین نقطهٔ مشترک بخش‌های متصل و گوشه‌های مستطیلی بیرونی جداگانهٔ هر بخش را پر می‌کند.
- `"miter"`
  - : بخش‌های متصل با امتداد یافتن لبه‌های بیرونی آن‌ها به یکدیگر و اتصال در یک نقطه به هم می‌پیوندند، به‌گونه‌ای که یک ناحیهٔ لوزی‌مانند اضافی پر شود. این تنظیم تحت تأثیر ویژگی {{domxref("CanvasRenderingContext2D.miterLimit", "miterLimit")}} قرار دارد. مقدار پیش‌فرض.

## مثال‌ها

### تغییر اتصال‌ها در یک مسیر

این مثال اتصال‌های گرد خط را روی یک مسیر اعمال می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.lineWidth = 20;
ctx.lineJoin = "round";
ctx.beginPath();
ctx.moveTo(20, 20);
ctx.lineTo(190, 100);
ctx.lineTo(280, 20);
ctx.lineTo(280, 150);
ctx.stroke();
```

#### نتیجه

{{ EmbedLiveSample('Changing_the_joins_in_a_path', 700, 180) }}

### مقایسهٔ اتصال خط‌ها

مثال زیر سه مسیر متفاوت رسم می‌کند و هر یک از سه گزینهٔ `lineJoin` را نشان می‌دهد.

```html hidden
<canvas id="canvas" width="150" height="150"></canvas>
```

```js
const ctx = document.getElementById("canvas").getContext("2d");
ctx.lineWidth = 10;

["round", "bevel", "miter"].forEach((join, i) => {
  ctx.lineJoin = join;
  ctx.beginPath();
  ctx.moveTo(-5, 5 + i * 40);
  ctx.lineTo(35, 45 + i * 40);
  ctx.lineTo(75, 5 + i * 40);
  ctx.lineTo(115, 45 + i * 40);
  ctx.lineTo(155, 5 + i * 40);
  ctx.stroke();
});
```

{{EmbedLiveSample("Comparison_of_line_joins", "", "180")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

### نکات مخصوص WebKit/Blink

- در مرورگرهای مبتنی بر WebKit و Blink، علاوه بر این ویژگی، یک متد غیراستاندارد و منسوخ به نام `ctx.setLineJoin()` نیز پیاده‌سازی شده است.

## جستارهای وابسته

- رابطی که این ویژگی را تعریف می‌کند: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.lineCap")}}
- {{domxref("CanvasRenderingContext2D.lineWidth")}}
- [اعمال استایل‌ها و رنگ](/en-US/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors)