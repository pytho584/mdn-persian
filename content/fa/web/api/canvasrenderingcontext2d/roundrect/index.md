---
title: "CanvasRenderingContext2D: roundRect() method"
short-title: roundRect()
slug: Web/API/CanvasRenderingContext2D/roundRect
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.roundRect
---

{{APIRef("Canvas API")}}

متد **`CanvasRenderingContext2D.roundRect()`** از Canvas 2D API یک مستطیل گردشده به مسیر فعلی اضافه می‌کند.

شعاع گوشه‌ها را می‌توان به همان شیوه‌ای که در ویژگی CSS {{cssxref("border-radius")}} مشخص می‌شود، تعیین کرد.

مانند سایر متدهایی که مسیر فعلی را تغییر می‌دهند، این متد مستقیماً چیزی را رسم نمی‌کند. برای رسم مستطیل گردشده روی بوم، می‌توانید از متدهای {{domxref("CanvasRenderingContext2D.fill", "fill()")}} یا {{domxref("CanvasRenderingContext2D.stroke", "stroke()")}} استفاده کنید.

## Syntax

```js-nolint
roundRect(x, y, width, height, radii)
```

### Parameters

- `x`
  - : مختصات محور x نقطه شروع مستطیل، بر حسب پیکسل.
- `y`
  - : مختصات محور y نقطه شروع مستطیل، بر حسب پیکسل.
- `width`
  - : عرض مستطیل. مقادیر مثبت به سمت راست و مقادیر منفی به سمت چپ هستند.
- `height`
  - : ارتفاع مستطیل. مقادیر مثبت به سمت پایین و مقادیر منفی به سمت بالا هستند.
- `radii`
  - : یک عدد یا لیستی که شعاع قوس دایره‌ای را برای گوشه‌های مستطیل مشخص می‌کند. تعداد و ترتیب شعاع‌ها به همان شیوه‌ای عمل می‌کند که ویژگی CSS {{cssxref("border-radius")}} زمانی که `width` و `height` _مثبت_ هستند عمل می‌کند:
    - `all-corners`
    - `[all-corners]`
    - `[top-left-and-bottom-right, top-right-and-bottom-left]`
    - `[top-left, top-right-and-bottom-left, bottom-right]`
    - `[top-left, top-right, bottom-right, bottom-left]`

    اگر `width` _منفی_ باشد، مستطیل گردشده به صورت افقی برعکس می‌شود، بنابراین مقادیر شعاعی که معمولاً برای گوشه‌های چپ اعمال می‌شوند برای راست استفاده می‌شوند و بالعکس. به طور مشابه، وقتی `height` منفی است، مستطیل گردشده به صورت عمودی برعکس می‌شود. ممکن است شعاع‌های مشخص‌شده مقیاس‌بندی (کاهش) شوند اگر هر یک از لبه‌ها کوتاه‌تر از مجموع شعاع رئوس در دو انتها باشند.

    پارامتر `radii` همچنین می‌تواند یک نمونه {{domxref("DOMPoint")}} یا {{domxref("DOMPointReadOnly")}} باشد، یا یک شیء حاوی همان ویژگی‌ها (`{x: 0, y: 0}`)، یا یک لیست از چنین اشیایی، یا یک لیست که اعداد و چنین اشیایی را ترکیب می‌کند.

### Return value

هیچ ({{jsxref("undefined")}}).

### Exceptions

- {{jsxref("RangeError")}}
  - : اگر `radii` یک لیست با صفر یا بیش از چهار عنصر باشد، یا اگر یکی از مقادیر آن یک عدد منفی باشد.

## Examples

### Drawing rectangles

این مثال تعدادی مسیر مستطیل گردشده را با استفاده از متد `roundRect()` ایجاد می‌کند. سپس مسیرها با استفاده از متد `stroke()` رسم می‌شوند.

#### HTML

```html
<canvas id="canvas" width="700" height="300"></canvas>
```

#### JavaScript

ابتدا یک بافت برای رسم مستطیل‌های گردشده خود ایجاد می‌کنیم.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
```

کد زیر دو مستطیل را رسم می‌کند که هر دو از نقطه (10, 20) شروع می‌شوند و عرض 150 و ارتفاع 100 دارند. مستطیل اول به رنگ قرمز رسم شده و با استفاده از یک عدد به عنوان آرگومان، شعاع صفر را برای همه گوشه‌ها مشخص می‌کند. دومی به رنگ آبی رسم شده و یک شعاع 40 پیکسلی را به عنوان یک عنصر تکی در یک لیست مشخص می‌کند.

```js
// Rounded rectangle with zero radius (specified as a number)
ctx.strokeStyle = "red";
ctx.beginPath();
ctx.roundRect(10, 20, 150, 100, 0);
ctx.stroke();

// Rounded rectangle with 40px radius (single element list)
ctx.strokeStyle = "blue";
ctx.beginPath();
ctx.roundRect(10, 20, 150, 100, [40]);
ctx.stroke();
```

در زیر مستطیل قبلی، مستطیل دیگری به رنگ نارنجی رسم می‌کنیم که مقادیر شعاع گوشه‌های مقابل را مشخص می‌کند.

```js
// Rounded rectangle with 2 different radii
ctx.strokeStyle = "orange";
ctx.beginPath();
ctx.roundRect(10, 150, 150, 100, [10, 40]);
ctx.stroke();
```

در نهایت، دو مستطیل گردشده رسم می‌کنیم که چهار مقدار برای شعاع‌ها و نقطه شروع یکسان دارند. تفاوت در اینجا این است که دومی با عرض منفی رسم شده است.

```js
// Rounded rectangle with four different radii
ctx.strokeStyle = "green";
ctx.beginPath();
ctx.roundRect(400, 20, 200, 100, [0, 30, 50, 60]);
ctx.stroke();

// Same rectangle drawn backwards
ctx.strokeStyle = "magenta";
ctx.beginPath();
ctx.roundRect(400, 150, -200, 100, [0, 30, 50, 60]);
ctx.stroke();
```

#### Result

نتیجه در زیر نشان داده شده است. برای دو مستطیل سمت راست، توجه کنید که مستطیل پایینی با عرض منفی رسم شده است و چگونه این کار مستطیل را به صورت افقی برعکس می‌کند.

{{ EmbedLiveSample('Drawing_a_rectangle', 700, 300) }}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- The interface defining this method: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.rect()")}}
- {{domxref("CanvasRenderingContext2D.fillRect")}}
- {{domxref("CanvasRenderingContext2D.strokeRect()")}}
- {{domxref("CanvasRenderingContext2D.fill()")}}
- {{domxref("CanvasRenderingContext2D.stroke()")}}