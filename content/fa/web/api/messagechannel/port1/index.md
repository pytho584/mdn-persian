---
title: "MessageChannel: port1 property"
short-title: port1
slug: Web/API/MessageChannel/port1
page-type: web-api-instance-property
browser-compat: api.MessageChannel.port1
---

{{APIRef("Channel Messaging API")}} {{AvailableInWorkers}}

ویژگی فقط-خواندنی **`port1`** از رابط {{domxref("MessageChannel")}}، اولین پورت کانال پیام را برمی‌گرداند — پورتی که به زمینه‌ای که کانال را ایجاد کرده متصل است.

## Value

یک شیء {{domxref("MessagePort")}}، اولین پورت کانال، که پورت متصل به زمینهٔ ایجادکنندهٔ کانال است.

## Examples

در بلوک کد زیر، می‌توانید ببینید که یک کانال جدید با استفاده از سازندهٔ {{domxref("MessageChannel.MessageChannel", "MessageChannel()")}} ایجاد می‌شود. پس از بارگذاری {{HTMLElement("iframe")}}، ما {{domxref("MessageChannel.port2", "port2")}} را به همراه یک پیام به {{HTMLElement("iframe")}} با استفاده از {{domxref("MessagePort.postMessage")}} ارسال می‌کنیم. سپس کنترل‌کنندهٔ `handleMessage` به پیامی که از `<iframe>` برگردانده می‌شود پاسخ می‌دهد (با استفاده از {{domxref("MessagePort.message_event", "onmessage")}}) و آن را در یک پاراگراف قرار می‌دهد. متد `handleMessage` به `port1` متصل می‌شود تا هنگام رسیدن پیام گوش دهد.

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

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از پیام‌رسانی کانال](/en-US/docs/Web/API/Channel_Messaging_API/Using_channel_messaging)