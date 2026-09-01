---
title: "DedicatedWorkerGlobalScope: message event"
short-title: message
slug: Web/API/DedicatedWorkerGlobalScope/message_event
page-type: web-api-event
browser-compat: api.DedicatedWorkerGlobalScope.message_event
---

{{APIRef("Web Workers API")}}{{AvailableInWorkers("dedicated")}}

رویداد `message` روی یک شیء {{domxref('DedicatedWorkerGlobalScope')}} شلیک می‌شود وقتی worker پیامی را از والد خود دریافت می‌کند (یعنی وقتی والد پیامی را با استفاده از [`Worker.postMessage()`](/en-US/docs/Web/API/Worker/postMessage) ارسال می‌کند).

این رویداد قابل لغو (cancellable) نیست و در DOM انتشار نمی‌یابد (bubble نمی‌کند).

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("message", (event) => { })

onmessage = (event) => { }
```

## Event type

یک {{domxref("MessageEvent")}}. از {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("MessageEvent")}}

## Example

قطعه کد زیر ایجاد یک شیء {{domxref("Worker")}} را با استفاده از سازنده {{domxref("Worker.Worker", "Worker()")}} نشان می‌دهد. وقتی مقدار موجود در ورودی فرم `first` تغییر کند، پیام‌هایی به worker ارسال می‌شوند. یک کنترل‌کننده {{domxref("Worker.message_event", "onmessage")}} نیز وجود دارد که پیام‌های بازگشتی از worker را مدیریت می‌کند.

```js
// main.js

const myWorker = new Worker("worker.js");

first.onchange = () => {
  myWorker.postMessage([first.value, second.value]);
  console.log("Message posted to worker");
};

// worker.js

self.onmessage = (e) => {
  console.log("Message received from main script");
  const workerResult = `Result: ${e.data[0] * e.data[1]}`;
  console.log("Posting message back to main script");
  postMessage(workerResult);
};
```

در اسکریپت `main.js`، از یک کنترل‌کننده `onmessage` برای مدیریت پیام‌های دریافتی از اسکریپت worker استفاده می‌شود:

```js
// main.js

myWorker.onmessage = (e) => {
  result.textContent = e.data;
  console.log("Message received from worker");
};
```

به‌عنوان جایگزین، اسکریپت می‌تواند با استفاده از [`addEventListener()`](/en-US/docs/Web/API/EventTarget/addEventListener) به رویداد `message` گوش دهد:

```js
// worker.js

self.addEventListener("message", (e) => {
  result.textContent = e.data;
  console.log("Message received from worker");
});
```

توجه کنید که در اسکریپت اصلی، `onmessage` باید روی `myWorker` فراخوانی شود، در حالی که در داخل اسکریپت worker فقط به `onmessage` نیاز دارید، زیرا worker عملاً همان حوزه سراسری ({{domxref("DedicatedWorkerGlobalScope")}}) است.

برای یک مثال کامل، به [Basic dedicated worker example](https://github.com/mdn/dom-examples/tree/main/web-workers/simple-web-worker) مراجعه کنید ([run dedicated worker](https://mdn.github.io/dom-examples/web-workers/simple-web-worker/)).

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("DedicatedWorkerGlobalScope")}}
- {{domxref("WorkerGlobalScope")}}
- رویدادهای مرتبط: [`messageerror`](/en-US/docs/Web/API/DedicatedWorkerGlobalScope/messageerror_event)
- [`Worker.postMessage()`](/en-US/docs/Web/API/Worker/postMessage)
- [استفاده از پیام‌رسانی کانالی](/en-US/docs/Web/API/Channel_Messaging_API/Using_channel_messaging)