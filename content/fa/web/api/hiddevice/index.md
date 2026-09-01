---
title: "HIDDevice"
---

---
title: HIDDevice
slug: Web/API/HIDDevice
page-type: web-api-interface
status:
  - experimental
browser-compat: api.HIDDevice
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

رابط **`HIDDevice`** از [WebHID API](/en-US/docs/Web/API/WebHID_API) یک دستگاه HID را نمایش می‌دهد. این رابط ویژگی‌هایی برای دسترسی به اطلاعات دستگاه، روش‌هایی برای باز و بسته کردن اتصال، و همچنین ارسال و دریافت گزارش‌ها فراهم می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

این رابط همچنین ویژگی‌های {{domxref("EventTarget")}} را به ارث می‌برد.

- {{domxref("HIDDevice.opened")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{jsxref("Boolean")}} برمی‌گرداند که در صورت باز بودن اتصال دستگاه، مقدار آن `true` است.
- {{domxref("HIDDevice.vendorId")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : مقدار `vendorId` دستگاه HID را برمی‌گرداند.
- {{domxref("HIDDevice.productId")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : مقدار `productId` دستگاه HID را برمی‌گرداند.
- {{domxref("HIDDevice.productName")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : رشته‌ای شامل نام محصول دستگاه HID را برمی‌گرداند.
- {{domxref("HIDDevice.collections")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : آرایه‌ای از قالب‌های گزارش (report formats) برای دستگاه HID را برمی‌گرداند.

### رویدادها

- {{domxref("HIDDevice.inputreport_event", "inputreport")}} {{Experimental_Inline}}
  - : هنگامی که گزارشی از دستگاه ارسال می‌شود، این رویداد فعال می‌شود.

## روش‌های نمونه

این رابط همچنین روش‌های {{domxref("EventTarget")}} را به ارث می‌برد.

- {{domxref("HIDDevice.open()")}} {{Experimental_Inline}}
  - : اتصالی به این دستگاه HID باز می‌کند و یک {{jsxref("Promise")}} برمی‌گرداند که پس از موفقیت‌آمیز بودن اتصال حل می‌شود.
- {{domxref("HIDDevice.close()")}} {{Experimental_Inline}}
  - : اتصال به این دستگاه HID را می‌بندد و یک {{jsxref("Promise")}} برمی‌گرداند که پس از بسته شدن اتصال حل می‌شود.
- {{domxref("HIDDevice.forget()")}} {{Experimental_Inline}}
  - : اتصال به این دستگاه HID را می‌بندد و مجوز دسترسی را بازنشانی می‌کند و یک {{jsxref("Promise")}} برمی‌گرداند که پس از بازنشانی مجوز حل می‌شود.
- {{domxref("HIDDevice.sendReport()")}} {{Experimental_Inline}}
  - : یک گزارش خروجی به این دستگاه HID می‌فرستد و یک {{jsxref("Promise")}} برمی‌گرداند که پس از ارسال گزارش حل می‌شود.
- {{domxref("HIDDevice.sendFeatureReport()")}} {{Experimental_Inline}}
  - : یک گزارش ویژگی (feature report) به این دستگاه HID می‌فرستد و یک {{jsxref("Promise")}} برمی‌گرداند که پس از ارسال گزارش حل می‌شود.
- {{domxref("HIDDevice.receiveFeatureReport()")}} {{Experimental_Inline}}
  - : یک گزارش ویژگی از این دستگاه HID دریافت می‌کند و آن را به صورت یک {{jsxref("Promise")}} برمی‌گرداند که با یک {{jsxref("DataView")}} حل می‌شود. این کار امکان دسترسی نوع‌دار (typed) به محتوای این پیام را فراهم می‌کند.

## مثال‌ها

مثال زیر نحوه گوش دادن به رویداد `inputreport` را نشان می‌دهد که به برنامه امکان می‌دهد تشخیص دهد کدام دکمه روی دستگاه Joy-Con Right فشرده شده است.

```js
device.addEventListener("inputreport", (event) => {
  const { data, device, reportId } = event;

  // Handle only the Joy-Con Right device and a specific report ID.
  if (device.productId !== 0x2007 && reportId !== 0x3f) return;

  const value = data.getUint8(0);
  if (value === 0) return;

  const someButtons = { 1: "A", 2: "X", 4: "B", 8: "Y" };
  console.log(`User pressed button ${someButtons[value]}.`);
});
```

در مثال زیر از `sendFeatureReport` برای چشمک زدن یک دستگاه استفاده شده است.

```js
const reportId = 1;
for (let i = 0; i < 10; i++) {
  // Turn off
  await device.sendFeatureReport(reportId, Uint32Array.from([0, 0]));
  await new Promise((resolve) => setTimeout(resolve, 100));
  // Turn on
  await device.sendFeatureReport(reportId, Uint32Array.from([512, 0]));
  await new Promise((resolve) => setTimeout(resolve, 100));
}
```

نمونه‌های بیشتر و نسخه‌های نمایشی زنده را می‌توانید در مقاله [Connecting to uncommon HID devices](https://developer.chrome.com/docs/capabilities/hid) ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}