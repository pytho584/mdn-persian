---
title: "MIDIAccess"
---

---
title: MIDIAccess
slug: Web/API/MIDIAccess
page-type: web-api-interface
browser-compat: api.MIDIAccess
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

رابط **`MIDIAccess`** در [Web MIDI API](/en-US/docs/Web/API/Web_MIDI_API) روش‌هایی برای فهرست‌کردن دستگاه‌های ورودی و خروجی MIDI و دسترسی به آن دستگاه‌ها فراهم می‌کند.

`MIDIAccess` یک [شیء قابل انتقال](/en-US/docs/Web/API/Web_Workers_API/Transferable_objects) است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("MIDIAccess.inputs")}} {{ReadOnlyInline}}
  - : یک نمونه از {{domxref("MIDIInputMap")}} برمی‌گرداند که دسترسی به هر پورت ورودی MIDI موجود را فراهم می‌کند.
- {{domxref("MIDIAccess.outputs")}} {{ReadOnlyInline}}
  - : یک نمونه از {{domxref("MIDIOutputMap")}} برمی‌گرداند که دسترسی به هر پورت خروجی MIDI موجود را فراهم می‌کند.
- {{domxref("MIDIAccess.sysexEnabled")}} {{ReadOnlyInline}}
  - : یک ویژگی بولی که نشان می‌دهد آیا پشتیبانی از System Exclusive در نمونه فعلی `MIDIAccess` فعال است یا خیر.

### رویدادها

- {{domxref("MIDIAccess.statechange_event", "statechange")}}
  - : هر زمان که یک پورت MIDI جدید اضافه شود یا پورت موجود تغییر وضعیت دهد، فراخوانی می‌شود.

## مثال‌ها

روش {{domxref("Navigator.requestMIDIAccess()")}} یک وعده (Promise) برمی‌گرداند که با یک شیء `MIDIAccess` حل می‌شود. اطلاعات مربوط به پورت‌های ورودی و خروجی بازگردانده می‌شود.

هنگامی که وضعیت یک پورت تغییر می‌کند، اطلاعات مربوط به آن پورت در کنسول چاپ می‌شود.

```js
navigator.requestMIDIAccess().then((access) => {
  // Get lists of available MIDI controllers
  const inputs = access.inputs.values();
  const outputs = access.outputs.values();

  access.onstatechange = (event) => {
    // Print information about the (dis)connected MIDI controller
    console.log(event.port.name, event.port.manufacturer, event.port.state);
  };
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}