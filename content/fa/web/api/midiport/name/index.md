---
title: "MIDIPort: name property"
short-title: name
slug: Web/API/MIDIPort/name
page-type: web-api-instance-property
browser-compat: api.MIDIPort.name
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

ویژگی فقط‌خواندنی **`name`** در رابط {{domxref("MIDIPort")}} نام سیستمی درگاه را بازمی‌گرداند.

## مقدار

رشته‌ای که نام سیستمی درگاه را شامل می‌شود.

## مثال‌ها

مثال زیر در همهٔ درگاه‌های ورودی گردش می‌کند و نام هر یک را در کنسول چاپ می‌کند.

```js
for (const entry of midiAccess.inputs) {
  const input = entry[1];
  console.log(input.name);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}