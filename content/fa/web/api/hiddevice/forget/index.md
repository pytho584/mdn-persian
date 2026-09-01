---
title: "HIDDevice: forget() method"
short-title: forget()
slug: Web/API/HIDDevice/forget
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.HIDDevice.forget
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

متد **`forget()`** از رابط {{domxref("HIDDevice")}} اتصال به دستگاه HID را می‌بندد و دستگاه را فراموش می‌کند.

## Syntax

```js-nolint
forget()
```

### Parameters

هیچ‌کدام.

### Return value

یک {{jsxref("Promise")}} که پس از بسته‌شدن اتصال، فراموش‌شدن دستگاه و بازنشانی مجوز، با مقدار `undefined` حل می‌شود.

## Example

در مثال زیر به یک دستگاه HID Joy-Con راست نینتندو سوییچ متصل می‌شویم، یک بار چشمک می‌زنیم و از آن جدا می‌شویم.

```js
async function blink() {
  const devices = await navigator.hid.requestDevice({
    filters: [
      {
        vendorId: 0x057e, // Nintendo Co., Ltd
        productId: 0x2007, // Joy-Con Right
      },
    ],
  });
  const device = devices[0];
  await device.open();
  // Turn off
  await device.sendFeatureReport(reportId, Uint32Array.from([0, 0]));
  await new Promise((resolve) => setTimeout(resolve, 100));
  // Turn on
  await device.sendFeatureReport(reportId, Uint32Array.from([512, 0]));
  await new Promise((resolve) => setTimeout(resolve, 100));
  // Finally, disconnect from it
  await device.forget();
}
blink();
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}