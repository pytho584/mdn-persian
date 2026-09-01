---
title: "GPUQueue: writeBuffer() method"
short-title: writeBuffer()
slug: Web/API/GPUQueue/writeBuffer
page-type: web-api-instance-method
browser-compat: api.GPUQueue.writeBuffer
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`writeBuffer()`** از رابط {{domxref("GPUQueue")}}، داده‌های یک منبع داده را در یک {{domxref("GPUBuffer")}} مشخص می‌نویسد.

این یک تابع کمکی است که جایگزینی برای تنظیم داده‌های بافر از طریق نگاشت بافر و کپی‌های بافر‌به‌بافر فراهم می‌کند. این تابع به عامل کاربر اجازه می‌دهد تا کارآمدترین روش را برای کپی کردن داده‌ها تعیین کند.

## نحو

```js-nolint
writeBuffer(buffer, bufferOffset, data, dataOffset, size)
```

### پارامترها

- `buffer`
  - : یک شیء {{domxref("GPUBuffer")}} که بافر مقصد برای نوشتن داده‌ها را نشان می‌دهد.
- `bufferOffset`
  - : عددی که آفست شروع نوشتن داده‌ها را در داخل {{domxref("GPUBuffer")}} بر حسب بایت مشخص می‌کند.
- `data`
  - : شیئی که منبع داده برای نوشتن در {{domxref("GPUBuffer")}} را نشان می‌دهد. این شیء می‌تواند یک {{jsxref("ArrayBuffer")}}، {{jsxref("TypedArray")}} یا {{jsxref("DataView")}} باشد.
- `dataOffset` {{optional_inline}}
  - : عددی که آفست شروع خواندن داده‌ها از داخل منبع داده را مشخص می‌کند. اگر `data` یک {{jsxref("TypedArray")}} باشد، این مقدار بر حسب تعداد عناصر است و در غیر این صورت بر حسب بایت. اگر حذف شود، `dataOffset` پیش‌فرض ۰ است.
- `size` {{optional_inline}}
  - : عددی که اندازه محتوایی را که باید از `data` به `buffer` نوشته شود مشخص می‌کند. اگر `data` یک {{jsxref("TypedArray")}} باشد، این مقدار بر حسب تعداد عناصر است و در غیر این صورت بر حسب بایت. اگر حذف شود، `size` برابر با اندازه کل `data` منهای `dataOffset` خواهد بود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `OperationError` {{domxref("DOMException")}}
  - : اگر معیارهای زیر برقرار نباشند، متد یک `OperationError` پرتاب می‌کند:
    - اندازه `data` بزرگ‌تر یا مساوی ۰ باشد.
    - `dataOffset` کوچک‌تر یا مساوی اندازه `data` باشد.
    - اندازه `data` (در صورت تبدیل به بایت، در مورد `TypedArray`ها) مضربی از ۴ باشد.

### اعتبارسنجی

هنگام فراخوانی **`writeBuffer()`** معیارهای زیر باید برقرار باشند؛ در غیر این صورت یک {{domxref("GPUValidationError")}} تولید و {{domxref("GPUQueue")}} نامعتبر می‌شود:

- `buffer` برای استفاده در دسترس باشد؛ یعنی ناموجود نباشد (`GPUBuffer`ها اگر در حال حاضر {{domxref("GPUBuffer.mapAsync", "mapped", "", "nocode")}} باشند یا (با متد {{domxref("GPUBuffer.destroy()")}}) نابود شده باشند، ناموجود محسوب می‌شوند).
- {{domxref("GPUBuffer.usage")}} بافر شامل پرچم `GPUBufferUsage.COPY_DST` باشد.
- `bufferOffset` پس از تبدیل به بایت، مضربی از ۴ باشد.
- اندازه `data` - `dataOffset` + `bufferOffset` پس از تبدیل به بایت، کوچک‌تر یا مساوی {{domxref("GPUBuffer.size")}} بافر باشد.

## مثال‌ها

در [نمونه رندر پایه](https://mdn.github.io/dom-examples/webgpu-render-demo/) ما، برخی داده‌های رأس را در یک {{jsxref("Float32Array")}} تعریف می‌کنیم که برای رسم مثلث از آن‌ها استفاده خواهیم کرد:

```js
const vertices = new Float32Array([
  0.0, 0.6, 0, 1, 1, 0, 0, 1, -0.5, -0.6, 0, 1, 0, 1, 0, 1, 0.5, -0.6, 0, 1, 0,
  0, 1, 1,
]);
```

برای استفاده از این داده‌ها در خط لوله رندر، باید آن‌ها را در یک {{domxref("GPUBuffer")}} قرار دهیم. ابتدا بافر را می‌سازیم:

```js
const vertexBuffer = device.createBuffer({
  size: vertices.byteLength, // make it big enough to store vertices in
  usage: GPUBufferUsage.VERTEX | GPUBufferUsage.COPY_DST,
});
```

برای انتقال داده‌ها به بافر می‌توانیم از `writeBuffer()` استفاده کنیم:

```js
device.queue.writeBuffer(vertexBuffer, 0, vertices, 0, vertices.length);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)