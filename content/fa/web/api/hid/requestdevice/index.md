---
title: "HID: requestDevice() method"
short-title: requestDevice()
slug: Web/API/HID/requestDevice
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.HID.requestDevice
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}

متد **`requestDevice()`** از رابط {{domxref("HID")}} درخواست دسترسی به یک دستگاه HID را انجام می‌دهد.

عامل کاربر (user agent) یک گفتگوی مجوز شامل فهرستی از دستگاه‌های متصل را نمایش می‌دهد و از کاربر می‌خواهد یکی از این دستگاه‌ها را انتخاب کرده و به آن اجازهٔ دسترسی بدهد.

## سینتکس

```js-nolint
requestDevice(options)
```

### پارامترها

- `options`
  - : شیئی که آرایه‌ای از اشیاء فیلتر برای دستگاه‌های احتمالی جهت جفت‌سازی را شامل می‌شود. هر شیء فیلتر می‌تواند ویژگی‌های زیر را داشته باشد:
    - `vendorId` {{optional_inline}}
      - : یک عدد صحیح که vendorId دستگاه HID درخواستی را نشان می‌دهد.
    - `productId` {{optional_inline}}
      - : یک عدد صحیح که productId دستگاه HID درخواستی را نشان می‌دهد.
    - `usagePage` {{optional_inline}}
      - : یک عدد صحیح که مؤلفهٔ usage page از HID usage دستگاه درخواستی را نشان می‌دهد. usage مربوط به یک مجموعهٔ سطح بالا (top-level collection) برای شناسایی نوع دستگاه استفاده می‌شود.

        مقادیر استاندارد HID usage را می‌توان در سند [HID Usage Tables](https://usb.org/document-library/hid-usage-tables-17) یافت.
    - `usage` {{optional_inline}}
      - : یک عدد صحیح که مؤلفهٔ usage ID از HID usage دستگاه درخواستی را نشان می‌دهد.

> [!NOTE]
> فیلترهای دستگاه برای محدود کردن فهرست دستگاه‌هایی که به کاربر نمایش داده می‌شوند به کار می‌روند. اگر فیلتری وجود نداشته باشد، همهٔ دستگاه‌های متصل نمایش داده می‌شوند. وقتی یک یا چند فیلتر وجود داشته باشد، دستگاهی در فهرست قرار می‌گیرد که با حداقل یکی از فیلترها مطابقت داشته باشد. برای اینکه یک فیلتر مطابقت داشته باشد، همهٔ قواعد موجود در آن فیلتر باید مطابقت داشته باشند.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با آرایه‌ای از اشیاء {{domxref("HIDDevice")}} متصل که با فیلترهای ارسال‌شده مطابقت دارند، حل می‌شود.

### استثناها

- `SecurityError` {{domxref("DOMException")}}
  - : اگر صفحه اجازهٔ دسترسی به قابلیت HID را ندهد، این خطا پرتاب می‌شود.

## امنیت

[Transient user activation](/en-US/docs/Web/Security/Defenses/User_activation) الزامی است. کاربر باید با صفحه یا یک عنصر رابط کاربری تعامل کند تا این قابلیت کار کند.

## مثال‌ها

### مطابقت یک دستگاه با هر چهار قانون فیلتر

در مثال زیر، یک دستگاه HID درخواست می‌شود که vendor ID آن `0xABCD`، product ID آن `0x1234`، usage page آن `0x0C` و usage ID آن `0x01` است. تنها دستگاه‌هایی که با همهٔ این قوانین مطابقت داشته باشند نمایش داده می‌شوند.

```js
let requestButton = document.getElementById("request-hid-device");
requestButton.addEventListener("click", async () => {
  let device;
  try {
    const devices = await navigator.hid.requestDevice({
      filters: [
        {
          vendorId: 0xabcd,
          productId: 0x1234,
          usagePage: 0x0c,
          usage: 0x01,
        },
      ],
    });
    device = devices[0];
  } catch (error) {
    console.log("An error occurred.");
  }

  if (!device) {
    console.log("No device was selected.");
  } else {
    console.log(`HID: ${device.productName}`);
  }
});
```

### مثالی با دو فیلتر

این مثال شامل دو فیلتر است. دستگاه‌هایی نشان داده می‌شوند که با یکی از این دو فیلتر مطابقت داشته باشند.

```js
// Filter on devices with the Nintendo Switch Joy-Con USB Vendor/Product IDs.
const filters = [
  {
    vendorId: 0x057e, // Nintendo Co., Ltd
    productId: 0x2006, // Joy-Con Left
  },
  {
    vendorId: 0x057e, // Nintendo Co., Ltd
    productId: 0x2007, // Joy-Con Right
  },
];

// Prompt user to select a Joy-Con device.
const [device] = await navigator.hid.requestDevice({ filters });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}