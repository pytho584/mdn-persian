---
title: "MessageEvent"
slug: Web/API/MessageEvent
page-type: web-api-interface
browser-compat: api.MessageEvent
---

{{APIRef("HTML DOM")}}{{AvailableInWorkers}}

رابط **`MessageEvent`** نشان‌دهنده یک پیام دریافتی توسط یک شیء هدف است.

این رابط برای نمایش پیام‌ها در موارد زیر استفاده می‌شود:

- [رویدادهای ارسال‌شده توسط سرور](/en-US/docs/Web/API/Server-sent_events) (به رویداد {{domxref("EventSource.message_event", "message")}} از {{domxref("EventSource")}} مراجعه کنید).
- [وب سوکت‌ها](/en-US/docs/Web/API/WebSockets_API) (به رویداد {{domxref("WebSocket.message_event", "message")}} از {{domxref("WebSocket")}} مراجعه کنید).
- [پیام‌رسانی بین سندها](/en-US/docs/Web/API/Window/postMessage) (به {{domxref("Window.postMessage()")}} و رویداد {{domxref("Window.message_event", "message")}} از {{domxref("Window")}} مراجعه کنید).
- [پیام‌رسانی کانال](/en-US/docs/Web/API/Channel_Messaging_API) (به {{domxref("MessagePort.postMessage()")}} و رویداد {{domxref("MessagePort.message_event", "message")}} از {{domxref("MessagePort")}} مراجعه کنید).
- [پیام‌رسانی بین کارگرها/سندها](/en-US/docs/Web/API/Worker/postMessage) (به دو مورد بالا و همچنین {{domxref("Worker.postMessage()")}}، رویداد {{domxref("Worker.message_event", "message")}} از {{domxref("Worker")}}، رویداد {{domxref("ServiceWorkerGlobalScope.message_event", "message")}} از {{domxref("ServiceWorkerGlobalScope")}} و غیره مراجعه کنید).
- [کانال‌های پخش](/en-US/docs/Web/API/Broadcast_Channel_API) (به {{domxref("BroadcastChannel.postMessage()")}} و رویداد {{domxref("BroadcastChannel.message_event", "message")}} از {{domxref("BroadcastChannel")}} مراجعه کنید).
- [کانال‌های داده WebRTC](/en-US/docs/Web/API/WebRTC_API) (به رویداد {{domxref("RTCDataChannel.message_event", "message")}} از {{domxref("RTCDataChannel")}} مراجعه کنید).

عملی که توسط این رویداد راه‌اندازی می‌شود، در یک تابع تعریف می‌شود که به عنوان مدیریت‌کننده رویداد برای رویداد `message` مربوطه تنظیم شده است.

{{InheritanceDiagram}}

## سازنده

- {{domxref("MessageEvent.MessageEvent", "MessageEvent()")}}
  - : یک `MessageEvent` جدید ایجاد می‌کند.

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌هایی را از والد خود، {{domxref("Event")}}، به ارث می‌برد._

- {{domxref("MessageEvent.data")}} {{ReadOnlyInline}}
  - : داده‌ای که توسط فرستنده پیام ارسال شده است.
- {{domxref("MessageEvent.origin")}} {{ReadOnlyInline}}
  - : یک رشته که نمایانگر مبدأ (origin) فرستنده پیام است.
- {{domxref("MessageEvent.lastEventId")}} {{ReadOnlyInline}}
  - : یک رشته که نمایانگر یک شناسه یکتا برای رویداد است.
- {{domxref("MessageEvent.source")}} {{ReadOnlyInline}}
  - : یک `MessageEventSource` (که می‌تواند یک شیء {{glossary("WindowProxy")}}، {{domxref("MessagePort")}} یا {{domxref("ServiceWorker")}} باشد) که نمایانگر فرستنده پیام است.
- {{domxref("MessageEvent.ports")}} {{ReadOnlyInline}}
  - : آرایه‌ای از اشیاء {{domxref("MessagePort")}} که شامل تمام اشیاء {{domxref("MessagePort")}} ارسال‌شده با پیام، به ترتیب است.

## روش‌های نمونه

_این رابط همچنین روش‌هایی را از والد خود، {{domxref("Event")}}، به ارث می‌برد._

- {{domxref("MessageEvent.initMessageEvent","initMessageEvent()")}} {{deprecated_inline}}
  - : یک رویداد پیام را مقداردهی اولیه می‌کند. **دیگر از این استفاده نکنید** — **به جای آن از سازنده {{domxref("MessageEvent.MessageEvent", "MessageEvent()")}} استفاده کنید.**

## مثال‌ها

در [مثال کارگر اشتراکی پایه](https://github.com/mdn/dom-examples/tree/main/web-workers/simple-shared-worker) ما ([اجرای کارگر اشتراکی](https://mdn.github.io/dom-examples/web-workers/simple-shared-worker/))، دو صفحه HTML داریم که هر کدام از مقداری جاوااسکریپت برای انجام یک محاسبه استفاده می‌کنند. اسکریپت‌های مختلف از یک فایل کارگر یکسان برای انجام محاسبه استفاده می‌کنند — هر دو می‌توانند به آن دسترسی داشته باشند، حتی اگر صفحاتشان در پنجره‌های مختلف اجرا شوند.

قطعه کد زیر ایجاد یک شیء {{domxref("SharedWorker")}} را با استفاده از سازنده {{domxref("SharedWorker.SharedWorker", "SharedWorker()")}} نشان می‌دهد. هر دو اسکریپت شامل این کد هستند:

```js
const myWorker = new SharedWorker("worker.js");
```

سپس هر دو اسکریپت از طریق یک شیء {{domxref("MessagePort")}} که با استفاده از ویژگی {{domxref("SharedWorker.port")}} ایجاد شده است، به کارگر دسترسی پیدا می‌کنند. اگر رویداد onmessage با استفاده از addEventListener متصل شود، پورت به صورت دستی با استفاده از متد `start()` آن شروع می‌شود:

```js
myWorker.port.start();
```

هنگامی که پورت شروع می‌شود، هر دو اسکریپت به ترتیب با استفاده از `port.postMessage()` و `port.onmessage` پیام‌ها را به کارگر ارسال می‌کنند و پیام‌های ارسال‌شده از آن را مدیریت می‌کنند:

```js
[first, second].forEach((input) => {
  input.onchange = () => {
    myWorker.port.postMessage([first.value, second.value]);
    console.log("Message posted to worker");
  };
});

myWorker.port.onmessage = (e) => {
  result1.textContent = e.data;
  console.log("Message received from worker");
};
```

در داخل کارگر، از مدیریت‌کننده {{domxref("SharedWorkerGlobalScope.connect_event", "onconnect")}} برای اتصال به همان پورت مورد بحث استفاده می‌کنیم. پورت‌های مرتبط با آن کارگر در ویژگی `ports` رویداد {{domxref("SharedWorkerGlobalScope/connect_event", "connect")}} قابل دسترسی هستند — سپس از متد `start()` {{domxref("MessagePort")}} برای شروع پورت و از مدیریت‌کننده `onmessage` برای رسیدگی به پیام‌های ارسال‌شده از رشته‌های اصلی استفاده می‌کنیم.

```js
onconnect = (e) => {
  const port = e.ports[0];

  port.addEventListener("message", (e) => {
    const workerResult = `Result: ${e.data[0] * e.data[1]}`;
    port.postMessage(workerResult);
  });

  port.start(); // Required when using addEventListener. Otherwise called implicitly by onmessage setter.
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ExtendableMessageEvent")}} — مشابه این رابط است اما در رابط‌هایی استفاده می‌شود که نیاز به انعطاف‌پذیری بیشتری برای نویسندگان دارند.