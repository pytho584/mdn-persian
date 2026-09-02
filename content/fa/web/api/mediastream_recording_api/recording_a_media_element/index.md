---
title: "Recording a media element"
slug: Web/API/MediaStream_Recording_API/Recording_a_media_element
page-type: guide
---

{{DefaultAPISidebar("MediaStream Recording")}}

در حالی که مقاله «استفاده از API ضبط MediaStream» نحوه استفاده از رابط {{domxref("MediaRecorder")}} برای ضبط یک {{domxref("MediaStream")}} تولید شده توسط یک دستگاه سخت‌افزاری (که توسط {{domxref("MediaDevices.getUserMedia()","navigator.mediaDevices.getUserMedia()")}} برگردانده می‌شود) را نشان می‌دهد، شما می‌توانید از یک عنصر رسانه‌ای HTML (یعنی {{HTMLElement("audio")}} یا {{HTMLElement("video")}}) به عنوان منبع `MediaStream` برای ضبط استفاده کنید. در این مقاله، مثالی را بررسی می‌کنیم که دقیقاً همین کار را انجام می‌دهد.

## مثال ضبط یک عنصر رسانه‌ای

### HTML

```html hidden
<p>
  برای شروع ضبط ویدیو به مدت چند ثانیه، روی دکمه «Start Recording» کلیک کنید. می‌توانید با کلیک بر روی دکمه «Stop Recording» ضبط را متوقف کنید. دکمه «Download» داده‌های دریافت‌شده را دانلود می‌کند (اگرچه این داده‌ها به صورت خام و بدون بسته‌بندی هستند و چندان مفید نیستند).
</p>
<br />
```

بیایید با بخش‌های کلیدی HTML شروع کنیم. کد HTML کمی بیشتر از این است، اما بقیه آن صرفاً اطلاعاتی هستند و بخش اصلی عملیات برنامه نیستند.

```html
<div class="left">
  <div id="startButton" class="button">Start Recording</div>
  <h2>پیش‌نمایش</h2>
  <video id="preview" width="160" height="120" autoplay muted></video>
</div>
```

ما رابط اصلی خود را در دو ستون ارائه می‌دهیم. در سمت چپ، یک دکمه شروع و یک عنصر {{HTMLElement("video")}} قرار دارد که پیش‌نمایش ویدیو را نمایش می‌دهد؛ این ویدیویی است که دوربین کاربر می‌بیند. توجه کنید که از ویژگی [`autoplay`](/en-US/docs/Web/HTML/Reference/Elements/video#autoplay) استفاده شده است تا به محض رسیدن جریان از دوربین، بلافاصله نمایش داده شود، و ویژگی [`muted`](/en-US/docs/Web/HTML/Reference/Elements/video#muted) برای اطمینان از عدم خروجی صدای میکروفون کاربر به بلندگوهایش (که باعث ایجاد یک حلقه بازخورد ناخوشایند می‌شود) مشخص شده است.

```html
<div class="right">
  <div id="stopButton" class="button">Stop Recording</div>
  <h2>در حال ضبط</h2>
  <video id="recording" width="160" height="120" controls></video>
  <a id="downloadButton" class="button">Download</a>
</div>
```

در سمت راست، یک دکمه توقف و عنصر `<video>` را می‌بینیم که برای پخش ویدیوی ضبط شده استفاده می‌شود. توجه کنید که پنل پخش ویژگی `autoplay` را ندارد (بنابراین پخش به محض رسیدن رسانه شروع نمی‌شود) و ویژگی [`controls`](/en-US/docs/Web/HTML/Reference/Elements/video#controls) برای آن تنظیم شده است که به کاربر کنترل‌هایی برای پخش، مکث و غیره نشان می‌دهد.

در زیر عنصر پخش، یک دکمه برای دانلود ویدیوی ضبط شده قرار دارد.

```html hidden
<div class="bottom">
  <pre id="log"></pre>
</div>
```

```css hidden
body {
  font:
    14px "Open Sans",
    "Arial",
    sans-serif;
}

video {
  margin-top: 2px;
  border: 1px solid black;
}

.button {
  cursor: pointer;
  display: block;
  width: 160px;
  border: 1px solid black;
  font-size: 16px;
  text-align: center;
  padding-top: 2px;
  padding-bottom: 4px;
  color: white;
  background-color: darkgreen;
  text-decoration: none;
}

h2 {
  margin-bottom: 4px;
}

.left {
  margin-right: 10px;
  float: left;
  width: 160px;
  padding: 0px;
}

.right {
  margin-left: 10px;
  float: left;
  width: 160px;
  padding: 0px;
}

.bottom {
  clear: both;
  padding-top: 10px;
}
```

حالا بیایید نگاهی به کد جاوااسکریپت بیندازیم؛ این جایی است که بیشتر عملیات انجام می‌شود!

### تنظیم متغیرهای سراسری

ما با ایجاد چند متغیر سراسری که به آن‌ها نیاز داریم شروع می‌کنیم.

```js
let preview = document.getElementById("preview");
let recording = document.getElementById("recording");
let startButton = document.getElementById("startButton");
let stopButton = document.getElementById("stopButton");
let downloadButton = document.getElementById("downloadButton");
let logElement = document.getElementById("log");

let recordingTimeMS = 5000;
```

بیشتر این‌ها ارجاع به عناصری هستند که باید با آن‌ها کار کنیم. آخرین مورد، `recordingTimeMS`، برابر با 5000 میلی‌ثانیه (5 ثانیه) تنظیم شده است؛ این طول ویدیوهایی را که ضبط می‌کنیم مشخص می‌کند.

### توابع کمکی

در ادامه، چند تابع کمکی ایجاد می‌کنیم که بعداً استفاده می‌شوند.

```js
function log(msg) {
  logElement.innerText += `${msg}\n`;
}
```

تابع `log()` برای خروجی متن به یک {{HTMLElement("div")}} استفاده می‌شود تا بتوانیم اطلاعات را با کاربر به اشتراک بگذاریم. خیلی زیبا نیست اما برای هدف ما کار را انجام می‌دهد.

```js
function wait(delayInMS) {
  return new Promise((resolve) => setTimeout(resolve, delayInMS));
}
```

تابع `wait()` یک {{jsxref("Promise")}} جدید برمی‌گرداند که پس از سپری شدن تعداد میلی‌ثانیه مشخص شده resolve می‌شود. این کار با استفاده از یک [arrow function](/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions) انجام می‌شود که {{domxref("Window.setTimeout", "setTimeout()")}} را فراخوانی می‌کند و handler resolve پرامیس را به عنوان تابع timeout تعیین می‌کند. این به ما امکان می‌دهد هنگام استفاده از timeoutها از syntax پرامیس استفاده کنیم که می‌تواند در زنجیره‌سازی پرامیس‌ها بسیار مفید باشد، همانطور که بعداً خواهیم دید.

### شروع ضبط رسانه

تابع `startRecording()` فرآیند شروع ضبط را مدیریت می‌کند:

```js
function startRecording(stream, lengthInMS) {
  let recorder = new MediaRecorder(stream);
  let data = [];

  recorder.ondataavailable = (event) => data.push(event.data);
  recorder.start();
  log(`${recorder.state} for ${lengthInMS / 1000} seconds…`);

  let stopped = new Promise((resolve, reject) => {
    recorder.onstop = resolve;
    recorder.onerror = (event) => reject(event.name);
  });

  let recorded = wait(lengthInMS).then(() => {
    if (recorder.state === "recording") {
      recorder.stop();
    }
  });

  return Promise.all([stopped, recorded]).then(() => data);
}
```

`startRecording()` دو پارامتر ورودی می‌گیرد: یک {{domxref("MediaStream")}} برای ضبط و طول مدت ضبط بر حسب میلی‌ثانیه. ما همیشه بیش از تعداد میلی‌ثانیه مشخص شده از رسانه را ضبط نمی‌کنیم، البته اگر رسانه قبل از آن زمان متوقف شود، {{domxref("MediaRecorder")}} به طور خودکار ضبط را نیز متوقف می‌کند.

- ابتدا `MediaRecorder` را ایجاد می‌کنیم که ضبط `stream` ورودی را مدیریت می‌کند.
- `data` یک آرایه است، در ابتدا خالی، که {{domxref("Blob")}}های داده رسانه‌ای ارائه شده به handler رویداد {{domxref("MediaRecorder.dataavailable_event", "ondataavailable")}} ما را نگه می‌دارد.
- مقداردهی `ondataavailable` handler رویداد {{domxref("MediaRecorder.dataavailable_event", "dataavailable")}} را تنظیم می‌کند. ویژگی `data` رویداد دریافت شده یک {{domxref("Blob")}} است که حاوی داده رسانه‌ای است. handler رویداد، `Blob` را به آرایه `data` اضافه می‌کند.
- فرآیند ضبط را با فراخوانی {{domxref("MediaRecorder.start", "recorder.start()")}} شروع می‌کنیم و یک پیام به log با وضعیت به‌روز شده ضبط‌کننده و تعداد ثانیه‌هایی که ضبط خواهد کرد، خروجی می‌دهیم.
- یک {{jsxref("Promise")}} جدید به نام `stopped` ایجاد می‌کنیم که وقتی handler رویداد {{domxref("MediaRecorder.stop_event", "onstop")}} مربوط به `MediaRecorder` فراخوانی شود resolve می‌شود و اگر handler رویداد {{domxref("MediaRecorder.error_event", "onerror")}} آن فراخوانی شود reject می‌شود. handler reject نام خطای رخ داده را به عنوان ورودی دریافت می‌کند.
- یک `Promise` جدید دیگر به نام `recorded` ایجاد می‌کنیم که وقتی تعداد میلی‌ثانیه مشخص شده سپری شود resolve می‌شود. پس از resolve، اگر `MediaRecorder` در حال ضبط باشد، آن را متوقف می‌کند.
- در نهایت، از {{jsxref("Promise.all")}} برای ایجاد یک `Promise` جدید استفاده می‌کنیم که وقتی هر دو `Promise` (`stopped` و `recorded`) resolve شوند، fulfilled می‌شود. پس از آن، آرایه `data` توسط `startRecording()` به caller خود برگردانده می‌شود.

### توقف جریان ورودی

تابع `stop()` جریان رسانه ورودی را متوقف می‌کند:

```js
function stop(stream) {
  stream.getTracks().forEach((track) => track.stop());
}
```

این کار با فراخوانی {{domxref("MediaStream.getTracks()")}} و استفاده از {{jsxref("Array.forEach", "forEach()")}} برای فراخوانی {{domxref("MediaStreamTrack.stop()")}} روی هر track در جریان انجام می‌شود.

### دریافت جریان ورودی و تنظیم ضبط‌کننده

حالا بیایید به پیچیده‌ترین بخش کد در این مثال نگاه کنیم: handler رویداد ما برای کلیک‌های روی دکمه شروع:

```js
startButton.addEventListener("click", () => {
  navigator.mediaDevices
    .getUserMedia({
      video: true,
      audio: true,
    })
    .then((stream) => {
      preview.srcObject = stream;
      downloadButton.href = stream;
      preview.captureStream = preview.captureStream || preview.mozCaptureStream;
      return new Promise((resolve) => {
        preview.onplaying = resolve;
      });
    })
    .then(() => startRecording(preview.captureStream(), recordingTimeMS))
    .then((recordedChunks) => {
      let recordedBlob = new Blob(recordedChunks, { type: "video/webm" });
      recording.src = URL.createObjectURL(recordedBlob);
      downloadButton.href = recording.src;
      downloadButton.download = "RecordedVideo.webm";

      log(
        `Successfully recorded ${recordedBlob.size} bytes of ${recordedBlob.type} media.`,
      );
    })
    .catch((error) => {
      if (error.name === "NotFoundError") {
        log("Camera or microphone not found. Can't record.");
      } else {
        log(error);
      }
    });
});
```

وقتی یک رویداد {{domxref("Element/click_event", "click")}} رخ می‌دهد، این اتفاق می‌افتد:

- {{domxref("MediaDevices.getUserMedia")}} برای درخواست یک {{domxref("MediaStream")}} جدید که دارای هر دو track ویدیو و صدا است فراخوانی می‌شود. این جریانی است که ما ضبط خواهیم کرد.
- وقتی Promise برگردانده شده توسط `getUserMedia()` resolve می‌شود، ویژگی {{domxref("HTMLMediaElement.srcObject","srcObject")}} عنصر پیش‌نمایش {{HTMLElement("video")}} به جریان ورودی تنظیم می‌شود که باعث می‌شود ویدیوی در حال ضبط توسط دوربین کاربر در جعبه پیش‌نمایش نمایش داده شود. از آنجایی که عنصر `<video>` بی‌صدا (muted) است، صدا پخش نخواهد شد. سپس لینک دکمه «Download» نیز به جریان ارجاع داده می‌شود. سپس، ترتیب می‌دهیم که `preview.captureStream()` `preview.mozCaptureStream()` را فراخوانی کند تا کد ما در Firefox کار کند (روشی که در آن {{domxref("HTMLMediaElement.captureStream()")}} prefixed است). سپس یک {{jsxref("Promise")}} جدید که وقتی ویدیوی پیش‌نمایش شروع به پخش می‌کند resolve می‌شود ایجاد و برگردانده می‌شود.
- وقتی ویدیوی پیش‌نمایش شروع به پخش می‌کند، می‌دانیم که رسانه‌ای برای ضبط وجود دارد، بنابراین با فراخوانی تابع [`startRecording()`](#شروع-ضبط-رسانه) که قبلاً ایجاد کردیم پاسخ می‌دهیم و جریان ویدیوی پیش‌نمایش (به عنوان منبع رسانه‌ای برای ضبط) و `recordingTimeMS` را به عنوان تعداد میلی‌ثانیه رسانه برای ضبط ارسال می‌کنیم. همانطور که قبلاً اشاره شد، `startRecording()` یک {{jsxref("Promise")}} برمی‌گرداند که handler resolve آن (با دریافت یک آرایه از اشیاء {{domxref("Blob")}} حاوی تکه‌های داده رسانه‌ای ضبط شده) پس از اتمام ضبط فراخوانی می‌شود.
- handler resolve فرآیند ضبط یک آرایه از تکه‌های داده رسانه‌ای `Blob` که در محلی به نام `recordedChunks` شناخته می‌شوند را به عنوان ورودی دریافت می‌کند. اولین کاری که انجام می‌دهیم این است که تکه‌ها را در یک {{domxref("Blob")}} واحد با نوع MIME `"video/webm"` ادغام می‌کنیم، با استفاده از این واقعیت که سازنده {{domxref("Blob.Blob", "Blob()")}} آرایه‌هایی از اشیاء را به یک شیء واحد متصل می‌کند. سپس از {{domxref("URL.createObjectURL_static", "URL.createObjectURL()")}} برای ایجاد یک URL که به blob ارجاع می‌دهد استفاده می‌شود؛ این URL به عنوان مقدار ویژگی [`src`](/en-US/docs/Web/HTML/Reference/Elements/video#src) عنصر پخش ویدیوی ضبط شده (تا بتوانید ویدیو را از blob پخش کنید) و همچنین به عنوان هدف لینک دکمه دانلود تنظیم می‌شود.

  سپس ویژگی [`download`](/en-US/docs/Web/HTML/Reference/Elements/a#download) دکمه دانلود تنظیم می‌شود. در حالی که ویژگی `download` می‌تواند یک مقدار Boolean باشد، همچنین می‌توانید آن را به یک رشته تنظیم کنید تا به عنوان نام فایل دانلود شده استفاده شود. بنابراین با تنظیم ویژگی `download` لینک دانلود بر روی `"RecordedVideo.webm"`، به مرورگر می‌گوییم که کلیک روی دکمه باید یک فایل با نام `"RecordedVideo.webm"` دانلود کند که محتوای آن ویدیوی ضبط شده است.

- اندازه و نوع رسانه ضبط شده در ناحیه log در زیر دو ویدیو و دکمه دانلود خروجی داده می‌شود.
- `catch()` برای تمام `Promise`ها خطا را با فراخوانی تابع `log()` ما به ناحیه log خروجی می‌دهد.

### مدیریت دکمه توقف

آخرین بخش کد یک handler برای رویداد {{domxref("Element/click_event", "click")}} روی دکمه توقف با استفاده از {{domxref("EventTarget.addEventListener", "addEventListener()")}} اضافه می‌کند:

```js
stopButton.addEventListener("click", () => {
  stop(preview.srcObject);
});
```

این کار تابع [`stop()`](#توقف-جریان-ورودی) را که قبلاً توضیح دادیم فراخوانی می‌کند.

### نتیجه

وقتی همه موارد به همراه بقیه HTML و CSS که در بالا نشان داده نشده است کنار هم قرار گیرند، به این شکل به نظر می‌رسد و کار می‌کند:

{{EmbedLiveSample('Example_of_recording_a_media_element', '600', '440', , , , 'camera;microphone')}}

می‌توانید این مثال را با استفاده از دکمه «Play» در playground نیز باز کنید، که به شما امکان می‌دهد کد ترکیبی را مشاهده کنید، از جمله بخش‌هایی که در بالا پنهان شده‌اند زیرا برای توضیح نحوه استفاده از APIها حیاتی نیستند.

## همچنین ببینید

- [صفحه اصلی API ضبط و جریان‌های رسانه‌ای (Media Capture and Streams API)](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- {{domxref("MediaDevices.getUserMedia()")}}