---
title: "GPUSupportedLimits"
slug: Web/API/GPUSupportedLimits
page-type: web-api-interface
browser-compat: api.GPUSupportedLimits
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط **`GPUSupportedLimits`** در {{domxref("WebGPU API", "WebGPU API", "", "nocode")}} محدودیت‌های پشتیبانی‌شده توسط یک {{domxref("GPUAdapter")}} را توصیف می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

محدودیت‌های زیر در قالب ویژگی‌های یک شیء `GPUSupportedLimits` نمایش داده می‌شوند. برای توضیحات دقیق دربارهٔ هر یک از این محدودیت‌ها، بخش [محدودیت‌ها](https://gpuweb.github.io/gpuweb/#limits) از مشخصات فنی را ببینید.

| نام محدودیت                                                                                                                                                                                                                                                             | مقدار پیش‌فرض            |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------ |
| `maxTextureDimension1D`                                                                                                                                                                                                                                                 | 8192                     |
| `maxTextureDimension2D`                                                                                                                                                                                                                                                 | 8192                     |
| `maxTextureDimension3D`                                                                                                                                                                                                                                                 | 2048                     |
| `maxTextureArrayLayers`                                                                                                                                                                                                                                                 | 256                      |
| `maxBindGroups`                                                                                                                                                                                                                                                         | 4                        |
| `maxBindingsPerBindGroup`                                                                                                                                                                                                                                               | 640                      |
| `maxDynamicUniformBuffersPerPipelineLayout`                                                                                                                                                                                                                             | 8                        |
| `maxDynamicStorageBuffersPerPipelineLayout`                                                                                                                                                                                                                             | 4                        |
| `maxSampledTexturesPerShaderStage`                                                                                                                                                                                                                                      | 16                       |
| `maxSamplersPerShaderStage`                                                                                                                                                                                                                                             | 16                       |
| `maxStorageBuffersInFragmentStage`                                                                                                                                                                                                                                      | 8                        |
| `maxStorageBuffersInVertexStage`                                                                                                                                                                                                                                        | 8                        |
| `maxStorageBuffersPerShaderStage`                                                                                                                                                                                                                                       | 8                        |
| `maxStorageTexturesInFragmentStage`                                                                                                                                                                                                                                     | 4                        |
| `maxStorageTexturesInVertexStage`                                                                                                                                                                                                                                       | 4                        |
| `maxStorageTexturesPerShaderStage`                                                                                                                                                                                                                                      | 4                        |
| `maxUniformBuffersPerShaderStage`                                                                                                                                                                                                                                       | 12                       |
| `maxUniformBufferBindingSize`                                                                                                                                                                                                                                           | 65536 بایت               |
| `maxStorageBufferBindingSize`                                                                                                                                                                                                                                           | 134217728 بایت (128 MB)  |
| `minUniformBufferOffsetAlignment`                                                                                                                                                                                                                                       | 256 بایت                 |
| `minStorageBufferOffsetAlignment`                                                                                                                                                                                                                                       | 256 بایت                 |
| `maxVertexBuffers`                                                                                                                                                                                                                                                      | 8                        |
| `maxBufferSize`                                                                                                                                                                                                                                                         | 268435456 بایت (256 MB)  |
| `maxVertexAttributes`                                                                                                                                                                                                                                                   | 16                       |
| `maxVertexBufferArrayStride`                                                                                                                                                                                                                                            | 2048 بایت                |
| `maxInterStageShaderComponents` {{deprecated_inline}} {{non-standard_inline}} (به جای آن از `maxInterStageShaderVariables` استفاده کنید؛ برای اطلاعات بیشتر [اعلام منسوخ‌شدن](https://developer.chrome.com/blog/new-in-webgpu-133#deprecate_maxinterstageshadercomponents_limit) را ببینید) | 60                       |
| `maxInterStageShaderVariables`                                                                                                                                                                                                                                          | 16                       |
| `maxColorAttachments`                                                                                                                                                                                                                                                   | 8                        |
| `maxColorAttachmentBytesPerSample`                                                                                                                                                                                                                                      | 32                       |
| `maxComputeWorkgroupStorageSize`                                                                                                                                                                                                                                        | 16384 بایت               |
| `maxComputeInvocationsPerWorkgroup`                                                                                                                                                                                                                                     | 256                      |
| `maxComputeWorkgroupSizeX`                                                                                                                                                                                                                                              | 256                      |
| `maxComputeWorkgroupSizeY`                                                                                                                                                                                                                                              | 256                      |
| `maxComputeWorkgroupSizeZ`                                                                                                                                                                                                                                              | 64                       |
| `maxComputeWorkgroupsPerDimension`                                                                                                                                                                                                                                      | 65535                    |

## توضیحات

شیء `GPUSupportedLimits` برای آداپتور فعلی از طریق ویژگی {{domxref("GPUAdapter.limits")}} قابل دسترسی است.

به جای گزارش دقیق محدودیت‌های هر GPU، مرورگرها معمولاً مقادیر رتبه‌بندی‌شده (tier) مختلفی از محدودیت‌های گوناگون را گزارش می‌دهند (تا اطلاعات منحصربه‌فرد موجود برای اثرانگشت‌گیری (fingerprinting) کاهش یابد). به عنوان مثال، رتبه‌های یک محدودیت خاص ممکن است 2048، 8192 و 32768 باشد. اگر محدودیت واقعی GPU شما 16384 باشد، مرورگر همچنان 8192 را گزارش می‌دهد.

با توجه به اینکه مرورگرهای مختلف این کار را به شکل متفاوت انجام می‌دهند و مقادیر رتبه‌بندی ممکن است در طول زمان تغییر کنند، ارائهٔ یک گزارش دقیق از مقادیر مورد انتظار محدودیت‌ها دشوار است؛ توصیه می‌شود آزمایش کامل انجام شود.

توجه داشته باشید که هنگام فراخوانی {{domxref("GPUAdapter.requestDevice()")}} برای درخواست یک {{domxref("GPUDevice")}} که حداقل نیازمندی‌های خاصی («محدودیت‌ها») را برآورده می‌کند، شما یک شیء ارسال می‌کنید که دارای همان نام‌های ویژگی `GPUSupportedLimits` است.

## مثال‌ها

در کد زیر، مقدار `maxBindGroups` از `GPUAdapter.limits` را بررسی می‌کنیم تا ببینیم آیا برابر یا بیشتر از 6 است. برنامهٔ نمونهٔ ما از نظر تئوری به 6 گروه bind نیاز دارد، بنابراین اگر مقدار برگشتی >= 6 باشد، یک محدودیت حداکثر 6 را به شیء `requiredLimits` اضافه می‌کنیم. سپس با استفاده از {{domxref("GPUAdapter.requestDevice()")}} یک دستگاه با آن نیازمندی محدودیت درخواست می‌کنیم:

```js
async function init() {
  if (!navigator.gpu) {
    throw Error("WebGPU not supported.");
  }

  const adapter = await navigator.gpu.requestAdapter();
  if (!adapter) {
    throw Error("Couldn't request WebGPU adapter.");
  }

  const requiredLimits = {};

  // برنامه از نظر ایده‌آل به 6 گروه bind نیاز دارد، بنابراین سعی می‌کنیم چیزی را که برنامه نیاز دارد درخواست کنیم
  if (adapter.limits.maxBindGroups >= 6) {
    requiredLimits.maxBindGroups = 6;
  }

  const device = await adapter.requestDevice({
    requiredLimits,
  });

  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)