---
title: "GPUComputePassEncoder: dispatchWorkgroupsIndirect() method"
short-title: dispatchWorkgroupsIndirect()
slug: Web/API/GPUComputePassEncoder/dispatchWorkgroupsIndirect
page-type: web-api-instance-method
browser-compat: api.GPUComputePassEncoder.dispatchWorkgroupsIndirect
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`dispatchWorkgroupsIndirect()`** از رابط {{domxref("GPUComputePassEncoder")}} شبکه‌ای از گروه‌های کاری را که ابعاد آن توسط پارامترهای یک {{domxref("GPUBuffer")}} تعریف شده است، برای انجام کار مربوط به {{domxref("GPUComputePipeline")}} جاری (یعنی خط لوله‌ای که با {{domxref("GPUComputePassEncoder.setPipeline()")}} تنظیم شده است) به اجرا درمی‌آورد.

## سینتکس

```js-nolint
dispatchWorkgroupsIndirect(indirectBuffer, indirectOffset)
```

### پارامترها

- `indirectBuffer`
  - : یک {{domxref("GPUBuffer")}} که ابعاد X، Y و Z شبکه گروه‌های کاری موردنظر برای اجرا را در خود دارد. این بافر باید شامل یک بلوک فشرده و پشت‌سرهم از سه مقدار عدد صحیح بدون علامت ۳۲-بیتی باشد که ابعاد را نشان می‌دهند (در مجموع ۱۲ بایت)، به همان ترتیبی که آرگومان‌های {{domxref("GPUComputePassEncoder.dispatchWorkgroups()")}} داده می‌شوند. بنابراین برای مثال:

    ```js
    const uint32 = new Uint32Array(3);
    uint32[0] = 25; // The X value
    uint32[1] = 1; // The Y value
    uint32[2] = 1; // The Z value

    // Write values into a GPUBuffer
    device.queue.writeBuffer(buffer, 0, uint32, 0, uint32.length);
    ```

- `indirectOffset`
  - : آفست (offset) بر حسب بایت در `indirectBuffer` که داده‌های ابعاد از آن‌جا شروع می‌شوند.

> [!NOTE]
> مقادیر ابعاد X، Y و Z که به {{domxref("GPUComputePassEncoder.dispatchWorkgroups()")}} و `dispatchWorkgroupsIndirect()` ارسال می‌شوند، تعداد گروه‌های کاری برای هر بعد هستند، نه تعداد فراخوانی‌های شیدر در هر بعد. این رفتار مطابق رفتار APIهای بومی مدرن GPU است، اما با رفتار OpenCL تفاوت دارد. به این معنا که اگر یک {{domxref("GPUShaderModule")}} نقطه ورود را با `@workgroup_size(4, 4)` تعریف کند و کار با فراخوانی `dispatchWorkgroupsIndirect(indirectBuffer);` در حالی که `indirectBuffer` ابعاد X و Y را ۸ و ۸ مشخص می‌کند، به آن ارسال شود، نقطه ورود در مجموع ۱۰۲۴ بار فراخوانی می‌شود — ارسال یک گروه کاری ۴×۴ به تعداد ۸ بار در امتداد هر دو محور X و Y. `4 * 4 * 8 * 8 = 1024`.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### اعتبارسنجی

هنگام فراخوانی **`dispatchWorkgroupsIndirect()`** باید معیارهای زیر برقرار باشند، در غیر این صورت یک {{domxref("GPUValidationError")}} تولید می‌شود و {{domxref("GPUComputePassEncoder")}} نامعتبر می‌شود:

- پرچم `GPUBufferUsage.INDIRECT` در {{domxref("GPUBuffer.usage")}} مربوط به `indirectBuffer` تنظیم شده باشد.
- `indirectOffset` به‌علاوه اندازه کل مشخص‌شده توسط ابعاد `X`، `Y` و `Z` کمتر یا مساوی {{domxref("GPUBuffer.size")}} مربوط به `indirectBuffer` باشد.
- `indirectOffset` مضربی از ۴ باشد.

## مثال‌ها

```js
// Set global buffer size
const BUFFER_SIZE = 1000;

// Compute shader; note workgroup size of 64
const shader = `
@group(0) @binding(0)
var<storage, read_write> output: array<f32>;

@compute @workgroup_size(64)

...

`;

// …

// Create GPUCommandEncoder to encode commands to issue to the GPU
const commandEncoder = device.createCommandEncoder();

// Initiate compute pass
const passEncoder = commandEncoder.beginComputePass();

// Issue commands
passEncoder.setPipeline(computePipeline);
passEncoder.setBindGroup(0, bindGroup);

const uint32 = new Uint32Array(3);
// Note workgroupCountX is set based on the global buffer size and the shader workgroup count.
uint32[0] = Math.ceil(BUFFER_SIZE / 64);
uint32[1] = 1;
uint32[2] = 1;

const workgroupDimensions = device.createBuffer({
  size: 12,
  usage: GPUBufferUsage.COPY_DST | GPUBufferUsage.INDIRECT,
});
device.queue.writeBuffer(workgroupDimensions, 0, uint32, 0, uint32.length);

passEncoder.dispatchWorkgroupsIndirect(workgroupDimensions, 0);

// End the render pass
passEncoder.end();

// Copy output buffer to staging buffer
commandEncoder.copyBufferToBuffer(
  output,
  0, // Source offset
  stagingBuffer,
  0, // Destination offset
  BUFFER_SIZE,
);

// End frame by passing array of command buffers to command queue for execution
device.queue.submit([commandEncoder.finish()]);

// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)