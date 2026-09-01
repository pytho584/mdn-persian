---
title: GPUQuerySet
slug: Web/API/GPUQuerySet
page-type: web-api-interface
browser-compat: api.GPUQuerySet
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط **`GPUQuerySet`** از {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} برای ثبت نتایج پرسوجوها روی پاس‌ها، مانند پرسوجوهای انسداد یا زمان‌سنجی استفاده می‌شود.

- پرسوجوهای انسداد در پاس‌های رندر در دسترس هستند تا بررسی کنند که آیا هر نمونه‌ی فرگمنت، همه‌ی آزمون‌های per-fragment را برای مجموعه‌ای از دستورات رسم (شامل آزمون‌های scissor، sample mask، alpha to coverage، stencil و depth) پاس می‌کند یا خیر. برای اجرای یک پرسوجوی انسداد، یک `GPUQuerySet` مناسب باید به‌عنوان مقدار ویژگی توصیفگر `occlusionQuerySet` هنگام فراخوانی {{domxref("GPUCommandEncoder.beginRenderPass()")}} برای اجرای یک پاس رندر ارائه شود.

- پرسوجوهای زمان‌سنجی به برنامه‌ها اجازه می‌دهند تا زمان‌ها را در یک `GPUQuerySet` بنویسند. برای اجرای یک پرسوجوی زمان‌سنجی، `GPUQuerySet`های مناسب باید درون مقدار ویژگی توصیفگر `timestampWrites` هنگام فراخوانی {{domxref("GPUCommandEncoder.beginRenderPass()")}} برای اجرای یک پاس رندر، یا {{domxref("GPUCommandEncoder.beginComputePass()")}} برای اجرای یک پاس محاسباتی ارائه شوند.

> [!NOTE]
> برای استفاده از پرسوجوهای زمان‌سنجی، [ویژگی](/en-US/docs/Web/API/GPUSupportedFeatures) `timestamp-query` باید فعال شده باشد.

یک نمونه از شیء `GPUQuerySet` با استفاده از متد {{domxref("GPUDevice.createQuerySet()")}} ایجاد می‌شود.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("GPUQuerySet.count", "count")}} {{ReadOnlyInline}}
  - : عددی که تعداد پرسوجوهای مدیریت‌شده توسط `GPUQuerySet` را مشخص می‌کند.
- {{domxref("GPUQuerySet.label", "label")}}
  - : رشته‌ای که برچسبی برای شناسایی شیء فراهم می‌کند؛ برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.
- {{domxref("GPUQuerySet.type", "type")}} {{ReadOnlyInline}}
  - : مقدار شمارشی (enumerated) که نوع پرسوجوهای مدیریت‌شده توسط `GPUQuerySet` را مشخص می‌کند.

## متدهای نمونه

- {{domxref("GPUQuerySet.destroy", "destroy()")}}
  - : `GPUQuerySet` را نابود می‌کند.

## مثال‌ها

قطعه کد زیر یک `GPUQuerySet` می‌سازد که ۳۲ نتیجه پرسوجوی انسداد را نگه می‌دارد و سپس `type` و `count` را برمی‌گرداند:

```js
const querySet = device.createQuerySet({
  type: "occlusion",
  count: 32,
});

console.log(querySet.count); // 32
console.log(querySet.type); // "occlusion"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابط [WebGPU API](/en-US/docs/Web/API/WebGPU_API)