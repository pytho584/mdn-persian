---
title: "MIDIPort: open() method"
short-title: open()
slug: Web/API/MIDIPort/open
page-type: web-api-instance-method
browser-compat: api.MIDIPort.open
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

متد **`open()`** از رابط {{domxref("MIDIPort")}}، دسترسی صریح به دستگاه MIDI متصل به این `MIDIPort` را فراهم می‌کند.

اگر پورت با موفقیت باز شود، یک {{domxref("MIDIConnectionEvent")}} جدید در صف رویدادهای `MIDIPort` از نوع {{domxref("MIDIPort.statechange_event", "statechange")}} و `MIDIAccess` از نوع {{domxref("MIDIAccess.statechange_event", "statechange")}} قرار می‌گیرد و ویژگی {{domxref("MIDIPort.connection")}} به `"open"` تغییر می‌کند.

اگر هنگام فراخوانی این متد، پورت از قبل باز باشد، Promise بازگردانده‌شده با موفقیت resolve خواهد شد.

## سینتکس

```js-nolint
open()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که پس از دریافت موفقیت‌آمیز دسترسی به پورت resolve می‌شود.

### استثناها

- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر پورت در دسترس نباشد و نتوان آن را باز کرد، Promise بازگردانده‌شده با این خطا رد می‌شود.

## مثال‌ها

مثال زیر باز شدن یک پورت خروجی را نشان می‌دهد.

```js
const output = midiAccess.outputs.get(portID);
output.open(); // opens the port
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}