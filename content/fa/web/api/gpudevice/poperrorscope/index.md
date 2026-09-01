---
title: "GPUDevice: popErrorScope() method"
---

---
title: "GPUDevice: popErrorScope() method"
short-title: popErrorScope()
slug: Web/API/GPUDevice/popErrorScope
page-type: web-api-instance-method
browser-compat: api.GPUDevice.popErrorScope
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`popErrorScope()`** از رابط {{domxref("GPUDevice")}} یک خطایابی (error scope) موجود GPU را از پشته خطایابی (که ابتدا با استفاده از {{domxref("GPUDevice.pushErrorScope()")}} به پشته اضافه شده بود) بیرون می‌کشد و یک {{jsxref("Promise")}} برمی‌گرداند. این Promise به یک شیء حاوی اولین خطای ثبت‌شده در آن خطایابی، یا در صورت عدم وقوع خطا، به `null` تبدیل می‌شود.

## نحو

```js-nolint
popErrorScope()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به یک شیء حاوی اولین خطای ثبت‌شده در خطایابی تبدیل می‌شود. این شیء می‌تواند از انواع زیر باشد:

- {{domxref("GPUInternalError")}}
- {{domxref("GPUOutOfMemoryError")}}
- {{domxref("GPUValidationError")}}

اگر خطایی رخ نداده باشد، به `null` تبدیل می‌شود.

## مثال‌ها

مثال زیر از یک خطایابی برای ثبت یک خطای اعتبارسنجی احتمالی استفاده می‌کند و آن را در کنسول ثبت می‌کند.

```js
device.pushErrorScope("validation");

let sampler = device.createSampler({
  maxAnisotropy: 0, // Invalid, maxAnisotropy must be at least 1.
});

device.popErrorScope().then((error) => {
  if (error) {
    sampler = null;
    console.error(`An error occurred while creating sampler: ${error.message}`);
  }
});
```

برای مثال‌ها و اطلاعات بیشتر به [بهترین شیوه‌های مدیریت خطای WebGPU](https://toji.dev/webgpu-best-practices/error-handling) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)