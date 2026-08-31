---
title: "Basic usage of canvas"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Basic_usage"
translated_by: "n8n + AI"
---

---
title: Basic usage of canvas
slug: Web/API/Canvas_API/Tutorial/Basic_usage
page-type: guide
---

{{DefaultAPISidebar("Canvas API")}} {{PreviousNext("Web/API/Canvas_API/Tutorial", "Web/API/Canvas_API/Tutorial/Drawing_shapes")}}

بیایید این آموزش را با نگاه کردن به عنصر {{HTMLElement("canvas")}} {{Glossary("HTML")}} شروع کنیم. در پایان این صفحه، خواهید دانست که چگونه یک بافت 2D برای canvas راه‌اندازی کنید و اولین مثال را در مرورگر خود رسم کنید.

## عنصر `<canvas>`

```html
<canvas id="canvas" width="150" height="150"></canvas>
```

در نگاه اول، {{HTMLElement("canvas")}} شبیه عنصر {{HTMLElement("img")}} به نظر می‌رسد، با تنها تفاوت آشکار این که ویژگی‌های `src` و `alt` را ندارد. در واقع، عنصر `<canvas>` فقط دو ویژگی دارد: [`width`](/en-US/docs/Web/HTML/Reference/Elements/canvas#width) و [`height`](/en-US/docs/Web/HTML/Reference/Elements/canvas#height). هر دوی این ویژگی‌ها اختیاری هستند و می‌توانند با استفاده از [ویژگی‌های](/en-US/docs/Web/API/HTMLCanvasElement) {{Glossary("DOM")}} تنظیم شوند. وقتی هیچ ویژگی `width` و `height` مشخص نشود، canvas در ابتدا **۳۰۰ پیکسل** عرض و **۱۵۰ پیکسل** ارتفاع خواهد داشت. اندازه عنصر را می‌توان با {{Glossary("CSS")}} به دلخواه تغییر داد، اما در هنگام رندر، تصویر به‌گونه‌ای مقیاس می‌شود که با اندازه چیدمان مطابقت یابد: اگر اندازه‌دهی CSS نسبت تصویر اولیه canvas را رعایت نکند، تصویر تحریف‌شده به نظر خواهد رسید.

> [!NOTE]
> اگر رندرهای شما تحریف‌شده به نظر می‌رسند، سعی کنید ویژگی‌های `width` و `height` را به‌صراحت در ویژگی‌های `<canvas>` مشخص کنید و از CSS استفاده نکنید.

ویژگی [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) مختص عنصر `<canvas>` نیست، بلکه یکی از [ویژگی‌های سراسری HTML](/en-US/docs/Web/HTML/Reference/Global_attributes) است که می‌تواند روی هر عنصر HTML اعمال شود (مانند [`class`](/en-US/docs/Web/HTML/Reference/Global_attributes/class) برای مثال). همیشه ایده خوبی است که یک `id` ارائه دهید، زیرا این کار شناسایی آن را در اسکریپت بسیار آسان‌تر می‌کند.

عنصر `<canvas>` را می‌توان دقیقاً مانند هر تصویر معمولی استایل داد ({{cssxref("margin")}}، {{cssxref("border")}}، {{cssxref("background")}} و ...). با این حال، این قوانین روی رسم واقعی در canvas تأثیر نمی‌گذارند. نحوه انجام این کار را در یک [فصل اختصاصی](/en-US/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors) از این آموزش خواهیم دید. وقتی هیچ قانون استایلی روی canvas اعمال نشود، در ابتدا کاملاً شفاف خواهد بود.

### محتوای قابل دسترس

عنصر `<canvas>`، مانند عناصر {{HTMLElement("img")}}، {{HTMLElement("video")}}، {{HTMLElement("audio")}} و {{HTMLElement("picture")}}، باید با ارائه متن جایگزین که وقتی رسانه بارگذاری نمی‌شود یا کاربر قادر به تجربه آن‌طور که انتظار می‌رود نیست، نمایش داده شود، قابل دسترس شود. همیشه باید محتوای جایگزین، زیرنویس و متن جایگزین متناسب با نوع رسانه ارائه دهید.

ارائه محتوای جایگزین بسیار ساده است: فقط محتوای جایگزین را داخل عنصر `<canvas>` قرار دهید تا توسط صفحه‌خوان‌ها، خزنده‌ها و سایر ربات‌های خودکار قابل دسترسی باشد. مرورگرها به‌طور پیش‌فرض محتوای داخل ظرف را نادیده می‌گیرند و canvas را به‌طور عادی رندر می‌کنند، مگر اینکه `<canvas>` پشتیبانی نشود.

برای مثال، می‌توانیم یک توصیف متنی از محتوای canvas ارائه دهیم یا یک تصویر ثابت از محتوای رندر شده پویا ارائه دهیم. این می‌تواند چیزی شبیه این باشد:

```html
<canvas id="stockGraph" width="150" height="150">
  قیمت فعلی سهام: 3.15 دلار + 0.15 دلار
</canvas>

<canvas id="clock" width="150" height="150">
  <img src="images/clock.png" width="150" height="150" alt="یک ساعت" />
</canvas>
```

گفتن به کاربر که از مرورگر دیگری که از canvas پشتیبانی می‌کند استفاده کند، به کاربرانی که به هیچ وجه نمی‌توانند canvas را بخوانند کمکی نمی‌کند. ارائه متن جایگزین مفید یا زیر DOM به دسترس‌پذیری عنصری که در غیر این صورت غیرقابل دسترس است، می‌افزاید.

### تگ پایانی `</canvas>` ضروری

در نتیجه نحوه ارائه جایگزین، برخلاف عنصر {{HTMLElement("img")}}، عنصر {{HTMLElement("canvas")}} **نیازمند** تگ پایانی (`</canvas>`) است. اگر این تگ وجود نداشته باشد، بقیه سند به‌عنوان محتوای جایگزین در نظر گرفته می‌شود و نمایش داده نمی‌شود.

اگر محتوای جایگزین لازم نیست، یک `<canvas id="foo" role="presentation" …></canvas>` ساده با همه مرورگرهایی که از canvas پشتیبانی می‌کنند کاملاً سازگار است. این کار فقط زمانی باید انجام شود که canvas صرفاً جنبه نمایشی داشته باشد.

## بافت رندر

عنصر {{HTMLElement("canvas")}} یک سطح رسم با اندازه ثابت ایجاد می‌کند که یک یا چند **بافت رندر** را در معرض دید قرار می‌دهد؛ این بافت‌ها برای ایجاد و دستکاری محتوای نمایش داده شده استفاده می‌شوند. در این آموزش، ما روی بافت رندر 2D تمرکز می‌کنیم. سایر بافت‌ها ممکن است انواع مختلفی از رندر را ارائه دهند؛ برای مثال، [WebGL](/en-US/docs/Web/API/WebGL_API) از یک بافت 3D مبتنی بر [OpenGL ES](https://www.khronos.org/opengles/) استفاده می‌کند.

canvas در ابتدا خالی است. برای نمایش چیزی، یک اسکریپت ابتدا باید به بافت رندر دسترسی پیدا کند و روی آن رسم کند. عنصر {{HTMLElement("canvas")}} دارای متدی به نام {{domxref("HTMLCanvasElement.getContext", "getContext()")}} است که برای دریافت بافت رندر و توابع رسم آن استفاده می‌شود. `getContext()` یک پارامتر دریافت می‌کند: نوع بافت. برای گرافیک 2D، مانند مواردی که در این آموزش پوشش داده می‌شود، شما `"2d"` را مشخص می‌کنید تا یک {{domxref("CanvasRenderingContext2D")}} دریافت کنید.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
```

خط اول در اسکریپت، گره DOM را که عنصر {{HTMLElement("canvas")}} را نشان می‌دهد، با فراخوانی متد {{domxref("document.getElementById()")}} بازیابی می‌کند. هنگامی که گره عنصر را دارید، می‌توانید با استفاده از متد `getContext()` آن به بافت رسم دسترسی پیدا کنید.

## بررسی پشتیبانی

محتوای جایگزین در مرورگرهایی نمایش داده می‌شود که از {{HTMLElement("canvas")}} پشتیبانی نمی‌کنند. اسکریپت‌ها همچنین می‌توانند به‌صورت برنامه‌نویسی با آزمایش وجود متد `getContext()` پشتیبانی را بررسی کنند. قطعه کد ما از بالا به چیزی شبیه این تبدیل می‌شود:

```js
const canvas = document.getElementById("canvas");

if (canvas.getContext) {
  const ctx = canvas.getContext("2d");
  // کد رسم در اینجا
} else {
  // کد عدم پشتیبانی از canvas در اینجا
}
```

## یک قالب اسکلتی

در اینجا یک قالب مینیمالیستی وجود دارد که از آن به‌عنوان نقطه شروع برای مثال‌های بعدی استفاده خواهیم کرد.

> [!NOTE]
> جاسازی اسکریپت در HTML کار خوبی نیست. ما این کار را در اینجا انجام می‌دهیم تا مثال مختصر بماند.

```html
<!doctype html>
<html lang="en-US">
  <head>
    <meta charset="utf-8" />
    <title>Canvas tutorial</title>
    <style>
      canvas {
        border: 1px solid black;
      }
    </style>
  </head>
  <body>
    <canvas id="canvas" width="150" height="150"></canvas>
    <script>
      function draw() {
        const canvas = document.getElementById("canvas");
        const ctx = canvas.getContext("2d");
      }
      draw();
    </script>
  </body>
</html>
```

اسکریپت شامل یک تابع به نام `draw()` است که پس از بارگذاری کامل صفحه اجرا می‌شود؛ این کار با قرار دادن اسکریپت پس از محتوای اصلی بدنه انجام می‌شود. این تابع، یا تابعی مشابه آن، می‌تواند با استفاده از {{domxref("Window.setTimeout", "setTimeout()")}}، {{domxref("Window.setInterval", "setInterval()")}} یا کنترل‌کننده رویداد {{domxref("Window/load_event", "load")}} نیز فراخوانی شود، به شرطی که صفحه ابتدا بارگذاری شده باشد.

در این مرحله، این سند باید خالی رندر شود.

## یک مثال ساده

برای شروع، بیایید به مثالی نگاه کنیم که دو مستطیل متقاطع را رسم می‌کند که یکی از آن‌ها شفافیت آلفا دارد. نحوه عملکرد این موضوع را در مثال‌های بعدی با جزئیات بیشتری بررسی خواهیم کرد. محتوای عنصر `script` خود را به این صورت به‌روزرسانی کنید:

```html hidden
<canvas id="canvas" width="150" height="150"></canvas>
```

```css hidden
canvas {
  border: 1px solid black;
}
```

```js
function draw() {
  const canvas = document.getElementById("canvas");
  const ctx = canvas.getContext("2d");

  ctx.fillStyle = "rgb(200 0 0)";
  ctx.fillRect(10, 10, 50, 50);

  ctx.fillStyle = "rgb(0 0 200 / 50%)";
  ctx.fillRect(30, 30, 50, 50);
}
draw();
```

این مثال به این شکل است:

{{EmbedLiveSample("A_simple_example", "", "160")}}

{{PreviousNext("Web/API/Canvas_API/Tutorial", "Web/API/Canvas_API/Tutorial/Drawing_shapes")}}