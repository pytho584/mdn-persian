---
title: "CanvasRenderingContext2D: fillText() method"
short-title: fillText()
slug: Web/API/CanvasRenderingContext2D/fillText
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.fillText
---

{{APIRef("HTML DOM")}}

متد **`fillText()`** از {{domxref("CanvasRenderingContext2D")}} که بخشی از Canvas 2D API است، یک رشته متنی را در مختصات مشخص‌شده رسم می‌کند و حروف آن رشته را با {{domxref("CanvasRenderingContext2D.fillStyle", "fillStyle")}} فعلی پر می‌کند. یک پارامتر اختیاری به شما امکان می‌دهد حداکثر عرض متن رندر شده را تعیین کنید؛ {{Glossary("user agent", "عامل کاربر")}} این کار را با فشرده‌سازی متن یا استفاده از اندازه قلم کوچک‌تر انجام می‌دهد.

این متد مستقیماً روی بوم (canvas) رسم می‌کند و مسیر جاری (current path) را تغییر نمی‌دهد؛ بنابراین فراخوانی‌های بعدی {{domxref("CanvasRenderingContext2D.fill()", "fill()")}} یا {{domxref("CanvasRenderingContext2D.stroke()", "stroke()")}} هیچ تأثیری روی آن نخواهند داشت.

متن با استفاده از قلم و پیکربندی چیدمان متنی که توسط ویژگی‌های {{domxref("CanvasRenderingContext2D.font","font")}}، {{domxref("CanvasRenderingContext2D.textAlign","textAlign")}}، {{domxref("CanvasRenderingContext2D.textBaseline","textBaseline")}} و {{domxref("CanvasRenderingContext2D.direction","direction")}} تعریف شده است، رندر می‌شود.

> [!NOTE]
> برای رسم فقط خط دور حروف یک رشته، متد {{domxref("CanvasRenderingContext2D.strokeText", "strokeText()")}} موجود در context را فراخوانی کنید.

## نحو

```js-nolint
fillText(text, x, y)
fillText(text, x, y, maxWidth)
```

### پارامترها

- `text`
  - : رشته‌ای که متن موردنظر برای رندر در context را مشخص می‌کند.
    متن با استفاده از تنظیمات مشخص‌شده توسط
    {{domxref("CanvasRenderingContext2D.font","font")}}،
    {{domxref("CanvasRenderingContext2D.textAlign","textAlign")}}،
    {{domxref("CanvasRenderingContext2D.textBaseline","textBaseline")}} و
    {{domxref("CanvasRenderingContext2D.direction","direction")}} رندر می‌شود.
- `x`
  - : مختصات محور x نقطه شروع رسم متن، بر حسب پیکسل.
- `y`
  - : مختصات محور y خط پایه (baseline) که رسم متن از آن آغاز می‌شود، بر حسب پیکسل.
- `maxWidth` {{optional_inline}}
  - : حداکثر عرض متن پس از رندر، بر حسب پیکسل. اگر مشخص نشود،
    محدودیتی برای عرض متن وجود ندارد. اما اگر این مقدار داده شود،
    عامل کاربر فاصله‌گذاری بین حروف (kerning) را تنظیم می‌کند، قلم فشرده‌تر در جهت افقی را انتخاب می‌کند (در صورت وجود یا امکان تولید بدون افت کیفیت)،
    یا اندازه قلم را کاهش می‌دهد تا متن در عرض مشخص‌شده جای بگیرد.

### مقدار بازگشتی

هیچ مقداری ({{jsxref("undefined")}}).

## مثال‌ها

### رسم متن توپُر

این مثال عبارت "Hello world" را با استفاده از متد `fillText()` می‌نویسد.

#### HTML

ابتدا به یک بوم (canvas) برای رسم نیاز داریم. این کد یک بوم به عرض ۴۰۰ پیکسل و ارتفاع ۱۵۰ پیکسل ایجاد می‌کند.

```html
<canvas id="canvas" width="400" height="150"></canvas>
```

#### JavaScript

کد جاوااسکریپت این مثال در ادامه آمده است.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.font = "50px serif";
ctx.fillText("Hello world", 50, 90);
```

این کد یک ارجاع از {{HTMLElement("canvas")}} می‌گیرد و سپس به زمینه گرافیکی دوبعدی آن دسترسی پیدا می‌کند.

سپس ویژگی {{domxref("CanvasRenderingContext2D.font", "font")}} را روی قلم "serif" با ارتفاع ۵۰ پیکسل (قلم [serif](https://en.wikipedia.org/wiki/Serif) پیش‌فرض کاربر) تنظیم می‌کنیم و بعد `fillText()` را برای رسم متن "Hello world" از مختصات (50, 90) فراخوانی می‌کنیم.

#### نتیجه

{{ EmbedLiveSample('Drawing_filled_text', 700, 180) }}

### محدود کردن اندازه متن

این مثال عبارت "Hello world" را با محدود کردن عرض آن به ۱۴۰ پیکسل می‌نویسد.

#### HTML

```html
<canvas id="canvas" width="400" height="150"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.font = "50px serif";
ctx.fillText("Hello world", 50, 90, 140);
```

#### نتیجه

{{ EmbedLiveSample('Restricting_the_text_size', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [رسم متن](/en-US/docs/Web/API/Canvas_API/Tutorial/Drawing_text)
- {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.strokeText()")}}