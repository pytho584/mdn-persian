---
title: "BroadcastChannel: close() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BroadcastChannel/close"
translated_by: "n8n + AI"
---

---
title: "BroadcastChannel: close() method"
short-title: close()
slug: Web/API/BroadcastChannel/close
page-type: web-api-instance-method
browser-compat: api.BroadcastChannel.close
---

{{APIRef("BroadCastChannel API")}} {{AvailableInWorkers}}

متد **`close()`** از رابط {{domxref("BroadcastChannel")}} اتصال به کانال زیرین را قطع می‌کند و به شیء اجازه می‌دهد که جمع‌آوری زباله شود. این یک گام ضروری است، زیرا راه دیگری برای مرورگر وجود ندارد که بداند این کانال دیگر مورد نیاز نیست.

## نحو

```js-nolint
close()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
// Connect to a channel
const bc = new BroadcastChannel("test_channel");

// More operations (like postMessage, …)

// When done, disconnect from the channel
bc.close();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("BroadcastChannel")}}، رابطی که این متد به آن تعلق دارد.