```
---
title: "GPUCommandEncoder: writeTimestamp() method"
---

---
title: "GPUCommandEncoder: writeTimestamp() method"
short-title: writeTimestamp()
slug: Web/API/GPUCommandEncoder/writeTimestamp
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.GPUCommandEncoder.writeTimestamp
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{deprecated_header}}{{non-standard_header}}{{AvailableInWorkers}}

متد **`writeTimestamp()`** از رابط {{domxref("GPUCommandEncoder")}} دستوری را کدگذاری می‌کند که پس از اجرای دستورات قبلیِ ثبت‌شده در همان {{domxref("GPUCommandBuffer")}} در صف، توسط GPU، یک مهر زمانی در {{domxref("GPUQuerySet")}} می‌نویسد.

> [!NOTE]
> برای استفاده از پرس‌وجوهای مهر زمانی، قابلیت `timestamp-query` {{domxref("GPUSupportedFeatures", "feature", "", "nocode")}} باید در {{domxref("GPUDevice")}} فعال باشد.

## نحو

```js-nolint
writeTimestamp(querySet, queryIndex)
```

### پارامترها

- `querySet`
  - : یک شیء {{domxref("GPUQuerySet")}} که مجموعه پرس‌وجویی را نشان می‌دهد که مقادیر مهر زمانی را ذخیره خواهد کرد.
- `queryIndex`
  - : عددی که شاخص پرس‌وجو را در مجموعه پرس‌وجو مشخص می‌کند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### اعتبارسنجی

هنگام فراخوانی **`writeTimestamp()`**، معیارهای زیر باید برقرار باشند؛ در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و {{domxref("GPUCommandEncoder")}} نامعتبر می‌شود:

- قابلیت `timestamp-query` {{domxref("GPUSupportedFeatures", "feature", "", "nocode")}} در {{domxref("GPUDevice")}} فعال باشد.
- `querySet` طوری باشد که {{domxref("GPUQuerySet.type")}} آن `"timestamp"` باشد.
- مقدار `queryIndex` کمتر از {{domxref("GPUQuerySet.count")}} باشد.

## مثال‌ها

```js
// …

const querySet = device.createQuerySet({
  type: "timestamp",
  count: 32,
});

// …

commandEncoder.writeTimestamp(querySet, 0);

// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
```