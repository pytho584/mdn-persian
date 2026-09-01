---
title: "GPUAdapter: requestDevice() method"
short-title: requestDevice()
slug: Web/API/GPUAdapter/requestDevice
page-type: web-api-instance-method
browser-compat: api.GPUAdapter.requestDevice
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`requestDevice()`** از رابط {{domxref("GPUAdapter")}} یک {{jsxref("Promise")}} برمی‌گرداند که با یک شیء {{domxref("GPUDevice")}} تکمیل می‌شود. این شیء رابط اصلی برای ارتباط با GPU است.

## نحو (Syntax)

```js-nolint
requestDevice()
requestDevice(descriptor)
```

### پارامترها

- `descriptor` {{optional_inline}}
  - : یک شیء حاوی ویژگی‌های زیر:
    - `defaultQueue` {{optional_inline}}
      - : شیئی که اطلاعاتی درباره {{domxref("GPUQueue")}} پیش‌فرض دستگاه فراهم می‌کند (مطابق با آنچه توسط {{domxref("GPUDevice.queue")}} برگردانده می‌شود). این شیء یک ویژگی واحد به نام `label` دارد که یک مقدار {{domxref("GPUQueue.label", "label")}} برای صف پیش‌فرض تعیین می‌کند. اگر مقداری ارائه نشود، به طور پیش‌فرض یک شیء خالی خواهد بود و برچسب صف پیش‌فرض یک رشتهٔ خالی خواهد بود.
    - `label` {{optional_inline}}
      - : رشته‌ای که یک برچسب برای شناسایی {{domxref("GPUDevice")}} فراهم می‌کند، مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.
    - `requiredFeatures` {{optional_inline}}
      - : آرایه‌ای از رشته‌ها که قابلیت‌های اضافی مورد نیاز برای پشتیبانی در {{domxref("GPUDevice")}} برگشتی را مشخص می‌کند. اگر `GPUAdapter` نتواند این قابلیت‌ها را فراهم کند، فراخوانی `requestDevice()` با شکست مواجه می‌شود. برای فهرست کامل قابلیت‌های ممکن، به {{domxref("GPUSupportedFeatures")}} مراجعه کنید. اگر مقداری ارائه نشود، این آرایه به طور پیش‌فرض خالی است.
    - `requiredLimits` {{optional_inline}}
      - : شیئی شامل ویژگی‌هایی که محدودیت‌های مورد نیاز برای پشتیبانی در {{domxref("GPUDevice")}} برگشتی را مشخص می‌کند. اگر `GPUAdapter` نتواند این محدودیت‌ها را فراهم کند، فراخوانی `requestDevice()` با شکست مواجه می‌شود. هر کلید با مقدار غیر `undefined` باید نام یکی از اعضای {{domxref("GPUSupportedLimits")}} باشد.
        > [!NOTE]
        > می‌توانید هنگام درخواست یک دستگاه GPU محدودیت‌های ناشناخته را نیز درخواست کنید بدون اینکه خطایی ایجاد شود. چنین محدودیت‌هایی `undefined` خواهند بود. این ویژگی مفید است زیرا کد WebGPU را کمتر شکننده می‌کند – یک پایگاه کد به دلیل عدم وجود یک محدودیت در آداپتر از کار نخواهد افتاد.

همه ویژگی‌ها و محدودیت‌ها در همه مرورگرهایی که از WebGPU پشتیبانی می‌کنند در دسترس نخواهند بود، حتی اگر توسط سخت‌افزار زیرین پشتیبانی شوند. برای اطلاعات بیشتر به صفحات {{domxref("GPUAdapter.features", "features")}} و {{domxref("GPUAdapter.limits", "limits")}} مراجعه کنید.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک نمونه شیء {{domxref("GPUDevice")}} تکمیل می‌شود.

اگر یک فراخوانی تکراری انجام دهید، یعنی `requestDevice()` را روی یک {{domxref("GPUAdapter")}} که قبلاً `requestDevice()` روی آن فراخوانی شده بود صدا بزنید، آنگاه Promise با یک `OperationError` رد می‌شود زیرا `GPUAdapter` مرتبط هنگام ایجاد یک `GPUDevice` مصرف می‌شود.

### استثناها (Exceptions)

- `OperationError` {{domxref("DOMException")}}
  - : Promise با یک `OperationError` رد می‌شود اگر یکی از موارد زیر رخ دهد:
    - محدودیت‌های موجود در ویژگی `requiredLimits` توسط {{domproxy("GPUAdapter")}} پشتیبانی نشوند، چه به دلیل معتبر نبودن محدودیت‌ها، یا به دلیل اینکه مقادیر آنها بیشتر از مقادیر آداپتر برای آن محدودیت‌ها باشد.
    - `GPUAdapter` با فراخوانی قبلی `requestDevice()` روی آن مصرف شده باشد.
- `TypeError` {{domxref("DOMException")}}
  - : Promise با یک `TypeError` رد می‌شود اگر ویژگی‌های موجود در ویژگی `requiredFeatures` توسط {{domproxy("GPUAdapter")}} پشتیبانی نشوند.

## مثال‌ها

### مثال پایه

```js
async function init() {
  if (!navigator.gpu) {
    throw Error("WebGPU not supported.");
  }

  const adapter = await navigator.gpu.requestAdapter();
  if (!adapter) {
    throw Error("Couldn't request WebGPU adapter.");
  }

  const device = await adapter.requestDevice();

  // …
}
```

### درخواست ویژگی‌ها و محدودیت‌های خاص

در کد زیر ما:

1. بررسی می‌کنیم که آیا {{domxref("GPUAdapter")}} قابلیت `texture-compression-astc` را دارد یا خیر. اگر دارد، آن را به آرایه `requiredFeatures` اضافه می‌کنیم.
2. مقدار `GPUAdapter.limits` مربوط به `maxBindGroups` را پرس‌وجو می‌کنیم تا ببینیم آیا برابر یا بزرگتر از ۶ است. برنامهٔ تئوری ما به ۶ گروه اتصال نیاز دارد، بنابراین اگر مقدار برگشتی >= ۶ باشد، یک حداکثر محدودیت ۶ را به شیء `requiredLimits` اضافه می‌کنیم.
3. یک دستگاه با آن نیازمندی‌های ویژگی و محدودیت، به همراه یک برچسب `defaultQueue` درخواست می‌کنیم.

```js
async function init() {
  if (!navigator.gpu) {
    throw Error("WebGPU not supported.");
  }

  const adapter = await navigator.gpu.requestAdapter();
  if (!adapter) {
    throw Error("Couldn't request WebGPU adapter.");
  }

  const requiredFeatures = [];

  if (adapter.features.has("texture-compression-astc")) {
    requiredFeatures.push("texture-compression-astc");
  }

  const requiredLimits = {};

  // App ideally needs 6 bind groups, so we'll try to request what the app needs
  if (adapter.limits.maxBindGroups >= 6) {
    requiredLimits.maxBindGroups = 6;
  }

  const device = await adapter.requestDevice({
    defaultQueue: {
      label: "my_queue",
    },
    requiredFeatures,
    requiredLimits,
  });

  // …
}
```

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)