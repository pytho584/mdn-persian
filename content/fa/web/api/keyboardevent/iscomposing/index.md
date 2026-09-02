---
title: "KeyboardEvent: isComposing property"
short-title: isComposing
slug: Web/API/KeyboardEvent/isComposing
page-type: web-api-instance-property
browser-compat: api.KeyboardEvent.isComposing
---

{{APIRef("UI Events")}}

ویژگی فقطخواندنی **`KeyboardEvent.isComposing`** یک مقدار بولین برمی‌گرداند که نشان می‌دهد آیا رویداد در یک نشستِ ترکیب (composition session) رخ داده است؛ یعنی پس از {{domxref("Element/compositionstart_event", "compositionstart")}} و پیش از {{domxref("Element/compositionend_event", "compositionend")}}.

## مقدار

یک مقدار بولین.

## مثال‌ها

```js
const kbdEvent = new KeyboardEvent("syntheticKey", false);
console.log(kbdEvent.isComposing); // return false
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element/compositionstart_event", "compositionstart")}} و {{domxref("Element/compositionend_event", "compositionend")}}
- {{domxref("KeyboardEvent")}}