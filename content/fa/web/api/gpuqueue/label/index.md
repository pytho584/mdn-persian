---
title: "GPUQueue: label property"
---

---
title: "GPUQueue: label property"
short-title: label
slug: Web/API/GPUQueue/label
page-type: web-api-instance-property
browser-compat: api.GPUQueue.label
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`label`** در رابط {{domxref("GPUQueue")}} یک رشته است که برای شناسایی شیء استفاده می‌شود؛ برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

می‌توانید آن را مستقیماً روی شیء `GPUQueue` بخوانید و تنظیم کنید.

## مقدار

یک رشته. اگر قبلاً هیچ مقدار برچسبی تنظیم نشده باشد، خواندن `label` یک رشته خالی بازمی‌گرداند.

## مثال‌ها

تنظیم و خواندن برچسب با استفاده از `GPUQueue.label`:

```js
device.queue.label = "my_queue";
console.log(device.queue.label); // "my_queue"
```

همچنین می‌توانید برچسب صف را هنگام درخواست دستگاه به این شکل تنظیم کنید:

```js
const device = adapter.requestDevice({
  defaultQueue: { label: "my_queue" },
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
