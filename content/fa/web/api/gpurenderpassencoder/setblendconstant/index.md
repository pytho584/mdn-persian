---
title: "GPURenderPassEncoder: setBlendConstant() method"
short-title: setBlendConstant()
slug: Web/API/GPURenderPassEncoder/setBlendConstant
page-type: web-api-instance-method
browser-compat: api.GPURenderPassEncoder.setBlendConstant
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`setBlendConstant()`** در رابط {{domxref("GPURenderPassEncoder")}}، رنگ و مقدار آلفای ثابتِ مورد استفاده برای ترکیب (blend) را با فاکتورهای ترکیب `"constant"` و `"one-minus-constant"` تنظیم می‌کند (همان‌طور که در توصیفگر متد {{domxref("GPUDevice.createRenderPipeline()")}}، در ویژگی `blend` تنظیم شده است).

## Syntax

```js-nolint
setBlendConstant(color)
```

### Parameters

- `color`
  - : یک شیء یا آرایه که رنگ مورد استفاده برای ترکیب را نشان می‌دهد — مؤلفه‌های `r`، `g`، `b` و `a` به صورت اعداد اعشاری بین 0.0 و 1.0 نمایش داده می‌شوند.

    در ادامه یک مثال با شیء آورده شده است:

    ```js
    const color = { r: 0.0, g: 0.5, b: 1.0, a: 1.0 };
    ```

    معادل آرایه‌ای آن به این صورت خواهد بود:

    ```js
    const color = [0.0, 0.5, 1.0, 1.0];
    ```

> [!NOTE]
> اگر فراخوانی `setBlendConstant()` انجام نشود، مقدار رنگ ثابت ترکیب برای هر پاس رندر به صورت پیش‌فرض `(0, 0, 0, 0)` خواهد بود.

### Return value

هیچ ({{jsxref("undefined")}}).

## Examples

```js
// …

const passEncoder = commandEncoder.beginRenderPass(renderPassDescriptor);

passEncoder.setPipeline(renderPipeline);
passEncoder.setVertexBuffer(0, vertexBuffer);
passEncoder.setBlendConstant([1.0, 0.0, 0.0, 1.0]);
passEncoder.draw(3);

passEncoder.end();

// …
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
