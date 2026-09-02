---
title: "MIDIPort: connection property"
short-title: connection
slug: Web/API/MIDIPort/connection
page-type: web-api-instance-property
browser-compat: api.MIDIPort.connection
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

ویژگی فقط‌خواندنی **`connection`** در رابط {{domxref("MIDIPort")}} وضعیت اتصال پورت را برمی‌گرداند.

## مقدار

رشته‌ای که وضعیت اتصال پورت را نشان می‌دهد، یکی از موارد زیر:

- `"open"`
  - : دستگاهی که این `MIDIPort` نشان می‌دهد باز شده و در دسترس است.
- `"closed"`
  - : دستگاهی که این `MIDIPort` نشان می‌دهد باز نشده است، یا بسته شده است.
- `"pending"`
  - : دستگاهی که این `MIDIPort` نشان می‌دهد باز شده اما پس از آن قطع شده است.

## مثال‌ها

مثال زیر روی همه پورت‌های ورودی حلقه می‌زند و وضعیت اتصال هر یک را در کنسول چاپ می‌کند.

```js
for (const entry of midiAccess.inputs) {
  const input = entry[1];
  console.log(input.connection);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}