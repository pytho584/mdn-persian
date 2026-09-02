---
title: "MessagePort: start() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/MessagePort/start"
---

---
title: "MessagePort: start() method"
short-title: start()
slug: Web/API/MessagePort/start
page-type: web-api-instance-method
browser-compat: api.MessagePort.start
---

{{APIRef("Channel Messaging API")}} {{AvailableInWorkers}}

متد **`start()`** در رابط {{domxref("MessagePort")}} ارسال پیام‌های در صف‌مانده روی پورت را آغاز می‌کند. این متد فقط هنگام استفاده از {{domxref("EventTarget.addEventListener")}} لازم است؛ هنگام استفاده از {{domxref("MessagePort.message_event", "onmessage")}} این کار به‌صورت ضمنی انجام می‌شود.

## Syntax

```js-nolint
start()
```

### Parameters

هیچ.

### Return value

هیچ ({{jsxref("undefined")}}).

## Examples

در بلوک کد زیر، یک تابع کنترل‌کننده به نام `handleMessage` را می‌بینید که هنگام ارسال پیام به این سند با استفاده از `onmessage` اجرا می‌شود:

```js
channel.port1.onmessage = handleMessage;
function handleMessage(e) {
  para.innerHTML = e.data;
}
```

گزینه دیگر استفاده از {{domxref("EventTarget.addEventListener")}} است؛ اما وقتی از این روش استفاده می‌کنید، باید به‌صورت صریح `start()` را فراخوانی کنید تا جریان پیام‌ها به این سند آغاز شود:

```js
channel.port1.addEventListener("message", handleMessage);
function handleMessage(e) {
  para.innerHTML = e.data;
  textInput.value = "";
}

channel.port1.start();
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از پیام‌رسانی کانال](/en-US/docs/Web/API/Channel_Messaging_API/Using_channel_messaging)