---
title: "MIDIOutput: send() method"
short-title: send()
slug: Web/API/MIDIOutput/send
page-type: web-api-instance-method
browser-compat: api.MIDIOutput.send
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

متد **`send()`** از رابط {{domxref("MIDIOutput")}} پیام‌ها را برای پورت MIDI مربوطه در صف قرار می‌دهد. پیام می‌تواند بلافاصله ارسال شود، یا با یک برچسب زمانی (timestamp) اختیاری، ارسال آن به تعویق بیفتد.

## نحو

```js-nolint
send(data)
send(data, timestamp)
```

### پارامترها

- `data`
  - : یک دنباله از یک یا چند [پیام معتبر MIDI](https://midi.org/about-midi-part-3midi-messages). هر ورودی نمایانگر یک بایت واحد از داده است.
- `timestamp` {{optional_inline}}
  - : یک {{domxref("DOMHighResTimestamp")}} شامل زمان بر حسب میلی‌ثانیه که پیام باید در آن زمان ارسال شود (نسبت به {{domxref("Performance.timeOrigin")}}).

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها

- {{jsxref("TypeError")}}
  - : اگر `data` یک دنبالهٔ معتبر نباشد یا شامل یک پیام MIDI معتبر نباشد، پرتاب می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر `data` یک پیام System Exclusive باشد و {{domxref("MIDIAccess")}} دسترسی انحصاری (exclusive access) را فعال نکرده باشد، پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر پورت قطع شده باشد، پرتاب می‌شود.

## مثال‌ها

در مثال زیر، یک نت C میانی (middle C) بلافاصله ارسال می‌شود و سپس یک پیام خاموشی نت (note off) یک ثانیه بعد ارسال می‌شود.

```js
function sendMiddleC(midiAccess, portID) {
  const noteOnMessage = [0x90, 60, 0x7f]; // Note on middle C, full velocity
  const output = midiAccess.outputs.get(portID);
  output.send(noteOnMessage); // Omitting the timestamp means send immediately.
  output.send([0x80, 60, 0x40], window.performance.now() + 1000.0); // timestamp = now + 1000ms.
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}