---
title: "MessagePort: message event"
---
---
title: "MessagePort: message event"
short-title: message
slug: Web/API/MessagePort/message_event
page-type: web-api-event
browser-compat: api.MessagePort.message_event
---

{{APIRef("Channel Messaging API")}} {{AvailableInWorkers}}

رویداد **`message`** بر روی یک شیء {{domxref('MessagePort')}} زمانی که یک پیام روی آن کانال می‌رسد، فعال می‌شود.

این رویداد قابل لغو نیست و منتشر نمی‌شود.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("message", (event) => { })

onmessage = (event) => { }
```

## نوع رویداد

یک {{domxref("MessageEvent")}}. از {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("MessageEvent")}}

## مثال‌ها

فرض کنید یک اسکریپت یک [`MessageChannel`](/en-US/docs/Web/API/MessageChannel) ایجاد می‌کند و یکی از پورت‌ها را به یک زمینه مرورگر متفاوت، مانند یک [`<iframe>`](/en-US/docs/Web/HTML/Reference/Elements/iframe) دیگر، با استفاده از کدی مانند زیر می‌فرستد:

```js
const channel = new MessageChannel();
const myPort = channel.port1;
const targetFrame = window.top.frames[1];
const targetOrigin = "https://example.org";

const messageControl = document.querySelector("#message");
const channelMessageButton = document.querySelector("#channel-message");

channelMessageButton.addEventListener("click", () => {
  myPort.postMessage(messageControl.value);
});

targetFrame.postMessage("init", targetOrigin, [channel.port2]);
```

هدف می‌تواند پورت را دریافت کرده و با استفاده از کدی مانند زیر شروع به گوش دادن به پیام‌ها و خطاهای پیام روی آن کند:

```js
window.addEventListener("message", (event) => {
  const myPort = event.ports[0];

  myPort.addEventListener("message", (event) => {
    received.textContent = event.data;
  });

  myPort.addEventListener("messageerror", (event) => {
    console.error(event.data);
  });

  myPort.start();
});
```

توجه داشته باشید که شنونده باید قبل از تحویل هر پیام به این پورت، [`MessagePort.start()`](/en-US/docs/Web/API/MessagePort/start) را فراخوانی کند. این فقط زمانی لازم است که از روش [`addEventListener()`](/en-US/docs/Web/API/EventTarget/addEventListener) استفاده می‌شود: اگر گیرنده به جای آن از `onmessage` استفاده کند، `start()` به طور ضمنی فراخوانی می‌شود:

```js
window.addEventListener("message", (event) => {
  const myPort = event.ports[0];

  myPort.onmessage = (event) => {
    received.textContent = event.data;
  };

  myPort.onmessageerror = (event) => {
    console.error(event.data);
  };
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویدادهای مرتبط: [`messageerror`](/en-US/docs/Web/API/MessagePort/messageerror_event).
- [استفاده از پیام‌رسانی کانال (Using channel messaging)](/en-US/docs/Web/API/Channel_Messaging_API/Using_channel_messaging)