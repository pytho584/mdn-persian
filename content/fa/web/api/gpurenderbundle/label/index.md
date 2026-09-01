---
title: "GPURenderBundle: label property"
short-title: label
slug: Web/API/GPURenderBundle/label
page-type: web-api-instance-property
browser-compat: api.GPURenderBundle.label
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`label`** از رابط {{domxref("GPURenderBundle")}} یک رشته است که برچسبی را ارائه می‌دهد که می‌توان از آن برای شناسایی شیء استفاده کرد، مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

این مقدار می‌تواند با ارائه یک ویژگی `label` در شیء توصیف‌کننده‌ای که به فراخوانی {{domxref("GPURenderBundleEncoder.finish()")}} اولیه ارسال می‌شود، تنظیم گردد، یا می‌توانید آن را مستقیماً روی شیء `GPURenderBundle` دریافت و تنظیم کنید.

## مقدار

یک رشته. اگر قبلاً مقداری برای برچسب تنظیم نشده باشد، دریافت برچسب یک رشته خالی برمی‌گرداند.

## نمونه‌ها

تنظیم و دریافت یک برچسب از طریق `GPURenderBundle.label`:

```js
const renderBundle = renderBundleEncoder.finish();

renderBundle.label = "my_render_bundle";
console.log(renderBundle.label); // "my_render_bundle"
```

تنظیم یک برچسب از طریق فراخوانی {{domxref("GPURenderBundleEncoder.finish()")}} اولیه، و سپس دریافت آن از طریق `GPURenderBundle.label`:

```js
const renderBundle = renderBundleEncoder.finish({
  label: "my_render_bundle",
});

console.log(renderBundle.label); // "my_render_bundle"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [رابط WebGPU API](/en-US/docs/Web/API/WebGPU_API)