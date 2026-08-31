---
title: "CanvasRenderingContext2D: strokeText() method"
short-title: strokeText()
slug: Web/API/CanvasRenderingContext2D/strokeText
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.strokeText
---

{{APIRef("Canvas API")}}

متد **`strokeText()`** در {{domxref("CanvasRenderingContext2D")}}، بخشی از Canvas 2D API، متن داده‌شده را با رسم خط دور حروف، یعنی فقط طرح کلی کاراکترها، در مختصات مشخص‌شده رسم می‌کند. یک پارامتر اختیاری به شما امکان می‌دهد حداکثر عرض متن را تعیین کنید؛ {{Glossary("user agent")}} این عرض را با فشرده‌سازی متن یا استفاده از اندازه قلم کوچک‌تر محقق می‌کند.

این متد مستقیماً روی بوم (canvas) رسم می‌کند و مسیر فعلی را تغییر نمی‌دهد، بنابراین فراخوانی‌های بعدی {{domxref("CanvasRenderingContext2D.fill()", "fill()")}} یا {{domxref("CanvasRenderingContext2D.stroke()", "stroke()")}} هیچ تأثیری روی آن نخواهند داشت.

> [!NOTE]
> از متد {{domxref('CanvasRenderingContext2D.fillText()', 'fillText()')}} استفاده کنید تا حروف متن پر شوند و فقط طرح دور آن‌ها رسم نشود.

## Syntax

```js-nolint
strokeText(text, x, y)
strokeText(text, x, y, maxWidth)
```

### Parameters

- `text`
  - : رشته‌ای که متن موردنظر برای رسم در context را مشخص می‌کند. متن با استفاده از تنظیمات تعیین‌شده توسط {{domxref("CanvasRenderingContext2D.font","font")}}، {{domxref("CanvasRenderingContext2D.textAlign","textAlign")}}، {{domxref("CanvasRenderingContext2D.textBaseline","textBaseline")}} و {{domxref("CanvasRenderingContext2D.direction","direction")}} رندر می‌شود.
- `x`
  - : مختصات محور x نقطه‌ای که رسم متن از آنجا آغاز می‌شود.
- `y`
  - : مختصات محور y نقطه‌ای که رسم متن از آنجا آغاز می‌شود.
- `maxWidth` {{optional_inline}}
  - : حداکثر عرضی که متن پس از رندر می‌تواند داشته باشد. اگر مشخص نشود، هیچ محدودیتی برای عرض متن وجود ندارد. با این حال، اگر این مقدار ارائه شود، عامل کاربر (user agent) کرنینگ را تنظیم می‌کند، فونت فشرده‌تری را در جهت افقی انتخاب می‌کند (در صورت موجود بودن یا امکان تولید بدون افت کیفیت)، یا اندازه قلم را کوچک‌تر می‌کند تا متن در عرض مشخص‌شده جای بگیرد.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

## Examples

### رسم طرح کلی متن

این مثال عبارت «Hello world» را با استفاده از متد `strokeText()` می‌نویسد.

#### HTML

ابتدا به یک بوم (canvas) برای رسم نیاز داریم. این کد یک context به عرض ۴۰۰ پیکسل و ارتفاع ۱۵۰ پیکسل ایجاد می‌کند.

```html
<canvas id="canvas" width="400" height="150"></canvas>
```

#### JavaScript

کد جاوااسکریپت این مثال در ادامه آمده است.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.font = "50px serif";
ctx.strokeText("Hello world", 50, 90);
```

این کد ارجاعی به {{HTMLElement("canvas")}} می‌گیرد و سپس ارجاع به context گرافیکی دوبعدی آن را دریافت می‌کند.

با این کار، {{domxref("CanvasRenderingContext2D.font", "font")}} را روی «serif» با ارتفاع ۵۰ پیکسل (فونت [serif](https://en.wikipedia.org/wiki/Serif) پیش‌فرض کاربر) تنظیم می‌کنیم و سپس `strokeText()` را برای رسم متن «Hello world» با شروع از مختصات (50, 90) فراخوانی می‌کنیم.

#### Result

{{ EmbedLiveSample('Drawing_text_outlines', 700, 180) }}

### محدود کردن اندازه متن

این مثال عبارت «Hello world» را با محدود کردن عرض آن به ۱۴۰ پیکسل می‌نویسد.

#### HTML

```html
<canvas id="canvas" width="400" height="150"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.font = "50px serif";
ctx.strokeText("Hello world", 50, 90, 140);
```

#### Result

{{ EmbedLiveSample('Restricting_the_text_size', 700, 180) }}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Drawing text](/en-US/docs/Web/API/Canvas_API/Tutorial/Drawing_text)
- The interface defining this method: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.fillText()")}}