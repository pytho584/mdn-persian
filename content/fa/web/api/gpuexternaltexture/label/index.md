---
title: "GPUExternalTexture: label property"
---

---
title: "GPUExternalTexture: label property"
short-title: label
slug: Web/API/GPUExternalTexture/label
page-type: web-api-instance-property
browser-compat: api.GPUExternalTexture.label
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

خاصیت **`label`** در رابط {{domxref("GPUExternalTexture")}} برچسبی را فراهم می‌کند که می‌توان از آن برای شناسایی شیء استفاده کرد، برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

این مقدار را می‌توان با ارائه یک ویژگی `label` در شیء توصیف‌گری که به فراخوانی {{domxref("GPUDevice.importExternalTexture()")}} ارسال می‌شود تنظیم کرد، یا می‌توانید آن را مستقیماً روی شیء `GPUExternalTexture` بخوانید و بنویسید.

## مقدار

یک رشته. اگر قبلاً به شکلی که در بالا توضیح داده شد تنظیم نشده باشد، یک رشتهٔ خالی خواهد بود.

## مثال‌ها

تنظیم و دریافت برچسب از طریق `GPUExternalTexture.label`:

```js
// …

const externalTexture = device.importExternalTexture({
  source: video,
});

externalTexture.label = "my_ext_texture";

console.log(externalTexture.label); // "my_ext_texture"
```

تنظیم برچسب از طریق فراخوانی {{domxref("GPUDevice.importExternalTexture()")}} مبدأ، و سپس دریافت آن از طریق `GPUExternalTexture.label`:

```js
// …

const externalTexture = device.importExternalTexture({
  source: video,
  label: "my_ext_texture",
});

console.log(externalTexture.label); //  "my_ext_texture"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)