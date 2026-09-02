---
title: "MIDIPort: close() method"
short-title: close()
slug: Web/API/MIDIPort/close
page-type: web-api-instance-method
browser-compat: api.MIDIPort.close
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

متد **`close()`** در رابط {{domxref("MIDIPort")}} دسترسی به دستگاه MIDI متصل به این `MIDIPort` را غیرفعال می‌کند.

اگر پورت با موفقیت بسته شود، یک {{domxref("MIDIConnectionEvent")}} جدید برای رویدادهای {{domxref("MIDIPort.statechange_event", "statechange")}} مربوط به `MIDIPort` و {{domxref("MIDIAccess.statechange_event", "statechange")}} مربوط به `MIDIAccess` در صف قرار می‌گیرد و ویژگی {{domxref("MIDIPort.connection")}} به `"closed"` تغییر می‌کند.

## نحو (Syntax)

```js-nolint
close()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} برمی‌گرداند که پس از بسته شدن پورت resolved می‌شود.

## مثال‌ها

مثال زیر بسته شدن یک پورت خروجی را نشان می‌دهد.

```js
let output = midiAccess.outputs.get(portID);
output.close(); // closes the port
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}