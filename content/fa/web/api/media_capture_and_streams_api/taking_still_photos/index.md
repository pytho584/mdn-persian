---
title: Taking still photos with getUserMedia()
slug: Web/API/Media_Capture_and_Streams_API/Taking_still_photos
page-type: guide
---

{{DefaultAPISidebar("Media Capture and Streams")}}

این مقاله نحوه استفاده از [`navigator.mediaDevices.getUserMedia()`](/en-US/docs/Web/API/MediaDevices/getUserMedia) برای دسترسی به دوربین رایانه یا تلفن همراه با پشتیبانی از `getUserMedia()` و گرفتن عکس با آن را نشان می‌دهد.

![برنامهٔ ضبط تصویر مبتنی بر getUserMedia – در سمت چپ یک جریان ویدیویی از دوربین وب و یک دکمهٔ عکس‌برداری دیده می‌شود، در سمت راست خروجی تصویر ثابت حاصل از عکس‌برداری قرار دارد](web-rtc-demo.png)

اگر مایل هستید، می‌توانید مستقیماً به بخش [نمایش زنده](#demo) بروید.

## نشانه‌گذاری HTML

رابط HTML ما دو بخش اصلی عملیاتی دارد: پنل جریان و ضبط و پنل نمایش. هر یک از این‌ها به صورت کنار هم در یک {{HTMLElement("div")}} مجزا قرار گرفته‌اند تا استایل‌دهی و کنترل آسان‌تر شود. یک عنصر {{HTMLElement("button")}} (`permissions-button`) وجود دارد که می‌توانیم بعداً در جاوااسکریپت از آن استفاده کنیم تا کاربر بتواند با استفاده از `getUserMedia()` مجوز دوربین را برای هر دستگاه مجاز یا مسدود کند.

جعبهٔ سمت چپ دو جزء دارد: یک عنصر {{HTMLElement("video")}} که جریان را از `navigator.mediaDevices.getUserMedia()` دریافت می‌کند و یک {{HTMLElement("button")}} برای شروع ضبط ویدیو. این ساده است و وقتی به کد جاوااسکریپت برسیم، نحوهٔ اتصال آن‌ها را خواهیم دید.

```css hidden live-sample___photo-capture live-sample___photo-capture-with-filters
body {
  font:
    1rem "Lucida Grande",
    "Arial",
    sans-serif;
  padding: 0.8rem;
}

button {
  display: block;
  margin-block: 1rem;
}

#start-button {
  position: relative;
  margin: auto;
  bottom: 32px;
  background-color: rgb(0 150 0 / 50%);
  border: 1px solid rgb(255 255 255 / 70%);
  box-shadow: 0px 0px 1px 2px rgb(0 0 0 / 20%);
  font-size: 14px;
  color: white;
}

#video,
#photo {
  border: 1px solid black;
  box-shadow: 2px 2px 3px black;
  width: 100%;
  height: auto;
}

#canvas {
  display: none;
}

.camera,
.output {
  display: inline-block;
  width: 49%;
  height: auto;
}

.output {
  vertical-align: top;
}

code {
  background-color: lightgrey;
}
```

```html hidden live-sample___photo-capture live-sample___photo-capture-with-filters
<h1>Still photo capture demo</h1>
<p>
  This example demonstrates how to use
  <code>navigator.mediaDevices.getUserMedia()</code> to set up a media stream
  using your webcam or other video device, fetch an image from that stream, and
  create a PNG using that image.
</p>
<button id="permissions-button">Allow camera</button>
```

```html hidden live-sample___photo-capture-with-filters
<p>
  &#9432; This example uses the same code as before, but this time, we're adding
  a filter effect to the <code>&lt;video&gt;</code> element using a CSS
  <code>filter: grayscale(100%)</code> declaration. We can then check if the
  video element has any CSS <code>filter</code> applied, and use the same filter
  when drawing to the canvas:
</p>
```

```html live-sample___photo-capture live-sample___photo-capture-with-filters
<div class="camera">
  <video id="video">Video stream not available.</video>
  <button id="start-button">Capture photo</button>
</div>
```

در ادامه، یک عنصر {{HTMLElement("canvas")}} داریم که فریم‌های ضبط‌شده در آن ذخیره می‌شوند، احتمالاً به نحوی دستکاری می‌شوند و سپس به یک فایل تصویری خروجی تبدیل می‌شوند. این بوم با استایل‌دهی با {{cssxref("display", "display: none")}} پنهان نگه داشته می‌شود تا صفحه شلوغ نشود – کاربر نیازی به دیدن این مرحلهٔ میانی ندارد.

همچنین یک عنصر {{HTMLElement("img")}} داریم که تصویر را در آن نمایش می‌دهیم – این نمایش نهایی است که به کاربر نشان داده می‌شود.

```html live-sample___photo-capture live-sample___photo-capture-with-filters
<canvas id="canvas"></canvas>
<div class="output">
  <img id="photo" src="" alt="The screen capture will appear in this box." />
</div>
```

## کد جاوااسکریپت

حالا بیایید نگاهی به کد جاوااسکریپت بیندازیم. آن را به چند بخش کوچک تقسیم می‌کنیم تا توضیح آن آسان‌تر شود.

### مقداردهی اولیه

با تعریف متغیرهای مختلفی که استفاده خواهیم کرد شروع می‌کنیم.

```js live-sample___photo-capture live-sample___photo-capture-with-filters
const width = 320; // We will scale the photo width to this
let height = 0; // This will be computed based on the input stream

let streaming = false;

const video = document.getElementById("video");
const canvas = document.getElementById("canvas");
const photo = document.getElementById("photo");
const startButton = document.getElementById("start-button");
const allowButton = document.getElementById("permissions-button");
```

این متغیرها عبارتند از:

- `width`
  - : صرف‌نظر از اندازهٔ ویدیوی ورودی، تصویر حاصل را به عرض ۳۲۰ پیکسل مقیاس می‌کنیم.
- `height`
  - : ارتفاع خروجی تصویر با توجه به `width` و {{glossary("aspect ratio", "نسبت تصویر")}} جریان محاسبه خواهد شد.
- `streaming`
  - : نشان می‌دهد که آیا در حال حاضر یک جریان ویدیویی فعال در حال اجرا است یا خیر.
- `video`
  - : ارجاعی به عنصر {{HTMLElement("video")}}.
- `canvas`
  - : ارجاعی به عنصر {{HTMLElement("canvas")}}.
- `photo`
  - : ارجاعی به عنصر {{HTMLElement("img")}}.
- `startButton`
  - : ارجاعی به عنصر {{HTMLElement("button")}} که برای شروع ضبط استفاده می‌شود.
- `allowButton`
  - : ارجاعی به عنصر {{HTMLElement("button")}} که برای کنترل دسترسی صفحه به دستگاه‌ها استفاده می‌شود.

#### دریافت جریان رسانه

وظیفهٔ بعدی دریافت جریان رسانه است: یک شنوندهٔ رویداد تعریف می‌کنیم که {{domxref("MediaDevices.getUserMedia()")}} را فراخوانی کرده و یک جریان ویدیویی (بدون صدا) را هنگامی که کاربر روی دکمهٔ «Allow camera» کلیک می‌کند درخواست می‌کند. این یک promise برمی‌گرداند که به آن توابع موفقیت و شکست را متصل می‌کنیم:

```js live-sample___photo-capture live-sample___photo-capture-with-filters
allowButton.addEventListener("click", () => {
  navigator.mediaDevices
    .getUserMedia({ video: true, audio: false })
    .then((stream) => {
      video.srcObject = stream;
      video.play();
    })
    .catch((err) => {
      console.error(`An error occurred: ${err}`);
    });
});
```

تابع موفقیت یک شیء `stream` را به عنوان ورودی دریافت می‌کند که به عنوان منبع عنصر {{HTMLElement("video")}} ما تنظیم می‌شود. پس از اتصال جریان به عنصر `<video>`، با فراخوانی [`HTMLMediaElement.play()`](/en-US/docs/Web/API/HTMLMediaElement/play_event) آن را شروع به پخش می‌کنیم.

تابع شکست در صورتی که باز کردن جریان موفقیت‌آمیز نباشد فراخوانی می‌شود. این اتفاق می‌افتد مثلاً اگر دوربین سازگاری متصل نباشد یا کاربر دسترسی را رد کرده باشد.

#### گوش دادن به شروع پخش ویدیو

پس از فراخوانی [`HTMLMediaElement.play()`](/en-US/docs/Web/API/HTMLMediaElement/play_event) روی {{HTMLElement("video")}}، یک دورهٔ زمانی (امیدواریم کوتاه) می‌گذرد تا جریان ویدیو شروع به جاری شدن کند. برای جلوگیری از توقف تا زمانی که این اتفاق بیفتد، یک شنوندهٔ رویداد به `video` برای رویداد {{domxref("HTMLMediaElement/canplay_event", "canplay")}} اضافه می‌کنیم که وقتی پخش ویدیو واقعاً شروع می‌شود، تحویل داده می‌شود. در آن نقطه، تمام ویژگی‌های موجود در شیء `video` بر اساس قالب جریان پیکربندی شده‌اند.

```js live-sample___photo-capture live-sample___photo-capture-with-filters
video.addEventListener("canplay", (ev) => {
  if (!streaming) {
    height = video.videoHeight / (video.videoWidth / width);

    video.setAttribute("width", width);
    video.setAttribute("height", height);
    canvas.setAttribute("width", width);
    canvas.setAttribute("height", height);
    streaming = true;
  }
});
```

این تابع فراخوانی کاری انجام نمی‌دهد مگر اینکه اولین بار باشد که فراخوانی می‌شود؛ این با بررسی مقدار متغیر `streaming` که در اولین اجرای این متد `false` است، آزمایش می‌شود.

اگر این اولین اجرا باشد، ارتفاع ویدیو را بر اساس تفاوت اندازهٔ واقعی ویدیو، `video.videoWidth` و عرضی که در آن رندر می‌کنیم، `width`، تنظیم می‌کنیم.

در نهایت، `width` و `height` هر دو ویدیو و بوم با فراخوانی {{domxref("Element.setAttribute()")}} روی هر یک از این دو ویژگی روی هر عنصر تنظیم می‌شوند و عرض‌ها و ارتفاع‌ها به طور مناسب تنظیم می‌شوند. در نهایت، متغیر `streaming` را به `true` تنظیم می‌کنیم تا از اجرای مجدد این کد راه‌اندازی به طور سهوی جلوگیری کنیم.

#### مدیریت کلیک روی دکمه

برای گرفتن یک عکس ثابت هر بار که کاربر روی `startButton` کلیک می‌کند، باید یک شنوندهٔ رویداد به دکمه اضافه کنیم که وقتی رویداد {{domxref("Element/click_event", "click")}} صادر می‌شود، فراخوانی شود:

```js live-sample___photo-capture live-sample___photo-capture-with-filters
startButton.addEventListener("click", (ev) => {
  takePicture();
  ev.preventDefault();
});
```

این متد ساده است: تابع `takePicture()` را که در بخش [گرفتن یک فریم از جریان](#گرفتن_یک_فریم_از_جریان) در زیر تعریف شده است فراخوانی می‌کند، سپس {{domxref("Event.preventDefault()")}} را روی رویداد دریافتی فراخوانی می‌کند تا از چندباره مدیریت کلیک جلوگیری شود.

### پاک کردن جعبهٔ عکس

پاک کردن جعبهٔ عکس شامل ایجاد یک تصویر و سپس تبدیل آن به قالبی قابل استفاده توسط عنصر {{HTMLElement("img")}} است که آخرین فریم ضبط‌شده را نمایش می‌دهد. این کد به صورت زیر است:

```js live-sample___photo-capture live-sample___photo-capture-with-filters
function clearPhoto() {
  const context = canvas.getContext("2d");
  context.fillStyle = "#aaaaaa";
  context.fillRect(0, 0, canvas.width, canvas.height);

  const data = canvas.toDataURL("image/png");
  photo.setAttribute("src", data);
}

clearPhoto();
```

با گرفتن یک ارجاع به عنصر {{HTMLElement("canvas")}} پنهان که برای رندر خارج از صفحه استفاده می‌کنیم شروع می‌کنیم. سپس `fillStyle` را به `#aaaaaa` (یک خاکستری نسبتاً روشن) تنظیم می‌کنیم و کل بوم را با آن رنگ با فراخوانی {{domxref("CanvasRenderingContext2D.fillRect()","fillRect()")}} پر می‌کنیم.

در پایان این تابع، بوم را به یک تصویر PNG تبدیل می‌کنیم و با فراخوانی {{domxref("Element.setAttribute", "photo.setAttribute()")}} باعث می‌شویم جعبهٔ عکس ثابت ضبط‌شده تصویر را نمایش دهد.

### گرفتن یک فریم از جریان

یک تابع نهایی برای تعریف باقی مانده است و این نقطهٔ اصلی کل تمرین است: تابع `takePicture()` که وظیفه آن گرفتن فریم ویدیوی در حال نمایش، تبدیل آن به یک فایل PNG و نمایش آن در جعبهٔ فریم ضبط‌شده است. کد به این صورت است:

```js live-sample___photo-capture
function takePicture() {
  const context = canvas.getContext("2d");
  if (width && height) {
    canvas.width = width;
    canvas.height = height;
    context.drawImage(video, 0, 0, width, height);

    const data = canvas.toDataURL("image/png");
    photo.setAttribute("src", data);
  } else {
    clearPhoto();
  }
}
```

همان‌طور که در هر زمانی که نیاز به کار با محتویات یک بوم داریم، با گرفتن [زمینهٔ ترسیم دو بعدی](/en-US/docs/Web/API/CanvasRenderingContext2D) برای بوم پنهان شروع می‌کنیم.

سپس، اگر عرض و ارتفاع هر دو غیر صفر باشند (به این معنی که حداقل احتمالاً داده‌های تصویر معتبری وجود دارد)، عرض و ارتفاع بوم را به گونه‌ای تنظیم می‌کنیم که با فریم ضبط‌شده مطابقت داشته باشد، سپس {{domxref("CanvasRenderingContext2D.drawImage()", "drawImage()")}} را فراخوانی می‌کنیم تا فریم جاری ویدیو را درون زمینه ترسیم کند و کل بوم را با تصویر فریم پر کند.

> [!NOTE]
> این از این واقعیت استفاده می‌کند که رابط {{domxref("HTMLVideoElement")}} برای هر API که یک `HTMLImageElement` را به عنوان پارامتر می‌پذیرد، مانند یک {{domxref("HTMLImageElement")}} به نظر می‌رسد، و فریم جاری ویدیو به عنوان محتوای تصویر ارائه می‌شود.

هنگامی که بوم حاوی تصویر گرفته شده است، آن را با فراخوانی {{domxref("HTMLCanvasElement.toDataURL()")}} روی آن به فرمت PNG تبدیل می‌کنیم؛ در نهایت، با فراخوانی {{domxref("Element.setAttribute", "photo.setAttribute()")}} باعث می‌شویم جعبهٔ عکس ثابت ضبط‌شده تصویر را نمایش دهد.

اگر تصویر معتبری در دسترس نباشد (یعنی `width` و `height` هر دو ۰ هستند)، محتویات جعبهٔ فریم ضبط‌شده را با فراخوانی `clearPhoto()` پاک می‌کنیم.

## نمایش زنده

روی «Allow camera» کلیک کنید تا یک دستگاه ورودی انتخاب کنید و به صفحه اجازه دسترسی به دوربین را بدهید. پس از شروع ویدیو، می‌توانید روی «Capture photo» کلیک کنید تا یک عکس ثابت از جریان به عنوان تصویری که روی بوم سمت راست کشیده شده است، بگیرید:

{{EmbedLiveSample('photo-capture', '', '500', , , , 'camera', 'allow-popups')}}

## سرگرمی با فیلترها

از آنجایی که ما با گرفتن فریم‌ها از یک عنصر {{HTMLElement("video")}} از دوربین وب کاربر تصاویر را ضبط می‌کنیم، می‌توانیم افکت‌های جذاب CSS {{cssxref("filter")}} را با فیلترها روی ویدیو اعمال کنیم. این فیلترها از پایه (سیاه و سفید کردن تصویر) تا پیچیده (تارشدگی گاوسی و چرخش رنگ) متغیر هستند.

```css live-sample___photo-capture-with-filters
#video {
  filter: grayscale(100%);
}
```

برای اعمال فیلترهای ویدیو روی عکس، تابع `takePicture()` نیاز به تغییرات زیر دارد.

```js live-sample___photo-capture-with-filters
function takePicture() {
  const context = canvas.getContext("2d");
  if (width && height) {
    canvas.width = width;
    canvas.height = height;

    // Get the computed CSS filter from the video element.
    // For example, it might return "grayscale(100%)"
    const videoStyles = window.getComputedStyle(video);
    const filterValue = videoStyles.getPropertyValue("filter");

    // Apply the filter to the canvas drawing context.
    // If there's no filter (i.e., it returns "none"), default to "none".
    context.filter = filterValue !== "none" ? filterValue : "none";

    context.drawImage(video, 0, 0, width, height);

    const dataUrl = canvas.toDataURL("image/png");
    photo.setAttribute("src", dataUrl);
  } else {
    clearPhoto();
  }
}
```

{{EmbedLiveSample('photo-capture-with-filters', , '600', , , , 'camera', 'allow-popups')}}

می‌توانید با این افکت با استفاده از مثلاً [ویرایشگر استایل](https://firefox-source-docs.mozilla.org/devtools-user/style_editor/index.html) ابزارهای توسعه‌دهندهٔ فایرفاکس بازی کنید؛ برای جزئیات نحوه انجام این کار به [ویرایش فیلترهای CSS](https://firefox-source-docs.mozilla.org/devtools-user/page_inspector/how-to/edit_css_filters/index.html) مراجعه کنید.

## استفاده از دستگاه‌های خاص

در صورت نیاز، می‌توانید مجموعهٔ منابع ویدیویی مجاز را به یک دستگاه یا مجموعه‌ای از دستگاه‌ها محدود کنید. برای این کار، {{domxref("MediaDevices.enumerateDevices")}} را فراخوانی کنید. هنگامی که promise با آرایه‌ای از اشیاء {{domxref("MediaDeviceInfo")}} که دستگاه‌های موجود را توصیف می‌کنند، برآورده شد، دستگاه‌هایی را که می‌خواهید مجاز کنید پیدا کرده و {{domxref("MediaTrackConstraints.deviceId", "deviceId")}} یا `deviceId`های مربوطه را در شیء {{domxref("MediaTrackConstraints")}} که به {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} ارسال می‌شود، مشخص کنید.

## همچنین ببینید

- {{domxref("MediaDevices.getUserMedia")}}
- {{domxref("CanvasRenderingContext2D.drawImage()")}}
- [استفاده از فریم‌های یک ویدیو](/en-US/docs/Web/API/Canvas_API/Tutorial/Using_images#using_frames_from_a_video) در آموزش Canvas