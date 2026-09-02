---
title: "MessageChannel: MessageChannel() constructor"
short-title: MessageChannel()
slug: Web/API/MessageChannel/MessageChannel
page-type: web-api-constructor
browser-compat: api.MessageChannel.MessageChannel
---

{{APIRef("Channel Messaging API")}} {{AvailableInWorkers}}

سازندهٔ **`MessageChannel()`** متعلق به رابط {{domxref("MessageChannel")}}، یک شیء جدید {{domxref("MessageChannel")}} بازمی‌گرداند که شامل دو شیء جدید {{domxref("MessagePort")}} است.

## نحو

```js-nolint
new MessageChannel()
```

### پارامترها

هیچ‌کدام ({{jsxref("undefined")}}).

### مقدار بازگشتی

یک شیء جدید {{domxref("MessageChannel")}}.

## مثال‌ها

در بلوک کد زیر می‌بینید که یک کانال جدید با استفاده از سازندهٔ `MessageChannel()` ساخته می‌شود. پس از بارگذاری {{HTMLElement("iframe")}}، {{domxref("MessageChannel.port2", "port2")}} به‌همراه یک پیام از طریق {{domxref("MessagePort.postMessage")}} به `<iframe>` فرستاده می‌شود. سپس کنترل‌کنندهٔ `handleMessage` با استفاده از {{domxref("MessagePort.message_event", "onmessage")}} به پیامی که از `<iframe>` بازگردانده شده واکنش نشان می‌دهد و آن را در یک پاراگراف قرار می‌دهد. همچنین به {{domxref("MessageChannel.port1", "port1")}} گوش داده می‌شود تا مشخص شود پیام چه زمانی می‌رسد.

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

برای یک مثال کامل و عملی، [دموی پایهٔ پیام‌رسانی کانال](https://github.com/mdn/dom-examples/tree/main/channel-messaging-basic) را در GitHub ببینید ([اجرای زندهٔ آن](https://mdn.github.io/dom-examples/channel-messaging-basic/)).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از پیام‌رسانی کانال](/en-US/docs/Web/API/Channel_Messaging_API/Using_channel_messaging)