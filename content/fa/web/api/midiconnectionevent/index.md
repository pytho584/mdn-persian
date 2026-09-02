---
title: MIDIConnectionEvent
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

رابط **`MIDIConnectionEvent`** در [Web MIDI API](/en-US/docs/Web/API/Web_MIDI_API) رویدادی است که به رویداد {{domxref("MIDIAccess.statechange_event","statechange")}} در رابط {{domxref("MIDIAccess")}} و رویداد {{domxref("MIDIPort.statechange_event","statechange")}} در رابط {{domxref("MIDIPort")}} ارسال می‌شود. این رویداد هر بار که یک پورت جدید در دسترس قرار می‌گیرد یا پورتی که قبلاً در دسترس بوده از دسترس خارج می‌شود، رخ می‌دهد. به عنوان مثال، این رویداد هر بار که یک دستگاه MIDI به رایانه متصل یا از آن جدا می‌شود، فعال می‌گردد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("MIDIConnectionEvent.MIDIConnectionEvent", "MIDIConnectionEvent()")}}
  - : یک شیء جدید `MIDIConnectionEvent` می‌سازد.

## ویژگی‌های نمونه

- {{domxref("MIDIConnectionEvent.port")}} {{ReadOnlyInline}}
  - : ارجاعی به یک نمونه {{domxref("MIDIPort")}} برای پورتی که متصل یا قطع شده است را برمی‌گرداند.

## مثال‌ها

متد {{domxref("Navigator.requestMIDIAccess()")}} یک وعده (Promise) برمی‌گرداند که با یک شیء {{domxref("MIDIAccess")}} حل می‌شود. وقتی وضعیت یک پورت تغییر می‌کند، یک `MIDIConnectionEvent` به رویداد {{domxref("MIDIAccess.statechange_event", "statechange")}} ارسال می‌شود. سپس می‌توان اطلاعات مربوط به پورت را در کنسول چاپ کرد.

```js
navigator.requestMIDIAccess().then((access) => {
  access.onstatechange = (event) => {
    console.log(event.port.name, event.port.manufacturer, event.port.state);
  };
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}