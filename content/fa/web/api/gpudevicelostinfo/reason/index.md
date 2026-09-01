---
title: "GPUDeviceLostInfo: reason property"
short-title: reason
slug: Web/API/GPUDeviceLostInfo/reason
page-type: web-api-instance-property
browser-compat: api.GPUDeviceLostInfo.reason
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

خصوصیت **`reason`** فقط‌خواندنی در رابط {{domxref("GPUDeviceLostInfo")}} دلیلی را که دستگاه از بین رفته است به صورت قابل خواندن توسط ماشین تعریف می‌کند.

## مقدار

یک مقدار شمارشی (enumerated value). در حال حاضر تنها مقدار تعریف‌شده در مشخصات، `"destroyed"` است که نشان می‌دهد دستگاه با فراخوانی {{domxref("GPUDevice.destroy()")}} از بین رفته است.

اگر دستگاه به دلیلی نامشخص که در مقادیر شمارشی موجود پوشش داده نشده است از بین برود، `reason` مقدار `undefined` را برمی‌گرداند.

## مثال‌ها

برای مشاهده مثال، به صفحه اصلی [`GPUDevice.lost`](/en-US/docs/Web/API/GPUDevice/lost#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)