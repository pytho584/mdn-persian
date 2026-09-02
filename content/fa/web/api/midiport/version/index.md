---
title: "MIDIPort: version property"
short-title: version
slug: Web/API/MIDIPort/version
page-type: web-api-instance-property
browser-compat: api.MIDIPort.version
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

ویژگی فقطخواندنی **`version`** در رابط {{domxref("MIDIPort")}} نسخهٔ پورت را برمی‌گرداند.

## مقدار

یک رشته که نسخهٔ پورت را در بر دارد.

## مثال‌ها

مثال زیر روی همهٔ پورت‌های ورودی حلقه می‌زند و نسخهٔ هر یک را در کنسول چاپ می‌کند.

```js
for (const entry of midiAccess.inputs) {
  const input = entry[1];
  console.log(input.version);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}