---
title: "Basic animations"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Basic_animations"
translated_by: "n8n + AI"
---

---
title: Basic animations
slug: Web/API/Canvas_API/Tutorial/Basic_animations
page-type: guide
---

{{DefaultAPISidebar("Canvas API")}} {{PreviousNext("Web/API/Canvas_API/Tutorial/Compositing", "Web/API/Canvas_API/Tutorial/Advanced_animations")}}

از آنجایی که از جاوااسکریپت برای کنترل عناصر {{HTMLElement("canvas")}} استفاده می‌کنیم، ساخت انیمیشن‌های (تعاملی) نیز بسیار آسان است. در این فصل نگاهی خواهیم داشت به نحوه انجام برخی انیمیشن‌های پایه.

احتمالاً بزرگترین محدودیت این است که وقتی یک شکل کشیده می‌شود، به همان شکل باقی می‌ماند. اگر نیاز به جابجایی آن داشته باشیم، باید آن و همه چیزهایی که قبلاً رسم شده‌اند را دوباره رسم کنیم. رسم مجدد فریم‌های پیچیده زمان زیادی می‌برد و عملکرد به شدت به سرعت کامپیوتری که روی آن اجرا می‌شود وابسته است.

## مراحل انیمیشن پایه

این مراحلی است که برای رسم یک فریم باید انجام دهید:

1. **پاک کردن بوم**
   مگر اینکه اشکالی که می‌کشید کل بوم را پر کنند (مثلاً یک تصویر پس‌زمینه)، باید هر شکلی که قبلاً رسم شده است را پاک کنید. ساده‌ترین راه برای این کار استفاده از متد {{domxref("CanvasRenderingContext2D.clearRect", "clearRect()")}} است.
2. **ذخیره وضعیت بوم**
   اگر در حال تغییر هر تنظیماتی (مانند سبک‌ها، تبدیل‌ها و غیره) هستید که بر وضعیت بوم تأثیر می‌گذارد و می‌خواهید مطمئن شوید که وضعیت اصلی هر بار که یک فریم رسم می‌شود استفاده می‌شود، باید آن وضعیت اصلی را ذخیره کنید.
3. **رسم اشکال متحرک**
   مرحله‌ای که در آن رندر واقعی فریم را انجام می‌دهید.
4. **بازیابی وضعیت بوم**
   اگر وضعیت را ذخیره کرده‌اید، قبل از رسم یک فریم جدید آن را بازیابی کنید.

## کنترل یک انیمیشن

اشکال با استفاده از متدهای بوم به طور مستقیم یا با فراخوانی توابع سفارشی روی بوم رسم می‌شوند. در شرایط عادی، ما فقط زمانی این نتایج را روی بوم می‌بینیم که اجرای اسکریپت به پایان برسد. به عنوان مثال، امکان انجام انیمیشن از داخل یک حلقه `for` وجود ندارد.

این بدان معناست که ما به راهی برای اجرای توابع رسم خود در یک بازه زمانی نیاز داریم. دو روش برای کنترل یک انیمیشن به این شکل وجود دارد.

### به‌روزرسانی‌های زمان‌بندی شده

ابتدا توابع {{domxref("Window.setInterval", "setInterval()")}}، {{domxref("Window.setTimeout", "setTimeout()")}} و {{domxref("Window.requestAnimationFrame", "requestAnimationFrame()")}} وجود دارند که می‌توان از آنها برای فراخوانی یک تابع خاص در یک بازه زمانی مشخص استفاده کرد.

- {{domxref("Window.setInterval", "setInterval()")}}
  - : شروع به اجرای مکرر تابع مشخص شده توسط `function` هر `delay` میلی‌ثانیه می‌کند.
- {{domxref("Window.setTimeout", "setTimeout()")}}
  - : تابع مشخص شده توسط `function` را پس از `delay` میلی‌ثانیه اجرا می‌کند.
- {{domxref("Window.requestAnimationFrame", "requestAnimationFrame()")}}
  - : به مرورگر اطلاع می‌دهد که می‌خواهید یک انیمیشن انجام دهید و از مرورگر می‌خواهد که یک تابع مشخص را برای به‌روزرسانی یک انیمیشن قبل از رنگ‌آمیزی مجدد بعدی فراخوانی کند.

اگر تعامل کاربری نمی‌خواهید می‌توانید از تابع `setInterval()` استفاده کنید که کد ارائه شده را به طور مکرر اجرا می‌کند. اگر می‌خواستیم یک بازی بسازیم، می‌توانستیم از رویدادهای صفحه کلید یا ماوس برای کنترل انیمیشن استفاده کنیم و از `setTimeout()` استفاده کنیم. با تنظیم شنوندگان با استفاده از {{domxref("EventTarget.addEventListener", "addEventListener()")}}، هر تعامل کاربری را ضبط کرده و توابع انیمیشن خود را اجرا می‌کنیم.

> [!NOTE]
> در مثال‌های زیر، از متد {{domxref("Window.requestAnimationFrame()")}} برای کنترل انیمیشن استفاده می‌کنیم. متد `requestAnimationFrame` روشی روان‌تر و کارآمدتر برای انیمیشن‌سازی با فراخوانی فریم انیمیشن زمانی که سیستم آماده نقاشی فریم است، فراهم می‌کند. تعداد فراخوانی‌ها معمولاً 60 بار در ثانیه است و ممکن است هنگام اجرا در برگه‌های پس‌زمینه به نرخ کمتری کاهش یابد. برای اطلاعات بیشتر در مورد حلقه انیمیشن، به خصوص برای بازی‌ها، مقاله [آناتومی یک بازی ویدیویی](/en-US/docs/Games/Anatomy) در [منطقه توسعه بازی](/en-US/docs/Games) ما را ببینید.

## یک منظومه شمسی متحرک

این مثال یک مدل کوچک از منظومه شمسی ما را متحرک می‌کند.

### HTML

```html
<canvas id="canvas" width="300" height="300"></canvas>
```

### JavaScript

```js
const sun = new Image();
const moon = new Image();
const earth = new Image();
const ctx = document.getElementById("canvas").getContext("2d");

function init() {
  sun.src = "canvas_sun.png";
  moon.src = "canvas_moon.png";
  earth.src = "canvas_earth.png";
  window.requestAnimationFrame(draw);
}

function draw() {
  ctx.globalCompositeOperation = "destination-over";
  ctx.clearRect(0, 0, 300, 300); // clear canvas

  ctx.fillStyle = "rgb(0 0 0 / 40%)";
  ctx.strokeStyle = "rgb(0 153 255 / 40%)";
  ctx.save();
  ctx.translate(150, 150);

  // Earth
  const time = new Date();
  ctx.rotate(
    ((2 * Math.PI) / 60) * time.getSeconds() +
      ((2 * Math.PI) / 60000) * time.getMilliseconds(),
  );
  ctx.translate(105, 0);
  ctx.fillRect(0, -12, 40, 24); // Shadow
  ctx.drawImage(earth, -12, -12);

  // Moon
  ctx.save();
  ctx.rotate(
    ((2 * Math.PI) / 6) * time.getSeconds() +
      ((2 * Math.PI) / 6000) * time.getMilliseconds(),
  );
  ctx.translate(0, 28.5);
  ctx.drawImage(moon, -3.5, -3.5);
  ctx.restore();

  ctx.restore();

  ctx.beginPath();
  ctx.arc(150, 150, 105, 0, Math.PI * 2, false); // Earth orbit
  ctx.stroke();

  ctx.drawImage(sun, 0, 0, 300, 300);

  window.requestAnimationFrame(draw);
}

init();
```

### نتیجه

{{EmbedLiveSample("An_animated_solar_system", "310", "340")}}

## یک ساعت متحرک

این مثال یک ساعت متحرک را رسم می‌کند که زمان فعلی شما را نشان می‌دهد.

### HTML

```html
<canvas id="canvas" width="150" height="150">The current time</canvas>
```

### JavaScript

```js
function clock() {
  const now = new Date();
  const canvas = document.getElementById("canvas");
  const ctx = canvas.getContext("2d");
  ctx.save();
  ctx.clearRect(0, 0, 150, 150);
  ctx.translate(75, 75);
  ctx.scale(0.4, 0.4);
  ctx.rotate(-Math.PI / 2);
  ctx.strokeStyle = "black";
  ctx.fillStyle = "white";
  ctx.lineWidth = 8;
  ctx.lineCap = "round";

  // Hour marks
  ctx.save();
  for (let i = 0; i < 12; i++) {
    ctx.beginPath();
    ctx.rotate(Math.PI / 6);
    ctx.moveTo(100, 0);
    ctx.lineTo(120, 0);
    ctx.stroke();
  }
  ctx.restore();

  // Minute marks
  ctx.save();
  ctx.lineWidth = 5;
  for (let i = 0; i < 60; i++) {
    if (i % 5 !== 0) {
      ctx.beginPath();
      ctx.moveTo(117, 0);
      ctx.lineTo(120, 0);
      ctx.stroke();
    }
    ctx.rotate(Math.PI / 30);
  }
  ctx.restore();

  const sec = now.getSeconds();
  // To display a clock with a sweeping second hand, use:
  // const sec = now.getSeconds() + now.getMilliseconds() / 1000;
  const min = now.getMinutes();
  const hr = now.getHours() % 12;

  ctx.fillStyle = "black";

  // Write image description
  canvas.innerText = `The time is: ${hr}:${min}`;

  // Write Hours
  ctx.save();
  ctx.rotate(
    (Math.PI / 6) * hr + (Math.PI / 360) * min + (Math.PI / 21600) * sec,
  );
  ctx.lineWidth = 14;
  ctx.beginPath();
  ctx.moveTo(-20, 0);
  ctx.lineTo(80, 0);
  ctx.stroke();
  ctx.restore();

  // Write Minutes
  ctx.save();
  ctx.rotate((Math.PI / 30) * min + (Math.PI / 1800) * sec);
  ctx.lineWidth = 10;
  ctx.beginPath();
  ctx.moveTo(-28, 0);
  ctx.lineTo(112, 0);
  ctx.stroke();
  ctx.restore();

  // Write seconds
  ctx.save();
  ctx.rotate((sec * Math.PI) / 30);
  ctx.strokeStyle = "#D40000";
  ctx.fillStyle = "#D40000";
  ctx.lineWidth = 6;
  ctx.beginPath();
  ctx.moveTo(-30, 0);
  ctx.lineTo(83, 0);
  ctx.stroke();
  ctx.beginPath();
  ctx.arc(0, 0, 10, 0, Math.PI * 2, true);
  ctx.fill();
  ctx.beginPath();
  ctx.arc(95, 0, 10, 0, Math.PI * 2, true);
  ctx.stroke();
  ctx.fillStyle = "transparent";
  ctx.arc(0, 0, 3, 0, Math.PI * 2, true);
  ctx.fill();
  ctx.restore();

  ctx.beginPath();
  ctx.lineWidth = 14;
  ctx.strokeStyle = "#325FA2";
  ctx.arc(0, 0, 142, 0, Math.PI * 2, true);
  ctx.stroke();

  ctx.restore();

  window.requestAnimationFrame(clock);
}

window.requestAnimationFrame(clock);
```

### نتیجه

> [!NOTE]
> اگرچه ساعت فقط یک بار در هر ثانیه به‌روز می‌شود، تصویر متحرک با 60 فریم در ثانیه (یا با نرخ تازه‌سازی نمایشگر مرورگر وب شما) به‌روز می‌شود. برای نمایش ساعت با عقربه ثانیه‌ای پیوسته، تعریف `const sec` بالا را با نسخه‌ای که در کامنت قرار داده شده است جایگزین کنید.

{{EmbedLiveSample("An_animated_clock", "180", "200")}}

## یک پانورامای حلقه‌ای

در این مثال، یک پانوراما از چپ به راست اسکرول می‌شود. ما از [تصویری از پارک ملی یوسیمیتی](https://commons.wikimedia.org/wiki/File:Capitan_Meadows,_Yosemite_National_Park.jpg) که از ویکی‌پدیا برداشتیم استفاده می‌کنیم، اما شما می‌توانید از هر تصویری که بزرگ‌تر از بوم است استفاده کنید.

### HTML

HTML شامل {{HTMLElement("canvas")}} است که تصویر در آن اسکرول می‌شود. توجه داشته باشید که عرض و ارتفاع مشخص شده در اینجا باید با مقادیر متغیرهای `canvasXSize` و `canvasYSize` در کد جاوااسکریپت مطابقت داشته باشد.

```html
<canvas id="canvas" width="800" height="200"
  >Yosemite National Park, meadow at the base of El Capitan</canvas
>
```

### JavaScript

```js
const img = new Image();

// User Variables - customize these to change the image being scrolled, its
// direction, and the speed.
img.src = "capitan_meadows_yosemite_national_park.jpg";
const canvasXSize = 800;
const canvasYSize = 200;
const speed = 30; // lower is faster
const scale = 1.05;
const y = -4.5; // vertical offset

// Main program
const dx = 0.75;
let imgW;
let imgH;
let x = 0;
let clearX;
let clearY;
let ctx;

img.onload = () => {
  imgW = img.width * scale;
  imgH = img.height * scale;

  if (imgW > canvasXSize) {
    // Image larger than canvas
    x = canvasXSize - imgW;
  }

  // Check if image dimension is larger than canvas
  clearX = Math.max(imgW, canvasXSize);
  clearY = Math.max(imgH, canvasYSize);

  // Get canvas context
  ctx = document.getElementById("canvas").getContext("2d");

  // Set refresh rate
  return setInterval(draw, speed);
};

function draw() {
  ctx.clearRect(0, 0, clearX, clearY); // clear the canvas

  // If image is <= canvas size
  if (imgW <= canvasXSize) {
    // Reset, start from beginning
    if (x > canvasXSize) {
      x = -imgW + x;
    }

    // Draw additional image1
    if (x > 0) {
      ctx.drawImage(img, -imgW + x, y, imgW, imgH);
    }

    // Draw additional image2
    if (x - imgW > 0) {
      ctx.drawImage(img, -imgW * 2 + x, y, imgW, imgH);
    }
  } else {
    // Image is > canvas size
    // Reset, start from beginning
    if (x > canvasXSize) {
      x = canvasXSize - imgW;
    }

    // Draw additional image
    if (x > canvasXSize - imgW) {
      ctx.drawImage(img, x - imgW + 1, y, imgW, imgH);
    }
  }

  // Draw image
  ctx.drawImage(img, x, y, imgW, imgH);

  // Amount to move
  x += dx;
}
```

### نتیجه

{{EmbedLiveSample("A_looping_panorama", "830", "250")}}

## انیمیشن دنبال کردن ماوس

### HTML

```html
<canvas id="cw"
  >Animation creating multi-colored disappearing stream of light that follow the
  cursor as it moves over the image
</canvas>
```

### CSS

```css
#cw {
  position: fixed;
  z-index: -1;
}

body {
  margin: 0;
  padding: 0;
  background-color: rgb(0 0 0 / 5%);
}
```

### JavaScript

```js
const canvas = document.getElementById("cw");
const context = canvas.getContext("2d");
context.globalAlpha = 0.5;

const cursor = {
  x: innerWidth / 2,
  y: innerHeight / 2,
};

let particlesArray = [];

generateParticles(101);
setSize();
anim();

addEventListener("mousemove", (e) => {
  cursor.x = e.clientX;
  cursor.y = e.clientY;
});

addEventListener(
  "touchmove",
  (e) => {
    e.preventDefault();
    cursor.x = e.touches[0].clientX;
    cursor.y = e.touches[0].clientY;
  },
  { passive: false },
);

addEventListener("resize", () => setSize());

function generateParticles(amount) {
  for (let i = 0; i < amount; i++) {
    particlesArray[i] = new Particle(
      innerWidth / 2,
      innerHeight / 2,
      4,
      generateColor(),
      0.02,
    );
  }
}

function generateColor() {
  let hexSet = "0123456789ABCDEF";
  let finalHexString = "#";
  for (let i = 0; i < 6; i++) {
    finalHexString += hexSet[Math.ceil(Math.random() * 15)];
  }
  return finalHexString;
}

function setSize() {
  canvas.height = innerHeight;
  canvas.width = innerWidth;
}

function Particle(x, y, particleTrailWidth, strokeColor, rotateSpeed) {
  this.x = x;
  this.y = y;
  this.particleTrailWidth = particleTrailWidth;
  this.strokeColor = strokeColor;
  this.theta = Math.random() * Math.PI * 2;
  this.rotateSpeed = rotateSpeed;
  this.t = Math.random() * 150;

  this.rotate = () => {
    const ls = {
      x: this.x,
      y: this.y,
    };
    this.theta += this.rotateSpeed;
    this.x = cursor.x + Math.cos(this.theta) * this.t;
    this.y = cursor.y + Math.sin(this.theta) * this.t;
    context.beginPath();
    context.lineWidth = this.particleTrailWidth;
    context.strokeStyle = this.strokeColor;
    context.moveTo(ls.x, ls.y);
    context.lineTo(this.x, this.y);
    context.stroke();
  };
}

function anim() {
  requestAnimationFrame(anim);

  context.fillStyle = "rgb(0 0 0 / 5%)";
  context.fillRect(0, 0, canvas.width, canvas.height);

  particlesArray.forEach((particle) => particle.rotate());
}
```

### نتیجه

{{EmbedLiveSample("Mouse_following_animation", "500", "500")}}

## سایر مثال‌ها

- [انیمیشن‌های پیشرفته](/en-US/docs/Web/API/Canvas_API/Tutorial/Advanced_animations)
  - : در فصل بعدی به برخی تکنیک‌های پیشرفته انیمیشن و فیزیک خواهیم پرداخت.

{{PreviousNext("Web/API/Canvas_API/Tutorial/Compositing", "Web/API/Canvas_API/Tutorial/Advanced_animations")}}