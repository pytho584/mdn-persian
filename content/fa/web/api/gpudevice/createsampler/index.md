---
title: "GPUDevice: createSampler() method"
short-title: createSampler()
slug: Web/API/GPUDevice/createSampler
page-type: web-api-instance-method
browser-compat: api.GPUDevice.createSampler
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`createSampler()`** در رابط {{domxref("GPUDevice")}} یک {{domxref("GPUSampler")}} ایجاد می‌کند که نحوه تبدیل و فیلتر کردن داده‌های منابع بافت توسط شیدرها را کنترل می‌کند.

## Syntax

```js-nolint
createSampler()
createSampler(descriptor)
```

### پارامترها

- `descriptor` {{optional_inline}}
  - : شیءای شامل ویژگی‌های زیر:
    - `addressModeU` {{optional_inline}}
      - : یک مقدار شمارشی که رفتار سمپلر را زمانی که عرض ردپای نمونه‌گیری از عرض بافت فراتر می‌رود مشخص می‌کند. مقادیر ممکن عبارتند از:
        - `"clamp-to-edge"`: مختصات بافت بین 0.0 و 1.0 (هر دو شامل) محدود می‌شوند.
        - `"repeat"`: مختصات بافت به سمت دیگر بافت می‌پیچد.
        - `"mirror-repeat"`: مختصات بافت به سمت دیگر بافت می‌پیچد، اما وقتی قسمت صحیح مختصات فرد باشد، بافت برعکس می‌شود.

        اگر حذف شود، `addressModeU` به‌صورت پیش‌فرض `"clamp-to-edge"` است.

    - `addressModeV` {{optional_inline}}
      - : یک مقدار شمارشی که رفتار سمپلر را زمانی که ارتفاع ردپای نمونه‌گیری از ارتفاع بافت فراتر می‌رود مشخص می‌کند. مقادیر ممکن و پیش‌فرض مانند `addressModeU` است.
    - `addressModeW` {{optional_inline}}
      - : یک مقدار شمارشی که رفتار سمپلر را زمانی که عمق ردپای نمونه‌گیری از عمق بافت فراتر می‌رود مشخص می‌کند. مقادیر ممکن و پیش‌فرض مانند `addressModeU` است.

    - `compare` {{optional_inline}}
      - : اگر مشخص شود، سمپلر یک سمپلر مقایسه‌ای از نوع مشخص‌شده خواهد بود. مقادیر (شمارشی) ممکن عبارتند از:
        - `"never"`: تست‌های مقایسه هرگز موفق نمی‌شوند.
        - `"less"`: یک مقدار داده‌شده اگر از مقدار نمونه‌گیری‌شده کمتر باشد، تست مقایسه را قبول می‌کند.
        - `"equal"`: یک مقدار داده‌شده اگر با مقدار نمونه‌گیری‌شده برابر باشد، تست مقایسه را قبول می‌کند.
        - `"less-equal"`: یک مقدار داده‌شده اگر از مقدار نمونه‌گیری‌شده کمتر یا مساوی باشد، تست مقایسه را قبول می‌کند.
        - `"greater"`: یک مقدار داده‌شده اگر از مقدار نمونه‌گیری‌شده بزرگ‌تر باشد، تست مقایسه را قبول می‌کند.
        - `"not-equal"`: یک مقدار داده‌شده اگر با مقدار نمونه‌گیری‌شده برابر نباشد، تست مقایسه را قبول می‌کند.
        - `"greater-equal"`: یک مقدار داده‌شده اگر از مقدار نمونه‌گیری‌شده بزرگ‌تر یا مساوی باشد، تست مقایسه را قبول می‌کند.
        - `"always"`: تست‌های مقایسه همیشه موفق می‌شوند.

        سمپلرهای مقایسه‌ای ممکن است از فیلتر کردن استفاده کنند، اما نتایج نمونه‌گیری به پیاده‌سازی وابسته خواهد بود و ممکن است با قوانین فیلتر معمولی متفاوت باشد.

    - `label` {{optional_inline}}
      - : رشته‌ای که برچسبی برای شناسایی شیء فراهم می‌کند، مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.

    - `lodMinClamp` {{optional_inline}}
      - : عددی که حداقل سطح جزئیات (level of detail) مورد استفاده داخلی هنگام نمونه‌گیری از بافت را مشخص می‌کند. اگر حذف شود، `lodMinClamp` به‌صورت پیش‌فرض 0 است.
    - `lodMaxClamp` {{optional_inline}}
      - : عددی که حداکثر سطح جزئیات مورد استفاده داخلی هنگام نمونه‌گیری از بافت را مشخص می‌کند. اگر حذف شود، `lodMaxClamp` به‌صورت پیش‌فرض 32 است.

    - `maxAnisotropy` {{optional_inline}}
      - : حداکثر مقدار گیره (clamp) ناهمسانگردی که توسط سمپلر استفاده می‌شود را مشخص می‌کند. اگر حذف شود، `maxAnisotropy` به‌صورت پیش‌فرض 1 است.

        بیشتر پیاده‌سازی‌ها از مقادیر `maxAnisotropy` در بازه بین 1 تا 16 (هر دو شامل) پشتیبانی می‌کنند. مقدار استفاده‌شده تا حداکثر مقداری که پلتفرم زیرین پشتیبانی می‌کند محدود (clamp) خواهد شد.

    - `magFilter` {{optional_inline}}
      - : یک مقدار شمارشی که رفتار نمونه‌گیری را زمانی که ردپای نمونه‌گیری کوچک‌تر یا مساوی یک تکسِل است مشخص می‌کند. مقادیر ممکن عبارتند از:
        - `"nearest"`: مقدار نزدیک‌ترین تکسِل به مختصات بافت را برمی‌گرداند.
        - `"linear"`: در هر بعد دو تکسِل انتخاب می‌کند و درون‌یابی خطی بین مقادیر آن‌ها را برمی‌گرداند.

        اگر حذف شود، `magFilter` به‌صورت پیش‌فرض `"nearest"` است.

        > [!NOTE]
        > برای اینکه بافت‌های {{domxref("GPUTexture")}} با [`format`](/en-US/docs/Web/API/GPUDevice/createTexture#format) های `r32float`، `rg32float` و `rgba32float` قابل فیلتر باشند، [ویژگی](/en-US/docs/Web/API/GPUSupportedFeatures) `float32-filterable` باید فعال باشد.

    - `minFilter` {{optional_inline}}
      - : یک مقدار شمارشی که رفتار نمونه‌گیری را زمانی که ردپای نمونه‌گیری بزرگ‌تر از یک تکسِل است مشخص می‌کند. مقادیر ممکن و پیش‌فرض مانند `magFilter` است.
    - `mipmapFilter` {{optional_inline}}
      - : یک مقدار شمارشی که رفتار هنگام نمونه‌گیری بین سطوح mipmap را مشخص می‌کند. مقادیر ممکن و پیش‌فرض مانند `magFilter` است.

### مقدار بازگشتی

یک نمونه شیء {{dompus()}}.

### اعتبارسنجی

هنگام فراخوانی **`createSampler()`** معیارهای زیر باید برآورده شوند، در غیر این صورت یک {{domxref("GPUValidationError")}} تولید شده و یک شیء نامعتبر {{dompus()}} بازگردانده می‌شود:

- `lodMinClamp` بزرگ‌تر یا مساوی 0 باشد.
- `lodMaxClamp` بزرگ‌تر یا مساوی `lodMinClamp` باشد.
- `maxAnisotropy` بزرگ‌تر یا مساوی 1 باشد.
- اگر `maxAnisotropy` بزرگ‌تر از 1 باشد، `magFilter`، `minFilter` و `mipmapFilter` برابر با `"linear"` باشند.

## مثال‌ها

قطعه کد زیر یک `GPUSampler` ایجاد می‌کند که فیلتر سه‌خطی (trilinear) انجام می‌دهد و مختصات بافت را تکرار می‌کند:

```js
// …

const sampler = device.createSampler({
  addressModeU: "repeat",
  addressModeV: "repeat",
  magFilter: "linear",
  minFilter: "linear",
  mipmapFilter: "linear",
});
```

نمونه [Shadow Mapping](https://webgpu.github.io/webgpu-samples/samples/shadowMapping/) از نمونه‌های WebGPU از سمپلرهای مقایسه‌ای برای نمونه‌گیری از بافت عمق جهت رندر سایه‌ها استفاده می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)