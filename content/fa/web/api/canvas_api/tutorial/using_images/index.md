---
title: "Using images"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Using_images"
translated_by: "n8n + AI"
---

---
title: Using images
slug: Web/API/Canvas_API/Tutorial/Using_images
page-type: guide
---

{{DefaultAPISidebar("Canvas API")}} {{PreviousNext("Web/API/Canvas_API/Tutorial/Drawing_text", "Web/API/Canvas_API/Tutorial/Transformations" )}}

تاکنون [شکل‌های](/en-US/docs/Web/API/Canvas_API/Tutorial/Drawing_shapes) خود را ایجاد کرده‌ایم و [سبک‌هایی](/en-US/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors) به آن‌ها اعمال کرده‌ایم. یکی از ویژگی‌های هیجان‌انگیزتر {{HTMLElement("canvas")}} قابلیت استفاده از تصاویر است. از این تصاویر می‌توان برای ترکیب‌بندی پویای عکس‌ها یا به عنوان پس‌زمینه نمودارها، برای اسپرایت‌ها در بازی‌ها و موارد دیگر استفاده کرد. تصاویر خارجی را می‌توان در هر قالبی که مرورگر پشتیبانی می‌کند، مانند PNG، GIF یا JPEG استفاده کرد. حتی می‌توانید از تصویری که توسط سایر عناصر canvas در همان صفحه تولید شده است به عنوان منبع استفاده کنید!

وارد کردن تصاویر به canvas اساساً یک فرآیند دو مرحله‌ای است:

1. یک مرجع به یک شی {{domxref("HTMLImageElement")}} یا به یک عنصر canvas دیگر به عنوان منبع به دست آورید. همچنین می‌توان با ارائه یک URL از تصاویر استفاده کرد.
2. تصویر را با استفاده از تابع `drawImage()` روی canvas رسم کنید.

بیایید نحوه انجام این کار را بررسی کنیم.

## به دست آوردن تصاویر برای رسم

API canvas قادر است از هر یک از انواع داده‌های زیر به عنوان منبع تصویر استفاده کند:

- {{domxref("HTMLImageElement")}}
  - : این‌ها تصاویری هستند که با استفاده از سازنده `Image()` ایجاد می‌شوند، همچنین هر عنصر {{HTMLElement("img")}}.
- {{domxref("SVGImageElement")}}
  - : این‌ها تصاویری هستند که با استفاده از عنصر {{SVGElement("image")}} جاسازی شده‌اند.
- {{domxref("HTMLVideoElement")}}
  - : استفاده از یک عنصر HTML {{HTMLElement("video")}} به عنوان منبع تصویر، فریم فعلی از ویدیو را گرفته و از آن به عنوان یک تصویر استفاده می‌کند.
- {{domxref("HTMLCanvasElement")}}
  - : می‌توانید از یک عنصر {{HTMLElement("canvas")}} دیگر به عنوان منبع تصویر خود استفاده کنید.
- {{domxref("ImageBitmap")}}
  - : یک تصویر بیت‌مپ، که احتمالاً برش خورده است. از این نوع برای استخراج بخشی از یک تصویر، یک _اسپرایت_، از یک تصویر بزرگتر استفاده می‌شود.
- {{domxref("OffscreenCanvas")}}
  - : یک نوع خاص از `<canvas>` که نمایش داده نمی‌شود و بدون نمایش آماده می‌شود. استفاده از چنین منبع تصویری امکان تغییر به آن را بدون اینکه ترکیب محتوا برای کاربر قابل مشاهده باشد، فراهم می‌کند.
- {{domxref("VideoFrame")}}
  - : یک تصویر که نمایانگر یک فریم واحد از یک ویدیو است.

چندین راه برای به دست آوردن تصاویر برای استفاده در canvas وجود دارد.

### استفاده از تصاویر از همان صفحه

می‌توانیم با استفاده از یکی از روش‌های زیر یک مرجع به تصاویر موجود در همان صفحه canvas به دست آوریم:

- مجموعه {{domxref("document.images")}}
- متد {{domxref("document.getElementsByTagName()")}}
- اگر ID تصویر خاصی را که می‌خواهید استفاده کنید می‌دانید، می‌توانید از {{domxref("document.getElementById()")}} برای بازیابی آن تصویر خاص استفاده کنید.

اگر می‌خواهید از تصاویر زیادی استفاده کنید یا [منابع را با بارگذاری تنبل (lazy-load)](/en-US/docs/Web/Performance/Guides/Lazy_loading) بارگذاری کنید، احتمالاً باید منتظر بمانید تا همه فایل‌ها قبل از رسم روی canvas در دسترس باشند.
مثال زیر با استفاده از یک تابع ناهمگام (async) و [`Promise.all`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/all) چندین تصویر را مدیریت می‌کند تا قبل از فراخوانی `drawImage()` منتظر بارگذاری همه تصاویر بماند:

```js
async function draw() {
  // Wait for all images to be loaded:
  await Promise.all(
    Array.from(document.images).map(
      (image) =>
        new Promise((resolve) => image.addEventListener("load", resolve)),
    ),
  );

  const ctx = document.getElementById("canvas").getContext("2d");
  // call drawImage() as usual
}
draw();
```

### ایجاد تصاویر از ابتدا

گزینه دیگر ایجاد اشیاء جدید {{domxref("HTMLImageElement")}} در اسکریپت ما است. برای این کار، یک سازنده `Image()` راحت داریم:

```js
const img = new Image(); // Create new img element
img.src = "myImage.png"; // Set source path
```

وقتی این اسکریپت اجرا می‌شود، تصویر شروع به بارگذاری می‌کند، اما اگر قبل از اتمام بارگذاری تصویر سعی کنید `drawImage()` را فراخوانی کنید، کاری انجام نمی‌دهد.
مرورگرهای قدیمی‌تر ممکن است حتی یک استثنا پرتاب کنند، بنابراین باید مطمئن شوید که از [رویداد load](/en-US/docs/Web/API/HTMLElement/load_event) استفاده می‌کنید تا تصویر را قبل از آماده شدن روی canvas رسم نکنید:

```js
const ctx = document.getElementById("canvas").getContext("2d");
const img = new Image();

img.addEventListener("load", () => {
  ctx.drawImage(img, 0, 0);
});

img.src = "myImage.png";
```

چه عناصر `<img>` در نشانه‌گذاری خود داشته باشید یا آن‌ها را به صورت برنامه‌نویسی در جاوااسکریپت ایجاد کنید، تصاویر خارجی ممکن است دارای محدودیت‌های [CORS](/en-US/docs/Web/HTTP/Guides/CORS) باشند. به طور پیش‌فرض، تصاویر واکشی شده از خارج [canvas را آلوده (taint) می‌کنند](/en-US/docs/Web/HTML/How_to/CORS_enabled_image#security_and_tainted_canvases) و از خواندن داده‌های بین‌دامنه‌ای توسط سایت شما جلوگیری می‌کنند. با استفاده از ویژگی [`crossorigin`](/en-US/docs/Web/HTML/Reference/Elements/img#crossorigin) یک عنصر {{HTMLElement("img")}} (که توسط ویژگی {{domxref("HTMLImageElement.crossOrigin")}} منعکس می‌شود)، می‌توانید برای بارگذاری یک تصویر از دامنه دیگر با استفاده از CORS درخواست مجوز دهید. اگر دامنه میزبان به دسترسی بین‌دامنه‌ای به تصویر اجازه دهد، می‌توان از تصویر در canvas شما بدون آلوده کردن آن استفاده کرد.

### جاسازی یک تصویر از طریق داده: URL

روش ممکن دیگر برای شامل کردن تصاویر از طریق [data: URL](/en-US/docs/Web/URI/Reference/Schemes/data) است. داده URLs به شما این امکان را می‌دهد که یک تصویر را به طور کامل به عنوان یک رشته کاراکتر کدگذاری شده Base64 مستقیماً در کد خود تعریف کنید.

```js
const img = new Image(); // Create new img element
img.src =
  "data:image/gif;base64,R0lGODlhCwALAIAAAAAA3pn/ZiH5BAEAAAEALAAAAAALAAsAAAIUhA+hkcuO4lmNVindo7qyrIXiGBYAOw==";
```

یک مزیت داده URLs این است که تصویر حاصل بلافاصله بدون رفت و برگشت اضافی به سرور در دسترس است. مزیت بالقوه دیگر این است که می‌توان تمام [CSS](/en-US/docs/Web/CSS)، [جاوااسکریپت](/en-US/docs/Web/JavaScript)، [HTML](/en-US/docs/Web/HTML) و تصاویر خود را در یک فایل کپسوله کرد و آن را به مکان‌های دیگر قابل حمل‌تر کرد.

برخی از معایب این روش این است که تصویر شما ذخیره نمی‌شود (cached) و برای تصاویر بزرگتر، URL کدگذاری شده می‌تواند بسیار طولانی شود.

### استفاده از سایر عناصر canvas

درست مانند تصاویر معمولی، با استفاده از متد {{domxref("document.getElementsByTagName()")}} یا {{domxref("document.getElementById()")}} به سایر عناصر canvas دسترسی پیدا می‌کنیم. قبل از استفاده از canvas منبع در canvas مقصد، مطمئن شوید که چیزی روی آن رسم کرده‌اید.

یکی از کاربردهای عملی‌تر این کار، استفاده از یک عنصر canvas دوم به عنوان نمای بندانگشتی از canvas بزرگتر دیگر است.

### استفاده از فریم‌های یک ویدیو

همچنین می‌توانید از فریم‌های یک ویدیو که توسط یک عنصر {{HTMLElement("video")}} ارائه می‌شود استفاده کنید (حتی اگر ویدیو قابل مشاهده نباشد). به عنوان مثال، اگر یک عنصر {{HTMLElement("video")}} با ID "myVideo" دارید، می‌توانید این کار را انجام دهید:

```js
const video = document.getElementById("myVideo");
video.currentTime = 10; // Seek to 10 seconds into the video
video.pause(); // Pause the video to freeze the frame
```

اکنون {{domxref("HTMLVideoElement")}} در ثانیه ۱۰ قرار دارد و می‌توانید فریم فعلی را روی canvas خود رسم کنید. برای اطمینان از اینکه فریم هنگام فراخوانی `drawImage()` در دسترس است، `drawImage()` را در داخل [`requestVideoFrameCallback()`](/en-US/docs/Web/API/HTMLVideoElement/requestVideoFrameCallback#drawing_video_frames_on_a_canvas) فراخوانی کنید.

## رسم تصاویر

هنگامی که یک مرجع به شیء تصویر منبع خود داریم، می‌توانیم از متد `drawImage()` برای رندر کردن آن روی canvas استفاده کنیم. همانطور که بعداً خواهیم دید، متد `drawImage()` بارگذاری شده (overloaded) است و چندین نوع دارد. در ساده‌ترین شکل آن به این صورت است:

- {{domxref("CanvasRenderingContext2D.drawImage", "drawImage(image, x, y)")}}
  - : تصویر مشخص شده توسط پارامتر `image` را در مختصات (`x`، `y`) رسم می‌کند.

> [!NOTE]
> تصاویر SVG باید یک عرض و ارتفاع در عنصر ریشه \<svg> مشخص کنند.

### مثال: یک نمودار خطی کوچک

در مثال زیر، از یک تصویر خارجی به عنوان پس‌زمینه یک نمودار خطی کوچک استفاده خواهیم کرد. استفاده از پس‌زمینه می‌تواند اسکریپت شما را به طور قابل توجهی کوچک‌تر کند زیرا از نیاز به کد برای تولید پس‌زمینه جلوگیری می‌کند. در این مثال، ما فقط از یک تصویر استفاده می‌کنیم، بنابراین از کنترل‌کننده رویداد `load` شیء تصویر برای اجرای دستورات رسم استفاده می‌کنم. متد `drawImage()` پس‌زمینه را در مختصات (0, 0) که گوشه بالا-چپ canvas است قرار می‌دهد.

```html hidden
<canvas id="canvas" width="180" height="150"></canvas>
```

```js
function draw() {
  const ctx = document.getElementById("canvas").getContext("2d");
  const img = new Image();
  img.onload = () => {
    ctx.drawImage(img, 0, 0);
    ctx.beginPath();
    ctx.moveTo(30, 96);
    ctx.lineTo(70, 66);
    ctx.lineTo(103, 76);
    ctx.lineTo(170, 15);
    ctx.stroke();
  };
  img.src = "backdrop.png";
}

draw();
```

نمودار حاصل به این شکل است:

{{EmbedLiveSample("Example_A_simple_line_graph", "", "160")}}

## مقیاس‌بندی

نوع دوم متد `drawImage()` دو پارامتر جدید اضافه می‌کند و به ما امکان می‌دهد تصاویر مقیاس‌بندی شده را روی canvas قرار دهیم.

- {{domxref("CanvasRenderingContext2D.drawImage", "drawImage(image, x, y, width, height)")}}
  - : این پارامترهای `width` و `height` را اضافه می‌کند که اندازه‌ای را مشخص می‌کنند که تصویر هنگام رسم روی canvas به آن مقیاس‌بندی شود.

### مثال: کاشی‌کاری یک تصویر

در این مثال، از یک تصویر به عنوان کاغذدیواری استفاده می‌کنیم و آن را چندین بار روی canvas تکرار می‌کنیم. این کار با حلقه زدن و قرار دادن تصاویر مقیاس‌بندی شده در موقعیت‌های مختلف انجام می‌شود. در کد زیر، اولین حلقه `for` روی ردیف‌ها تکرار می‌شود. دومین حلقه `for` روی ستون‌ها تکرار می‌شود. تصویر به یک سوم اندازه اصلی خود مقیاس‌بندی می‌شود که ۵۰x۳۸ پیکسل است.

> [!NOTE]
> تصاویر هنگام بزرگ‌نمایی می‌توانند تار شوند یا اگر بیش از حد کوچک شوند دانه‌دار شوند. اگر متنی در تصویر دارید که باید خوانا باقی بماند، احتمالاً بهتر است مقیاس‌بندی انجام نشود.

```html hidden
<canvas id="canvas" width="150" height="150"></canvas>
```

```js
function draw() {
  const ctx = document.getElementById("canvas").getContext("2d");
  const img = new Image();
  img.onload = () => {
    for (let i = 0; i < 4; i++) {
      for (let j = 0; j < 3; j++) {
        ctx.drawImage(img, j * 50, i * 38, 50, 38);
      }
    }
  };
  img.src = "https://mdn.github.io/shared-assets/images/examples/rhino.jpg";
}

draw();
```

canvas حاصل به این شکل است:

{{EmbedLiveSample("Example_Tiling_an_image", "", "160")}}

## برش

سومین و آخرین نوع متد `drawImage()` علاوه بر منبع تصویر، هشت پارامتر دارد. این به ما امکان می‌دهد بخشی از تصویر منبع را برش دهیم، سپس آن را مقیاس‌بندی کرده و روی canvas خود رسم کنیم.

- {{domxref("CanvasRenderingContext2D.drawImage", "drawImage(image, sx, sy, sWidth, sHeight, dx, dy, dWidth, dHeight)")}}
  - : با توجه به یک `image`، این تابع ناحیه‌ای از تصویر منبع را که توسط مستطیلی با گوشه بالا-چپ (`sx`، `sy`) و عرض و ارتفاع `sWidth` و `sHeight` مشخص شده است، می‌گیرد و آن را روی canvas رسم می‌کند، آن را در (`dx`، `dy`) روی canvas قرار می‌دهد و به اندازه مشخص شده توسط `dWidth` و `dHeight` مقیاس‌بندی می‌کند، در حالی که {{glossary("aspect ratio")}} آن حفظ می‌شود.

برای درک واقعی این موضوع، ممکن است نگاه کردن به این تصویر کمک کند:

![مختصات گوشه بالا-چپ تصویر منبع مستطیلی sx و sy با عرض و ارتفاع به ترتیب sWidth و sHeight است. تصویر منبع به canvas مقصد منتقل می‌شود که در آن مختصات گوشه بالا-چپ dx و dy با عرض و ارتفاع به ترتیب dWidth و dHeight است.](canvas_drawimage.jpg)

چهار پارامتر اول مکان و اندازه برش را روی تصویر منبع تعریف می‌کنند. چهار پارامتر آخر مستطیلی را تعریف می‌کنند که تصویر در آن روی canvas مقصد رسم می‌شود.

برش می‌تواند یک ابزار مفید زمانی باشد که می‌خواهید ترکیب‌بندی ایجاد کنید. می‌توانید همه عناصر را در یک فایل تصویری واحد داشته باشید و از این روش برای ترکیب یک نقاشی کامل استفاده کنید. به عنوان مثال، اگر می‌خواهید یک نمودار بسازید، می‌توانید یک تصویر PNG داشته باشید که شامل تمام متن‌های لازم در یک فایل است و بسته به داده‌های خود می‌توانید مقیاس نمودار خود را به راحتی تغییر دهید. مزیت دیگر این است که نیازی به بارگذاری هر تصویر به صورت جداگانه ندارید که می‌تواند عملکرد بارگذاری را بهبود بخشد.

### مثال: قاب‌بندی یک تصویر

در این مثال، از همان کرگدن مثال قبلی استفاده می‌کنیم، اما سر آن را برش می‌دهیم و آن را در یک قاب عکس ترکیب می‌کنیم. تصویر قاب عکس یک PNG 24 بیتی است که شامل یک سایه افتاده است. از آنجایی که تصاویر PNG 24 بیتی شامل یک کانال آلفای کامل 8 بیتی هستند، برخلاف تصاویر GIF و PNG 8 بیتی، می‌توان آن را بدون نگرانی از رنگ مات روی هر پس‌زمینه‌ای قرار داد.

```html
<canvas id="canvas" width="150" height="150"></canvas>
<div class="hidden">
  <img
    id="source"
    src="https://mdn.github.io/shared-assets/images/examples/rhino.jpg"
    width="300"
    height="227" />
  <img id="frame" src="canvas_picture_frame.png" width="132" height="150" />
</div>
```

```css hidden
.hidden {
  display: none;
}
```

```js
async function draw() {
  // Wait for all images to be loaded.
  await Promise.all(
    Array.from(document.images).map(
      (image) =>
        new Promise((resolve) => image.addEventListener("load", resolve)),
    ),
  );

  const canvas = document.getElementById("canvas");
  const ctx = canvas.getContext("2d");

  // Draw slice
  ctx.drawImage(
    document.getElementById("source"),
    33,
    71,
    104,
    124,
    21,
    20,
    87,
    104,
  );

  // Draw frame
  ctx.drawImage(document.getElementById("frame"), 0, 0);
}

draw();
```

این بار رویکرد متفاوتی برای بارگذاری تصاویر در پیش گرفتیم. به جای بارگذاری آن‌ها با ایجاد اشیاء جدید {{domxref("HTMLImageElement")}}، آن‌ها را به عنوان تگ‌های {{HTMLElement("img")}} در منبع HTML خود قرار دادیم و هنگام رسم روی canvas، تصاویر را از آن‌ها بازیابی کردیم. تصاویر با تنظیم ویژگی CSS {{cssxref("display")}} روی `none` برای آن تصاویر از صفحه پنهان شده‌اند.

{{EmbedLiveSample("example_framing_an_image", "", "160")}}

به هر {{HTMLElement("img")}} یک ویژگی ID اختصاص داده شده است، بنابراین ما یکی برای `source` و یکی برای `frame` داریم که انتخاب آن‌ها را با استفاده از {{domxref("document.getElementById()")}} آسان می‌کند.
ما از [Promise.all](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/all) برای انتظار برای بارگذاری همه تصاویر قبل از فراخوانی `drawImage()` استفاده می‌کنیم.
`drawImage()` کرگدن را از تصویر اول برش می‌دهد و آن را روی canvas مقیاس‌بندی می‌کند.
در نهایت، قاب عکس را با استفاده از یک فراخوانی دوم `drawImage()` رسم می‌کنیم.

## مثال گالری هنر

در مثال نهایی این فصل، یک گالری هنری کوچک می‌سازیم. گالری از یک جدول شامل چندین تصویر تشکیل شده است. وقتی صفحه بارگذاری می‌شود، یک عنصر {{HTMLElement("canvas")}} برای هر تصویر درج می‌شود و یک قاب دور آن رسم می‌شود.

در این مورد، هر تصویر دارای عرض و ارتفاع ثابتی است، همانطور که قاب دور آن‌ها رسم می‌شود. می‌توانید اسکریپت را بهبود دهید تا از عرض و ارتفاع تصویر برای تطبیق کامل قاب دور آن استفاده کند.

در کد زیر، ما از [Promise.all](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/all) برای انتظار برای بارگذاری همه تصاویر قبل از رسم هر تصویری روی canvas استفاده می‌کنیم.
ما از طریق ظرف {{domxref("document.images")}} حلقه می‌زنیم و برای هر یک عناصر canvas جدید اضافه می‌کنیم. نکته دیگری که باید به آن توجه کرد استفاده از متد {{domxref("Node.insertBefore")}} است. `insertBefore()` یک متد از گره والد (یک سلول جدول) عنصر (تصویر) است که می‌خواهیم گره جدید خود (عنصر canvas) را قبل از آن درج کنیم.

```html
<table>
  <tbody>
    <tr>
      <td><img src="gallery_1.jpg" /></td>
      <td><img src="gallery_2.jpg" /></td>
      <td><img src="gallery_3.jpg" /></td>
      <td><img src="gallery_4.jpg" /></td>
    </tr>
    <tr>
      <td><img src="gallery_5.jpg" /></td>
      <td><img src="gallery_6.jpg" /></td>
      <td><img src="gallery_7.jpg" /></td>
      <td><img src="gallery_8.jpg" /></td>
    </tr>
  </tbody>
</table>
<img id="frame" src="canvas_picture_frame.png" width="132" height="150" />
```

و در اینجا مقداری CSS برای زیبا کردن ظاهر:

```css
body {
  background: 0 -100px repeat-x url("bg_gallery.png") #4f191a;
  margin: 10px;
}

img {
  display: none;
}

table {
  margin: 0 auto;
}

td {
  padding: 15px;
}
```

جاوااسکریپت زیر همه چیز را به هم متصل می‌کند تا تصاویر قاب‌بندی شده ما رسم شوند:

```js
async function draw() {
  // Wait for all images to be loaded.
  await Promise.all(
    Array.from(document.images).map(
      (image) =>
        new Promise((resolve) => image.addEventListener("load", resolve)),
    ),
  );

  // Loop through all images.
  for (const image of document.images) {
    // Don't add a canvas for the frame image
    if (image.getAttribute("id") !== "frame") {
      // Create canvas element
      const canvas = document.createElement("canvas");
      canvas.setAttribute("width", 132);
      canvas.setAttribute("height", 150);

      // Insert before the image
      image.parentNode.insertBefore(canvas, image);

      ctx = canvas.getContext("2d");

      // Draw image to canvas
      ctx.drawImage(image, 15, 20);

      // Add frame
      ctx.drawImage(document.getElementById("frame"), 0, 0);
    }
  }
}

draw();
```

{{EmbedLiveSample("Art_gallery_example", 725, 400)}}

## کنترل رفتار مقیاس‌بندی تصویر

همانطور که قبلاً اشاره شد، مقیاس‌بندی تصاویر می‌تواند به دلیل فرآیند مقیاس‌بندی منجر به مصنوعات تار یا دانه‌دار شود. می‌توانید از ویژگی {{domxref("CanvasRenderingContext2D.imageSmoothingEnabled", "imageSmoothingEnabled")}} زمینه نقاشی برای کنترل استفاده از الگوریتم‌های هموارسازی تصویر هنگام مقیاس‌بندی تصاویر در زمینه خود استفاده کنید. به طور پیش‌فرض، این ویژگی `true` است، به این معنی که تصاویر هنگام مقیاس‌بندی هموار می‌شوند.

{{PreviousNext("Web/API/Canvas_API/Tutorial/Drawing_text", "Web/API/Canvas_API/Tutorial/Transformations")}}