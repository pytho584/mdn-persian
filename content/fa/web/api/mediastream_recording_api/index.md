---
title: "MediaStream Recording API"
---

---
title: MediaStream Recording API
slug: Web/API/MediaStream_Recording_API
page-type: web-api-overview
browser-compat: api.MediaRecorder
spec-urls: https://w3c.github.io/mediacapture-record/
---

{{DefaultAPISidebar("MediaStream Recording")}}

**MediaStream Recording API** که گاهی از آن با نام‌های _Media Recording API_ یا _MediaRecorder API_ نیز یاد می‌شود، ارتباط نزدیکی با [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API) و [WebRTC API](/en-US/docs/Web/API/WebRTC_API) دارد. این API امکان ضبط داده‌های تولیدشده توسط یک شیء {{domxref("MediaStream")}} یا {{domxref("HTMLMediaElement")}} را برای تحلیل، پردازش یا ذخیره‌سازی روی دیسک فراهم می‌کند. کار با آن نیز به‌طور شگفت‌آوری ساده است.

## مفاهیم و نحوه استفاده

MediaStream Recording API از یک رابط اصلی واحد به نام {{domxref("MediaRecorder")}} تشکیل شده است که تمام کارهای دریافت داده از یک {{domxref("MediaStream")}} و تحویل آن به شما برای پردازش را انجام می‌دهد. داده‌ها از طریق یک سری رویدادهای {{domxref("MediaRecorder.dataavailable_event", "dataavailable")}} و در قالبی که هنگام ایجاد `MediaRecorder` مشخص می‌کنید تحویل داده می‌شوند. سپس می‌توانید داده‌ها را بیشتر پردازش کنید یا در صورت تمایل آن‌ها را در فایل ذخیره کنید.

### مروری بر فرآیند ضبط

فرآیند ضبط یک جریان رسانه‌ای ساده است:

1. یک {{domxref("MediaStream")}} یا {{domxref("HTMLMediaElement")}} (در قالب یک عنصر {{HTMLElement("audio")}} یا {{HTMLElement("video")}}) را به‌عنوان منبع داده‌های رسانه‌ای تنظیم کنید.
2. یک شیء {{domxref("MediaRecorder")}} ایجاد کنید و جریان منبع و هر گزینه دلخواه (مانند نوع MIME ظرف یا نرخ بیت مورد نظر برای trackهای آن) را مشخص کنید.
3. {{domxref("MediaRecorder.dataavailable_event", "ondataavailable")}} را به‌عنوان کنترل‌کننده رویداد برای رویداد {{domxref("MediaRecorder.dataavailable_event", "dataavailable")}} تنظیم کنید؛ این کنترل‌کننده هر زمان که داده‌ای در دسترس باشد فراخوانی می‌شود.
4. پس از اینکه رسانه منبع در حال پخش بود و به نقطه‌ای رسیدید که برای ضبط ویدیو آماده هستید، {{domxref("MediaRecorder.start()")}} را برای شروع ضبط فراخوانی کنید.
5. کنترل‌کننده رویداد {{domxref("MediaRecorder.dataavailable_event", "dataavailable")}} شما هر بار که داده‌ای آماده باشد تا هرطور که می‌خواهید با آن کار کنید فراخوانی می‌شود؛ این رویداد یک ویژگی `data` دارد که مقدار آن یک {{domxref("Blob")}} حاوی داده‌های رسانه‌ای است. می‌توانید وقوع یک رویداد `dataavailable` را اجباری کنید و بدین ترتیب آخرین داده صوتی را برای فیلتر کردن، ذخیره‌سازی یا هر کار دیگری تحویل بگیرید.
6. ضبط به‌طور خودکار زمانی متوقف می‌شود که پخش رسانه منبع متوقف شود.
7. می‌توانید در هر زمان با فراخوانی {{domxref("MediaRecorder.stop()")}} ضبط را متوقف کنید.

> [!NOTE]
> شیءهای {{domxref("Blob")}} جداگانه‌ای که حاوی تکه‌هایی از رسانه ضبط‌شده هستند لزوماً به‌صورت تکی قابل پخش نیستند. رسانه باید قبل از پخش، دوباره کنار هم قرار گیرد.

اگر در طول ضبط مشکلی پیش بیاید، یک رویداد {{domxref("MediaRecorder/error_event", "error")}} به `MediaRecorder` ارسال می‌شود. می‌توانید با تنظیم یک کنترل‌کننده رویداد {{domxref("MediaRecorder.error_event", "onerror")}} به رویدادهای `error` گوش دهید.

در اینجا یک مثال آورده شده است که در آن از یک بوم HTML (Canvas) به‌عنوان منبع {{domxref("MediaStream")}} استفاده می‌کنیم و ضبط را پس از ۹ ثانیه متوقف می‌کنیم.

```js
const canvas = document.querySelector("canvas");

// آرگومان اختیاری فریم در ثانیه.
const stream = canvas.captureStream(25);
const recordedChunks = [];

console.log(stream);
const options = { mimeType: "video/webm; codecs=vp9" };
const mediaRecorder = new MediaRecorder(stream, options);

mediaRecorder.ondataavailable = handleDataAvailable;
mediaRecorder.start();

function handleDataAvailable(event) {
  console.log("data-available");
  if (event.data.size > 0) {
    recordedChunks.push(event.data);
    console.log(recordedChunks);
    download();
  } else {
    // …
  }
}
function download() {
  const blob = new Blob(recordedChunks, {
    type: "video/webm",
  });
  const url = URL.createObjectURL(blob);
  const a = document.createElement("a");
  document.body.appendChild(a);
  a.style = "display: none";
  a.href = url;
  a.download = "test.webm";
  a.click();
  URL.revokeObjectURL(url);
}

// نمایش: برای دانلود پس از ۹ ثانیه
setTimeout((event) => {
  console.log("stopping");
  mediaRecorder.stop();
}, 9000);
```

### بررسی و کنترل وضعیت ضبط

همچنین می‌توانید از ویژگی‌های شیء `MediaRecorder` برای تعیین وضعیت فرآیند ضبط استفاده کنید و از متدهای {{domxref("MediaRecorder.pause", "pause()")}} و {{domxref("MediaRecorder.resume", "resume()")}} آن برای توقف موقت و از سرگیری ضبط رسانه منبع بهره ببرید.

اگر نیاز یا تمایل دارید بررسی کنید که آیا یک نوع MIME خاص پشتیبانی می‌شود یا نه، این کار نیز امکان‌پذیر است. فقط کافی است {{domxref("MediaRecorder.isTypeSupported_static", "MediaRecorder.isTypeSupported()")}} را فراخوانی کنید.

### بررسی منابع ورودی بالقوه

اگر هدف شما ضبط ورودی دوربین و/یا میکروفون است، ممکن است بخواهید قبل از شروع فرآیند ساخت `MediaRecorder`، دستگاه‌های ورودی موجود را بررسی کنید. برای این کار باید {{domxref("MediaDevices.enumerateDevices", "navigator.mediaDevices.enumerateDevices()")}} را فراخوانی کنید تا فهرستی از دستگاه‌های رسانه‌ای موجود دریافت کنید. سپس می‌توانید آن فهرست را بررسی کرده و منابع ورودی بالقوه را شناسایی کنید و حتی فهرست را بر اساس معیارهای دلخواه فیلتر کنید.

در این قطعه کد، از `enumerateDevices()` برای بررسی دستگاه‌های ورودی موجود، یافتن دستگاه‌هایی که ورودی صوتی هستند و ایجاد عناصر {{HTMLElement("option")}} استفاده می‌شود که سپس به یک عنصر {{HTMLElement("select")}} که نمایانگر انتخاب‌گر منبع ورودی است اضافه می‌شوند.

```js
navigator.mediaDevices.enumerateDevices().then((devices) => {
  devices.forEach((device) => {
    const menu = document.getElementById("input-devices");
    if (device.kind === "audioinput") {
      const item = document.createElement("option");
      item.textContent = device.label;
      item.value = device.deviceId;
      menu.appendChild(item);
    }
  });
});
```

کدی مشابه این می‌تواند برای اجازه دادن به کاربر جهت محدود کردن مجموعه دستگاه‌هایی که می‌خواهد استفاده کند به کار رود.

### برای اطلاعات بیشتر

برای یادگیری بیشتر درباره استفاده از MediaStream Recording API، مقاله [استفاده از MediaStream Recording API](/en-US/docs/Web/API/MediaStream_Recording_API/Using_the_MediaStream_Recording_API) را ببینید که نحوه استفاده از این API برای ضبط کلیپ‌های صوتی را نشان می‌دهد. مقاله دوم، [ضبط یک عنصر رسانه‌ای](/en-US/docs/Web/API/MediaStream_Recording_API/Recording_a_media_element)، نحوه دریافت جریان از یک عنصر {{HTMLElement("audio")}} یا {{HTMLElement("video")}} و استفاده از جریان ضبط‌شده (در این مورد، ضبط آن و ذخیره‌سازی روی دیسک محلی) را شرح می‌دهد.

## رابط‌ها (Interfaces)

- {{domxref("BlobEvent")}}
  - : هر بار که ضبط یک تکه از داده‌های رسانه‌ای به پایان می‌رسد، این داده‌ها در قالب {{domxref("Blob")}} با استفاده از یک {{domxref("BlobEvent")}} از نوع `dataavailable` به مصرف‌کنندگان تحویل داده می‌شود.
- {{domxref("MediaRecorder")}}
  - : رابط اصلی که MediaStream Recording API را پیاده‌سازی می‌کند.
- {{domxref("MediaRecorderErrorEvent")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : ربطی که خطاهای پرتاب‌شده توسط MediaStream Recording API را نمایش می‌دهد. ویژگی {{domxref("MediaRecorderErrorEvent.error", "error")}} آن یک {{domxref("DOMException")}} است که خطای رخ‌داده را مشخص می‌کند.

## مثال‌ها

### ضبط ویدیوی پایه

```html
<button id="record-btn">Start</button>
<video id="player" src="" autoplay controls></video>
```

```js
const recordBtn = document.getElementById("record-btn");
const video = document.getElementById("player");

let chunks = [];
let isRecording = false;
let mediaRecorder = null;

const constraints = { video: true };

recordBtn.addEventListener("click", async () => {
  if (!isRecording) {
    // دریافت یک ضبط‌کننده در زمان بارگذاری
    if (!mediaRecorder) {
      const stream = await navigator.mediaDevices.getUserMedia(constraints);
      mediaRecorder = new MediaRecorder(stream);
      mediaRecorder.addEventListener("dataavailable", (e) => {
        console.log("data available");
        chunks.push(e.data);
      });
      mediaRecorder.addEventListener("stop", (e) => {
        console.log("onstop fired");
        const blob = new Blob(chunks, { type: "video/ogv; codecs=opus" });
        video.src = window.URL.createObjectURL(blob);
      });
      mediaRecorder.addEventListener("error", (e) => {
        console.error("An error occurred:", e);
      });
    }
    isRecording = true;
    recordBtn.textContent = "Stop";
    chunks = [];
    mediaRecorder.start();
    console.log("recorder started");
  } else {
    isRecording = false;
    recordBtn.textContent = "Start";
    mediaRecorder.stop();
    console.log("recorder stopped");
  }
});
```

<!-- TODO: re-enable when blob: URLs are allowed by CSP settings -->
<!-- {{EmbedLiveSample("Basic video recording", , "400", , , , "camera")}} -->

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- صفحه اصلی [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- {{domxref("MediaDevices.getUserMedia()")}}
- [نمایش MediaStream Recording در simpl.info](https://simpl.info/mediarecorder/) توسط [Sam Dutton](https://github.com/samdutton)
- [API ضبط رسانه HTML5 در عمل در Chrome و Firefox](https://blog.addpipe.com/mediarecorder-api/)
- [polyfill مربوط به MediaRecorder](https://github.com/ai/audio-recorder-polyfill) برای Safari و Edge
- [TutorRoom](https://github.com/chrisjohndigital/TutorRoom): ضبط/پخش/دانلود ویدیوی HTML با استفاده از getUserMedia و MediaStream Recording API ([منبع در GitHub](https://github.com/chrisjohndigital/TutorRoom))
- [نمونه پیشرفته ضبط جریان رسانه‌ای](https://quickblox.github.io/javascript-media-recorder/sample/)
- [OpenLang](https://github.com/chrisjohndigital/OpenLang): برنامه وب آزمایشگاه زبان ویدیویی HTML با استفاده از MediaDevices و MediaStream Recording API برای ضبط ویدیو ([منبع در GitHub](https://github.com/chrisjohndigital/OpenLang))
- [API ضبط‌کننده MediaStream اکنون در Safari Technology Preview 73 در دسترس است](https://blog.addpipe.com/safari-technology-preview-73-adds-limited-mediastream-recorder-api-support/)