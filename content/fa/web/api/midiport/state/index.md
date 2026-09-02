---
title: "MIDIPort: state property"
---

---
title: "MIDIPort: state property"
short-title: state
slug: Web/API/MIDIPort/state
page-type: web-api-instance-property
browser-compat: api.MIDIPort.state
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

ویژگی فقط‌خواندنی **`state`** از رابط {{domxref("MIDIPort")}}، وضعیت پورت را بازمی‌گرداند.

## Value

یک رشته (string) شامل وضعیت پورت، که یکی از این مقادیر است:

- `"disconnected"`
  - : دستگاهی که این `MIDIPort` معرف آن است، از سیستم قطع شده است.
- `"connected"`
  - : دستگاهی که این `MIDIPort` معرف آن است، در حال حاضر متصل است.

## Examples

مثال زیر همه‌ی پورت‌های ورودی را پیمایش می‌کند و وضعیت هر یک را در کنسول چاپ می‌کند.

```js
for (const entry of midiAccess.inputs) {
  const input = entry[1];
  console.log(input.state);
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}