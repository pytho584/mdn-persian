---
title: "HTMLImageElement: x property"
short-title: x
slug: Web/API/HTMLImageElement/x
page-type: web-api-instance-property
browser-compat: api.HTMLImageElement.x
---

{{APIRef("HTML DOM")}}

ویژگی فقط خواندنی **`x`** از رابط {{domxref("HTMLImageElement")}}، مختصات x لبه چپ حاشیه عنصر {{HTMLElement("img")}} را نسبت به مبدأ عنصر ریشه نشان می‌دهد.

## مقدار

یک مقدار صحیح (integer) که فاصله را بر حسب پیکسل از لبه چپ نزدیکترین عنصر ریشه تا لبه چپ جعبه حاشیه (border box) عنصر {{HTMLElement("img")}} مشخص می‌کند. نزدیکترین عنصر ریشه، بیرونی‌ترین عنصر {{HTMLElement("html")}} است که تصویر را در خود دارد. اگر تصویر در یک {{HTMLElement("iframe")}} قرار داشته باشد، `x` آن نسبت به آن فریم محاسبه می‌شود.

در نمودار زیر، لبه چپ حاشیه، همان لبه چپ ناحیه آبی padding است. بنابراین مقدار بازگشتی توسط `x`، فاصله از آن نقطه تا لبه چپ ناحیه محتوا خواهد بود.

![نموداری که روابط بین جعبه‌های مختلف مرتبط با یک عنصر را نشان می‌دهد](boxmodel-3.png)

## مثال‌ها

مثال زیر استفاده از ویژگی‌های `x` و {{domxref("HTMLImageElement.y", "y")}} را در `HTMLImageElement` نشان می‌دهد.

### HTML

```html
<img id="avatar" src="/shared-assets/images/examples/grapefruit-slice.jpg" />
<pre id="log"></pre>
```

### JavaScript

کد جاوااسکریپت که تصویر را دریافت کرده و مقادیر `x` و `y` آن را بررسی می‌کند در زیر آورده شده است.

```js
const logBox = document.querySelector("pre");

const log = (msg) => {
  logBox.innerText += `${msg}\n`;
};

const image = document.getElementById("avatar");

log(`مختصات X تصویر: ${image.x}`);
log(`مختصات Y تصویر: ${image.y}`);
```

در نهایت، می‌توانیم مقادیر ویژگی‌های `x` و `y` این `HTMLImageElement` را بررسی و نمایش دهیم.

### CSS

CSS که اندازه و موقعیت تصویر را مشخص می‌کند:

```css
img {
  margin-left: 30px;
  margin-top: 20px;
  max-width: 4em;
}
```

### نتیجه

تصویر نهایی به این شکل خواهد بود:

{{EmbedLiveSample("Example", 600, 200)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLImageElement.y")}}