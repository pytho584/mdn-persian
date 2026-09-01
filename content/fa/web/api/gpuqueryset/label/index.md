---
title: "GPUQuerySet: label property"
short-title: label
slug: Web/API/GPUQuerySet/label
page-type: web-api-instance-property
browser-compat: api.GPUQuerySet.label
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی **`label`** از رابط {{domxref("GPUQuerySet")}} یک رشته است که برچسبی را فراهم می‌کند که می‌توان از آن برای شناسایی شیء استفاده کرد، برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

این ویژگی می‌تواند با ارائهٔ یک ویژگی `label` در شیء توصیف‌کننده‌ای که به فراخوانی {{domxref("GPUDevice.createQuerySet()")}} اصلی ارسال می‌شود، تنظیم گردد، یا می‌توانید آن را مستقیماً روی شیء `GPUQuerySet` دریافت و تنظیم کنید.

## مقدار

یک رشته. اگر این مقدار قبلاً به‌صورت گفته شده تنظیم نشده باشد، یک رشتهٔ خالی خواهد بود.

## نمونه‌ها

تنظیم و دریافت یک برچسب از طریق `GPUQuerySet.label`:

```js
const querySet = device.createQuerySet({
  type: "occlusion",
  count: 32,
});

querySet.label = "my_query_set";

console.log(querySet.label); // "my_query_set"
```

تنظیم یک برچسب از طریق فراخوانی {{domxref("GPUDevice.createQuerySet()")}} اصلی و سپس دریافت آن از طریق `GPUQuerySet.label`:

```js
const querySet = device.createQuerySet({
  type: "occlusion",
  count: 32,
  label: "my_query_set",
});

console.log(querySet.label); // "my_query_set"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)