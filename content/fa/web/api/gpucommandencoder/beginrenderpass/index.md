---
title: "GPUCommandEncoder: beginRenderPass() method"
---

---
title: "GPUCommandEncoder: beginRenderPass() method"
short-title: beginRenderPass()
slug: Web/API/GPUCommandEncoder/beginRenderPass
page-type: web-api-instance-method
browser-compat: api.GPUCommandEncoder.beginRenderPass
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`beginRenderPass()`** از رابط {{domxref("GPUCommandEncoder")}} رمزگذاری یک پاس رندر را آغاز می‌کند و یک {{domxref("GPURenderPassEncoder")}} برمی‌گرداند که می‌توان از آن برای کنترل رندر استفاده کرد.

## Syntax

```js-nolint
beginRenderPass(descriptor)
```

### Parameters

- `descriptor`
  - : یک شیء شامل ویژگی‌های زیر:
    - `colorAttachments`
      - : آرایه‌ای از اشیاء (به [Color attachment object structure](#color_attachment_object_structure) مراجعه کنید) که پیوست‌های رنگی مورد استفاده برای خروجی هنگام اجرای این پاس رندر را تعریف می‌کند.
    - `depthStencilAttachment` {{optional_inline}}
      - : یک شیء (به [Depth/stencil attachment object structure](#depthstencil_attachment_object_structure) مراجعه کنید) که پیوست عمق/استنسیل مورد استفاده برای خروجی و آزمایش هنگام اجرای این پاس رندر را تعریف می‌کند.
    - `label` {{optional_inline}}
      - : رشته‌ای که برچسبی برای شناسایی شیء فراهم می‌کند؛ برای مثال در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.
    - `maxDrawCount` {{optional_inline}}
      - : عددی که حداکثر تعداد فراخوانی‌های draw انجام‌شده در پاس رندر را مشخص می‌کند. برخی پیاده‌سازی‌ها از این مقدار برای اندازه‌دهی کار تزریق‌شده قبل از پاس رندر استفاده می‌کنند. بهتر است مقدار پیش‌فرض یعنی 50000000 را حفظ کنید، مگر اینکه بدانید تعداد فراخوانی‌های draw بیشتری انجام خواهد شد.
    - `occlusionQuerySet` {{optional_inline}}
      - : {{domxref("GPUQuerySet")}}ای که نتایج پرس‌وجوی occlusion را برای این پاس ذخیره می‌کند.
    - `timestampWrites` {{optional_inline}}
      - : آرایه‌ای از اشیاء که مشخص می‌کند مقادیر پرس‌وجوی timestamp کجا و چه زمانی برای این پاس نوشته می‌شوند. این اشیاء ویژگی‌های زیر را دارند:
        - `querySet`
          - : یک {{domxref("GPUQuerySet")}} از نوع `"timestamp"` که نتایج پرس‌وجوی timestamp در آن نوشته می‌شود.
        - `beginningOfPassWriteIndex`
          - : عددی که ایندکس پرس‌وجو در `querySet` را مشخص می‌کند و timestamp مربوط به ابتدای پاس رندر در آن نوشته می‌شود. این ویژگی اختیاری است — اگر تعریف نشود، هیچ timestampای برای ابتدای پاس نوشته نمی‌شود.
        - `endOfPassWriteIndex`
          - : عددی که ایندکس پرس‌وجو در `querySet` را مشخص می‌کند و timestamp مربوط به پایان پاس رندر در آن نوشته می‌شود. این ویژگی اختیاری است — اگر تعریف نشود، هیچ timestampای برای پایان پاس نوشته نمی‌شود.

        > [!NOTE]
        > برای استفاده از پرس‌وجوهای timestamp باید [feature](/en-US/docs/Web/API/GPUSupportedFeatures) به نام `timestamp-query` فعال باشد. مقادیر پرس‌وجوی timestamp بر حسب نانوثانیه نوشته می‌شوند، اما نحوه تعیین این مقدار به پیاده‌سازی وابسته است.

### Color attachment object structure

اشیاء پیوست رنگ می‌توانند ویژگی‌های زیر را داشته باشند:

- `clearValue` {{optional_inline}}
  - : مقدار رنگی که بافت `view` پیش از اجرای پاس رندر با آن پاک‌سازی می‌شود. اگر `loadOp` برابر `"clear"` نباشد، این مقدار نادیده گرفته می‌شود. `clearValue` یک آرایه یا شیء شامل چهار مؤلفه رنگ `r`، `g`، `b` و `a` به صورت اعشاری دریافت می‌کند.

    برای مثال، می‌توانید آرایه‌ای مانند `[0.0, 0.5, 1.0, 1.0]` یا شیء معادل آن `{ r: 0.0, g: 0.5, b: 1.0, a: 1.0 }` را پاس دهید.

    اگر `clearValue` حذف شود، مقدار پیش‌فرض آن `{ r: 0, g: 0, b: 0, a: 0 }` است.

- `depthSlice` {{optional_inline}}
  - : عددی که ایندکس برش عمق سه‌بعدی را مشخص می‌کند و در مورد یک `view` از نوع {{domxref("GPUTextureView")}} سه‌بعدی، خروجی این پیوست رنگ به آن برش نوشته می‌شود. وقتی این مقدار مشخص شود، WebGPU می‌تواند مستقیماً به برش‌های بافت‌های سه‌بعدی درون پاس‌های رندر رندر کند.

- `loadOp`
  - : یک مقدار شمارشی که عملیات بارگذاری مورد نظر برای `view` پیش از اجرای پاس رندر را مشخص می‌کند. مقادیر ممکن عبارت‌اند از:
    - `"clear"`: مقدار `clearValue` را برای این پیوست در پاس رندر بارگذاری می‌کند.
    - `"load"`: مقدار موجود این پیوست را در پاس رندر بارگذاری می‌کند.

    > [!NOTE]
    > توصیه می‌شود در مواردی که مقدار اولیه مهم نیست همیشه از `"clear"` استفاده کنید، زیرا روی برخی دستگاه‌ها مانند گوشی‌های موبایل عملکرد بهتری خواهد داشت.

- `storeOp`
  - : یک مقدار شمارشی که عملیات ذخیره‌سازی مورد نظر برای `view` پس از اجرای پاس رندر را مشخص می‌کند. مقادیر ممکن عبارت‌اند از:
    - `"discard"`: مقدار حاصل از پاس رندر را برای این پیوست دور می‌ریزد.
    - `"store"`: مقدار حاصل از پاس رندر را برای این پیوست ذخیره می‌کند.

- `resolveTarget` {{optional_inline}}
  - : شیءای که زیرمنبع بافت دریافت‌کننده خروجی resolve شده این پیوست رنگ را مشخص می‌کند، اگر `view` چندنمونه‌ای (multisampled) باشد. این می‌تواند یکی از موارد زیر باشد:
    - {{domxref("GPUTextureView")}}
    - {{domxref("GPUTexture")}}: در صورت تمایل به نمای پیش‌فرض می‌تواند به جای `GPUTextureView` استفاده شود. در این زمینه، `GPUTexture` معادل شیء `GPUTextureView`ای است که با فراخوانی {{domxref("GPUTexture.createView()")}} بدون آرگومان ساخته شده باشد.

- `view`
  - : شیءای که زیرمنبع بافت مورد نظر برای خروجی این پیوست رنگ را مشخص می‌کند. این می‌تواند یکی از موارد زیر باشد:
    - {{domxref("GPUTextureView")}}
    - {{domxref("GPUTexture")}}: در صورت تمایل به نمای پیش‌فرض می‌تواند به جای `GPUTextureView` استفاده شود. در این زمینه، `GPUTexture` معادل شیء `GPUTextureView`ای است که با فراخوانی {{domxref("GPUTexture.createView()")}} بدون آرگومان ساخته شده باشد.

    > [!NOTE]
    > هر پیوست رنگ یا عمق/استنسیل باید یک زیرمنبع بافت یکتا باشد و زیرمنبع‌های بافتی که به عنوان پیوست استفاده می‌شوند نمی‌توانند داخل پاس رندر استفاده شوند.

### Depth/stencil attachment object structure

شیء `depthStencilAttachment` می‌تواند ویژگی‌های زیر را داشته باشد:

- `depthClearValue` {{optional_inline}}
  - : عددی که مقدار پاک‌سازی مؤلفه عمق `view` پیش از اجرای پاس رندر را مشخص می‌کند. اگر `depthLoadOp` برابر `"clear"` نباشد، این مقدار نادیده گرفته می‌شود.

    مقدار باید بین 0.0 و 1.0 باشد (شمول).

- `depthLoadOp` {{optional_inline}}
  - : یک مقدار شمارشی که عملیات بارگذاری مورد نظر برای مؤلفه عمق `view` پیش از اجرای پاس رندر را مشخص می‌کند. مقادیر ممکن عبارت‌اند از:
    - `"clear"`: مقدار `clearValue` را برای این پیوست در پاس رندر بارگذاری می‌کند.
    - `"load"`: مقدار موجود این پیوست را در پاس رندر بارگذاری می‌کند.

    > [!NOTE]
    > توصیه می‌شود در مواردی که مقدار اولیه مهم نیست همیشه از `"clear"` استفاده کنید، زیرا روی برخی دستگاه‌ها مانند گوشی‌های موبایل عملکرد بهتری خواهد داشت.

- `depthReadOnly` {{optional_inline}}
  - : یک مقدار بولی. قرار دادن این مقدار روی `true` باعث می‌شود مؤلفه عمق `view` فقط‌خواندنی شود. اگر `depthReadOnly` حذف شود، مقدار پیش‌فرض آن `false` است.

- `depthStoreOp` {{optional_inline}}
  - : یک مقدار شمارشی که عملیات ذخیره‌سازی مورد نظر برای مؤلفه عمق `view` پس از اجرای پاس رندر را مشخص می‌کند. مقادیر ممکن عبارت‌اند از:
    - `"discard"`: مقدار حاصل از پاس رندر را برای این پیوست دور می‌ریزد.
    - `"store"`: مقدار حاصل از پاس رندر را برای این پیوست ذخیره می‌کند.

- `stencilClearValue` {{optional_inline}}
  - : عددی که مقدار پاک‌سازی مؤلفه استنسیل `view` پیش از اجرای پاس رندر را مشخص می‌کند. اگر `stencilLoadOp` برابر `"clear"` نباشد، این مقدار نادیده گرفته می‌شود.

    اگر `stencilClearValue` حذف شود، مقدار پیش‌فرض آن 0 است.

- `stencilLoadOp` {{optional_inline}}
  - : یک مقدار شمارشی که عملیات بارگذاری مورد نظر برای مؤلفه استنسیل `view` پیش از اجرای پاس رندر را مشخص می‌کند. مقادیر ممکن عبارت‌اند از:
    - `"clear"`: مقدار `clearValue` را برای این پیوست در پاس رندر بارگذاری می‌کند.
    - `"load"`: مقدار موجود این پیوست را در پاس رندر بارگذاری می‌کند.

    > [!NOTE]
    > توصیه می‌شود در مواردی که مقدار اولیه مهم نیست همیشه از `"clear"` استفاده کنید، زیرا روی برخی دستگاه‌ها مانند گوشی‌های موبایل عملکرد بهتری خواهد داشت.

- `stencilReadOnly` {{optional_inline}}
  - : یک مقدار بولی. قرار دادن این مقدار روی `true` باعث می‌شود مؤلفه استنسیل `view` فقط‌خواندنی شود. اگر `stencilReadOnly` حذف شود، مقدار پیش‌فرض آن `false` است.

- `stencilStoreOp` {{optional_inline}}
  - : یک مقدار شمارشی که عملیات ذخیره‌سازی مورد نظر برای مؤلفه استنسیل `view` پس از اجرای پاس رندر را مشخص می‌کند. مقادیر ممکن عبارت‌اند از:
    - `"discard"`: مقدار حاصل از پاس رندر را برای این پیوست دور می‌ریزد.
    - `"store"`: مقدار حاصل از پاس رندر را برای این پیوست ذخیره می‌کند.

- `view`
  - : شیءای که زیرمنبع بافت مورد نظر برای خروجی و خواندن در این پیوست عمق/استنسیل را مشخص می‌کند. این می‌تواند یکی از موارد زیر باشد:
    - {{domxref("GPUTextureView")}}
    - {{domxref("GPUTexture")}}: در صورت تمایل به نمای پیش‌فرض می‌تواند به جای `GPUTextureView` استفاده شود. در این زمینه، `GPUTexture` معادل شیء `GPUTextureView`ای است که با فراخوانی {{domxref("GPUTexture.createView()")}} بدون آرگومان ساخته شده باشد.

### Return value

یک نمونه از شیء {{domxref("GPURenderPassEncoder")}}.

### Validation

هنگام فراخوانی **`beginRenderPass()`** باید معیارهای زیر برقرار باشند؛ در غیر این صورت یک {{domxref("GPUValidationError")}} تولید می‌شود و یک {{domxref("GPURenderPassEncoder")}} نامعتبر بازگردانده می‌شود.

عمومی:

- `colorAttachments.length` کمتر یا مساوی `maxColorAttachments` (یکی از {{domxref("GPUSupportedLimits", "limit", "", "nocode")}} در {{domxref("GPUDevice")}}) است.
- اگر `colorAttachments` فقط شامل مقادیر `null` باشد، `depthStencilAttachment` ارائه می‌شود.
- همه `view`ها در `colorAttachments` و `depthStencilAttachment` دارای مقادیر {{domxref("GPUTexture.sampleCount")}} و ابعاد رندر یکسان هستند ({{domxref("GPUTexture.height")}}، {{domxref("GPUTexture.width")}} و {{domxref("GPUTexture.depthOrArrayLayers")}}).
- اگر `occlusionQuerySet` تنظیم شده باشد، {{domxref("GPUQuerySet")}} ارجاع‌داده‌شده دارای `type` از نوع `"occlusion"` است.

برای اشیاء پیوست رنگ:

- `view` قابل رندر است و قالب `view` (یعنی قالبی که در توصیفگر فراخوانی مبدأ {{domxref("GPUTexture.createView()")}} مشخص شده است) یک قالب رنگی قابل رندر است.
- اگر `resolveTarget` ارائه شده باشد:
  - مقدار {{domxref("GPUTexture.sampleCount", "sampleCount")}} بافت مبدأ `view` بزرگ‌تر از 1 است.
  - مقدار {{domxref("GPUTexture.sampleCount", "sampleCount")}} بافت مبدأ `resolveTarget` برابر 1 است.
  - `resolveTarget` قابل رندر است.
  - اندازه زیرمنبع‌هایی که `view` و `resolveTarget` نمای آن‌ها را ارائه می‌دهند با هم مطابقت دارند.
  - قالب‌های `view` و `resolveTarget` با هم مطابقت دارند.
- مقدار [Color attachments bytes per sample](https://gpuweb.github.io/gpuweb/#abstract-opdef-validating-gpurenderpassdescriptors-color-attachment-bytes-per-sample) کمتر یا مساوی `maxColorAttachmentBytesPerSample` (یکی از {{domxref("GPUSupportedLimits", "limit", "", "nocode")}} در {{domxref("GPUDevice")}}) است.
- اگر [`usage`](/en-US/docs/Web/API/GPUTexture/createView#usage) عملیات `GPUTexture.createView()` که نمای مرتبط را ایجاد کرده شامل بیت `TRANSIENT_ATTACHMENT` باشد:
  - `loadOp` برابر `"clear"` است.
  - `storeOp` برابر `"discard"` است.

برای اشیاء پیوست عمق/استنسیل:

- `view` قابل رندر است و قالب آن یک قالب [depth-or-stencil](https://gpuweb.github.io/gpuweb/#depth-or-stencil-format) است.
- اگر `depthLoadOp` برابر `"clear"` تنظیم شده باشد، یک `depthClearValue` معتبر ارائه شده است.
- اگر قالب `view` یک قالب ترکیبی depth-or-stencil باشد، `depthReadOnly` با `stencilReadOnly` مطابقت دارد.
- اگر قالب `view` دارای جنبه عمق باشد و `depthReadOnly` برابر `false` باشد، `depthLoadOp` و `depthStoreOp` ارائه شده‌اند.
- اگر قالب `view` دارای جنبه عمق باشد و `depthReadOnly` برابر `true` باشد، `depthLoadOp` و `depthStoreOp` ارائه نشده‌اند.
- اگر قالب `view` دارای جنبه استنسیل باشد و `stencilReadOnly` برابر `false` باشد، `stencilLoadOp` و `stencilStoreOp` ارائه شده‌اند.
- اگر قالب `view` دارای جنبه استنسیل باشد و `stencilReadOnly` برابر `true` باشد، `stencilLoadOp` و `stencilStoreOp` ارائه نشده‌اند.
- اگر [`usage`](/en-US/docs/Web/API/GPUTexture/createView#usage) عملیات `GPUTexture.createView()` که نمای مرتبط را ایجاد کرده شامل بیت `TRANSIENT_ATTACHMENT` باشد:
  - اگر قالب `view` دارای جنبه عمق است:
    - `depthLoadOp` برابر `"clear"` است.
    - `depthStoreOp` برابر `"discard"` است.
  - اگر قالب `view` دارای جنبه استنسیل است:
    - `stencilLoadOp` برابر `"clear"` است.
    - `stencilStoreOp` برابر `"discard"` است.

برای پرس‌وجوهای timestamp:

- ویژگی `timestamp-query` ({{domxref("GPUSupportedFeatures", "feature", "", "nocode")}}) در {{domxref("GPUDevice")}} فعال شده است.

## Examples

در [basic render demo](https://mdn.github.io/dom-examples/webgpu-render-demo/) ما، تعدادی دستور از طریق یک {{domxref("GPUCommandEncoder")}} ثبت می‌شوند. این دستورها از {{domxref("GPURenderPassEncoder")}}ای که با `beginRenderPass()` ایجاد شده سرچشمه می‌گیرند:

```js
// …

// Create GPUCommandEncoder
const commandEncoder = device.createCommandEncoder();

// Create GPURenderPassDescriptor to tell WebGPU which texture to draw into, then initiate render pass

const renderPassDescriptor = {
  colorAttachments: [
    {
      clearValue: clearColor,
      loadOp: "clear",
      storeOp: "store",
      view: context.getCurrentTexture().createView(),
    },
  ],
};

const passEncoder = commandEncoder.beginRenderPass(renderPassDescriptor);

// Draw a triangle

passEncoder.setPipeline(renderPipeline);
passEncoder.setVertexBuffer(0, vertexBuffer);
passEncoder.draw(3);

// End the render pass

passEncoder.end();

device.queue.submit([commandEncoder.finish()]);

// …
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- The [WebGPU API](/en-US/docs/Web/API/WebGPU_API)
