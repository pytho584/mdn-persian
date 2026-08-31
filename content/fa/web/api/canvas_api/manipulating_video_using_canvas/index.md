---
title: "Manipulating video using canvas"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Manipulating_video_using_canvas"
translated_by: "n8n + AI"
---

---
title: Manipulating video using canvas
slug: Web/API/Canvas_API/Manipulating_video_using_canvas
page-type: guide
---

{{DefaultAPISidebar("Canvas API")}}

با ترکیب قابلیت‌های عنصر [`video`](/en-US/docs/Web/HTML/Reference/Elements/video) با یک [`canvas`](/en-US/docs/Web/HTML/Reference/Elements/canvas)، می‌توانید داده‌های ویدیویی را در زمان واقعی دستکاری کرده و جلوه‌های بصری گوناگونی بر ویدیوی در حال پخش اعمال کنید. این آموزش نحوه اجرای کروماکی (که با نام «جلوه صفحه سبز» نیز شناخته می‌شود) را با استفاده از کد جاوااسکریپت نشان می‌دهد.

{{EmbedGHLiveSample('dom-examples/canvas/chroma-keying/index.html', 700, 400) }}

## محتوای سند

سند HTML که برای نمایش این محتوا استفاده شده است در زیر نشان داده شده است.

```html
<!doctype html>
<html lang="en-US">
  <head>
    <meta charset="UTF-8" />
    <title>Video test page</title>
    <style>
      body {
        background: black;
        color: #cccccc;
      }
      #c2 {
        background-image: url("media/foo.png");
        background-repeat: no-repeat;
      }
      div {
        float: left;
        border: 1px solid #444444;
        padding: 10px;
        margin: 10px;
        background: #3b3b3b;
      }
    </style>
  </head>

  <body>
    <div>
      <video
        id="video"
        src="media/video.mp4"
        controls
        crossorigin="anonymous"></video>
    </div>
    <div>
      <canvas id="c1" width="160" height="96"></canvas>
      <canvas id="c2" width="160" height="96"></canvas>
    </div>
    <script src="processor.js"></script>
  </body>
</html>
```

نکات کلیدی که از این بخش باید در نظر بگیرید عبارتند از:

1. این سند دو عنصر [`canvas`](/en-US/docs/Web/HTML/Reference/Elements/canvas) با شناسه‌های `c1` و `c2` ایجاد می‌کند. از بوم `c1` برای نمایش فریم فعلی ویدیوی اصلی استفاده می‌شود، در حالی که `c2` برای نمایش ویدیو پس از اعمال افکت کروماکی به کار می‌رود؛ `c2` از قبل با تصویر ثابتی بارگذاری شده است که برای جایگزینی پس‌زمینه سبز در ویدیو استفاده خواهد شد.
2. کد جاوااسکریپت از اسکریپتی به نام `processor.js` وارد می‌شود.

## کد جاوااسکریپت

کد جاوااسکریپت در `processor.js` از سه روش تشکیل شده است.

### مقداردهی اولیه پخش‌کننده کروماکی

متد `doLoad()` زمانی فراخوانی می‌شود که سند HTML در ابتدا بارگذاری می‌شود. وظیفه این متد آماده‌سازی متغیرهای مورد نیاز برای پردازش کروماکی و تنظیم یک شنونده رویداد است تا بتوانیم زمانی را که کاربر شروع به پخش ویدیو می‌کند تشخیص دهیم.

```js
const processor = {};

processor.doLoad = function doLoad() {
  const video = document.getElementById("video");
  this.video = video;

  this.c1 = document.getElementById("c1");
  this.ctx1 = this.c1.getContext("2d");

  this.c2 = document.getElementById("c2");
  this.ctx2 = this.c2.getContext("2d");

  video.addEventListener("play", () => {
    this.width = video.videoWidth / 2;
    this.height = video.videoHeight / 2;
    this.timerCallback();
  });
};
```

این کد ارجاعاتی به عناصر مورد نظر در سند HTML می‌گیرد، یعنی عنصر `video` و دو عنصر `canvas`. همچنین ارجاع به زمینه‌های گرافیکی هر یک از دو بوم را دریافت می‌کند. این‌ها زمانی که واقعاً افکت کروماکی را اجرا می‌کنیم استفاده خواهند شد.

سپس `addEventListener()` فراخوانی می‌شود تا عنصر `video` را زیر نظر بگیرد و زمانی که کاربر دکمه پخش را روی ویدیو فشار می‌دهد، اعلان دریافت کنیم. در پاسخ به شروع پخش توسط کاربر، این کد عرض و ارتفاع ویدیو را دریافت و هر یک را نصف می‌کند (هنگام اجرای افکت کروماکی اندازه ویدیو را نصف خواهیم کرد)، سپس متد `timerCallback()` را برای شروع تماشای ویدیو و محاسبه افکت بصری فراخوانی می‌کند.

### فراخوانی زمان‌سنج (Timer Callback)

فراخوانی زمان‌سنج ابتدا وقتی ویدیو شروع به پخش می‌کند (هنگام رخداد «play») فراخوانی می‌شود و سپس مسئولیت تنظیم خود را برای فراخوانی دوره‌ای به عهده می‌گیرد تا افکت کروماکی برای هر فریم اجرا شود.

```js
processor.timerCallback = function timerCallback() {
  if (this.video.paused || this.video.ended) {
    return;
  }
  this.computeFrame();
  setTimeout(() => {
    this.timerCallback();
  }, 0);
};
```

اولین کاری که این فراخوانی انجام می‌دهد بررسی این است که آیا ویدیو اصلاً در حال پخش است یا نه؛ اگر در حال پخش نباشد، فراخوانی بلافاصله بدون انجام هیچ کاری بازمی‌گردد.

سپس متد `computeFrame()` را فراخوانی می‌کند که افکت کروماکی را روی فریم فعلی ویدیو اعمال می‌کند.

آخرین کاری که فراخوانی انجام می‌دهد، فراخوانی `setTimeout()` برای زمان‌بندی فراخوانی دوباره خود در سریع‌ترین زمان ممکن است. در دنیای واقعی، احتمالاً این کار را بر اساس آگاهی از نرخ فریم ویدیو زمان‌بندی می‌کنید.

### دستکاری داده‌های فریم ویدیو

متد `computeFrame()` که در زیر نشان داده شده است، مسئول دریافت واقعی یک فریم از داده‌ها و اعمال افکت کروماکی است.

```js
processor.computeFrame = function () {
  this.ctx1.drawImage(this.video, 0, 0, this.width, this.height);
  const frame = this.ctx1.getImageData(0, 0, this.width, this.height);
  const data = frame.data;

  for (let i = 0; i < data.length; i += 4) {
    const red = data[i + 0];
    const green = data[i + 1];
    const blue = data[i + 2];
    if (green > 100 && red > 100 && blue < 43) {
      data[i + 3] = 0;
    }
  }
  this.ctx2.putImageData(frame, 0, 0);
};
```

وقتی این روال فراخوانی می‌شود، عنصر ویدیو آخرین فریم از داده‌های ویدیویی را نمایش می‌دهد که به این شکل است:

![یک فریم از عنصر ویدیو. شخصی با تیشرت مشکی وجود دارد. رنگ پس‌زمینه زرد است.](video.png)

آن فریم از ویدیو به زمینه گرافیکی `ctx1` بوم اول کپی می‌شود، و ارتفاع و عرض همان مقادیری که قبلاً برای ترسیم فریم در نصف اندازه ذخیره کرده‌ایم تعیین می‌شود. توجه داشته باشید که می‌توانید عنصر ویدیو را به متد `drawImage()` زمینه بدهید تا فریم جاری ویدیو در آن زمینه ترسیم شود. نتیجه به این شکل است:

![یک فریم از عنصر ویدیو. شخصی با تیشرت مشکی وجود دارد. رنگ پس‌زمینه زرد است. این نسخه کوچک‌تر تصویر بالاست.](sourcectx.png)

فراخوانی متد `getImageData()` روی زمینه اول، یک کپی از داده‌های گرافیکی خام فریم جاری ویدیو دریافت می‌کند. این کار داده‌های خام تصویری ۳۲-بیتی پیکسلی فراهم می‌کند که می‌توانیم سپس آن‌ها را دستکاری کنیم. سپس تعداد پیکسل‌های تصویر را با تقسیم اندازه کل داده‌های تصویر فریم بر چهار محاسبه می‌کنیم.

حلقه `for` پیکسل‌های فریم را اسکن می‌کند و مقادیر قرمز، سبز و آبی را برای هر پیکسل استخراج می‌کند و آن‌ها را با اعداد از پیش تعیین‌شده‌ای مقایسه می‌کند که برای تشخیص صفحه سبزی که با تصویر پس‌زمینه ثابت وارد شده از `foo.png` جایگزین می‌شود، استفاده می‌شوند.

هر پیکسل در داده‌های تصویر فریم که در محدوده پارامترهایی که بخشی از صفحه سبز محسوب می‌شوند قرار گیرد، مقدار آلفای آن با صفر جایگزین می‌شود و این نشان می‌دهد که پیکسل کاملاً شفاف است. در نتیجه، تصویر نهایی کل ناحیه صفحه سبز را ۱۰۰٪ شفاف دارد، به طوری که وقتی با استفاده از `ctx2.putImageData` در زمینه مقصد ترسیم می‌شود، نتیجه یک روی‌هم‌گذاری روی پس‌زمینه ثابت است.

تصویر حاصل به این شکل است:

![یک فریم از عنصر ویدیو همان شخص با تیشرت مشکی را نشان می‌دهد که در تصاویر بالا دیده می‌شود. پس‌زمینه متفاوت است: لوگوی فایرفاکس است.](output.png)

این کار به‌طور مکرر در حین پخش ویدیو انجام می‌شود، بنابراین فریم به فریم با افکت کروماکی پردازش و نمایش داده می‌شود.

[مشاهده منبع کامل این مثال](https://github.com/mdn/dom-examples/tree/main/canvas/chroma-keying).

## همچنین ببینید

- [فناوری‌های رسانه‌ای وب](/en-US/docs/Web/Media)
- [راهنمای انواع و قالب‌های رسانه در وب](/en-US/docs/Web/Media/Guides/Formats)
- [منطقه یادگیری: ویدیو و صوت HTML](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_video_and_audio)