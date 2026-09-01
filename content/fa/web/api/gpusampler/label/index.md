---
title: "GPUSampler: label property"
---

---
title: "GPUSampler: label property"
short-title: label
slug: Web/API/GPUSampler/label
page-type: web-api-instance-property
browser-compat: api.GPUSampler.label
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی **`label`** در رابط {{domxref("GPUSampler")}} برچسبی را فراهم می‌کند که می‌توان از آن برای شناسایی شیء استفاده کرد، مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

این برچسب را می‌توان با ارائه‌ی یک ویژگی `label` در شیء توصیفگر که به فراخوانی {{domxref("GPUDevice.createSampler()")}} اصلی منتقل می‌شود تنظیم کرد، یا می‌توانید آن را مستقیماً روی شیء `GPUSampler` بخوانید یا بنویسید.

## مقدار

یک رشته. اگر قبلاً به شکل بالا تنظیم نشده باشد، یک رشته‌ی خالی خواهد بود.

## مثال‌ها

تنظیم و خواندن برچسب از طریق `GPUSampler.label`:

```js
// …

const sampler = device.createSampler({
  compare: "less",
});

sampler.label = "my_sampler";

console.log(sampler.label); // "my_sampler"
```

تنظیم برچسب از طریق فراخوانی {{domxref("GPUDevice.createSampler()")}} اصلی و سپس خواندن آن از طریق `GPUSampler.label`:

```js
// …

const sampler = device.createSampler({
  compare: "less",
  label: "my_sampler",
});

console.log(sampler.label); // "my_sampler"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)