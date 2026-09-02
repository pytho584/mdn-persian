---
title: "HTMLVideoElement: requestVideoFrameCallback() method"
short-title: requestVideoFrameCallback()
slug: Web/API/HTMLVideoElement/requestVideoFrameCallback
page-type: web-api-instance-method
browser-compat: api.HTMLVideoElement.requestVideoFrameCallback
---

{{APIRef("HTML DOM")}}

متد **`requestVideoFrameCallback()`** در واسط {{domxref("HTMLVideoElement")}} یک تابع بازخوانی (callback) ثبت می‌کند که وقتی یک فریم ویدیویی جدید به ترکیب‌کننده (compositor) ارسال می‌شود، اجرا می‌شود. این کار به توسعه‌دهندگان امکان می‌دهد عملیات کارآمدی را روی هر فریم ویدیو انجام دهند.

## نحو

```js-nolint
requestVideoFrameCallback(callback)
```

### پارامترها

- `callback`
  - : تابع بازخوانی که وقتی یک فریم ویدیویی جدید به ترکیب‌کننده ارسال می‌شود اجرا می‌شود. این تابع شامل دو پارامتر است:
    - `now`
      - : یک {{domxref("DOMHighResTimeStamp")}} که زمان فراخوانی callback را نشان می‌دهد.
    - `metadata`
      - : یک شیء حاوی ویژگی‌های زیر:
        - `expectedDisplayTime`
          - : یک {{domxref("DOMHighResTimeStamp")}} که زمانی را نشان می‌دهد که مرورگر انتظار دارد فریم قابل مشاهده باشد.
        - `height`
          - : یک عدد، بر حسب پیکسل رسانه‌ای، که ارتفاع فریم ویدیو را نشان می‌دهد (پیکسل‌های قابل مشاهدهٔ رمزگشایی‌شده، بدون تنظیمات نسبت تصویر).
        - `mediaTime`
          - : یک عدد، بر حسب ثانیه، که برچسب زمانی ارائهٔ رسانه‌ای (media presentation timestamp) فریم ارائه‌شده را نشان می‌دهد. این مقدار با برچسب زمانی فریم در خط زمانی {{domxref("HTMLMediaElement.currentTime")}} برابر است.
        - `presentationTime`
          - : یک {{domxref("DOMHighResTimeStamp")}} که زمانی را نشان می‌دهد که مرورگر فریم را برای ترکیب (composition) ارسال کرد.
        - `presentedFrames`
          - : یک عدد که تعداد فریم‌های ارسال‌شده برای ترکیب تا کنون در کنار callback فعلی را نشان می‌دهد. می‌توان از آن برای تشخیص اینکه آیا بین نمونه‌های callback فریم‌هایی از دست رفته‌اند استفاده کرد.
        - `processingDuration`
          - : یک عدد، بر حسب ثانیه، که مدت زمان بین ارسال بستهٔ رمزگذاری‌شده با همان برچسب زمانی ارائهٔ این فریم به رمزگشا (یعنی `mediaTime`) و آماده شدن فریم رمزگشایی‌شده برای ارائه را نشان می‌دهد.
        - `width`
          - : یک عدد، بر حسب پیکسل رسانه‌ای، که عرض فریم ویدیو را نشان می‌دهد (پیکسل‌های قابل مشاهدهٔ رمزگشایی‌شده، بدون تنظیمات نسبت تصویر).

        ویژگی‌های فرادادهٔ اضافی ممکن است در callback های `requestVideoFrameCallback()` که در برنامه‌های {{domxref("WebRTC_API", "WebRTC", "", "nocode")}} استفاده می‌شوند در دسترس باشند:
        - `captureTime`
          - : یک {{domxref("DOMHighResTimeStamp")}} که زمان ضبط فریم را نشان می‌دهد. این مورد برای فریم‌های ویدیویی که از منبع محلی یا راه دور می‌آیند صدق می‌کند. برای منبع راه دور، زمان ضبط با استفاده از همگام‌سازی ساعت و گزارش‌های فرستندهٔ RTCP برای تبدیل برچسب‌های زمانی RTP به زمان ضبط تخمین زده می‌شود.
        - `receiveTime`
          - : یک {{domxref("DOMHighResTimeStamp")}} که زمانی را نشان می‌دهد که فریم رمزگذاری‌شده توسط پلتفرم دریافت شد. این مورد برای فریم‌های ویدیویی که از منبع راه دور می‌آیند صدق می‌کند. به‌طور مشخص، این مقدار مطابق با زمانی است که آخرین بستهٔ متعلق به این فریم از طریق شبکه دریافت شد.
        - `rtpTimestamp`
          - : یک عدد که برچسب زمانی RTP مرتبط با این فریم ویدیو را نشان می‌دهد.

> [!NOTE]
> ممکن است `width` و `height` در موارد خاصی با {{domxref("HTMLVideoElement.videoWidth")}} و {{domxref("HTMLVideoElement.videoHeight")}} تفاوت داشته باشند (مثلاً یک ویدیوی آنامورفیک ممکن است پیکسل‌های مستطیلی داشته باشد).

### مقدار بازگشتی

یک عدد که شناسهٔ یکتای callback را نشان می‌دهد.

این عدد می‌تواند به {{DOMxRef("HTMLVideoElement.cancelVideoFrameCallback()")}} ارسال شود تا ثبت callback لغو شود.

## توضیحات

موارد استفادهٔ معمول برای `requestVideoFrameCallback()` شامل پردازش ویدیو و نقاشی روی canvas، تحلیل ویدیو و همگام‌سازی با منابع صوتی خارجی است. پردازش هر فریم قبلاً به شیوه‌ای کم‌دقت‌تر یا کم‌بازده‌تر با اجرای عملیات روی نمایش ویدیوی فعلی در هر بار رخداد {{domxref("HTMLMediaElement.timeupdate_event", "timeupdate")}} انجام می‌شد. این روش به فریم‌های واقعی ویدیو دسترسی نداشت.

از `requestVideoFrameCallback()` به همان شیوهٔ {{domxref("Window.requestAnimationFrame()")}} استفاده می‌شود. از آن برای اجرای یک تابع callback استفاده می‌کنید که وقتی فریم ویدیویی بعدی به ترکیب‌کننده ارسال می‌شود، عملیاتی را انجام می‌دهد. callback با فراخوانی دوبارهٔ `requestVideoFrameCallback()` به پایان می‌رسد تا callback را هنگام ترکیب شدن فریم ویدیویی بعدی اجرا کند و به همین ترتیب ادامه می‌یابد. با این حال، `requestVideoFrameCallback()` از چند نظر برای عملیات ویدیویی طراحی شده است:

- `requestVideoFrameCallback()` دسترسی مطمئنی به هر فریم ویدیویی به‌صورت جداگانه فراهم می‌کند.
- `requestAnimationFrame()` تلاش می‌کند با نرخ تازه‌سازی نمایشگر که معمولاً ۶۰ هرتز است مطابقت داشته باشد. از سوی دیگر، `requestVideoFrameCallback()` تلاش می‌کند با نرخ فریم ویدیو مطابقت داشته باشد. به‌طور دقیق‌تر، callback با کمترین مقدار از نرخ فریم ویدیو و نرخ تازه‌سازی نقاشی مرورگر اجرا می‌شود. برای مثال، ویدیویی با نرخ فریم ۲۵ فریم‌برثانیه در مرورگری که با ۶۰ هرتز نقاشی می‌کند، callback ها را با نرخ ۲۵ هرتز اجرا می‌کند. ویدیویی با نرخ فریم ۱۲۰ فریم‌برثانیه در همان مرورگر ۶۰ هرتزی، callback ها را با نرخ ۶۰ هرتز اجرا می‌کند.
- `requestVideoFrameCallback()` فراداده‌های مفید ویدیو را در تابع callback در دسترس قرار می‌دهد.

یک نکته که باید در نظر داشته باشید این است که `requestVideoFrameCallback()` هیچ تضمین دقیقی ارائه نمی‌دهد که خروجی callback شما با نرخ فریم ویدیو همگام باقی بماند. ممکن است در نهایت یک چرخهٔ همگام‌سازی عمودی (v-sync) دیرتر از زمانی که فریم ویدیویی جدید ارائه شده است اجرا شود. (V-sync یک فناوری گرافیکی است که نرخ فریم یک ویدیو را با نرخ تازه‌سازی مانیتور همگام می‌کند.)

این API روی نخ اصلی (main thread) اجرا می‌شود، در حالی که ترکیب ویدیو احتمالاً روی یک نخ ترکیب جداگانه انجام می‌شود. باید زمان لازم برای تکمیل این عملیات و همچنین زمانی را که طول می‌کشد تا خود ویدیو و نتیجهٔ عملیات `requestVideoFrameCallback()` شما روی صفحه نمایش داده شود، در نظر بگیرید.

می‌توانید پارامتر `now` و ویژگی فرادادهٔ `expectedDisplayTime` را مقایسه کنید تا تعیین کنید آیا callback شما به اندازهٔ یک v-sync عقب است یا خیر. اگر `expectedDisplayTime` حدود پنج تا ده میکروثانیه با `now` فاصله داشته باشد، فریم قبلاً رندر شده است. اگر `expectedDisplayTime` تقریباً شانزده میلی‌ثانیه در آینده باشد (با فرض اینکه مرورگر/صفحه‌نمایش شما با ۶۰ هرتز تازه‌سازی می‌کند)، آنگاه callback یک v-sync فاصله دارد.

## مثال‌ها

### رسم فریم‌های ویدیو روی canvas

این مثال نشان می‌دهد که چگونه از `requestVideoFrameCallback()` برای رسم فریم‌های یک ویدیو روی عنصر {{htmlelement("canvas")}} دقیقاً با همان نرخ فریم ویدیو استفاده کنید. همچنین فراداده‌های فریم را برای اهداف اشکال‌زدایی روی صفحه ثبت می‌کند.

```js
const button = document.querySelector("button");
const video = document.querySelector("video");
const canvas = document.querySelector("canvas");
const ctx = canvas.getContext("2d");
const fpsInfo = document.querySelector("#fps-info");
const metadataInfo = document.querySelector("#metadata-info");

button.addEventListener("click", () =>
  video.paused ? video.play() : video.pause(),
);

video.addEventListener("play", () => {
  if (!("requestVideoFrameCallback" in HTMLVideoElement.prototype)) {
    console.error(
      "Your browser does not support the `Video.requestVideoFrameCallback()` API.",
    );
  }
});

let width = canvas.width;
let height = canvas.height;

let paintCount = 0;
let startTime = 0.0;

const updateCanvas = (now, metadata) => {
  if (startTime === 0.0) {
    startTime = now;
  }

  ctx.drawImage(video, 0, 0, width, height);

  const elapsed = (now - startTime) / 1000.0;
  const fps = (++paintCount / elapsed).toFixed(3);
  fpsInfo.innerText = !isFinite(fps) ? 0 : fps;
  metadataInfo.innerText = JSON.stringify(metadata, null, 2);

  video.requestVideoFrameCallback(updateCanvas);
};

video.src = "https://mdn.github.io/shared-assets/videos/flower.mp4";
video.requestVideoFrameCallback(updateCanvas);
```

```css
video,
canvas {
  max-width: 49%;
}
```

```html
<p>
  Start <button type="button">⏯</button> playing the video. Pause the video to
  read the metadata. Drawing video frames on the canvas is synced with the
  actual video framerate.
</p>
<video controls playsinline></video>
<canvas width="960" height="540"></canvas>
<p><span id="fps-info">0</span>fps</p>
<pre id="metadata-info"></pre>
```

{{embedlivesample("drawing_video_frames_on_a_canvas", , "540")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر {{HTMLElement("video")}}
- {{DOMxRef("HTMLVideoElement.cancelVideoFrameCallback()")}}
- [انجام عملیات کارآمد روی هر فریم ویدیو با `requestVideoFrameCallback()`](https://web.dev/articles/requestvideoframecallback-rvfc) در developer.chrome.com (۲۰۲۳)