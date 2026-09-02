---
title: "MediaSource: handle property"
short-title: handle
slug: Web/API/MediaSource/handle
page-type: web-api-instance-property
browser-compat: api.MediaSource.handle
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("dedicated")}}

ویژگی فقط‌خواندنی **`handle`** از رابط {{domxref("MediaSource")}} یک شیء {{domxref("MediaSourceHandle")}} برمی‌گرداند؛ یک نماینده (proxy) برای `MediaSource` که می‌تواند از یک worker اختصاصی به thread اصلی منتقل شود و از طریق ویژگی {{domxref("HTMLMediaElement.srcObject")}} به یک عنصر رسانه‌ای متصل شود.

> [!NOTE]
> `handle` فقط روی نمونه‌های {{domxref("MediaSource")}} در workerهای اختصاصی در دسترس است.

هر شیء `MediaSource` که در داخل یک worker اختصاصی ساخته می‌شود، `MediaSourceHandle` متمایز خودش را دارد. getter مربوط به `handle` همیشه نمونه `MediaSourceHandle` مختص نمونه `MediaSource` موجود در worker اختصاصی مرتبط را برمی‌گرداند. اگر handle قبلاً با استفاده از {{domxref("DedicatedWorkerGlobalScope.postMessage()", "postMessage()")}} به thread اصلی منتقل شده باشد، نمونه handle در worker از نظر فنی جدا (detached) شده و نمی‌توان دوباره آن را انتقال داد.

## مقدار

یک نمونه شیء {{domxref("MediaSourceHandle")}}.

## مثال‌ها

ویژگی `handle` را می‌توان در داخل یک worker اختصاصی فراخوانی کرد و شیء حاصل {{domxref("MediaSourceHandle")}} سپس از طریق یک فراخوانی {{domxref("DedicatedWorkerGlobalScope.postMessage()", "postMessage()")}} به thread سازنده worker (در اینجا thread اصلی) منتقل می‌شود:

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

در thread اصلی، ما handle را از طریق یک event handler مربوط به {{domxref("Worker.message_event", "message")}} دریافت می‌کنیم، آن را از طریق ویژگی {{domxref("HTMLMediaElement.srcObject")}} به یک {{htmlelement("video")}} متصل می‌کنیم و ویدیو را با {{domxref("HTMLMediaElement.play()", "play")}} پخش می‌کنیم:

```js
worker.addEventListener("message", (msg) => {
  let mediaSourceHandle = msg.data.arg;
  video.srcObject = mediaSourceHandle;
  video.play();
});
```

> [!NOTE]
> اشیاء {{domxref("MediaSourceHandle")}} را نمی‌توان با موفقیت به داخل یا از طریق یک shared worker یا service worker انتقال داد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [نسخه نمایشی MSE-in-Workers اثر Matt Wolenetz](https://wolenetz.github.io/mse-in-workers-demo/mse-in-workers-demo.html)
- {{domxref("Media Source Extensions API", "Media Source Extensions API", "", "nocode")}}
- {{domxref("MediaSource")}}
- {{domxref("SourceBuffer")}}