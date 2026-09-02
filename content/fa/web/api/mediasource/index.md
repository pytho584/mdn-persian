---
title: MediaSource
slug: Web/API/MediaSource
page-type: web-api-interface
browser-compat: api.MediaSource
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}

رابط **`MediaSource`** متعلق به {{domxref("Media Source Extensions API", "Media Source Extensions API", "", "nocode")}}، یک منبع داده‌های رسانه‌ای برای یک شیء {{domxref("HTMLMediaElement")}} را نشان می‌دهد. یک شیء `MediaSource` را می‌توان به یک {{domxref("HTMLMediaElement")}} متصل کرد تا در عامل کاربر پخش شود.

{{InheritanceDiagram}}

## سازنده

- {{domxref("MediaSource.MediaSource", "MediaSource()")}}
  - : یک شیء `MediaSource` جدید بدون هیچ بافر منبع مرتبطی می‌سازد و آن را برمی‌گرداند.

## ویژگی‌های نمونه

- {{domxref("MediaSource.activeSourceBuffers")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("SourceBufferList")}} برمی‌گرداند که شامل زیرمجموعه‌ای از اشیاء {{domxref("SourceBuffer")}} موجود در {{domxref("MediaSource.sourceBuffers", "sourceBuffers")}} است؛ فهرستی از اشیایی که تراک ویدیویی انتخاب‌شده، تراک‌های صوتی فعال و تراک‌های متنی نمایش‌داده‌شده/پنهان را فراهم می‌کنند.

- {{domxref("MediaSource.duration")}}
  - : مدت‌زمان رسانهٔ در حال ارائه را دریافت و تنظیم می‌کند.

- {{domxref("MediaSource.handle")}} {{ReadOnlyInline}}
  - : در داخل یک dedicated worker یک شیء {{domxref("MediaSourceHandle")}} برمی‌گرداند. این شیء نماینده‌ای (proxy) برای `MediaSource` است که می‌توان آن را از worker به نخ اصلی انتقال داد و از طریق ویژگی {{domxref("HTMLMediaElement.srcObject")}} به یک عنصر رسانه‌ای متصل کرد.

- {{domxref("MediaSource.readyState")}} {{ReadOnlyInline}}
  - : یک مقدار enum برمی‌گرداند که وضعیت `MediaSource` فعلی را نشان می‌دهد: اینکه آیا در حال حاضر به یک عنصر رسانه‌ای متصل نیست (`closed`)، متصل است و آماده دریافت اشیاء {{domxref("SourceBuffer")}} است (`open`)، یا متصل است اما جریان از طریق {{domxref("MediaSource.endOfStream()")}} پایان یافته است (`ended`).

- {{domxref("MediaSource.sourceBuffers")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("SourceBufferList")}} برمی‌گرداند که شامل فهرست اشیاء {{domxref("SourceBuffer")}} مرتبط با این `MediaSource` است.

## ویژگی‌های ایستا

- {{domxref("MediaSource.canConstructInDedicatedWorker_static", "MediaSource.canConstructInDedicatedWorker")}} {{ReadOnlyInline}}
  - : یک مقدار بولین؛ اگر پشتیبانی از `MediaSource` در worker پیاده‌سازی شده باشد، `true` برمی‌گرداند و سازوکاری با تأخیر کم برای تشخیص قابلیت (feature detection) فراهم می‌کند.

## متدهای نمونه

_متدهای رابط والد خود، {{domxref("EventTarget")}} را به ارث می‌برد._

- {{domxref("MediaSource.addSourceBuffer()")}}
  - : یک {{domxref("SourceBuffer")}} جدید با نوع MIME داده‌شده ایجاد می‌کند و آن را به فهرست {{domxref("MediaSource.sourceBuffers", "sourceBuffers")}} اضافه می‌کند.

- {{domxref("MediaSource.clearLiveSeekableRange()")}}
  - : یک بازهٔ قابل‌پرش (seekable range) را که قبلاً با فراخوانی setLiveSeekableRange() تنظیم شده بود، پاک می‌کند.

- {{domxref("MediaSource.endOfStream()")}}
  - : پایان جریان را اعلام می‌کند.

- {{domxref("MediaSource.removeSourceBuffer()")}}
  - : {{domxref("SourceBuffer")}} داده‌شده را از فهرست {{domxref("MediaSource.sourceBuffers", "sourceBuffers")}} حذف می‌کند.

- {{domxref("MediaSource.setLiveSeekableRange()")}}
  - : بازه‌ای را تنظیم می‌کند که کاربر می‌تواند در عنصر رسانه‌ای به آن پرش کند.

## متدهای ایستا

- {{domxref("MediaSource.isTypeSupported_static", "MediaSource.isTypeSupported()")}}
  - : یک مقدار بولین برمی‌گرداند که نشان می‌دهد آیا عامل کاربر فعلی از نوع MIME داده‌شده پشتیبانی می‌کند یا خیر — به عبارت دیگر، آیا می‌تواند اشیاء {{domxref("SourceBuffer")}} را برای آن نوع MIME با موفقیت ایجاد کند.

## رویدادها

- {{domxref("MediaSource.sourceclose_event", "sourceclose")}}
  - : زمانی رخ می‌دهد که نمونهٔ `MediaSource` دیگر به یک عنصر رسانه‌ای متصل نیست.

- {{domxref("MediaSource.sourceended_event", "sourceended")}}
  - : زمانی رخ می‌دهد که نمونهٔ `MediaSource` همچنان به یک عنصر رسانه‌ای متصل است، اما متد {{domxref("MediaSource.endOfStream()")}} فراخوانی شده است.

- {{domxref("MediaSource.sourceopen_event", "sourceopen")}}
  - : زمانی رخ می‌دهد که یک عنصر رسانه‌ای نمونهٔ `MediaSource` را باز کرده است و آماده است داده‌ها به اشیاء {{domxref("SourceBuffer")}} در {{domxref("MediaSource.sourceBuffers", "sourceBuffers")}} اضافه شوند.

## مثال‌ها

### مثال پایهٔ کامل

مثال پایهٔ زیر با استفاده از {{domxref("XMLHttpRequest")}} یک ویدیو را بارگذاری می‌کند و به محض امکان آن را پخش می‌کند. این مثال را می‌توانید [به‌صورت زنده اینجا](https://nickdesaulniers.github.io/netfix/demo/bufferAll.html) ببینید (همچنین می‌توانید [سورس آن را](https://github.com/nickdesaulniers/netfix/blob/gh-pages/demo/bufferAll.html) برای بررسی بیشتر دانلود کنید).

```js
const video = document.querySelector("video");

const assetURL = "frag_bunny.mp4";
// Need to be specific for Blink regarding codecs
// ./mp4info frag_bunny.mp4 | grep Codec
const mimeCodec = 'video/mp4; codecs="avc1.42E01E, mp4a.40.2"';
let mediaSource;

if ("MediaSource" in window && MediaSource.isTypeSupported(mimeCodec)) {
  mediaSource = new MediaSource();
  console.log(mediaSource.readyState); // closed
  video.src = URL.createObjectURL(mediaSource);
  mediaSource.addEventListener("sourceopen", sourceOpen);
} else {
  console.error("Unsupported MIME type or codec: ", mimeCodec);
}

function sourceOpen() {
  console.log(this.readyState); // open
  const sourceBuffer = mediaSource.addSourceBuffer(mimeCodec);
  fetchAB(assetURL, (buf) => {
    sourceBuffer.addEventListener("updateend", () => {
      mediaSource.endOfStream();
      video.play();
      console.log(mediaSource.readyState); // ended
    });
    sourceBuffer.appendBuffer(buf);
  });
}

function fetchAB(url, cb) {
  console.log(url);
  const xhr = new XMLHttpRequest();
  xhr.open("get", url);
  xhr.responseType = "arraybuffer";
  xhr.onload = () => {
    cb(xhr.response);
  };
  xhr.send();
}
```

### ساخت یک `MediaSource` در dedicated worker و ارسال آن به نخ اصلی

ویژگی {{domxref("MediaSource.handle", "handle")}} را می‌توان در داخل یک dedicated worker مقداردهی کرد و شیء {{domxref("MediaSourceHandle")}} حاصل را با استفاده از یک فراخوانی {{domxref("DedicatedWorkerGlobalScope.postMessage()", "postMessage()")}} به نخی که worker را ایجاد کرده است (در این مورد، نخ اصلی) انتقال داد:

```js
// Inside dedicated worker
let mediaSource = new MediaSource();
let handle = mediaSource.handle;
// Transfer the handle to the context that created the worker
postMessage({ arg: handle }, [handle]);

mediaSource.addEventListener("sourceopen", () => {
  // Await sourceopen on MediaSource before creating SourceBuffers
  // and populating them with fetched media — MediaSource won't
  // accept creation of SourceBuffers until it is attached to the
  // HTMLMediaElement and its readyState is "open"
});
```

در سمت نخ اصلی، handle را از طریق یک هندلر رویداد {{domxref("Worker.message_event", "message")}} دریافت می‌کنیم، آن را از طریق ویژگی {{domxref("HTMLMediaElement.srcObject")}} به یک {{htmlelement("video")}} متصل می‌کنیم و ویدیو را با {{domxref("HTMLMediaElement.play()", "play")}} پخش می‌کنیم:

```js
worker.addEventListener("message", (msg) => {
  let mediaSourceHandle = msg.data.arg;
  video.srcObject = mediaSourceHandle;
  video.play();
});
```

> [!NOTE]
> اشیاء {{domxref("MediaSourceHandle")}} را نمی‌توان با موفقیت به داخل یک shared worker یا service worker منتقل کرد و نیز نمی‌توان آنها را از طریق این نوع workerها منتقل نمود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("SourceBuffer")}}
- {{domxref("SourceBufferList")}}