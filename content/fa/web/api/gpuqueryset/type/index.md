---
title: "GPUQuerySet: type property"
short-title: type
slug: Web/API/GPUQuerySet/type
page-type: web-api-instance-property
browser-compat: api.GPUQuerySet.type
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`type`** در رابط {{domxref("GPUQuerySet")}} یک مقدار شمارشی است که نوع پرس‌وجوهای مدیریت‌شده توسط `GPUQuerySet` را مشخص می‌کند.

## مقدار

یک مقدار شمارشی. مقادیر ممکن عبارتند از:

- `"occlusion"`
  - : `GPUQuerySet` پرس‌وجوهای انسداد را مدیریت می‌کند.
- `"timestamp"` {{experimental_inline}}
  - : `GPUQuerySet` پرس‌وجوهای زمانی را مدیریت می‌کند.

> [!NOTE]
> برای استفاده از پرس‌وجوهای زمانی، باید [ویژگی](/en-US/docs/Web/API/GPUSupportedFeatures) `timestamp-query` فعال باشد.

## مثال‌ها

برای مثال، صفحهٔ اصلی [`GPUQuerySet`](/en-US/docs/Web/API/GPUQuerySet#examples) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)