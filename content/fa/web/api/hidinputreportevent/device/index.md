---
title: "HIDInputReportEvent: device property"
short-title: device
slug: Web/API/HIDInputReportEvent/device
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HIDInputReportEvent.device
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

ویژگی **`device`** در رابط {{domxref("HIDInputReportEvent")}} نمونه‌ای از {{domxref("HIDDevice")}} را برمی‌گرداند که نمایانگر رابط HID ارسال‌کننده گزارش ورودی است.

## مقدار

یک {{domxref("HIDDevice")}}.

## مثال‌ها

در مثال زیر، `device` یک نمونه {{domxref("HIDDevice")}} است که نمایانگر دستگاه ارسال‌کننده گزارش است. `productName` این دستگاه در کنسول ثبت می‌شود.

```js
device.addEventListener("inputreport", (event) => {
  const { data, device, reportId } = event;
  console.log(device.productName);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}