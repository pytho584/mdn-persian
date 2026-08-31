---
title: "Optimizing canvas"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Optimizing_canvas"
translated_by: "n8n + AI"
---

---
title: Optimizing canvas
slug: Web/API/Canvas_API/Tutorial/Optimizing_canvas
page-type: guide
---

{{DefaultAPISidebar("Canvas API")}} {{PreviousNext("Web/API/Canvas_API/Tutorial/Pixel_manipulation_with_canvas", "Web/API/Canvas_API/Tutorial/Finale")}}

عنصر {{HTMLElement("canvas")}} یکی از پرکاربردترین ابزارها برای رندر کردن گرافیک دو بعدی در وب است. با این حال، هنگامی که وب‌سایت‌ها و برنامه‌ها Canvas API را تا حد توان خود تحت فشار قرار می‌دهند، عملکرد افت می‌کند. این مقاله پیشنهادهایی برای بهینه‌سازی استفاده از عنصر canvas ارائه می‌دهد تا گرافیک شما عملکرد خوبی داشته باشد.

## نکات عملکرد

در ادامه مجموعه‌ای از نکات برای بهبود عملکرد canvas آورده شده است.

### پیش‌رندر کردن اولیه‌های مشابه یا اشیاء تکراری روی یک بوم خارج از صفحه (offscreen canvas)

اگر متوجه می‌شوید که برخی از عملیات‌های ترسیم یکسان را در هر فریم انیمیشن تکرار می‌کنید، آنها را به یک بوم خارج از صفحه (offscreen canvas) منتقل کنید. سپس می‌توانید تصویر خارج از صفحه را هر چند بار که نیاز است به بوم اصلی خود رندر کنید، بدون اینکه مراحل لازم برای تولید آن را به طور غیرضروری تکرار کنید.

```js
myCanvas.offscreenCanvas = document.createElement("canvas");
myCanvas.offscreenCanvas.width = myCanvas.width;
myCanvas.offscreenCanvas.height = myCanvas.height;

myCanvas.getContext("2d").drawImage(myCanvas.offScreenCanvas, 0, 0);
```

### از مختصات اعشاری خودداری کرده و به جای آن از اعداد صحیح استفاده کنید

رندر زیرپیکسل زمانی رخ می‌دهد که اشیاء را روی بوم بدون مقادیر کامل رندر کنید.

```js
ctx.drawImage(myImage, 0.3, 0.5);
```

این کار مرورگر را مجبور می‌کند محاسبات اضافی برای ایجاد اثر ضد آلیاسینگ انجام دهد. برای جلوگیری از این کار، مطمئن شوید که تمام مختصات استفاده شده در فراخوانی‌های {{domxref("CanvasRenderingContext2D.drawImage", "drawImage()")}} را با استفاده از {{jsxref("Math.floor()")}} گرد کنید.

### در `drawImage` تصاویر را مقیاس‌بندی نکنید

اندازه‌های مختلف تصاویر خود را هنگام بارگذاری روی یک بوم خارج از صفحه ذخیره کنید (کش کنید) به جای اینکه دائماً آنها را در {{domxref("CanvasRenderingContext2D.drawImage", "drawImage()")}} مقیاس‌بندی کنید.

### برای صحنه‌های پیچیده از چندین بوم لایه‌ای استفاده کنید

در برنامه خود، ممکن است متوجه شوید که برخی اشیاء نیاز به حرکت یا تغییر مکرر دارند، در حالی که برخی دیگر نسبتاً ثابت می‌مانند. یک بهینه‌سازی ممکن در این وضعیت، لایه‌بندی آیتم‌ها با استفاده از چندین عنصر `<canvas>` است.

به عنوان مثال، فرض کنید یک بازی دارید با یک رابط کاربری در بالا، اکشن بازی در وسط، و یک پس‌زمینه ثابت در پایین. در این حالت، می‌توانید بازی خود را به سه لایه `<canvas>` تقسیم کنید. رابط کاربری فقط با ورودی کاربر تغییر می‌کند، لایه بازی با هر فریم جدید تغییر می‌کند، و پس‌زمینه عموماً بدون تغییر باقی می‌ماند.

```html
<div id="stage">
  <canvas id="ui-layer" width="480" height="320"></canvas>
  <canvas id="game-layer" width="480" height="320"></canvas>
  <canvas id="background-layer" width="480" height="320"></canvas>
</div>
```

```css
#stage {
  width: 480px;
  height: 320px;
  position: relative;
  border: 2px solid black;
}

canvas {
  position: absolute;
}
#ui-layer {
  z-index: 3;
}
#game-layer {
  z-index: 2;
}
#background-layer {
  z-index: 1;
}
```

### برای تصاویر پس‌زمینه بزرگ از CSS ساده استفاده کنید

اگر یک تصویر پس‌زمینه ثابت دارید، می‌توانید آن را روی یک عنصر {{HTMLElement("div")}} ساده با استفاده از ویژگی CSS {{cssxref("background")}} رسم کنید و آن را زیر بوم قرار دهید. این کار نیاز به رندر کردن پس‌زمینه روی بوم در هر تیک را از بین می‌برد.

### مقیاس‌بندی بوم با استفاده از تبدیل‌های CSS

[تبدیل‌های CSS](/en-US/docs/Web/CSS/Guides/Transforms/Using) از آنجایی که از GPU استفاده می‌کنند سریع‌تر هستند. بهترین حالت این است که بوم را مقیاس‌بندی نکنید، یا یک بوم کوچک‌تر داشته باشید و بزرگنمایی کنید به جای یک بوم بزرگ‌تر و کوچکنمایی.

```js
const scaleX = window.innerWidth / canvas.width;
const scaleY = window.innerHeight / canvas.height;

const scaleToFit = Math.min(scaleX, scaleY);
const scaleToCover = Math.max(scaleX, scaleY);

stage.style.transformOrigin = "0 0"; // Scale from top left
stage.style.transform = `scale(${scaleToFit})`;
```

### شفافیت را غیرفعال کنید

اگر برنامه شما از canvas استفاده می‌کند و نیازی به پس‌زمینه شفاف ندارد، گزینه `alpha` را هنگام ایجاد یک زمینه ترسیم با {{domxref("HTMLCanvasElement.getContext()")}} روی `false` تنظیم کنید. این اطلاعات می‌تواند توسط مرورگر به صورت داخلی برای بهینه‌سازی رندر استفاده شود.

```js
const ctx = canvas.getContext("2d", { alpha: false });
```

### مقیاس‌بندی برای نمایشگرهای با وضوح بالا

ممکن است متوجه شوید که آیتم‌های بوم روی نمایشگرهای با وضوح بالا تار به نظر می‌رسند. در حالی که راه‌حل‌های زیادی ممکن است وجود داشته باشد، یک گام اول ساده این است که اندازه بوم را همزمان با استفاده از ویژگی‌ها، استایل‌دهی و مقیاس زمینه آن، بزرگ و کوچک کنید.

```js
// Get the DPR and size of the canvas
const dpr = window.devicePixelRatio;
const rect = canvas.getBoundingClientRect();

// Set the "actual" size of the canvas
canvas.width = rect.width * dpr;
canvas.height = rect.height * dpr;

// Scale the context to ensure correct drawing operations
ctx.scale(dpr, dpr);

// Set the "drawn" size of the canvas
canvas.style.width = `${rect.width}px`;
canvas.style.height = `${rect.height}px`;
```

### نکات بیشتر

- فراخوانی‌های بوم را دسته‌بندی کنید. به عنوان مثال، به جای چند خط جداگانه، یک چندخطی (polyline) رسم کنید.
- از تغییرات غیرضروری وضعیت بوم خودداری کنید.
- فقط تفاوت‌های صفحه را رندر کنید، نه کل وضعیت جدید.
- تا حد امکان از ویژگی {{domxref("CanvasRenderingContext2D.shadowBlur", "shadowBlur")}} خودداری کنید.
- تا حد امکان از [رندر متن](/en-US/docs/Web/API/Canvas_API/Tutorial/Drawing_text) خودداری کنید.
- روش‌های مختلف برای پاک کردن بوم را امتحان کنید ({{domxref("CanvasRenderingContext2D.clearRect", "clearRect()")}} در مقابل {{domxref("CanvasRenderingContext2D.fillRect", "fillRect()")}} در مقابل تغییر اندازه بوم).
- با انیمیشن‌ها، از {{domxref("Window.requestAnimationFrame()")}} به جای {{domxref("Window.setInterval", "setInterval()")}} استفاده کنید.
- با کتابخانه‌های فیزیک سنگین محتاط باشید.

{{PreviousNext("Web/API/Canvas_API/Tutorial/Pixel_manipulation_with_canvas", "Web/API/Canvas_API/Tutorial/Finale")}}