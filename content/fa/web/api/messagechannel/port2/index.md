---
title: "MessageChannel: port2 property"
short-title: port2
slug: Web/API/MessageChannel/port2
page-type: web-api-instance-property
browser-compat: api.MessageChannel.port2
---

{{APIRef("Channel Messaging API")}} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`port2`** در رابط {{domxref("MessageChannel")}}، دومین پورت کانال پیام را برمی‌گرداند — پورتی که به زمینه (context) در آن سوی کانال متصل است و پیام ابتدا به آن ارسال می‌شود.

## مقدار

یک شیء {{domxref("MessagePort")}} که نشان‌دهنده دومین پورت کانال است؛ پورتی که به زمینه در آن سوی کانال متصل شده است.

## مثال‌ها

در بلوک کد زیر، می‌بینید که یک کانال جدید با استفاده از سازنده {{domxref("MessageChannel.MessageChannel", "MessageChannel()")}} ساخته می‌شود. وقتی IFrame بارگذاری شد، `port2` را همراه با یک پیام، از طریق {{domxref("Window.postMessage()")}} به IFrame ارسال می‌کنیم. سپس هندلر `handleMessage` به پیامی که از IFrame برگشت داده شده پاسخ می‌دهد (با استفاده از {{domxref("MessagePort.message_event", "onmessage")}}) و آن را در یک پاراگراف قرار می‌دهد. به {{domxref("MessageChannel.port1", "port1")}} گوش داده می‌شود تا بررسی شود پیام چه زمانی می‌رسد.

```js
const channel = new MessageChannel();
const para = document.querySelector("p");

const ifr = document.querySelector("iframe");
const otherWindow = ifr.contentWindow;

ifr.addEventListener("load", iframeLoaded);

function iframeLoaded() {
  otherWindow.postMessage("Hello from the main page!", "*", [channel.port2]);
}

channel.port1.onmessage = handleMessage;
function handleMessage(e) {
  para.innerHTML = e.data;
}
```

برای یک مثال کامل و قابل اجرا، به [دموی پایه messaging کانال](https://github.com/mdn/dom-examples/tree/main/channel-messaging-basic) در GitHub مراجعه کنید ([اجرای زنده آن](https://mdn.github.io/dom-examples/channel-messaging-basic/)).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از messaging کانال](/en-US/docs/Web/API/Channel_Messaging_API/Using_channel_messaging)