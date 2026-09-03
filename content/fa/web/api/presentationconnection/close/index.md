---
title: "PresentationConnection: close() method"
short-title: close()
slug: Web/API/PresentationConnection/close
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PresentationConnection.close
---

{{APIRef("Presentation API")}}{{SeeCompatTable}}{{SecureContext_Header}}

هنگامی که متد `close()` روی یک {{domxref("PresentationConnection")}} فراخوانی میشود، {{Glossary("user agent")}} فرایند بستن اتصال را با ارسال یک `closeMessage` خالی که در آن `closeReason` برابر با `closed` تنظیم شده است، آغاز میکند.

## Syntax

```js-nolint
close()
```

### Parameters

بدون پارامتر.

### Return value

هیچ ({{jsxref("undefined")}}).

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}