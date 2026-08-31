---
title: "Pixel manipulation with canvas"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Pixel_manipulation_with_canvas"
translated_by: "n8n + AI"
---

---
title: Pixel manipulation with canvas
slug: Web/API/Canvas_API/Tutorial/Pixel_manipulation_with_canvas
page-type: guide
---

{{DefaultAPISidebar("Canvas API")}} {{PreviousNext("Web/API/Canvas_API/Tutorial/Advanced_animations", "Web/API/Canvas_API/Tutorial/Optimizing_canvas")}}

تاکنون به پیکسل‌های واقعی بوم (canvas) نگاه نکرده‌ایم. با استفاده از شیء `ImageData` می‌توانید مستقیماً یک آرایه داده را برای دستکاری داده‌های پیکسل بخوانید و بنویسید. همچنین بررسی خواهیم کرد که چگونه می‌توان هموارسازی تصویر (anti-aliasing) را کنترل کرد و چگونه تصاویر را از بوم خود ذخیره کرد.

## شیء ImageData

شیء {{domxref("ImageData")}} داده‌های پیکسلی زیرین یک ناحیه از یک شیء canvas را نشان می‌دهد.
ویژگی `data` آن یک {{jsxref("Uint8ClampedArray")}} (یا در صورت درخواست، {{jsxref("Float16Array")}}) برمی‌گرداند که می‌توان برای بررسی داده‌های خام پیکسل به آن دسترسی داشت؛ هر پیکسل با چهار مقدار یک‌بایتی (قرمز، سبز، آبی و آلفا، به همین ترتیب؛ یعنی قالب «RGBA») نمایش داده می‌شود. هر مؤلفه رنگی با یک عدد صحیح بین ۰ تا ۲۵۵ نمایش داده می‌شود. به هر مؤلفه یک ایندکس متوالی در آرایه اختصاص داده می‌شود، به طوری که مؤلفه قرمز پیکسل بالا-چپ در ایندکس ۰ آرایه قرار دارد. سپس پیکسل‌ها در سراسر آرایه از چپ به راست و سپس به سمت پایین ادامه می‌یابند.

{{jsxref("Uint8ClampedArray")}} شامل `height` × `width` × ۴ بایت داده است و مقادیر ایندکس از ۰ تا (`height` × `width` × ۴) - ۱ متغیر است.

برای مثال، برای خواندن مقدار مؤلفه آبی از پیکسل واقع در ستون ۲۰۰ و ردیف ۵۰ در تصویر، می‌توانید کار زیر را انجام دهید:

```js
const blueComponent = imageData.data[50 * (imageData.width * 4) + 200 * 4 + 2];
```

اگر یک مجموعه مختصات (X و Y) داشته باشید، ممکن است به کاری مانند زیر برسید:

```js
const xCoord = 50;
const yCoord = 100;
const canvasWidth = 1024;

const getColorIndicesForCoord = (x, y, width) => {
  const red = y * (width * 4) + x * 4;
  return [red, red + 1, red + 2, red + 3];
};

const colorIndices = getColorIndicesForCoord(xCoord, yCoord, canvasWidth);

const [redIndex, greenIndex, blueIndex, alphaIndex] = colorIndices;
```

همچنین می‌توانید با خواندن ویژگی `Uint8ClampedArray.length` به اندازه آرایه پیکسل بر حسب بایت دسترسی پیدا کنید:

```js
const numBytes = imageData.data.length;
```

## ایجاد یک شیء ImageData

برای ایجاد یک شیء `ImageData` جدید و خالی، باید از متد {{domxref("CanvasRenderingContext2D.createImageData", "createImageData()")}} استفاده کنید. دو نسخه از متد `createImageData()` وجود دارد:

```js
const myImageData = ctx.createImageData(width, height);
```

این کار یک شیء `ImageData` جدید با ابعاد مشخص‌شده ایجاد می‌کند. همه پیکسل‌ها از پیش شفاف تنظیم شده‌اند.

همچنین می‌توانید یک شیء `ImageData` جدید با همان ابعاد شیء مشخص‌شده توسط `anotherImageData` ایجاد کنید. پیکسل‌های شیء جدید همگی از پیش روی مشکی شفاف تنظیم شده‌اند. **این کار داده‌های تصویر را کپی نمی‌کند!**

```js
const myImageData = ctx.createImageData(anotherImageData);
```

## به‌دست آوردن داده‌های پیکسل برای یک بافت

برای دریافت یک شیء `ImageData` حاوی کپی‌ای از داده‌های پیکسل برای بافت canvas، می‌توانید از متد `getImageData()` استفاده کنید:

```js
const myImageData = ctx.getImageData(left, top, width, height);
```

این متد یک شیء `ImageData` برمی‌گرداند که داده‌های پیکسل را برای ناحیه‌ای از canvas نشان می‌دهد که گوشه‌های آن با نقاط (`left`, `top`)، (`left+width`, `top`)، (`left`, `top+height`) و (`left+width`, `top+height`) نمایش داده می‌شود. مختصات در واحدهای فضای مختصات canvas مشخص می‌شوند.

> [!NOTE]
> هر پیکسلی که خارج از canvas باشد، در شیء `ImageData` حاصل به صورت مشکی شفاف برگردانده می‌شود.

این روش همچنین در مقاله [دستکاری ویدیو با استفاده از canvas](/en-US/docs/Web/API/Canvas_API/Manipulating_video_using_canvas) نشان داده شده است.

## ایجاد یک انتخاب‌گر رنگ

در این مثال، از متد [`getImageData()`](/en-US/docs/Web/API/CanvasRenderingContext2D/getImageData) برای نمایش رنگ زیر نشانگر ماوس استفاده می‌کنیم.
برای این کار، به موقعیت فعلی ماوس نیاز داریم، سپس داده‌های پیکسل را در آن موقعیت در آرایه پیکسلی که [`getImageData()`](/en-US/docs/Web/API/CanvasRenderingContext2D/getImageData) فراهم می‌کند جستجو می‌کنیم.
در نهایت، از داده‌های آرایه برای تنظیم رنگ پس‌زمینه و متنی در `<div>` برای نمایش رنگ استفاده می‌کنیم.
کلیک روی تصویر همان عملیات را انجام می‌دهد اما از رنگ انتخاب‌شده استفاده می‌کند.

```html
<table>
  <thead>
    <tr>
      <th>Source</th>
      <th>Hovered color</th>
      <th>Selected color</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <canvas id="canvas" width="300" height="227"></canvas>
      </td>
      <td class="color-cell" id="hovered-color"></td>
      <td class="color-cell" id="selected-color"></td>
    </tr>
  </tbody>
</table>
```

```js
const img = new Image();
img.crossOrigin = "anonymous";
img.src = "/shared-assets/images/examples/rhino.jpg";
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
img.addEventListener("load", () => {
  ctx.drawImage(img, 0, 0);
  img.style.display = "none";
});
const hoveredColor = document.getElementById("hovered-color");
const selectedColor = document.getElementById("selected-color");

const pick = (event, destination) => {
  const bounding = canvas.getBoundingClientRect();
  const x = event.clientX - bounding.left;
  const y = event.clientY - bounding.top;
  const pixel = ctx.getImageData(x, y, 1, 1);
  const data = pixel.data;

  const rgbColor = `rgb(${data[0]} ${data[1]} ${data[2]} / ${data[3] / 255})`;
  destination.style.background = rgbColor;
  destination.textContent = rgbColor;

  return rgbColor;
};

canvas.addEventListener("mousemove", (event) => pick(event, hoveredColor));
canvas.addEventListener("click", (event) => pick(event, selectedColor));
```

```css hidden
body {
  font-family: sans-serif;
}
.color-cell {
  color: white;
}
th {
  width: 30%;
}
td {
  font-family: monospace;
  font-weight: bold;
  padding-left: 1rem;
}
```

نشانگر ماوس را هر جای تصویر ببرید تا نتیجه را در ستون «Hovered color» ببینید. روی هر نقطه از تصویر کلیک کنید تا نتیجه را در ستون «Selected color» مشاهده کنید.

{{embedlivesample("creating_a_color_picker", , 300)}}

## نقاشی کردن داده‌های پیکسل در یک بافت

می‌توانید از متد [putImageData()](/en-US/docs/Web/API/CanvasRenderingContext2D/putImageData) برای نقاشی کردن داده‌های پیکسل در یک بافت استفاده کنید:

```js
ctx.putImageData(myImageData, dx, dy);
```

پارامترهای `dx` و `dy` مختصات دستگاه را در داخل بافت نشان می‌دهند که در آن گوشه بالا-چپ داده‌های پیکسلی که می‌خواهید رسم کنید، نقاشی می‌شود.

برای مثال، برای نقاشی کردن کل تصویر نمایش‌داده‌شده توسط `myImageData` در گوشه بالا-چپ بافت، می‌توانید کار زیر را انجام دهید:

```js
ctx.putImageData(myImageData, 0, 0);
```

## خاکستری‌سازی و وارونه‌سازی رنگ‌ها

در این مثال، روی همه پیکسل‌ها پیمایش می‌کنیم تا مقادیر آن‌ها را تغییر دهیم، سپس آرایه پیکسل اصلاح‌شده را با استفاده از [putImageData()](/en-US/docs/Web/API/CanvasRenderingContext2D/putImageData) روی canvas بازمی‌گردانیم.
تابع `invert` هر رنگ را از حداکثر مقدار، یعنی `255` کم می‌کند.
تابع `grayscale` از میانگین قرمز، سبز و آبی استفاده می‌کند. همچنین می‌توانید از میانگین وزنی استفاده کنید، مثلاً با فرمول `x = 0.299r + 0.587g + 0.114b`.
برای اطلاعات بیشتر، [Grayscale](https://en.wikipedia.org/wiki/Grayscale) را در ویکی‌پدیا ببینید.

```html
<canvas id="canvas" width="300" height="227"></canvas>
<form>
  <input type="radio" id="original" name="color" value="original" checked />
  <label for="original">Original</label>

  <input type="radio" id="grayscale" name="color" value="grayscale" />
  <label for="grayscale">Grayscale</label>

  <input type="radio" id="inverted" name="color" value="inverted" />
  <label for="inverted">Inverted</label>

  <input type="radio" id="sepia" name="color" value="sepia" />
  <label for="sepia">Sepia</label>
</form>
```

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

const img = new Image();
img.crossOrigin = "anonymous";
img.src = "/shared-assets/images/examples/rhino.jpg";
img.onload = () => {
  ctx.drawImage(img, 0, 0);
};

const original = () => {
  ctx.drawImage(img, 0, 0);
};

const invert = () => {
  ctx.drawImage(img, 0, 0);
  const imageData = ctx.getImageData(0, 0, canvas.width, canvas.height);
  const data = imageData.data;
  for (let i = 0; i < data.length; i += 4) {
    data[i] = 255 - data[i]; // red
    data[i + 1] = 255 - data[i + 1]; // green
    data[i + 2] = 255 - data[i + 2]; // blue
  }
  ctx.putImageData(imageData, 0, 0);
};

const grayscale = () => {
  ctx.drawImage(img, 0, 0);
  const imageData = ctx.getImageData(0, 0, canvas.width, canvas.height);
  const data = imageData.data;
  for (let i = 0; i < data.length; i += 4) {
    const avg = (data[i] + data[i + 1] + data[i + 2]) / 3;
    data[i] = avg; // red
    data[i + 1] = avg; // green
    data[i + 2] = avg; // blue
  }
  ctx.putImageData(imageData, 0, 0);
};

const sepia = () => {
  ctx.drawImage(img, 0, 0);
  const imageData = ctx.getImageData(0, 0, canvas.width, canvas.height);
  const data = imageData.data;
  for (let i = 0; i < data.length; i += 4) {
    let r = data[i], // red
      g = data[i + 1], // green
      b = data[i + 2]; // blue

    data[i] = Math.min(Math.round(0.393 * r + 0.769 * g + 0.189 * b), 255);
    data[i + 1] = Math.min(Math.round(0.349 * r + 0.686 * g + 0.168 * b), 255);
    data[i + 2] = Math.min(Math.round(0.272 * r + 0.534 * g + 0.131 * b), 255);
  }
  ctx.putImageData(imageData, 0, 0);
};

const inputs = document.querySelectorAll("[name=color]");
for (const input of inputs) {
  input.addEventListener("change", (evt) => {
    switch (evt.target.value) {
      case "inverted":
        return invert();
      case "grayscale":
        return grayscale();
      case "sepia":
        return sepia();
      default:
        return original();
    }
  });
}
```

برای مشاهده نتیجه به صورت عملی، گزینه‌های مختلف را کلیک کنید.

{{embedlivesample("grayscaling_and_inverting_colors", , 300)}}

## بزرگ‌نمایی و ضدهموارسازی

با کمک متد {{domxref("CanvasRenderingContext2D.drawImage", "drawImage()")}}، یک canvas دوم و ویژگی {{domxref("CanvasRenderingContext2D.imageSmoothingEnabled", "imageSmoothingEnabled")}}، می‌توانیم روی تصویر خود بزرگنمایی کنیم و جزئیات را ببینیم. یک canvas سوم بدون {{domxref("CanvasRenderingContext2D.imageSmoothingEnabled", "imageSmoothingEnabled")}} نیز رسم می‌شود تا امکان مقایسه کنار هم فراهم شود.

```html
<table>
  <thead>
    <tr>
      <th>Source</th>
      <th>Smoothing enabled = true</th>
      <th>Smoothing enabled = false</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <canvas id="canvas" width="300" height="227"></canvas>
      </td>
      <td>
        <canvas id="smoothed" width="200" height="200"></canvas>
      </td>
      <td>
        <canvas id="pixelated" width="200" height="200"></canvas>
      </td>
    </tr>
  </tbody>
</table>
```

```css hidden
body {
  font-family: monospace;
}
```

موقعیت ماوس را می‌گیریم و تصویری به ابعاد ۵ پیکسل به چپ و بالا تا ۵ پیکسل به راست و پایین برش می‌دهیم.
سپس آن را روی canvas دیگری کپی می‌کنیم و اندازه تصویر را به اندازه دلخواه تغییر می‌دهیم. در canvas بزرگنمایی، یک برش ۱۰×۱۰ پیکسل از canvas اصلی را به ۲۰۰×۲۰۰ تغییر اندازه می‌دهیم:

```js
const img = new Image();
img.crossOrigin = "anonymous";
img.src = "/shared-assets/images/examples/rhino.jpg";
img.onload = () => {
  draw(img);
};

function draw(image) {
  const canvas = document.getElementById("canvas");
  const ctx = canvas.getContext("2d");
  ctx.drawImage(image, 0, 0);

  const smoothCtx = document.getElementById("smoothed").getContext("2d");
  smoothCtx.imageSmoothingEnabled = true;

  const pixelatedCtx = document.getElementById("pixelated").getContext("2d");
  pixelatedCtx.imageSmoothingEnabled = false;

  const zoom = (ctx, x, y) => {
    ctx.drawImage(
      canvas,
      Math.min(Math.max(0, x - 5), image.width - 10),
      Math.min(Math.max(0, y - 5), image.height - 10),
      10,
      10,
      0,
      0,
      200,
      200,
    );
  };

  canvas.addEventListener("mousemove", (event) => {
    const x = event.layerX;
    const y = event.layerY;
    zoom(smoothCtx, x, y);
    zoom(pixelatedCtx, x, y);
  });
}
```

{{embedlivesample("zooming_and_anti-aliasing", , 300)}}

## ذخیره تصاویر

{{domxref("HTMLCanvasElement")}} یک متد `toDataURL()` ارائه می‌دهد که برای ذخیره تصاویر مفید است. این متد یک [data URL](/en-US/docs/Web/URI/Reference/Schemes/data) شامل نمایشی از تصویر در قالبی که توسط پارامتر `type` مشخص شده است (پیش‌فرض [PNG](https://en.wikipedia.org/wiki/Portable_Network_Graphics)) برمی‌گرداند. تصویر برگشتی در وضوح ۹۶ dpi است.

> [!NOTE]
> توجه داشته باشید که اگر canvas شامل هر پیکسلی باشد که از {{Glossary("origin")}} دیگری بدون استفاده از CORS به دست آمده باشد، canvas به وضعیت **آلوده (tainted)** در می‌آید و دیگر نمی‌توان محتوای آن را خواند و ذخیره کرد. به [مشکلات امنیتی و canvasهای آلوده](/en-US/docs/Web/HTML/How_to/CORS_enabled_image#security_and_tainted_canvases) مراجعه کنید.

- {{domxref("HTMLCanvasElement.toDataURL", "canvas.toDataURL('image/png')")}}
  - : تنظیم پیش‌فرض. یک تصویر PNG ایجاد می‌کند.
- {{domxref("HTMLCanvasElement.toDataURL", "canvas.toDataURL('image/jpeg', quality)")}}
  - : یک تصویر JPG ایجاد می‌کند. به‌صورت اختیاری، می‌توانید کیفیتی در بازه ۰ تا ۱ ارائه دهید که ۱ بهترین کیفیت و ۰ تقریباً غیرقابل تشخیص اما با حجم فایل کوچک است.

هنگامی که یک data URL از canvas خود تولید کردید، می‌توانید از آن به عنوان منبع هر {{HTMLElement("img")}} استفاده کنید، یا مثلاً آن را در یک پیوند با [ویژگی download](/en-US/docs/Web/HTML/Reference/Elements/a#download) قرار دهید تا روی دیسک ذخیره شود.

همچنین می‌توانید یک {{domxref("Blob")}} از canvas ایجاد کنید.

- {{domxref("HTMLCanvasElement.toBlob", "canvas.toBlob(callback, type, encoderOptions)")}}
  - : یک شیء `Blob` ایجاد می‌کند که تصویر موجود در canvas را نشان می‌دهد.

## همچنین ببینید

- {{domxref("ImageData")}}
- [دستکاری ویدیو با استفاده از canvas](/en-US/docs/Web/API/Canvas_API/Manipulating_video_using_canvas)
- [دانلود تصاویر تولیدشده با Canvas API با استفاده از toBlob](https://www.digitalocean.com/community/tutorials/js-canvas-toblob)

{{PreviousNext("Web/API/Canvas_API/Tutorial/Advanced_animations", "Web/API/Canvas_API/Tutorial/Optimizing_canvas")}}