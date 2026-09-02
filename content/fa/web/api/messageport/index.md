---
title: "MessagePort"
slug: Web/API/MessagePort
page-type: web-api-interface
browser-compat: api.MessagePort
---

{{APIRef("Channel Messaging API")}} {{AvailableInWorkers}}

**`MessagePort`** از رابطهای [Channel Messaging API](/en-US/docs/Web/API/Channel_Messaging_API) است که یکی از دو درگاه یک {{domxref("MessageChannel")}} را نمایش میدهد و امکان ارسال پیام از یک درگاه و گوش دادن به رسیدن آنها در درگاه دیگر را فراهم میکند.

`MessagePort` یک [شیء قابل انتقال](/en-US/docs/Web/API/Web_Workers_API/Transferable_objects) است.

{{InheritanceDiagram}}

## روشهای نمونه

_روشها را از والد خود، {{domxref("EventTarget")}}، به ارث میبرد._

- {{domxref("MessagePort.postMessage","postMessage()")}}
  - : پیامی را از درگاه ارسال میکند و بهصورت اختیاری مالکیت اشیاء را به زمینههای مرورگر دیگر منتقل میکند.
- {{domxref("MessagePort.start","start()")}}
  - : ارسال پیامهای صفبندیشده روی درگاه را آغاز میکند (فقط هنگام استفاده از {{domxref("EventTarget.addEventListener")}} لازم است؛ هنگام استفاده از {{domxref("MessagePort.message_event", "onmessage")}} بهصورت ضمنی انجام میشود).
- {{domxref("MessagePort.close","close()")}}
  - : درگاه را قطع میکند تا دیگر فعال نباشد.

## رویدادها

_رویدادها را از والد خود، {{domxref("EventTarget")}}، به ارث میبرد._

- {{domxref("MessagePort.message_event","message")}}
  - : وقتی یک شیء `MessagePort` پیامی دریافت میکند، این رویداد رخ میدهد.
- {{domxref("MessagePort.messageerror_event","messageerror")}}
  - : وقتی یک شیء `MessagePort` پیامی دریافت میکند که نمیتوان آن را از حالت سریالی خارج کرد، این رویداد رخ میدهد.

## مثال

در مثال زیر، میبینید که یک کانال جدید با استفاده از سازنده {{domxref("MessageChannel.MessageChannel","MessageChannel()")}} ساخته میشود.

وقتی IFrame بارگذاری شد، ما یک کنترلکننده {{domxref("MessagePort/message_event","onmessage")}} برای {{domxref("MessageChannel.port1")}} ثبت میکنیم و {{domxref("MessageChannel.port2")}} را با استفاده از روش {{domxref("window.postMessage")}} همراه با یک پیام به IFrame منتقل میکنیم.

وقتی پیامی از IFrame برگردانده میشود، تابع `onMessage` پیام را در یک پاراگراف نمایش میدهد.

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

برای یک مثال کامل و قابل اجرا، به [نمونه اصلی پیامرسانی کانال](https://github.com/mdn/dom-examples/tree/main/channel-messaging-basic) در گیتهاب مراجعه کنید ([اجرای زنده آن](https://mdn.github.io/dom-examples/channel-messaging-basic/)).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از پیامرسانی کانال](/en-US/docs/Web/API/Channel_Messaging_API/Using_channel_messaging)