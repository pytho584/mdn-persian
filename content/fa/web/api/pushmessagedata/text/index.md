---
title: "PushMessageData: text() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/PushMessageData/text"
status: "needs-translation"
---

---
title: "PushMessageData: text() method"
short-title: text()
slug: Web/API/PushMessageData/text
page-type: web-api-instance-method
browser-compat: api.PushMessageData.text
---

{{APIRef("Push API")}}{{SecureContext_Header}}{{AvailableInWorkers("service")}}

The **`text()`** method of the {{domxref("PushMessageData")}} interface extracts push message data as a plain text string.

## Syntax

```js-nolint
text()
```

### Parameters

None.

### Return value

A string.

## Examples

```js
self.addEventListener("push", (event) => {
  const textObj = event.data.text();

  // do something with your text
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
