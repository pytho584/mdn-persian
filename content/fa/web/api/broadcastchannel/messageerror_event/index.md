---
title: "BroadcastChannel: messageerror event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BroadcastChannel/messageerror_event"
translated_by: "n8n + AI"
---

---
title: "BroadcastChannel: messageerror event"
short-title: messageerror
slug: Web/API/BroadcastChannel/messageerror_event
page-type: web-api-event
browser-compat: api.BroadcastChannel.messageerror_event
---

{{APIRef("BroadCastChannel API")}}{{AvailableInWorkers}}

رویداد **`messageerror`** از رابط {{domxref("BroadcastChannel")}} زمانی رخ می‌دهد که پیامی که امکان تبدیل آن به داده وجود ندارد (deserialize) روی کانال دریافت شود.

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("messageerror", (event) => { })

onmessageerror = (event) => { }
```

## نوع رویداد

یک {{domxref("MessageEvent")}}. از {{domxref("Event")}} ارث می‌برد.

{{InheritanceDiagram("MessageEvent")}}

## مثال‌ها

### گوش دادن به رویدادهای messageerror

این کد از {{domxref("EventTarget.addEventListener", "addEventListener()")}} برای گوش دادن به پیام‌ها و خطاها استفاده می‌کند:

```js
const channel = new BroadcastChannel("example-channel");

channel.addEventListener("message", (event) => {
  received.textContent = event.data;
});

channel.addEventListener("messageerror", (event) => {
  console.error(event);
});
```

مشابه همین، اما با استفاده از ویژگی‌های کنترل‌کننده رویداد `onmessage` و `onmessageerror`:

```js
const channel = new BroadcastChannel("example-channel");

channel.onmessage = (event) => {
  received.textContent = event.data;
};

channel.onmessageerror = (event) => {
  console.log(event);
};
```

### تلاش برای به اشتراک‌گذاری حافظه

یک علت رایج رویدادهای `messageerror` تلاش برای ارسال یک {{jsxref("SharedArrayBuffer")}} یا نمایش بافری مبتنی بر آن، در میان [خوشه‌های عامل](/en-US/docs/Web/JavaScript/Reference/Execution_model#agent_clusters_and_memory_sharing) است. کد زیر این موضوع را نشان می‌دهد.

صفحه A کد زیر را اجرا می‌کند:

```js
const channel = new BroadcastChannel("hello");
channel.postMessage({ data: new SharedArrayBuffer(1024) });
```

صفحه B کد زیر را اجرا می‌کند:

```js
const channel = new BroadcastChannel("hello");
channel.addEventListener("messageerror", (event) => {
  console.error("Message error");
});
```

سپس صفحه B یک رویداد `messageerror` دریافت می‌کند وقتی سعی می‌کند پیام ارسال‌شده از صفحه A را به داده تبدیل کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویدادهای مرتبط: {{domxref("BroadcastChannel/message_event", "message")}}.