---
title: "CanvasRenderingContext2D: lineCap property"
short-title: lineCap
slug: Web/API/CanvasRenderingContext2D/lineCap
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.lineCap
---

{{APIRef("Canvas API")}}

ویژگی **`CanvasRenderingContext2D.lineCap`** از Canvas 2D API شکل مورد استفاده برای رسم نقاط انتهایی خطوط را تعیین می‌کند.

> [!NOTE]
> خطوط را می‌توان با استفاده از متدهای {{domxref("CanvasRenderingContext2D.stroke()", "stroke()")}}، {{domxref("CanvasRenderingContext2D.strokeRect()", "strokeRect()")}} و {{domxref("CanvasRenderingContext2D.strokeText()", "strokeText()")}} رسم کرد.

## مقدار

یکی از موارد زیر:

- `"butt"`
  - : انتهای خطوط در نقاط انتهایی به صورت مربعی بریده می‌شوند. مقدار پیش‌فرض.
- `"round"`
  - : انتهای خطوط گرد می‌شوند.
- `"square"`
  - : انتهای خطوط با افزودن یک جعبه با عرض برابر و نصف ارتفاع ضخامت خط به صورت مربعی بریده می‌شوند.

## مثال‌ها

### تغییر شکل سرپوش‌های خط

این مثال سرپوش‌های انتهای یک خط مستقیم را گرد می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.beginPath();
ctx.moveTo(20, 20);
ctx.lineWidth = 15;
ctx.lineCap = "round";
ctx.lineTo(100, 100);
ctx.stroke();
```

#### نتیجه

{{ EmbedLiveSample('Changing_the_shape_of_line_caps', 700, 180) }}

### مقایسه سرپوش‌های خط

در این مثال سه خط رسم شده‌اند که هر کدام مقدار متفاوتی برای ویژگی `lineCap` دارند. دو راهنما برای مشاهده تفاوت‌های دقیق بین سه خط اضافه شده است. هر یک از این خطوط دقیقاً روی این راهنماها شروع و پایان می‌یابند.

خط سمت چپ از گزینه پیش‌فرض `"butt"` استفاده می‌کند. این خط کاملاً هم‌سطح با راهنماها رسم شده است. خط دوم با گزینه `"round"` تنظیم شده است. این گزینه یک نیم‌دایره به انتهای خط اضافه می‌کند که شعاع آن نصف عرض خط است. خط سمت راست از گزینه `"square"` استفاده می‌کند. این گزینه یک جعبه با عرض برابر و نصف ارتفاع ضخامت خط اضافه می‌کند.

```html hidden
<canvas id="canvas" width="150" height="150"></canvas>
```

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// رسم راهنماها
ctx.strokeStyle = "#0099ff";
ctx.beginPath();
ctx.moveTo(10, 10);
ctx.lineTo(140, 10);
ctx.moveTo(10, 140);
ctx.lineTo(140, 140);
ctx.stroke();

// رسم خطوط
ctx.strokeStyle = "black";
["butt", "round", "square"].forEach((lineCap, i) => {
  ctx.lineWidth = 15;
  ctx.lineCap = lineCap;
  ctx.beginPath();
  ctx.moveTo(25 + i * 50, 10);
  ctx.lineTo(25 + i * 50, 140);
  ctx.stroke();
});
```

{{EmbedLiveSample("Comparison_of_line_caps", "180", "180")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

### یادداشت‌های مخصوص WebKit/Blink

- در مرورگرهای مبتنی بر WebKit و Blink، یک متد غیراستاندارد و منسوخ شده به نام `ctx.setLineCap()` علاوه بر این ویژگی پیاده‌سازی شده است.

## همچنین ببینید

- رابط تعریف‌کننده این ویژگی: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.lineWidth")}}
- {{domxref("CanvasRenderingContext2D.lineJoin")}}
- [اعمال سبک‌ها و رنگ‌ها](/en-US/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors)