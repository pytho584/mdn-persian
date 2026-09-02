---
title: "MessageChannel"
---

---
title: MessageChannel
slug: Web/API/MessageChannel
page-type: web-api-interface
browser-compat: api.MessageChannel
---

{{APIRef("Channel Messaging API")}} {{AvailableInWorkers}}

رابط **`MessageChannel`** از [API پیام‌رسانی کانال](/en-US/docs/Web/API/Channel_Messaging_API) به ما امکان می‌دهد یک کانال پیام جدید ایجاد کرده و از طریق دو ویژگی {{domxref("MessagePort")}} آن داده ارسال کنیم.

## Constructor

- {{domxref("MessageChannel.MessageChannel", "MessageChannel()")}}
  - : یک شیء `MessageChannel` جدید با دو شیء {{domxref("MessagePort")}} جدید برمی‌گرداند.

## ویژگی‌های نمونه

- {{domxref("MessageChannel.port1")}} {{ReadOnlyInline}}
  - : port1 کانال را برمی‌گرداند.
- {{domxref("MessageChannel.port2")}} {{ReadOnlyInline}}
  - : port2 کانال را برمی‌گرداند.

## مثال

در مثال زیر، می‌توانید یک کانال جدید را با استفاده از سازنده {{domxref("MessageChannel.MessageChannel", "MessageChannel()")}} ایجاد کنید.

هنگامی که IFrame بارگذاری شد، یک handler {{domxref("MessagePort/message_event","onmessage")}} برای {{domxref("MessageChannel.port1")}} ثبت می‌کنیم و {{domxref("MessageChannel.port2")}} را با استفاده از متد {{domxref("window.postMessage")}} به همراه یک پیام به IFrame منتقل می‌کنیم.

هنگامی که یک پیام از IFrame بازگردانده می‌شود، تابع `onMessage` پیام را در یک پاراگراف نمایش می‌دهد.

```js
const channel = new MessageChannel();
const output = document.querySelector(".output");
const iframe = document.querySelector("iframe");

// Wait for the iframe to load
iframe.addEventListener("load", onLoad);

function onLoad() {
  // Listen for messages on port1
  channel.port1.onmessage = onMessage;

  // Transfer port2 to the iframe
  iframe.contentWindow.postMessage("Hello from the main page!", "*", [
    channel.port2,
  ]);
}

// Handle messages received on port1
function onMessage(e) {
  output.innerHTML = e.data;
}
```

برای یک مثال کامل عملی، به [نمونه اصلی پیام‌رسانی کانال](https://github.com/mdn/dom-examples/tree/main/channel-messaging-basic) در GitHub مراجعه کنید ([همچنین به صورت زنده اجرا کنید](https://mdn.github.io/dom-examples/channel-messaging-basic/)).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از پیام‌رسانی کانال](/en-US/docs/Web/API/Channel_Messaging_API/Using_channel_messaging)