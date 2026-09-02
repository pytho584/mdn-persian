---
title: "MIDIPort: id property"
short-title: id
slug: Web/API/MIDIPort/id
page-type: web-api-instance-property
browser-compat: api.MIDIPort.id
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

ویژگی فقط‌خواندنی **`id`** در رابط {{domxref("MIDIPort")}} شناسه یکتای پورت را برمی‌گرداند.

## مقدار

رشته‌ای (string) شامل شناسه پورت.

## مثال‌ها

مثال زیر در تمام پورت‌های ورودی حلقه می‌زند و شناسه هر یک را در کنسول چاپ می‌کند.

```js
for (const entry of midiAccess.inputs) {
  const input = entry[1];
  console.log(input.id);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}