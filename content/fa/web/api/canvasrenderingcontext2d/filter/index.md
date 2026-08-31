```
---
title: "CanvasRenderingContext2D: filter property"
short-title: filter
slug: Web/API/CanvasRenderingContext2D/filter
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.filter
---

{{APIRef("Canvas API")}}

ویژگی **`CanvasRenderingContext2D.filter`** در رابط Canvas 2D افکت‌های فیلتری مانند تارکردن (blur) و خاکستری‌کردن (grayscale) را فراهم می‌کند. این ویژگی مشابه ویژگی CSS {{cssxref("filter")}} است و همان مقادیر را می‌پذیرد.

## مقدار

ویژگی `filter` مقدار `"none"` یا یک یا چند تابع فیلتر زیر را به‌صورت یک رشته می‌پذیرد.

- {{cssxref("url_function", "url()")}}
  - : یک {{cssxref("url_function", "url()")}} در CSS. هر URL که به یک عنصر فیلتر SVG اشاره کند را می‌پذیرد. این مقدار می‌تواند شناسه یک عنصر، مسیری به یک فایل XML خارجی، یا حتی یک مقدار SVG کدگذاری‌شده به‌صورت data باشد.
- {{cssxref("filter-function/blur", "blur()")}}
  - : یک {{cssxref("&lt;length&gt;")}} در CSS. یک محو شدگی گاوسی (Gaussian blur) روی ترسیم اعمال می‌کند. این مقدار انحراف معیار تابع گاوسی را مشخص می‌کند؛ یعنی اینکه چند پیکسل روی صفحه با یکدیگر ترکیب شوند؛ بنابراین مقدار بزرگ‌تر محو شدگی بیشتری ایجاد می‌کند. مقدار `0` ورودی را بدون تغییر باقی می‌گذارد.
- {{cssxref("filter-function/brightness", "brightness()")}}
  - : یک {{cssxref("&lt;percentage&gt;")}} در CSS. یک ضریب خطی روی ترسیم اعمال می‌کند و آن را روشن‌تر یا تیره‌تر نشان می‌دهد. مقدار زیر `100%` تصویر را تیره‌تر می‌کند و مقدار بالای `100%` آن را روشن‌تر می‌کند. مقدار `0%` تصویری کاملاً سیاه ایجاد می‌کند و مقدار `100%` ورودی را بدون تغییر باقی می‌گذارد.
- {{cssxref("filter-function/contrast", "contrast()")}}
  - : یک {{cssxref("&lt;percentage&gt;")}} در CSS. کنتراست ترسیم را تنظیم می‌کند. مقدار `0%` ترسیمی کاملاً سیاه ایجاد می‌کند و مقدار `100%` ترسیم را بدون تغییر باقی می‌گذارد.
- {{cssxref("filter-function/drop-shadow", "drop-shadow()")}}
  - : یک افکت سایه پایه (drop shadow) روی ترسیم اعمال می‌کند. سایه پایه عملاً نسخه‌ای محوشده و آفست‌شده از ماسک آلفای ترسیم است که به رنگ خاصی کشیده می‌شود و در زیر ترسیم ترکیب می‌شود. این تابع تا پنج آرگومان می‌پذیرد:
    - `<offset-x>`
      - : برای واحدهای ممکن به {{cssxref("&lt;length&gt;")}} مراجعه کنید. فاصله افقی سایه را مشخص می‌کند.
    - `<offset-y>`
      - : برای واحدهای ممکن به {{cssxref("&lt;length&gt;")}} مراجعه کنید. فاصله عمودی سایه را مشخص می‌کند.
    - `<blur-radius>`
      - : هرچه این مقدار بزرگ‌تر باشد، محو شدگی بیشتر است و سایه بزرگ‌تر و روشن‌تر می‌شود. مقادیر منفی مجاز نیستند.
    - `<color>`
      - : برای کلیدواژه‌ها و نمادهای ممکن به مقادیر {{cssxref("&lt;color&gt;")}} مراجعه کنید.

- {{cssxref("filter-function/grayscale", "grayscale()")}}
  - : یک {{cssxref("&lt;percentage&gt;")}} در CSS. ترسیم را به حالت خاکستری تبدیل می‌کند. مقدار `100%` کاملاً خاکستری است. مقدار `0%` ترسیم را بدون تغییر باقی می‌گذارد.
- {{cssxref("filter-function/hue-rotate", "hue-rotate()")}}
  - : یک {{cssxref("&lt;angle&gt;")}} در CSS. یک چرخش فام (hue rotation) روی ترسیم اعمال می‌کند. مقدار `0deg` ورودی را بدون تغییر باقی می‌گذارد.
- {{cssxref("filter-function/invert", "invert()")}}
  - : یک {{cssxref("&lt;percentage&gt;")}} در CSS. ترسیم را وارونه می‌کند. مقدار `100%` به معنای وارونگی کامل است. مقدار `0%` ترسیم را بدون تغییر باقی می‌گذارد.
- {{cssxref("filter-function/opacity", "opacity()")}}
  - : یک {{cssxref("&lt;percentage&gt;")}} در CSS. شفافیت را روی ترسیم اعمال می‌کند. مقدار `0%` به معنای کاملاً شفاف است. مقدار `100%` ترسیم را بدون تغییر باقی می‌گذارد.
- {{cssxref("filter-function/saturate", "saturate()")}}
  - : یک {{cssxref("&lt;percentage&gt;")}} در CSS. اشباع رنگ ترسیم را تنظیم می‌کند. مقدار `0%` به معنای کاملاً بی‌اشباع است. مقدار `100%` ترسیم را بدون تغییر باقی می‌گذارد.
- {{cssxref("filter-function/sepia", "sepia()")}}
  - : یک {{cssxref("&lt;percentage&gt;")}} در CSS. ترسیم را به حالت قهوه‌ای (سپیا) تبدیل می‌کند. مقدار `100%` به معنای کاملاً سپیا است. مقدار `0%` ترسیم را بدون تغییر باقی می‌گذارد.
- `none`
  - : هیچ فیلتری اعمال نمی‌شود. مقدار اولیه.

## مثال‌ها

برای مشاهده این مثال‌ها، حتماً از مرورگری استفاده کنید که از این ویژگی پشتیبانی می‌کند؛ جدول سازگاری پایین را ببینید.

### اعمال تارکردن

این مثال با استفاده از ویژگی `filter` یک متن را تار می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.filter = "blur(4px)";
ctx.font = "48px serif";
ctx.fillText("Hello world", 50, 100);
```

#### نتیجه

{{ EmbedLiveSample('Applying_a_blur', 700, 180) }}

### اعمال چند فیلتر به‌طور هم‌زمان

می‌توانید هر تعداد فیلتر که بخواهید را ترکیب کنید. این مثال فیلترهای `contrast`، `sepia` و `drop-shadow` را روی عکس یک کرگدن اعمال می‌کند.

#### HTML

```html
<canvas id="canvas" width="400" height="150"></canvas>
<div class="hidden">
  <img
    id="source"
    src="https://mdn.github.io/shared-assets/images/examples/rhino.jpg" />
</div>
```

```css hidden
.hidden {
  display: none;
}
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
const image = document.getElementById("source");

image.addEventListener("load", (e) => {
  // Draw unfiltered image
  ctx.drawImage(image, 0, 0, image.width * 0.6, image.height * 0.6);

  // Draw image with filter
  ctx.filter = "contrast(1.4) sepia(1) drop-shadow(-9px 9px 3px #ee8811)";
  ctx.drawImage(image, 400, 0, -image.width * 0.6, image.height * 0.6);
});
```

#### نتیجه

{{ EmbedLiveSample('Applying_multiple_filters', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این ویژگی: {{domxref("CanvasRenderingContext2D")}}
- ویژگی CSS {{cssxref("filter")}}
- {{cssxref("&lt;filter-function&gt;")}} در CSS
```