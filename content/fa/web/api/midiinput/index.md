---
title: MIDIInput
slug: Web/API/MIDIInput
page-type: web-api-interface
browser-compat: api.MIDIInput
---

{{APIRef("Web MIDI API")}}{{securecontext_header}}

رابط **`MIDIInput`** در [Web MIDI API](/en-US/docs/Web/API/Web_MIDI_API) پیام‌ها را از یک درگاه ورودی MIDI دریافت می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این رابط هیچ ویژگی خاصی را پیاده‌سازی نمی‌کند، اما ویژگی‌هایی را از {{domxref("MIDIPort")}} به ارث می‌برد._

## روش‌های نمونه

_این رابط هیچ روش خاصی را پیاده‌سازی نمی‌کند، اما روش‌هایی را از {{domxref("MIDIPort")}} به ارث می‌برد._

### رویدادها

- {{domxref("MIDIInput.midimessage_event", "midimessage")}}
  - : زمانی که درگاه فعلی یک پیام MIDI دریافت می‌کند، رخ می‌دهد.

## مثال‌ها

در مثال زیر، نام هر `MIDIInput` در کنسول چاپ می‌شود. سپس، رویدادهای `midimessage` در همه درگاه‌های ورودی شنیده می‌شوند. هنگامی که پیامی دریافت می‌شود، ویژگی {{domxref("MIDIMessageEvent.data")}} در کنسول چاپ می‌شود.

```js
inputs.forEach((input) => {
  console.log(input.name); /* ویژگی به‌ارث‌برده از MIDIPort */
  input.onmidimessage = (message) => {
    console.log(message.data);
  };
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}