---
title: "GPUDevice: createQuerySet() method"
short-title: createQuerySet()
slug: Web/API/GPUDevice/createQuerySet
page-type: web-api-instance-method
browser-compat: api.GPUDevice.createQuerySet
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`createQuerySet()`** در رابط {{domxref("GPUDevice")}} یک {{domxref("GPUQuerySet")}} ایجاد می‌کند که می‌توان از آن برای ثبت نتایج پرس‌وجوها در پاس‌ها (passes) مانند پرس‌وجوهای occlusion (مخفی‌شدگی) یا timestamp (برچسب زمانی) استفاده کرد.

## Syntax

```js-nolint
createQuerySet(descriptor)
```

### Parameters

- `descriptor`
  - : یک شیء حاوی ویژگی‌های زیر:
    - `count`
      - : عددی که تعداد پرس‌وجوهایی را مشخص می‌کند که توسط {{domxref("GPUQuerySet")}} حاصل مدیریت می‌شوند.
    - `label` {{optional_inline}}
      - : رشته‌ای که برچسبی را فراهم می‌کند و می‌توان از آن برای شناسایی شیء استفاده کرد، برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.
    - `type`
      - : یک مقدار شمارشی (enumerated value) که نوع پرس‌وجوهایی را که باید توسط {{domxref("GPUQuerySet")}} حاصل مدیریت شوند مشخص می‌کند. مقادیر احتمالی عبارت‌اند از:
        - `"occlusion"`
          - : پرس‌وجوهای occlusion در پاس‌های رندر (render passes) در دسترس هستند تا تعداد نمونه‌های فرگمنت (fragment samples) را که تمام تست‌های per-fragment را برای مجموعه‌ای از دستورات رسم (شامل تست‌های scissor، sample mask، alpha to coverage، stencil و depth) با موفقیت پشت سر می‌گذارند، پرس‌وجو کنند. برای اجرای یک پرس‌وجوی occlusion، باید یک {{domxref("GPUQuerySet")}} مناسب به عنوان مقدار ویژگی توصیف‌گر `occlusionQuerySet` هنگام فراخوانی {{domxref("GPUCommandEncoder.beginRenderPass()")}} برای اجرای یک پاس رندر ارائه شود.
        - `"timestamp"`
          - : پرس‌وجوهای timestamp به برنامه‌ها اجازه می‌دهند تا برچسب‌های زمانی را در یک {{domxref("GPUQuerySet")}} بنویسند. برای اجرای یک پرس‌وجوی timestamp، باید {{domxref("GPUQuerySet")}}های مناسب در داخل مقدار ویژگی توصیف‌گر `timestampWrites` هنگام فراخوانی {{domxref("GPUCommandEncoder.beginRenderPass()")}} برای اجرای یک پاس رندر، یا {{domxref("GPUCommandEncoder.beginComputePass()")}} برای اجرای یک پاس محاسباتی ارائه شوند. همچنین می‌توانید در هر زمان با فراخوانی {{domxref("GPUCommandEncoder.writeTimeStamp()")}} با یک {{domxref("GPUQuerySet")}} مناسب به عنوان پارامتر، یک پرس‌وجوی timestamp واحد اجرا کنید.

            > [!NOTE]
            > برای استفاده از پرس‌وجوهای timestamp باید [ویژگی](/en-US/docs/Web/API/GPUSupportedFeatures) `timestamp-query` فعال شده باشد.

### Return value

یک نمونه شیء از {{domxref("GPUQuerySet")}}.

### Validation

هنگام فراخوانی **`createQuerySet()`** معیارهای زیر باید برآورده شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و یک شیء {{domxref("GPUQuerySet")}} نامعتبر بازگردانده می‌شود:

- `count` کمتر از یا مساوی 4096 باشد.

## Examples

قطعه کد زیر یک {{domxref("GPUQuerySet")}} ایجاد می‌کند که 32 نتیجه پرس‌وجوی occlusion را نگه می‌دارد:

```js
const querySet = device.createQuerySet({
  type: "occlusion",
  count: 32,
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)