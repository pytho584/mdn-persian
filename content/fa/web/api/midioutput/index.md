---
title: MIDIOutput
slug: Web/API/MIDIOutput
page-type: web-api-interface
browser-compat: api.MIDIOutput
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

رابط **`MIDIOutput`** در {{domxref('Web MIDI API','','',' ')}} متدهایی برای افزودن پیام به صف یک دستگاه خروجی و پاک کردن صف پیام‌ها فراهم می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این رابط ویژگی خاصی را پیاده‌سازی نمی‌کند، اما ویژگی‌های {{domxref("MIDIPort")}} را به ارث می‌برد._

## متدهای نمونه

_این رابط همچنین متدهای {{domxref("MIDIPort")}} را به ارث می‌برد._

- {{domxref("MIDIOutput.send()")}}
  - : یک پیام را برای ارسال به پورت MIDI در صف قرار می‌دهد.
- {{domxref("MIDIOutput.clear()")}}
  - : هر داده ارسالی در انتظار را از صف پاک می‌کند.

## مثال‌ها

مثال زیر یک نت C میانی را بلافاصله در کانال MIDI 1 ارسال می‌کند.

```js
function sendMiddleC(midiAccess, portID) {
  const noteOnMessage = [0x90, 60, 0x7f]; // note on, middle C, full velocity
  const output = midiAccess.outputs.get(portID);
  output.send(noteOnMessage); // sends the message.
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}
