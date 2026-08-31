---
title: "CanvasRenderingContext2D: scale() method"
short-title: scale()
slug: Web/API/CanvasRenderingContext2D/scale
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.scale
---

{{APIRef("Canvas API")}}

متد
**`CanvasRenderingContext2D.scale()`**
از API بوم (Canvas) 2D، یک تبدیل مقیاسبندی به واحدهای بوم بهصورت افقی و/یا عمودی اضافه میکند.

بهطور پیشفرض، یک واحد روی بوم دقیقاً برابر با یک پیکسل است. یک تبدیل مقیاسبندی این رفتار را تغییر میدهد. برای مثال، ضریب مقیاس 0.5 باعث میشود اندازه هر واحد به 0.5 پیکسل تبدیل شود؛ بنابراین اشکال با نصف اندازه معمولی رسم میشوند. بهطور مشابه، ضریب مقیاس 2.0 اندازه واحد را افزایش میدهد بهگونهای که یک واحد به دو پیکسل تبدیل میشود؛ بنابراین اشکال با دو برابر اندازه معمولی رسم میشوند.

## Syntax

```js-nolint
scale(x, y)
```

### Parameters

- `x`
  - : ضریب مقیاس در جهت افقی. مقدار منفی پیکسلها را حول محور عمودی برعکس میکند. مقدار `1` به این معناست که هیچ مقیاسبندی افقی اعمال نمیشود.
- `y`
  - : ضریب مقیاس در جهت عمودی. مقدار منفی پیکسلها را حول محور افقی برعکس میکند. مقدار `1` به این معناست که هیچ مقیاسبندی عمودی اعمال نمیشود.

### Return value

هیچ ({{jsxref("undefined")}}).

## Examples

### مقیاسبندی یک شکل

این مثال یک مستطیل مقیاسبندیشده رسم میکند. یک مستطیل بدون مقیاس نیز برای مقایسه رسم شده است.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

مستطیل دارای عرض مشخص 8 و ارتفاع 20 است. ماتریس تبدیل آن را بهصورت افقی 9 برابر و بهصورت عمودی 3 برابر مقیاسبندی میکند. بنابراین، اندازه نهایی آن عرض 72 و ارتفاع 60 است.

توجه داشته باشید که موقعیت آن روی بوم نیز تغییر میکند. از آنجا که گوشه مشخصشده آن (10, 10) است، گوشه رندر شده آن به (90, 30) تبدیل میشود.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// Scaled rectangle
ctx.scale(9, 3);
ctx.fillStyle = "red";
ctx.fillRect(10, 10, 8, 20);

// Reset current transformation matrix to the identity matrix
ctx.setTransform(1, 0, 0, 1, 0, 0);

// Non-scaled rectangle
ctx.fillStyle = "gray";
ctx.fillRect(10, 10, 8, 20);
```

#### Result

مستطیل مقیاسبندیشده قرمز است و مستطیل بدون مقیاس خاکستری.

{{ EmbedLiveSample('Scaling_a_shape', 700, 180) }}

### برعکس کردن افقی یا عمودی اشیا

میتوانید از `scale(-1, 1)` برای برعکس کردن افقی بافت و از `scale(1, -1)` برای برعکس کردن عمودی آن استفاده کنید. در این مثال، عبارت «Hello world!» بهصورت افقی برعکس میشود.

توجه داشته باشید که فراخوانی {{domxref("CanvasRenderingContext2D.fillText()", "fillText()")}} یک مختصات x منفی را مشخص میکند. این تنظیم برای جبران ضریب مقیاس منفی است: `-280 * -1` به `280` تبدیل میشود و متن از آن نقطه به سمت چپ رسم میشود.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.scale(-1, 1);
ctx.font = "48px serif";
ctx.fillText("Hello world!", -280, 90);
ctx.setTransform(1, 0, 0, 1, 0, 0);
```

#### Result

{{ EmbedLiveSample('Flipping_things_horizontally_or_vertically', 700, 180) }}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- رابط تعریفکننده این متد: {{domxref("CanvasRenderingContext2D")}}