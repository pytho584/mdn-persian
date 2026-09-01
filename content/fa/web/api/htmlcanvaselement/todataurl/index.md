---
title: "HTMLCanvasElement: toDataURL() method"
short-title: toDataURL()
slug: Web/API/HTMLCanvasElement/toDataURL
page-type: web-api-instance-method
browser-compat: api.HTMLCanvasElement.toDataURL
---

{{APIRef("Canvas API")}}

متد **`HTMLCanvasElement.toDataURL()`** یک [نشانی اینترنتی داده (data URL)](/en-US/docs/Web/URI/Reference/Schemes/data) برمی‌گرداند که نمایندهٔ تصویر در قالبی است که توسط پارامتر `type` مشخص می‌شود.

قالب فایل دلخواه و کیفیت تصویر را می‌توان تعیین کرد. اگر قالب فایل مشخص نشود، یا اگر قالب داده‌شده پشتیبانی نشود، داده‌ها به‌صورت `image/png` خروجی گرفته می‌شوند. به عبارت دیگر، اگر مقدار برگشتی برای هر `type` درخواستی دیگری با `data:image/png` شروع شود، یعنی آن قالب پشتیبانی نمی‌شود.

مرورگرها موظف به پشتیبانی از `image/png` هستند؛ بسیاری از آن‌ها فرمت‌های دیگری از جمله `image/jpeg` و `image/webp` را نیز پشتیبانی می‌کنند.

داده‌های تصویر ایجادشده برای فرمت‌های فایلی که از فرادادهٔ وضوح پشتیبانی می‌کنند، وضوح ۹۶dpi خواهند داشت.

> [!WARNING]
> متد `toDataURL()` کل تصویر را در یک رشتهٔ درون‌حافظه‌ای کدگذاری می‌کند. برای تصاویر بزرگ‌تر، این کار می‌تواند پیامدهای عملکردی داشته باشد و حتی وقتی به {{domxref("HTMLImageElement.src")}} اختصاص داده شود، ممکن است از محدودیت طول نشانی مرورگرها فراتر رود. به‌طور کلی بهتر است به‌جای آن از [`toBlob()`](/en-US/docs/Web/API/HTMLCanvasElement/toBlob) در ترکیب با {{domxref("URL/createObjectURL_static", "URL.createObjectURL()")}} استفاده کنید.

## نحو (Syntax)

```js-nolint
toDataURL()
toDataURL(type)
toDataURL(type, quality)
```

### پارامترها

- `type` {{optional_inline}}
  - : رشته‌ای که قالب تصویر را مشخص می‌کند. نوع پیش‌فرض `image/png` است؛ اگر نوع مشخص‌شده پشتیبانی نشود نیز از همین قالب تصویر استفاده خواهد شد.
- `quality` {{optional_inline}}
  - : یک {{jsxref("Number")}} بین `0` و `1` که کیفیت تصویر را هنگام ایجاد تصاویر با استفاده از فرمت‌های فایلی که فشرده‌سازی اتلافی را پشتیبانی می‌کنند (مانند `image/jpeg` یا `image/webp`) مشخص می‌کند. اگر این گزینه مشخص نشود، یا اگر عدد خارج از بازهٔ مجاز باشد، عامل کاربر (user agent) از مقدار کیفیت پیش‌فرض خود استفاده خواهد کرد.

### مقدار برگشتی

رشته‌ای شامل [نشانی اینترنتی داده (data URL)](/en-US/docs/Web/URI/Reference/Schemes/data) درخواستی.

اگر ارتفاع یا عرض بوم (canvas) برابر با `0` یا بزرگ‌تر از [حداکثر اندازهٔ بوم](/en-US/docs/Web/HTML/Reference/Elements/canvas#maximum_canvas_size) باشد، رشتهٔ `"data:,"` برگردانده می‌شود.

### استثناها (Exceptions)

- `SecurityError`
  - : بیت‌نگاشت بوم از نظر مبدأ پاک (origin clean) نیست؛ دست‌کم بخشی از محتوای آن از سایتی غیر از سایتی که خود سند از آن بارگذاری شده، بارگذاری شده است یا ممکن است بارگذاری شده باشد.

## مثال‌ها

با توجه به این عنصر {{HTMLElement("canvas")}}:

```html
<canvas id="canvas" width="5" height="5"></canvas>
```

می‌توانید با خطوط زیر یک data-URL از بوم دریافت کنید:

```js
const canvas = document.getElementById("canvas");
const dataURL = canvas.toDataURL();
console.log(dataURL);
// "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAUAAAAFCAYAAACNby
// blAAAADElEQVQImWNgoBMAAABpAAFEI8ARAAAAAElFTkSuQmCC"
```

### تنظیم کیفیت تصویر با jpeg

```js
const fullQuality = canvas.toDataURL("image/jpeg", 1.0);
// data:image/jpeg;base64,/9j/4AAQSkZJRgABAQ…9oADAMBAAIRAxEAPwD/AD/6AP/Z"
const mediumQuality = canvas.toDataURL("image/jpeg", 0.5);
const lowQuality = canvas.toDataURL("image/jpeg", 0.1);
```

### مثال: تغییر پویای تصاویر

می‌توانید از این تکنیک در هماهنگی با رویدادهای ماوس برای تغییر پویای تصاویر استفاده کنید (در این مثال، مقیاس خاکستری در برابر رنگی):

#### HTML

```html
<img class="grayscale" src="myPicture.png" alt="Description of my picture" />
```

#### جاوااسکریپت

```js
function showColorImg() {
  this.style.display = "none";
  this.nextSibling.style.display = "inline";
}

function showGrayImg() {
  this.previousSibling.style.display = "inline";
  this.style.display = "none";
}

function removeColors() {
  const images = document.getElementsByClassName("grayscale");
  const canvas = document.createElement("canvas");
  const ctx = canvas.getContext("2d");

  for (const colorImg of images) {
    const width = colorImg.offsetWidth;
    const height = colorImg.offsetHeight;
    canvas.width = width;
    canvas.height = height;
    ctx.drawImage(colorImg, 0, 0);
    const imgData = ctx.getImageData(0, 0, width, height);
    const pix = imgData.data;
    const pixLen = pix.length;
    for (let pixel = 0; pixel < pixLen; pixel += 4) {
      pix[pixel + 2] =
        pix[pixel + 1] =
        pix[pixel] =
          (pix[pixel] + pix[pixel + 1] + pix[pixel + 2]) / 3;
    }
    ctx.putImageData(imgData, 0, 0);
    const grayImg = new Image();
    grayImg.src = canvas.toDataURL();
    grayImg.onmouseover = showColorImg;
    colorImg.onmouseout = showGrayImg;
    ctx.clearRect(0, 0, width, height);
    colorImg.style.display = "none";
    colorImg.parentNode.insertBefore(grayImg, colorImg);
  }
}

removeColors();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [نشانی‌های اینترنتی داده (Data URLs)](/en-US/docs/Web/URI/Reference/Schemes/data) در مرجع [HTTP](/en-US/docs/Web/HTTP).