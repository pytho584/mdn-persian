---
title: "MIDIAccess: outputs property"
short-title: outputs
slug: Web/API/MIDIAccess/outputs
page-type: web-api-instance-property
browser-compat: api.MIDIAccess.outputs
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

ویژگی فقط‌خواندنی **`outputs`** از رابط {{domxref("MIDIAccess")}} دسترسی به هر پورت خروجی MIDI موجود را فراهم می‌کند.

## مقدار

یک نمونه از {{domxref("MIDIOutputMap")}}.

## مثال‌ها

متد {{domxref("Navigator.requestMIDIAccess()")}} یک promise برمی‌گرداند که با یک شیء {{domxref("MIDIAccess")}} resolved می‌شود. چاپ مقدار `outputs` در کنسول یک {{domxref("MIDIOutputMap")}} برمی‌گرداند.

```js
navigator.requestMIDIAccess().then((access) => {
  console.log(access.outputs);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}