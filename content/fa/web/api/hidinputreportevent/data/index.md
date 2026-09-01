---
title: "HIDInputReportEvent: data property"
short-title: data
slug: Web/API/HIDInputReportEvent/data
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HIDInputReportEvent.data
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

ویژگی **`data`** از رابط {{domxref("HIDInputReportEvent")}} یک {{jsxref("DataView")}} شامل داده‌های گزارش ورودی را برمی‌گرداند، به جز `reportId` در صورتی که رابط HID از شناسه‌های گزارش استفاده کند.

## مقدار

یک {{jsxref("DataView")}}.

## مثال‌ها

در مثال زیر، `data` برگشت‌داده‌شده در کنسول ثبت می‌شود.

```js
device.addEventListener("inputreport", (event) => {
  const { data, device, reportId } = event;
  console.log(data);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}