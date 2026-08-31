---
title: "CanvasRenderingContext2D: getContextAttributes() method"
short-title: getContextAttributes()
slug: Web/API/CanvasRenderingContext2D/getContextAttributes
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.getContextAttributes
---

{{APIRef("WebGL")}}

متد **`CanvasRenderingContext2D.getContextAttributes()`** شیءای را برمی‌گرداند که شامل ویژگی‌های استفاده‌شده توسط بافتار (context) است.

توجه داشته باشید که ویژگی‌های بافتار را می‌توان هنگام ایجاد بافتار با [`HTMLCanvasElement.getContext()`](/en-US/docs/Web/API/HTMLCanvasElement/getContext) درخواست کرد، اما ویژگی‌هایی که در عمل پشتیبانی و استفاده می‌شوند ممکن است متفاوت باشند.

## نحو (Syntax)

```js-nolint
getContextAttributes()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء `CanvasRenderingContext2DSettings` که شامل پارامترهای واقعی بافتار است.
این شیء اعضای زیر را دارد:

- `alpha` {{optional_inline}}
  - : یک مقدار بولی که نشان می‌دهد آیا بوم (canvas) دارای کانال آلفا (alpha channel) است یا خیر.
    اگر `false` باشد، پس‌زمینه همیشه مات (opaque) است که می‌تواند ترسیم محتوای شفاف و تصاویر را سرعت ببخشد.
- `colorSpace` {{optional_inline}}
  - : فضای رنگی بافتار رندرینگ را نشان می‌دهد. مقادیر ممکن عبارتند از:
    - `srgb`: بیانگر [فضای رنگی sRGB](https://en.wikipedia.org/wiki/SRGB)
    - `display-p3`: بیانگر [فضای رنگی display-p3](https://en.wikipedia.org/wiki/DCI-P3)
- `colorType` {{optional_inline}}
  - : نوع رنگ بافتار رندرینگ را نشان می‌دهد. مقادیر ممکن عبارتند از:
    - `"unorm8"` بیانگر کانال‌های رنگی به‌صورت مقادیر ۸ بیتی بدون علامت (unsigned). این مقدار پیش‌فرض است.
    - `"float16"` بیانگر کانال‌های رنگی به‌صورت مقادیر ممیز شناور (floating-point) ۱۶ بیتی.
- `desynchronized` {{optional_inline}}
  - : یک مقدار بولی که نشان می‌دهد آیا عامل کاربر (user agent) با خارج کردن چرخه نقاشی بوم از حلقه رویداد (event loop)، تأخیر (latency) را کاهش داده است یا خیر.
- `willReadFrequently` {{optional_inline}}
  - : یک مقدار بولی که نشان می‌دهد آیا این بوم برای پشتیبانی از عملیات مکرر خواندن بازگشتی (read-back) از طریق {{domxref("CanvasRenderingContext2D.getImageData", "getImageData()")}} از شتاب نرم‌افزاری (به جای شتاب سخت‌افزاری) استفاده می‌کند یا خیر.

## مثال‌ها

این مثال نشان می‌دهد که چگونه می‌توانید ویژگی‌های بافتار را هنگام ایجاد یک بافتار بوم مشخص کنید و سپس با فراخوانی `getContextAttributes()` پارامترهای واقعی استفاده‌شده توسط مرورگر را بخوانید.

```html hidden
<pre id="log"></pre>
```

```js hidden
const logElement = document.getElementById("log");
function log(text) {
  logElement.innerText += text;
}
```

ابتدا یک بافتار را با استفاده از [`HTMLCanvasElement.getContext()`](/en-US/docs/Web/API/HTMLCanvasElement/getContext) ایجاد می‌کنیم و فقط یک ویژگی بافتار را مشخص می‌کنیم.

```js
let canvas = document.createElement("canvas");
let ctx = canvas.getContext("2d", { alpha: false });
```

اگر متد `getContextAttributes()` پشتیبانی می‌شود، از آن برای خواندن ویژگی‌های واقعی استفاده‌شده توسط مرورگر (از جمله مواردی که به‌صراحت مشخص کرده‌ایم) استفاده می‌کنیم:

```js
if (ctx.getContextAttributes) {
  const attributes = ctx.getContextAttributes();
  log(JSON.stringify(attributes));
} else {
  log("CanvasRenderingContext2D.getContextAttributes() is not supported");
}
```

بسته به ویژگی‌های پشتیبانی‌شده توسط مرورگر، خروجی زیر باید رشته‌ای شبیه به این نمایش دهد: `{alpha: false, colorSpace: 'srgb', desynchronized: false, willReadFrequently: false}`

{{EmbedLiveSample('Examples','100%','50')}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [`HTMLCanvasElement.getContext()`](/en-US/docs/Web/API/HTMLCanvasElement/getContext)
- [`WebGLRenderingContext.getContextAttributes()`](/en-US/docs/Web/API/WebGLRenderingContext/getContextAttributes)