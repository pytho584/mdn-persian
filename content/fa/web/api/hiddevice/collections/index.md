---
title: "HIDDevice: collections property"
---

---
title: "HIDDevice: collections property"
short-title: collections
slug: Web/API/HIDDevice/collections
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HIDDevice.collections
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

ویژگی فقط‌خواندنی **`collections`** در رابط {{domxref("HIDDevice")}} آرایه‌ای از قالب‌های گزارش را برمی‌گرداند.

## مقدار

آرایه‌ای از قالب‌های گزارش. هر ورودی شامل موارد زیر است:

- `usagePage`
  - : یک عدد صحیح که مؤلفهٔ Usage Page از کاربرد HID مرتبط با این مجموعه را نشان می‌دهد. کاربرد (Usage) برای یک مجموعهٔ سطح بالا برای شناسایی نوع دستگاه استفاده می‌شود.

    مقادیر استاندارد کاربرد HID را می‌توانید در سند [HID Usage Tables](https://usb.org/document-library/hid-usage-tables-17) بیابید.

- `usage`
  - : عددی صحیح که مؤلفهٔ Usage ID از کاربرد HID مرتبط با این مجموعه را نشان می‌دهد.
- `type`
  - : یک مقدار ۸ بیتی که نوع مجموعه را نشان می‌دهد و رابطهٔ متفاوتی را بین موارد گروه‌بندی‌شده توصیف می‌کند. یکی از مقادیر زیر:
    - `0x00`
      - : فیزیکی (گروه محورها)
    - `0x01`
      - : کاربردی (ماوس، صفحه‌کلید)
    - `0x02`
      - : منطقی (داده‌های مرتبط با یکدیگر)
    - `0x03`
      - : گزارش (Report)
    - `0x04`
      - : آرایهٔ نام‌گذاری‌شده (Named array)
    - `0x05`
      - : تغییردهندهٔ کاربرد (Usage switch)
    - `0x06`
      - : کاربرد اصلاح‌شده (Usage modified)
    - `0x07` تا `0x7F`
      - : برای استفاده در آینده رزرو شده است
    - `0x80` تا `0xFF`
      - : تعریف‌شده توسط فروشنده

    اطلاعات بیشتر دربارهٔ این انواع را می‌توانید در سند [Device Class Definition](https://www.usb.org/document-library/device-class-definition-hid-111) بیابید.

- `children`
  - : آرایه‌ای از زیرمجموعه‌ها که همان قالب یک مجموعهٔ سطح بالا را دارد.
- `inputReports`
  - : آرایه‌ای از موارد `inputReport` که نشان‌دهندهٔ گزارش‌های ورودی جداگانه توصیف‌شده در این مجموعه هستند.
- `outputReports`
  - : آرایه‌ای از موارد `outputReport` که نشان‌دهندهٔ گزارش‌های خروجی جداگانه توصیف‌شده در این مجموعه هستند.
- `featureReports`
  - : آرایه‌ای از موارد `featureReport` که نشان‌دهندهٔ گزارش‌های ویژگی جداگانه توصیف‌شده در این مجموعه هستند.

## مثال‌ها

مثال زیر نحوهٔ دسترسی به عناصر مختلف را پس از برگردانده‌شدن ویژگی `collections` نشان می‌دهد. مثال‌های بیشتر و نمایش‌های زنده را می‌توانید در مقالهٔ [Connecting to uncommon HID devices](https://developer.chrome.com/docs/capabilities/hid) ببینید.

```js
for (const collection of device.collections) {
  // A HID collection includes usage, usage page, reports, and subcollections.
  console.log(`Usage: ${collection.usage}`);
  console.log(`Usage page: ${collection.usagePage}`);

  for (const inputReport of collection.inputReports) {
    console.log(`Input report: ${inputReport.reportId}`);
    // Loop through inputReport.items
  }

  for (const outputReport of collection.outputReports) {
    console.log(`Output report: ${outputReport.reportId}`);
    // Loop through outputReport.items
  }

  for (const featureReport of collection.featureReports) {
    console.log(`Feature report: ${featureReport.reportId}`);
    // Loop through featureReport.items
  }

  // Loop through subcollections with collection.children
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}