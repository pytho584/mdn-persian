---
title: "Insertable Streams for MediaStreamTrack API"
---

---
title: Insertable Streams for MediaStreamTrack API
slug: Web/API/Insertable_Streams_for_MediaStreamTrack_API
page-type: web-api-overview
status:
  - experimental
browser-compat: api.VideoTrackGenerator
spec-urls: https://w3c.github.io/mediacapture-transform/
---

{{DefaultAPISidebar("Insertable Streams for MediaStreamTrack API")}}{{SeeCompatTable}}{{AvailableInWorkers("dedicated")}}

**API جریان‌های قابل درج برای MediaStreamTrack** روشی برای پردازش فریم‌های ویدیوی یک {{domxref("MediaStreamTrack")}} در حین مصرف شدن فراهم می‌کند.

## مفاهیم و کاربرد

هنگام پردازش ویدیوی بلادرنگ، گاهی می‌خواهید عناصر بصری را وارد کنید یا به‌گونه‌ای دیگر جریان فریم‌های ویدیو را پردازش نمایید. برای مثال، یک برنامه ممکن است شامل دو track باشد که باید با هم ترکیب شوند، مانند نقشه آب‌وهوا و ویدیوی مجری‌ای که نقشه را توضیح می‌دهد. یا ممکن است بخواهید روی یک track پردازشی انجام دهید تا پس‌زمینه را محو کنید یا عناصر دیگری (مثلاً کلاه‌های بامزه روی افراد) اضافه کنید. APIهای شرح‌داده‌شده در اینجا دسترسی مستقیم به جریان ویدیو فراهم می‌کنند و به شما امکان می‌دهند آن را در زمان واقعی دستکاری کنید.

برای اطمینان از عملکرد بهینه، این APIها فقط در [کارگران اختصاصی](/en-US/docs/Web/API/DedicatedWorkerGlobalScope) در دسترس هستند (مگر اینکه خلاف آن ذکر شده باشد).

## رابط‌ها

- {{domxref("MediaStreamTrackProcessor")}} {{Experimental_Inline}}
  - : منبع یک شیء {{domxref("MediaStreamTrack")}} را مصرف کرده و جریانی از فریم‌های ویدیو تولید می‌کند.
- {{domxref("VideoTrackGenerator")}} {{Experimental_Inline}}
  - : یک {{domxref("WritableStream")}} ایجاد می‌کند که به عنوان یک منبع ویدیوی {{domxref("MediaStreamTrack")}} عمل می‌کند.
- {{domxref("MediaStreamTrackGenerator")}} {{Experimental_Inline}} {{Non-standard_Inline}}
  - : یک {{domxref("WritableStream")}} ایجاد می‌کند که به عنوان یک منبع {{domxref("MediaStreamTrack")}} برای ویدیو یا صدا عمل می‌کند. فقط در {{Glossary("main thread")}} در دسترس است.

## مثال‌ها

مثال زیر از مقاله [Unbundling MediaStreamTrackProcessor and VideoTrackGenerator](https://blog.mozilla.org/webrtc/unbundling-mediastreamtrackprocessor-and-videotrackgenerator/) گرفته شده است. این مثال یک {{domxref("MediaStreamTrack")}} دوربین را برای پردازش به یک worker [انتقال](/en-US/docs/Web/API/Web_Workers_API/Transferable_objects) می‌دهد. worker یک خط لوله ایجاد می‌کند که یک فیلتن sepia tone روی فریم‌های ویدیو اعمال کرده و آن‌ها را آینه می‌کند. خط لوله به یک {{domxref("VideoTrackGenerator")}} ختم می‌شود که {{domxref("MediaStreamTrack")}} آن به عقب منتقل شده و پخش می‌شود. رسانه اکنون در زمان واقعی و خارج از {{Glossary("main thread")}} از طریق تبدیل جریان می‌یابد.

```js
const stream = await navigator.mediaDevices.getUserMedia({ video: true });
const [track] = stream.getVideoTracks();
const worker = new Worker("worker.js");
worker.postMessage({ track }, [track]);
const { data } = await new Promise((r) => (worker.onmessage = r));
video.srcObject = new MediaStream([data.track]);
```

worker.js:

```js
onmessage = async ({ data: { track } }) => {
  const vtg = new VideoTrackGenerator();
  self.postMessage({ track: vtg.track }, [vtg.track]);
  const { readable } = new MediaStreamTrackProcessor({ track });
  await readable
    .pipeThrough(new TransformStream({ transform }))
    .pipeTo(vtg.writable);
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}