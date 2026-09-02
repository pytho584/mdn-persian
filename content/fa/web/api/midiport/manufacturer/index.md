---
title: "MIDIPort: manufacturer property"
short-title: manufacturer
slug: Web/API/MIDIPort/manufacturer
page-type: web-api-instance-property
browser-compat: api.MIDIPort.manufacturer
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

ویژگی فقط‌خواندنی `manufacturer` از رابط {{domxref("MIDIPort")}}، نام سازندهٔ پورت را برمی‌گرداند.

## مقدار

یک رشته که نام سازندهٔ پورت را در خود دارد.

## مثال‌ها

مثال زیر روی همهٔ پورت‌های ورودی حلقه می‌زند و نام سازندهٔ هرکدام را در کنسول چاپ می‌کند.

```js
for (const entry of midiAccess.inputs) {
  const input = entry[1];
  console.log(input.manufacturer);
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}