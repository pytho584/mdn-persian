---
title: "MIDIAccess: inputs property"
short-title: inputs
slug: Web/API/MIDIAccess/inputs
page-type: web-api-instance-property
browser-compat: api.MIDIAccess.inputs
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

ویژگی فقط‌خواندنی **`inputs`** در رابط {{domxref("MIDIAccess")}} دسترسی به هر درگاه ورودی MIDI موجود را فراهم می‌کند.

## مقدار

یک نمونه از {{domxref("MIDIInputMap")}}.

## مثال‌ها

متد {{domxref("Navigator.requestMIDIAccess()")}} یک promise برمی‌گرداند که با یک شیء {{domxref("MIDIAccess")}} resolve می‌شود. چاپ مقدار `inputs` در کنسول، یک {{domxref("MIDIInputMap")}} را برمی‌گرداند.

```js
navigator.requestMIDIAccess().then((access) => {
  console.log(access.inputs);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
