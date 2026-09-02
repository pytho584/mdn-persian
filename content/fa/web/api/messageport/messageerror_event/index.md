---
title: "MessagePort: messageerror event"
short-title: messageerror
slug: Web/API/MessagePort/messageerror_event
page-type: web-api-event
browser-compat: api.MessagePort.messageerror_event
---

{{APIRef("Channel Messaging API")}} {{AvailableInWorkers}}

رویداد **`messageerror`** روی یک شیء {{domxref('MessagePort')}} زمانی رخ می‌دهد که آن شیء پیامی دریافت کند که نمی‌توان آن را deserialize کرد.

این رویداد قابل لغو نیست و bubble هم نمی‌شود.

## نحو

برای کار با این رویداد می‌توانید نام آن را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی رویدادگردان تنظیم کنید.

```js-nolint
addEventListener("messageerror", (event) => { })

onmessageerror = (event) => { }
```

## نوع رویداد

یک {{domxref("MessageEvent")}}. این رویداد از {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("MessageEvent")}}

## مثال‌ها

### تلاش برای به اشتراک گذاشتن حافظه

یکی از دلایل رایج رویدادهای `messageerror`، تلاش برای ارسال یک شیء {{jsxref("SharedArrayBuffer")}} یا یک نمای بافر (buffer view) که پشتیبان آن چنین بافری است، در میان [خوشه‌های عامل (agent clusters)](/en-US/docs/Web/JavaScript/Reference/Execution_model#agent_clusters_and_memory_sharing) است. برای مثال، یک پنجره در همان خوشهٔ عاملی که کارگر اشتراکیِ ایجادشده توسط خودش در آن قرار دارد نیست؛ بنابراین فرض کنید صفحه کد زیر را اجرا می‌کند:

```js
const worker = new SharedWorker("worker.js");
worker.port.start();
worker.port.addEventListener("message", (event) => {
  worker.port.postMessage(new SharedArrayBuffer(1024));
});
```

و `worker.js` شامل کد زیر است:

```js
self.addEventListener("connect", (event) => {
  console.log("Hello");
  const port = event.ports[0];
  port.start();
  port.postMessage("Port connected");
  port.addEventListener("messageerror", (event) => {
    console.log("Message error");
  });
});
```

در این صورت، کارگر اشتراکی وقتی بخواهد پیام ارسال‌شده از پنجره را deserialize کند، رویداد `messageerror` دریافت می‌کند.

> [!NOTE]
> می‌توانید برای اشکال‌زدایی SharedWorker خود از ابزارهای توسعه‌دهنده مرورگر (browser devtools) استفاده کنید؛ با وارد کردن یک URL در نوار آدرس مرورگر، به بازرس کارگرها (workers inspector) در DevTools دسترسی پیدا می‌کنید. برای مثال، در Chrome آدرس `chrome://inspect/#workers` و در Firefox آدرس `about:debugging#workers`.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویدادهای مرتبط: [`message`](/en-US/docs/Web/API/MessagePort/message_event).
- [استفاده از پیام‌رسانی کانال](/en-US/docs/Web/API/Channel_Messaging_API/Using_channel_messaging)
