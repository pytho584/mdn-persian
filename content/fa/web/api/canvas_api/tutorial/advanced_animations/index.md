---
title: "Advanced animations"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Advanced_animations"
translated_by: "n8n + AI"
---

---
title: Advanced animations
slug: Web/API/Canvas_API/Tutorial/Advanced_animations
page-type: guide
---

{{DefaultAPISidebar("Canvas API")}} {{PreviousNext("Web/API/Canvas_API/Tutorial/Basic_animations", "Web/API/Canvas_API/Tutorial/Pixel_manipulation_with_canvas")}}

در فصل قبل، تعدادی [انیمیشن پایه](/en-US/docs/Web/API/Canvas_API/Tutorial/Basic_animations) ساختیم و با روش‌های حرکت دادن اشیا آشنا شدیم. در این بخش، نگاه دقیق‌تری به خود حرکت خواهیم داشت و فیزیک را اضافه خواهیم کرد تا انیمیشن‌های پیشرفته‌تری بسازیم.

## رسم یک توپ

ما برای مطالعهٔ انیمیشن از یک توپ استفاده خواهیم کرد، بنابراین بیایید ابتدا آن توپ را روی بوم رسم کنیم. کد زیر ما را آماده می‌کند.

```html
<canvas id="canvas" width="600" height="300"></canvas>
```

طبق معمول، ابتدا به یک زمینهٔ ترسیم نیاز داریم. برای رسم توپ، یک شیء `ball` ایجاد می‌کنیم که شامل ویژگی‌ها و یک متد `draw()` برای رسم آن روی بوم است.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

const ball = {
  x: 100,
  y: 100,
  radius: 25,
  color: "blue",
  draw() {
    ctx.beginPath();
    ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2, true);
    ctx.closePath();
    ctx.fillStyle = this.color;
    ctx.fill();
  },
};

ball.draw();
```

در اینجا چیز خاصی وجود ندارد؛ توپ در واقع یک دایرهٔ ساده است و با کمک متد {{domxref("CanvasRenderingContext2D.arc()", "arc()")}} رسم می‌شود.

## افزودن سرعت

حالا که توپ را داریم، آماده‌ایم یک انیمیشن پایه مانند آنچه در [فصل قبل](/en-US/docs/Web/API/Canvas_API/Tutorial/Basic_animations) این آموزش یاد گرفتیم اضافه کنیم. باز هم، {{domxref("window.requestAnimationFrame()")}} به ما در کنترل انیمیشن کمک می‌کند. توپ با افزودن بردار سرعت به موقعیت، به حرکت در می‌آید. برای هر فریم، ما همچنین بوم را {{domxref("CanvasRenderingContext2D.clearRect", "پاک‌سازی", "", 1)}} می‌کنیم تا دایره‌های قدیمی فریم‌های قبلی حذف شوند.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
let raf;

const ball = {
  x: 100,
  y: 100,
  vx: 5,
  vy: 2,
  radius: 25,
  color: "blue",
  draw() {
    ctx.beginPath();
    ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2, true);
    ctx.closePath();
    ctx.fillStyle = this.color;
    ctx.fill();
  },
};

function draw() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  ball.draw();
  ball.x += ball.vx;
  ball.y += ball.vy;
  raf = window.requestAnimationFrame(draw);
}

canvas.addEventListener("mouseover", (e) => {
  raf = window.requestAnimationFrame(draw);
});

canvas.addEventListener("mouseout", (e) => {
  window.cancelAnimationFrame(raf);
});

ball.draw();
```

## مرزها

بدون تست برخورد مرزی، توپ ما به سرعت از بوم خارج می‌شود. باید بررسی کنیم که آیا موقعیت `x` و `y` توپ خارج از ابعاد بوم است و جهت بردارهای سرعت را معکوس کنیم. برای انجام این کار، بررسی‌های زیر را به متد `draw` اضافه می‌کنیم:

```js
if (
  ball.y + ball.vy > canvas.height - ball.radius ||
  ball.y + ball.vy < ball.radius
) {
  ball.vy = -ball.vy;
}
if (
  ball.x + ball.vx > canvas.width - ball.radius ||
  ball.x + ball.vx < ball.radius
) {
  ball.vx = -ball.vx;
}
```

### نمایش اول

بیایید ببینیم تا اینجا در عمل چگونه به نظر می‌رسد.

#### HTML

```html
<canvas id="canvas" width="600" height="300"></canvas>
```

```css hidden
#canvas {
  border: 1px solid black;
}
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
let raf;

const ball = {
  x: 100,
  y: 100,
  vx: 5,
  vy: 2,
  radius: 25,
  color: "blue",
  draw() {
    ctx.beginPath();
    ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2, true);
    ctx.closePath();
    ctx.fillStyle = this.color;
    ctx.fill();
  },
};

function draw() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  ball.draw();
  ball.x += ball.vx;
  ball.y += ball.vy;

  if (
    ball.y + ball.vy > canvas.height - ball.radius ||
    ball.y + ball.vy < ball.radius
  ) {
    ball.vy = -ball.vy;
  }
  if (
    ball.x + ball.vx > canvas.width - ball.radius ||
    ball.x + ball.vx < ball.radius
  ) {
    ball.vx = -ball.vx;
  }

  raf = window.requestAnimationFrame(draw);
}

canvas.addEventListener("mouseover", (e) => {
  raf = window.requestAnimationFrame(draw);
});

canvas.addEventListener("mouseout", (e) => {
  window.cancelAnimationFrame(raf);
});

ball.draw();
```

#### نتیجه

برای شروع انیمیشن، ماوس خود را داخل بوم ببرید.

{{EmbedLiveSample("First_demo", "610", "340")}}

## شتاب

برای واقعی‌تر کردن حرکت، می‌توانید سرعت را به این صورت تغییر دهید، برای مثال:

```js
ball.vy *= 0.99;
ball.vy += 0.25;
```

این کار سرعت عمودی را در هر فریم کاهش می‌دهد، به طوری که در نهایت توپ فقط روی زمین می‌پرد.

### نمایش دوم

#### HTML

```html
<canvas id="canvas" width="600" height="300"></canvas>
```

```css hidden
#canvas {
  border: 1px solid black;
}
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
let raf;

const ball = {
  x: 100,
  y: 100,
  vx: 5,
  vy: 2,
  radius: 25,
  color: "blue",
  draw() {
    ctx.beginPath();
    ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2, true);
    ctx.closePath();
    ctx.fillStyle = this.color;
    ctx.fill();
  },
};

function draw() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  ball.draw();
  ball.x += ball.vx;
  ball.y += ball.vy;
  ball.vy *= 0.99;
  ball.vy += 0.25;

  if (
    ball.y + ball.vy > canvas.height - ball.radius ||
    ball.y + ball.vy < ball.radius
  ) {
    ball.vy = -ball.vy;
  }
  if (
    ball.x + ball.vx > canvas.width - ball.radius ||
    ball.x + ball.vx < ball.radius
  ) {
    ball.vx = -ball.vx;
  }

  raf = window.requestAnimationFrame(draw);
}

canvas.addEventListener("mouseover", (e) => {
  raf = window.requestAnimationFrame(draw);
});

canvas.addEventListener("mouseout", (e) => {
  window.cancelAnimationFrame(raf);
});

ball.draw();
```

#### نتیجه

{{EmbedLiveSample("Second_demo", "610", "340")}}

## اثر دنباله

تا کنون هنگام پاک‌سازی فریم‌های قبلی از متد {{domxref("CanvasRenderingContext2D.clearRect", "clearRect")}} استفاده کرده‌ایم. اگر این متد را با یک {{domxref("CanvasRenderingContext2D.fillRect", "fillRect")}} نیمه‌شفاف جایگزین کنید، می‌توانید به راحتی یک اثر دنباله ایجاد کنید.

```js
ctx.fillStyle = "rgb(255 255 255 / 30%)";
ctx.fillRect(0, 0, canvas.width, canvas.height);
```

### نمایش سوم

#### HTML

```html
<canvas id="canvas" width="600" height="300"></canvas>
```

```css hidden
#canvas {
  border: 1px solid black;
}
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
let raf;

const ball = {
  x: 100,
  y: 100,
  vx: 5,
  vy: 2,
  radius: 25,
  color: "blue",
  draw() {
    ctx.beginPath();
    ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2, true);
    ctx.closePath();
    ctx.fillStyle = this.color;
    ctx.fill();
  },
};

function draw() {
  ctx.fillStyle = "rgb(255 255 255 / 30%)";
  ctx.fillRect(0, 0, canvas.width, canvas.height);
  ball.draw();
  ball.x += ball.vx;
  ball.y += ball.vy;
  ball.vy *= 0.99;
  ball.vy += 0.25;

  if (
    ball.y + ball.vy > canvas.height - ball.radius ||
    ball.y + ball.vy < ball.radius
  ) {
    ball.vy = -ball.vy;
  }
  if (
    ball.x + ball.vx > canvas.width - ball.radius ||
    ball.x + ball.vx < ball.radius
  ) {
    ball.vx = -ball.vx;
  }

  raf = window.requestAnimationFrame(draw);
}

canvas.addEventListener("mouseover", (e) => {
  raf = window.requestAnimationFrame(draw);
});

canvas.addEventListener("mouseout", (e) => {
  window.cancelAnimationFrame(raf);
});

ball.draw();
```

#### نتیجه

{{EmbedLiveSample("Third_demo", "610", "340")}}

## افزودن کنترل ماوس

برای به دست آوردن کنترل بر روی توپ، می‌توانیم آن را با استفاده از رویداد [`mousemove`](/en-US/docs/Web/API/Element/mousemove_event) دنبال ماوس حرکت دهیم، برای مثال. رویداد [`click`](/en-US/docs/Web/API/Element/click_event) توپ را آزاد می‌کند و اجازه می‌دهد دوباره بپرد.

### نمایش چهارم

#### HTML

```html
<canvas id="canvas" width="600" height="300"></canvas>
```

```css hidden
#canvas {
  border: 1px solid black;
}
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
let raf;
let running = false;

const ball = {
  x: 100,
  y: 100,
  vx: 5,
  vy: 1,
  radius: 25,
  color: "blue",
  draw() {
    ctx.beginPath();
    ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2, true);
    ctx.closePath();
    ctx.fillStyle = this.color;
    ctx.fill();
  },
};

function clear() {
  ctx.fillStyle = "rgb(255 255 255 / 30%)";
  ctx.fillRect(0, 0, canvas.width, canvas.height);
}

function draw() {
  clear();
  ball.draw();
  ball.x += ball.vx;
  ball.y += ball.vy;

  if (
    ball.y + ball.vy > canvas.height - ball.radius ||
    ball.y + ball.vy < ball.radius
  ) {
    ball.vy = -ball.vy;
  }
  if (
    ball.x + ball.vx > canvas.width - ball.radius ||
    ball.x + ball.vx < ball.radius
  ) {
    ball.vx = -ball.vx;
  }

  raf = window.requestAnimationFrame(draw);
}

canvas.addEventListener("mousemove", (e) => {
  if (!running) {
    clear();
    ball.x = e.clientX;
    ball.y = e.clientY;
    ball.draw();
  }
});

canvas.addEventListener("click", (e) => {
  if (!running) {
    raf = window.requestAnimationFrame(draw);
    running = true;
  }
});

canvas.addEventListener("mouseout", (e) => {
  window.cancelAnimationFrame(raf);
  running = false;
});

ball.draw();
```

#### نتیجه

توپ را با ماوس خود حرکت دهید و با یک کلیک آن را آزاد کنید.

{{EmbedLiveSample("Fourth_demo", "610", "340")}}

## بریکاوت

این فصل کوتاه فقط برخی تکنیک‌ها برای ایجاد انیمیشن‌های پیشرفته‌تر را توضیح می‌دهد. تکنیک‌های بسیار بیشتری نیز وجود دارد! چه‌طور است یک پارو، چند آجر اضافه کنید و این نمایش را به یک بازی [بریکاوت](https://en.wikipedia.org/wiki/Breakout_%28video_game%29) تبدیل کنید؟ برای مقالات بیشتر مرتبط با بازی، به بخش [توسعه بازی](/en-US/docs/Games) ما مراجعه کنید.

## همچنین ببینید

- {{domxref("window.requestAnimationFrame()")}}

{{PreviousNext("Web/API/Canvas_API/Tutorial/Basic_animations", "Web/API/Canvas_API/Tutorial/Pixel_manipulation_with_canvas")}}