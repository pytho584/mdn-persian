---
title: "BroadcastChannel: name property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BroadcastChannel/name"
short-title: name
slug: Web/API/BroadcastChannel/name
page-type: web-api-instance-property
browser-compat: api.BroadcastChannel.name
translated_by: "n8n + AI"
---

{{APIRef("BroadCastChannel API")}} {{AvailableInWorkers}}

ویژگی فقط-خواندنی **`name`** از رابط {{domxref("BroadcastChannel")}} یک رشته را برمی‌گرداند که به طور یکتا کانال داده شده را با نام آن شناسایی می‌کند. این نام به سازنده {{domxref("BroadcastChannel.BroadCastChannel", "BroadcastChannel()")}} در زمان ایجاد ارسال می‌شود و بنابراین فقط-خواندنی است.

## مقادیر

یک رشته.

## مثال‌ها

```js
// Connect to a channel
const bc = new BroadcastChannel("test_channel");

// More operations (like postMessage, …)

// Log the channel name to the console
console.log(bc.name); // "test_channel"

// When done, disconnect from the channel
bc.close();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("BroadcastChannel")}}، رابطی که به آن تعلق دارد.