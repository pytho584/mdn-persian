---
title: "HIDInputReportEvent: reportId property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/HIDInputReportEvent/reportId"
---

---
title: "HIDInputReportEvent: reportId property"
short-title: reportId
slug: Web/API/HIDInputReportEvent/reportId
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HIDInputReportEvent.reportId
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

**`reportId`** ویژگی از رابط {{domxref("HIDInputReportEvent")}}، پیشوند شناسایی یک‌بایتی این گزارش را برمی‌گرداند، یا اگر رابط HID از شناسه‌های گزارش استفاده نکند، مقدار 0 را برمی‌گرداند.

## مقدار

یک پیشوند شناسایی یک‌بایتی.

## مثال‌ها

در مثال زیر، `reportId` یک گزارش ورودی دریافتی در کنسول ثبت می‌شود.

```js
device.addEventListener("inputreport", (event) => {
  const { data, device, reportId } = event;
  console.log(reportId);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}