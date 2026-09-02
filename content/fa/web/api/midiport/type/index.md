---
title: "MIDIPort: type property"
short-title: type
slug: Web/API/MIDIPort/type
page-type: web-api-instance-property
browser-compat: api.MIDIPort.type
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

ویژگی فقط‌خواندنی **`type`** در رابط {{domxref("MIDIPort")}} نوع پورت را برمی‌گرداند و مشخص می‌کند که این پورت، یک پورت ورودی یا خروجی MIDI است.

## مقدار

رشته‌ای که نوع پورت را مشخص می‌کند، یکی از موارد زیر:

- `"input"`
  - : «MIDIPort» یک پورت ورودی است.
- `"output"`
  - : «MIDIPort» یک پورت خروجی است.

## مثال‌ها

مثال زیر روی همه پورت‌های ورودی حلقه می‌زند و `type` هر یک را در کنسول چاپ می‌کند.

```js
for (const entry of midiAccess.inputs) {
  const input = entry[1];
  console.log(input.type); // should always be input
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}