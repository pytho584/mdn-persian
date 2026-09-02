---
title: "MessagePort: close() method"
short-title: close()
slug: Web/API/MessagePort/close
page-type: web-api-instance-method
browser-compat: api.MessagePort.close
---

{{APIRef("Channel Messaging API")}} {{AvailableInWorkers}}

متد **`close()`** از رابط {{domxref("MessagePort")}} پورت را قطع می‌کند، به طوری که دیگر فعال نیست. این کار جریان پیام‌ها به آن پورت را متوقف می‌کند.

## Syntax

```js-nolint
close()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

در بلوک کد زیر، می‌توانید یک تابع مدیریت‌کننده به نام `handleMessage` را ببینید که هنگام ارسال پیام به این سند با استفاده از {{domxref("EventTarget.addEventListener")}} اجرا می‌شود.

```js
channel.port1.addEventListener("message", handleMessage);
function handleMessage(e) {
  para.innerHTML = e.data;
  textInput.value = "";
}

channel.port1.start();
```

می‌توانید در هر زمانی ارسال پیام را با استفاده از این کد متوقف کنید:

```js
channel.port1.close();
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از پیام‌رسانی کانال](/en-US/docs/Web/API/Channel_Messaging_API/Using_channel_messaging)