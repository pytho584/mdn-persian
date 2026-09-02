---
title: "MIDIPort"
---

---
title: MIDIPort
slug: Web/API/MIDIPort
page-type: web-api-interface
browser-compat: api.MIDIPort
---

{{securecontext_header}}{{APIRef("Web MIDI API")}}

رابط **`MIDIPort`** در {{domxref('Web MIDI API','','',' ')}} یک درگاه ورودی یا خروجی MIDI را نمایش می‌دهد.

یک نمونه از `MIDIPort` زمانی ساخته می‌شود که یک دستگاه MIDI جدید متصل شود. بنابراین این رابط سازنده (constructor) ندارد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("MIDIPort.id")}} {{ReadOnlyInline}}
  - : رشته‌ای شامل شناسه یکتای درگاه را برمی‌گرداند.
- {{domxref("MIDIPort.manufacturer")}} {{ReadOnlyInline}}
  - : رشته‌ای شامل نام تولیدکننده درگاه را برمی‌گرداند.
- {{domxref("MIDIPort.name")}} {{ReadOnlyInline}}
  - : رشته‌ای شامل نام سیستمی درگاه را برمی‌گرداند.
- {{domxref("MIDIPort.type")}} {{ReadOnlyInline}}
  - : رشته‌ای شامل نوع درگاه را برمی‌گرداند که یکی از این مقادیر است:
    - `"input"`
      - : این `MIDIPort` یک درگاه ورودی است.
    - `"output"`
      - : این `MIDIPort` یک درگاه خروجی است.

- {{domxref("MIDIPort.version")}} {{ReadOnlyInline}}
  - : رشته‌ای شامل نسخه درگاه را برمی‌گرداند.
- {{domxref("MIDIPort.state")}} {{ReadOnlyInline}}
  - : رشته‌ای شامل وضعیت درگاه را برمی‌گرداند که یکی از این مقادیر است:
    - `"disconnected"`
      - : دستگاهی که این `MIDIPort` نمایش می‌دهد از سیستم قطع شده است.
    - `"connected"`
      - : دستگاهی که این `MIDIPort` نمایش می‌دهد در حال حاضر متصل است.

- {{domxref("MIDIPort.connection")}} {{ReadOnlyInline}}
  - : رشته‌ای شامل وضعیت اتصال درگاه را برمی‌گرداند که یکی از این مقادیر است:
    - `"open"`
      - : دستگاهی که این `MIDIPort` نمایش می‌دهد باز شده و در دسترس است.
    - `"closed"`
      - : دستگاهی که این `MIDIPort` نمایش می‌دهد باز نشده است یا بسته شده است.
    - `"pending"`
      - : دستگاهی که این `MIDIPort` نمایش می‌دهد باز شده است اما پس از آن قطع شده است.

## روش‌های نمونه

_این رابط همچنین روش‌هایی را از {{domxref("EventTarget")}} به ارث می‌برد._

- {{domxref("MIDIPort.open()")}}
  - : دستگاه MIDI متصل به این `MIDIPort` را به‌صورت صریح در دسترس قرار می‌دهد و یک {{jsxref("Promise")}} برمی‌گرداند که پس از موفقیت‌آمیز بودن دسترسی به درگاه حل می‌شود.
- {{domxref("MIDIPort.close()")}}
  - : دستگاه MIDI متصل به این `MIDIPort` را در دسترس‌ناپذیر می‌کند و {{domxref("MIDIPort.state","state")}} را از `"open"` به `"closed"` تغییر می‌دهد. این کار یک {{jsxref("Promise")}} برمی‌گرداند که پس از بسته شدن درگاه حل می‌شود.

## رویدادها

- {{domxref("MIDIPort.statechange_event", "statechange")}}
  - : زمانی فراخوانی می‌شود که یک درگاه موجود وضعیت یا اتصال خود را تغییر دهد.

## مثال‌ها

### فهرست کردن درگاه‌ها و اطلاعات آن‌ها

مثال زیر درگاه‌های ورودی و خروجی را فهرست می‌کند و اطلاعاتی درباره آن‌ها را با استفاده از ویژگی‌های `MIDIPort` نمایش می‌دهد.

```js
function listInputsAndOutputs(midiAccess) {
  for (const entry of midiAccess.inputs) {
    const input = entry[1];
    console.log(
      `Input port [type:'${input.type}'] id:'${input.id}' manufacturer: '${input.manufacturer}' name: '${input.name}' version: '${input.version}'`,
    );
  }

  for (const entry of midiAccess.outputs) {
    const output = entry[1];
    console.log(
      `Output port [type:'${output.type}'] id: '${output.id}' manufacturer: '${output.manufacturer}' name: '${output.name}' version: '${output.version}'`,
    );
  }
}
```

### افزودن درگاه‌های موجود به یک فهرست انتخابی

مثال زیر فهرست درگاه‌های ورودی را گرفته و آن‌ها را به یک فهرست انتخابی (select) اضافه می‌کند تا کاربر بتواند دستگاهی را که می‌خواهد استفاده کند انتخاب نماید.

```js
inputs.forEach((port, key) => {
  const opt = document.createElement("option");
  opt.text = port.name;
  document.getElementById("port-selector").add(opt);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}