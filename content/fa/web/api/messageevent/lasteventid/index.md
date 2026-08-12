---
title: "MessageEvent: lastEventId property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/MessageEvent/lastEventId"
status: "needs-translation"
---

---
title: "MessageEvent: lastEventId property"
short-title: lastEventId
slug: Web/API/MessageEvent/lastEventId
page-type: web-api-instance-property
browser-compat: api.MessageEvent.lastEventId
---

{{APIRef("HTML DOM")}}{{AvailableInWorkers}}

The **`lastEventId`** read-only property of the
{{domxref("MessageEvent")}} interface is a string representing a
unique ID for the event.

## Value

A string representing the ID.

## Examples

```js
myWorker.onmessage = (e) => {
  result.textContent = e.data;
  console.log("Message received from worker");
  console.log(e.lastEventId);
};
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("ExtendableMessageEvent")}} — similar to this interface but used in
  interfaces that needs to give more flexibility to authors.
