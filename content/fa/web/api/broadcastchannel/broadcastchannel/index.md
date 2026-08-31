---
title: "BroadcastChannel: BroadcastChannel() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BroadcastChannel/BroadcastChannel"
translated_by: "n8n + AI"
---

---
title: "BroadcastChannel: BroadcastChannel() constructor"
short-title: BroadcastChannel()
slug: Web/API/BroadcastChannel/BroadcastChannel
page-type: web-api-constructor
browser-compat: api.BroadcastChannel.BroadcastChannel
---

{{APIRef("BroadCastChannel API")}} {{AvailableInWorkers}}

سازندهٔ **`BroadcastChannel()`** یک {{domxref("BroadcastChannel")}} جدید می‌سازد و آن را به کانال اصلی متصل می‌کند.

## نحو (Syntax)

```js-nolint
new BroadcastChannel(channelName)
```

### پارامترها

- `channelName`
  - : رشته‌ای که نام کانال را نشان می‌دهد؛ برای همهٔ {{glossary("browsing context", "زمینه‌های مرور")}} با {{glossary("origin", "خاستگاه")}} یکسان، فقط یک کانال با این نام وجود دارد.

## مثال‌ها

```js
// ایجاد یک کانال جدید که به کانال "internal_notification" گوش می‌دهد.

const bc = new BroadcastChannel("internal_notification");
bc.postMessage("New listening connected!");
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("BroadcastChannel")}}، واسطی که این به آن تعلق دارد.