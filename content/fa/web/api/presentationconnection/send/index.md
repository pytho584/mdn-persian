---
title: "PresentationConnection: send() method"
short-title: send()
slug: Web/API/PresentationConnection/send
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PresentationConnection.send
---

{{APIRef("Presentation")}}{{SeeCompatTable}}{{SecureContext_Header}}

متد **`send()`** از رابط {{domxref("PresentationConnection")}} به یک زمینهٔ مرورگر کنترل‌کننده می‌گوید که داده‌های متنی یا باینری را به یک زمینهٔ مرورگر ارائه‌دهنده ارسال کند.

## سینتکس

```js-nolint
send(data)
```

### پارامترها

- `data`
  - : داده‌ای که به زمینهٔ ارائه ارسال می‌شود. این داده یکی از موارد زیر خواهد بود:
    - {{jsxref("String")}}
    - {{domxref("Blob")}}
    - {{jsxref("Array")}}

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}