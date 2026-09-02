---
title: "InputEvent: isComposing property"
short-title: isComposing
slug: Web/API/InputEvent/isComposing
page-type: web-api-instance-property
browser-compat: api.InputEvent.isComposing
---

{{APIRef("UI Events")}}

خاصیت فقط خواندنی **`InputEvent.isComposing`** یک مقدار بولین (boolean) برمی‌گرداند که نشان می‌دهد آیا رویداد پس از {{domxref("Element/compositionstart_event", "compositionstart")}} و پیش از {{domxref("Element/compositionend_event", "compositionend")}} فعال شده است یا خیر.

## مقدار

یک بولین.

## مثال‌ها

```js
const inputEvent = new InputEvent("syntheticInput", false);
console.log(inputEvent.isComposing); // return false
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("Element/compositionstart_event", "compositionstart")}} و {{domxref("Element/compositionend_event", "compositionend")}}
- {{domxref("InputEvent")}}