---
title: MIDIMessageEvent
slug: Web/API/MIDIMessageEvent
page-type: web-api-interface
browser-compat: api.MIDIMessageEvent
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

**`MIDIMessageEvent`** رابط интерфейс [Web MIDI API](/en-US/docs/Web/API/Web_MIDI_API) است که رویداد ارسال‌شده به رویداد {{domxref("MIDIInput.midimessage_event","midimessage")}} از رابط {{domxref("MIDIInput")}} را نشان می‌دهد. یک رویداد `midimessage` هر بار که یک پیام MIDI از دستگاهی که توسط {{domxref("MIDIInput")}} نمایش داده می‌شود ارسال می‌گردد، فعال می‌شود؛ به عنوان مثال وقتی کلیدی از صفحه‌کلید MIDI فشرده می‌شود، یک دستگیره چرخانده می‌شود، یا یک لغزاننده جابه‌جا می‌شود.

{{InheritanceDiagram}}

## سازنده

- {{domxref("MIDIMessageEvent.MIDIMessageEvent", "MIDIMessageEvent()")}}
  - : یک نمونهٔ جدید از شیء `MIDIMessageEvent` ایجاد می‌کند.

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌های {{domxref("Event")}} را به ارث می‌برد._

- {{domxref("MIDIMessageEvent.data")}}
  - : یک {{jsxref("Uint8Array")}} شامل بایت‌های داده یک پیام MIDI واحد. برای اطلاعات بیشتر درباره شکل آن، به [مشخصات MIDI](https://midi.org/summary-of-midi-1-0-messages) مراجعه کنید.

## روش‌های نمونه

_این رابط هیچ روش خاصی را پیاده‌سازی نمی‌کند، اما روش‌های {{domxref("Event")}} را به ارث می‌برد._

## مثال‌ها

مثال زیر تمام پیام‌های MIDI را در کنسول چاپ می‌کند.

```js
navigator.requestMIDIAccess().then((midiAccess) => {
  Array.from(midiAccess.inputs).forEach((input) => {
    input[1].onmidimessage = (msg) => {
      console.log(msg);
    };
  });
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
