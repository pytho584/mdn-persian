---
title: "HTMLMediaElement: srcObject property"
short-title: srcObject
slug: Web/API/HTMLMediaElement/srcObject
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.srcObject
---

{{APIRef("HTML DOM")}}

خصوصیت **`srcObject`** از رابط {{domxref("HTMLMediaElement")}}، شیئی را که به‌عنوان منبع رسانه‌های مرتبط با {{domxref("HTMLMediaElement")}} عمل می‌کند تنظیم یا برمی‌گرداند؛ اگر اختصاص نیافته باشد، مقدار `null` برمی‌گرداند.

این شیء می‌تواند یک {{domxref("MediaStream")}}، یک {{domxref("MediaSource")}}، یک {{domxref("Blob")}} یا یک {{domxref("File")}} باشد (که از `Blob` به ارث می‌رسد).

> [!NOTE]
> از مارس ۲۰۲۰، تنها سافاری از `srcObject` پشتیبانی کامل دارد؛ یعنی می‌تواند اشیاء `MediaSource`، `MediaStream`، `Blob` و `File` را به‌عنوان مقدار بپذیرد. سایر مرورگرها از اشیاء `MediaStream` پشتیبانی می‌کنند؛ تا زمانی که به این سطح نرسیده‌اند، در نظر بگیرید که با {{domxref("URL.createObjectURL_static", "URL.createObjectURL()")}} یک URL بسازید و آن را به {{domxref("HTMLMediaElement.src")}} اختصاص دهید (نمونه را در زیر ببینید). علاوه بر این، از نسخه ۱۰۸، کرومیوم از اتصال یک شیء `MediaSource` متعلق به worker اختصاصی با انتساب نمونه {{domxref("MediaSourceHandle")}} آن (که از worker منتقل شده) به `srcObject` پشتیبانی می‌کند.

## مقدار

یک شیء {{domxref('MediaStream')}}، {{domxref('MediaSource')}}، {{domxref('Blob')}} یا {{domxref('File')}} (البته برای اطلاع از پشتیبانی واقعی، جدول سازگاری را ببینید)، یا در صورت عدم تنظیم، `null`.

## نکات استفاده

نسخه‌های قدیمی‌تر مشخصات Media Source ایجاب می‌کردند که با استفاده از {{domxref("URL.createObjectURL_static", "URL.createObjectURL()")}} یک object URL بسازید و سپس {{domxref("HTMLMediaElement.src", "src")}} را روی آن URL تنظیم کنید. اکنون می‌توانید به‌سادگی `srcObject` را مستقیماً روی {{domxref("MediaStream")}} تنظیم کنید.

## مثال‌ها

### مثال پایه

در این مثال، یک {{domxref("MediaStream")}} دوربین به یک عنصر {{HTMLElement("video")}} تازه‌ساخته اختصاص داده می‌شود.

```js
const mediaStream = await navigator.mediaDevices.getUserMedia({ video: true });
const video = document.createElement("video");
video.srcObject = mediaStream;
```

در این مثال، یک {{domxref('MediaSource')}} جدید به یک عنصر {{HTMLElement("video")}} تازه‌ساخته اختصاص داده می‌شود.

```js
const mediaSource = new MediaSource();
const video = document.createElement("video");
video.srcObject = mediaSource;
```

### پشتیبانی از بازگشت به خصوصیت src

مثال‌های زیر از نسخه‌های قدیمی‌تر مرورگر پشتیبانی می‌کنند که در آن‌ها لازم است یک object URL بسازید و در صورت عدم پشتیبانی از `srcObject`، آن را به `src` اختصاص دهید.

ابتدا، یک {{domxref("MediaStream")}} دوربین به یک عنصر {{HTMLElement("video")}} تازه‌ساخته اختصاص داده می‌شود، با مکانیزم جایگزین (fallback) برای مرورگرهای قدیمی‌تر.

```js
const mediaStream = await navigator.mediaDevices.getUserMedia({ video: true });
const video = document.createElement("video");
if ("srcObject" in video) {
  video.srcObject = mediaStream;
} else {
  // Avoid using this in new browsers, as it is going away.
  video.src = URL.createObjectURL(mediaStream);
}
```

دوم، یک {{domxref('MediaSource')}} جدید به یک عنصر {{HTMLElement("video")}} تازه‌ساخته اختصاص داده می‌شود، با مکانیزم جایگزین برای مرورگرهای قدیمی‌تر و مرورگرهایی که هنوز از انتساب مستقیم {{domxref('MediaSource')}} پشتیبانی نمی‌کنند.

```js
const mediaSource = new MediaSource();
const video = document.createElement("video");
// Older browsers may not have srcObject
if ("srcObject" in video) {
  try {
    video.srcObject = mediaSource;
  } catch (err) {
    if (err.name !== "TypeError") {
      throw err;
    }
    // Even if they do, they may only support MediaStream
    video.src = URL.createObjectURL(mediaSource);
  }
} else {
  video.src = URL.createObjectURL(mediaSource);
}
```

### ساخت `MediaSource` در worker و ارسال آن به نخ اصلی برای پخش

خصوصیت {{domxref("MediaSource.handle")}} را می‌توان درون یک worker اختصاصی (dedicated worker) فراخوانی کرد و شیء حاصل از آن، یعنی {{domxref("MediaSourceHandle")}}، از طریق فراخوانی {{domxref("DedicatedWorkerGlobalScope.postMessage()", "postMessage()")}} به نخی که worker را ایجاد کرده (در اینجا نخ اصلی) منتقل می‌شود:

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

در نخ اصلی، handle را از طریق یک event handler به نام {{domxref("Worker.message_event", "message")}} دریافت می‌کنیم، آن را از طریق خصوصیت `HTMLMediaElement.srcObject` به یک {{htmlelement("video")}} متصل می‌کنیم و ویدیو را با {{domxref("HTMLMediaElement.play()", "play")}} پخش می‌کنیم:

```js
worker.addEventListener("message", (msg) => {
  let mediaSourceHandle = msg.data.arg;
  video.srcObject = mediaSourceHandle;
  video.play();
});
```

> [!NOTE]
> {{domxref("MediaSourceHandle")}}ها را نمی‌توان با موفقیت به یک shared worker یا service worker منتقل کرد یا از طریق آن‌ها منتقل نمود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
