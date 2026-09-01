---
title: "GPUDevice: createRenderPipeline() method"
short-title: createRenderPipeline()
slug: Web/API/GPUDevice/createRenderPipeline
page-type: web-api-instance-method
browser-compat: api.GPUDevice.createRenderPipeline
---

{{APIRef("WebGPU API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`createRenderPipeline()`** از رابط {{domxref("GPUDevice")}} یک {{domxref("GPURenderPipeline")}} ایجاد می‌کند که می‌تواند مراحل shading رأس (vertex) و پیکسل (fragment) را کنترل کرده و در یک {{domxref("GPURenderPassEncoder")}} یا {{domxref("GPURenderBundleEncoder")}} استفاده شود.

## Syntax

```js-nolint
createRenderPipeline(descriptor)
```

### Parameters

- `descriptor`
  - : یک شیء شامل ویژگی‌های زیر:
    - `depthStencil` {{optional_inline}}
      - : یک شیء (به [ساختار شیء `depthStencil`](#depthstencil_object_structure) مراجعه کنید) که ویژگی‌های depth-stencil از جمله آزمایش، عملیات و بایاس را توصیف می‌کند.
    - `fragment` {{optional_inline}}
      - : یک شیء (به [ساختار شیء `fragment`](#fragment_object_structure) مراجعه کنید) که نقطه ورود shader پیکسل (fragment) خط لوله و رنگ‌های خروجی آن را توصیف می‌کند. اگر هیچ نقطه ورود shader پیکسلی تعریف نشود، خط لوله هیچ خروجی attachment رنگی تولید نمی‌کند، اما همچنان رسترایزاسیون (rasterization) انجام می‌دهد و بر اساس خروجی موقعیت رأس، مقادیر depth تولید می‌کند. آزمایش عمق و عملیات stencil همچنان قابل استفاده هستند.
    - `label` {{optional_inline}}
      - : یک رشته که برچسبی برای شناسایی شیء فراهم می‌کند، مثلاً در پیام‌های {{domxref("GPUError")}} یا هشدارهای کنسول.
    - `layout`
      - : چیدمان (ساختار، هدف و نوع) تمام منابع GPU (بافرها، بافت‌ها و غیره) که در حین اجرای خط لوله استفاده می‌شوند را تعریف می‌کند. مقادیر ممکن عبارتند از:
        - یک شیء {{domxref("GPUPipelineLayout")}} که با استفاده از {{domxref("GPUDevice.createPipelineLayout()")}} ایجاد شده است و به GPU اجازه می‌دهد از قبل بفهمد چگونه خط لوله را به بهترین شکل اجرا کند.
        - رشته `"auto"` که باعث می‌شود خط لوله بر اساس هر binding تعریف‌شده در کد shader، یک چیدمان گروه binding ضمنی (implicit bind group layout) تولید کند. اگر از `"auto"` استفاده شود، چیدمان‌های گروه binding تولیدشده فقط با خط لوله فعلی قابل استفاده هستند.
    - `multisample` {{optional_inline}}
      - : یک شیء (به [ساختار شیء `multisample`](#multisample_object_structure) مراجعه کنید) که نحوه تعامل خط لوله با attachment های چندنمونه‌ای (multisampled) یک render pass را توصیف می‌کند.
    - `primitive` {{optional_inline}}
      - : یک شیء (به [ساختار شیء `primitive`](#primitive_object_structure) مراجعه کنید) که نحوه ساخت و رسترایزاسیون primitives توسط خط لوله از ورودی‌های رأس آن را توصیف می‌کند.
    - `vertex`
      - : یک شیء (به [ساختار شیء `vertex`](#vertex_object_structure) مراجعه کنید) که نقطه ورود shader رأس خط لوله و چیدمان بافرهای ورودی آن را توصیف می‌کند.

### ساختار شیء `depthStencil`

شیء `depthStencil` می‌تواند شامل ویژگی‌های زیر باشد:

- `depthBias` {{optional_inline}}
  - : عددی که یک بایاس عمق ثابت را نشان می‌دهد که به هر fragment اضافه می‌شود. اگر حذف شود، `depthBias` پیش‌فرض 0 است.
    > [!NOTE]
    > ویژگی‌های `depthBias`، `depthBiasClamp` و `depthBiasSlopeScale` باید برای توپولوژی‌های خط و نقطه روی `0` تنظیم شوند، یعنی اگر [`topology`](#topology) روی `"line-list"`، `"line-strip"` یا `"point-list"` تنظیم شده باشد. در غیر این صورت، یک {{domxref("GPUValidationError")}} تولید شده و {{domxref("GPURenderPipeline")}} برگشتی نامعتبر خواهد بود.
- `depthBiasClamp` {{optional_inline}}
  - : عددی که حداکثر بایاس عمق یک fragment را نشان می‌دهد. اگر حذف شود، `depthBiasClamp` پیش‌فرض 0 است.
- `depthBiasSlopeScale` {{optional_inline}}
  - : عددی که بایاس عمقی را نشان می‌دهد که با شیب fragment مقیاس می‌شود. اگر حذف شود، `depthBiasSlopeScale` پیش‌فرض 0 است.
- `depthCompare` {{optional_inline}}
  - : یک مقدار شمارشی (enumerated) که عملیات مقایسه مورد استفاده برای آزمایش عمق fragment ها در برابر مقادیر depth `depthStencilAttachment` را مشخص می‌کند. مقادیر ممکن عبارتند از:
    - `"never"`: آزمایش‌های مقایسه هرگز موفق نمی‌شوند.
    - `"less"`: یک مقدار ارائه‌شده اگر از مقدار نمونه‌برداری‌شده کمتر باشد، آزمایش مقایسه را قبول می‌کند.
    - `"equal"`: یک مقدار ارائه‌شده اگر با مقدار نمونه‌برداری‌شده برابر باشد، آزمایش مقایسه را قبول می‌کند.
    - `"less-equal"`: یک مقدار ارائه‌شده اگر از مقدار نمونه‌برداری‌شده کمتر یا برابر باشد، آزمایش مقایسه را قبول می‌کند.
    - `"greater"`: یک مقدار ارائه‌شده اگر از مقدار نمونه‌برداری‌شده بیشتر باشد، آزمایش مقایسه را قبول می‌کند.
    - `"not-equal"`: یک مقدار ارائه‌شده اگر با مقدار نمونه‌برداری‌شده برابر نباشد، آزمایش مقایسه را قبول می‌کند.
    - `"greater-equal"`: یک مقدار ارائه‌شده اگر از مقدار نمونه‌برداری‌شده بیشتر یا برابر باشد، آزمایش مقایسه را قبول می‌کند.
    - `"always"`: آزمایش‌های مقایسه همیشه موفق می‌شوند.

    `depthCompare` اگر `format` مشخص‌شده دارای مؤلفه depth نباشد، یا اگر عملیات مقایسه استفاده نشود، الزامی نیست.

- `depthWriteEnabled` {{optional_inline}}
  - : یک مقدار بولی. مقدار `true` مشخص می‌کند که {{domxref("GPURenderPipeline")}} می‌تواند مقادیر depth `depthStencilAttachment` را پس از ایجاد تغییر دهد. تنظیم آن روی `false` به این معنی است که نمی‌تواند.

    `depthWriteEnabled` اگر `format` مشخص‌شده دارای مؤلفه depth نباشد، الزامی نیست.

- `format`
  - : یک مقدار شمارشی که فرمت `depthStencilAttachment` را که {{domxref("GPURenderPipeline")}} با آن سازگار خواهد بود مشخص می‌کند. برای همه مقادیر `format` موجود، به بخش [Texture Formats](https://gpuweb.github.io/gpuweb/#enumdef-gputextureformat) در مشخصات مراجعه کنید.
- `stencilBack` {{optional_inline}}
  - : یک شیء که نحوه انجام مقایسه‌ها و عملیات stencil برای primitives رو به عقب (back-facing) را تعریف می‌کند. ویژگی‌های آن می‌توانند شامل موارد زیر باشند:
    - `compare` {{optional_inline}}
      - : یک مقدار شمارشی که عملیات مقایسه مورد استفاده هنگام آزمایش fragment ها در برابر مقادیر stencil `depthStencilAttachment` را مشخص می‌کند. مقادیر ممکن همانند مقادیر ویژگی `depthCompare` هستند؛ به بالا مراجعه کنید. اگر حذف شود، `compare` پیش‌فرض `"always"` است.
    - `depthFailOp` {{optional_inline}}
      - : یک مقدار شمارشی که عملیات stencil انجام‌شده در صورت شکست مقایسه عمق fragment که توسط `depthCompare` توصیف شده را مشخص می‌کند. مقادیر ممکن عبارتند از:
        - `"decrement-clamp"`: مقدار stencil حالت رندر فعلی را کاهش می‌دهد و آن را روی 0 قفل می‌کند.
        - `"decrement-wrap"`: مقدار stencil حالت رندر فعلی را کاهش می‌دهد و اگر مقدار به زیر 0 برود، آن را به حداکثر مقدار قابل نمایش جنبه stencil مربوط به `depthStencilAttachment` می‌پیچاند.
        - `"invert"`: مقدار stencil حالت رندر فعلی را به صورت بیتی معکوس می‌کند.
        - `"increment-clamp"`: مقدار stencil حالت رندر فعلی را افزایش می‌دهد و آن را به حداکثر مقدار قابل نمایش جنبه stencil مربوط به `depthStencilAttachment` قفل می‌کند.
        - `"increment-wrap"`: مقدار stencil حالت رندر فعلی را افزایش می‌دهد و اگر مقدار از حداکثر مقدار قابل نمایش جنبه stencil مربوط به `depthStencilAttachment` بیشتر شود، آن را به صفر می‌پیچاند.
        - `"keep"`: مقدار stencil فعلی را حفظ می‌کند.
        - `"replace"`: مقدار stencil را به مقدار stencil حالت رندر فعلی تنظیم می‌کند.
        - `"zero"`: مقدار stencil را روی 0 تنظیم می‌کند.

        اگر حذف شود، `depthFailOp` پیش‌فرض `"keep"` است.

        > [!NOTE]
        > مقدار stencil حالت رندر در شروع یک render pass روی 0 مقداردهی اولیه می‌شود.

    - `failOp` {{optional_inline}}
      - : یک مقدار شمارشی که عملیات stencil انجام‌شده در صورت شکست آزمایش مقایسه stencil fragment که توسط `compare` توصیف شده را مشخص می‌کند. مقادیر ممکن و پیش‌فرض همانند `depthFailOp` هستند.
    - `passOp` {{optional_inline}}
      - : یک مقدار شمارشی که عملیات stencil انجام‌شده در صورت موفقیت آزمایش مقایسه stencil fragment که توسط `compare` توصیف شده را مشخص می‌کند. مقادیر ممکن و پیش‌فرض همانند `depthFailOp` هستند.

- `stencilFront` {{optional_inline}}
  - : یک شیء که نحوه انجام مقایسه‌ها و عملیات stencil برای primitives رو به جلو (front-facing) را تعریف می‌کند. ویژگی‌های آن همانند `stencilBack` هستند.
- `stencilReadMask` {{optional_inline}}
  - : یک bitmask که کنترل می‌کند کدام بیت‌های مقدار stencil `depthStencilAttachment` هنگام انجام آزمایش‌های مقایسه stencil خوانده شوند. اگر حذف شود، `stencilReadMask` پیش‌فرض `0xFFFFFFFF` است.
- `stencilWriteMask` {{optional_inline}}
  - : یک bitmask که کنترل می‌کند کدام بیت‌های مقدار stencil `depthStencilAttachment` هنگام انجام عملیات stencil نوشته شوند. اگر حذف شود، `stencilWriteMask` پیش‌فرض `0xFFFFFFFF` است.

> [!NOTE]
> مقادیر `depthStencilAttachment` در طول فراخوانی‌های {{domxref("GPUCommandEncoder.beginRenderPass()")}}، زمانی که {{domxref("GPURenderPipeline")}} واقعاً برای اجرای یک render pass استفاده می‌شود، مشخص می‌شوند.

### ساختار شیء `fragment`

شیء `fragment` شامل یک آرایه از اشیاء است که هر کدام می‌توانند ویژگی‌های زیر را داشته باشند:

- `constants` {{optional_inline}}
  - : یک دنباله از انواع رکورد، با ساختار `(id, value)`، که مقادیر override برای [WGSL constant های قابل override در خط لوله](https://gpuweb.github.io/gpuweb/#typedefdef-gpupipelineconstantvalue) را نشان می‌دهند. اینها مانند [نقشه‌های مرتب](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map) رفتار می‌کنند. در هر مورد، `id` کلیدی است که برای شناسایی یا انتخاب رکورد استفاده می‌شود و `constant` یک مقدار شمارشی است که یک WGSL را نشان می‌دهد.

    بسته به اینکه کدام constant را می‌خواهید override کنید، `id` ممکن است به صورت شناسه عددی constant (اگر مشخص شده باشد) یا در غیر این صورت نام شناسه constant باشد.

    یک قطعه کد که مقادیر override را برای چند constant قابل override فراهم می‌کند ممکن است به این شکل باشد:

    ```js
    ({
      // …
      constants: {
        0: false,
        1200: 3.0,
        1300: 2.0,
        width: 20,
        depth: -1,
        height: 15,
      },
    });
    ```

- `entryPoint` {{optional_inline}}
  - : نام تابع در `module` که این مرحله برای انجام کار خود از آن استفاده خواهد کرد. تابع shader مربوطه باید ویژگی `@fragment` را داشته باشد تا به عنوان این نقطه ورود شناسایی شود. برای اطلاعات بیشتر به [Entry Point Declaration](https://gpuweb.github.io/gpuweb/wgsl/#entry-point-decl) مراجعه کنید.

    اگر کد shader شما فقط یک تابع با ویژگی `@fragment` داشته باشد، می‌توانید ویژگی `entryPoint` را حذف کنید — مرورگر از آن به عنوان نقطه ورود پیش‌فرض استفاده خواهد کرد. اگر `entryPoint` حذف شود و مرورگر نتواند نقطه ورود پیش‌فرض را تعیین کند، یک {{domxref("GPUValidationError")}} تولید شده و {{domxref("GPURenderPipeline")}} حاصل نامعتبر خواهد بود.

- `module`
  - : یک شیء {{domxref("GPUShaderModule")}} حاوی کد [WGSL](https://gpuweb.github.io/gpuweb/wgsl/) که این مرحله قابل برنامه‌ریزی اجرا خواهد کرد.
- `targets`
  - : آرایه‌ای از اشیاء که حالت‌های رنگی را نشان می‌دهند و جزئیات پیکربندی رنگ‌های خروجی مرحله shader پیکسل را فراهم می‌کنند. این اشیاء می‌توانند شامل ویژگی‌های زیر باشند:
    - `blend` {{optional_inline}}
      - : یک شیء که حالت ترکیب (blend mode) را که باید روی رنگ خروجی اعمال شود توصیف می‌کند. `blend` دو ویژگی دارد:
        - `alpha`
          - : مقدار کانال آلفا را توصیف می‌کند.
        - `color`
          - : مقدار رنگ را توصیف می‌کند.

        هر دو `alpha` و `color` یک شیء را به عنوان مقدار می‌پذیرند که می‌تواند شامل ویژگی‌های زیر باشد:
        - `dstFactor` {{optional_inline}}
          - : یک مقدار شمارشی که عملیات factor ترکیب را که باید روی مقادیر attachment هدف انجام شود تعریف می‌کند. مقادیر ممکن عبارتند از:
            - `"constant"`
            - `"dst"`
            - `"dst-alpha"`
            - `"one"`
            - `"one-minus-dst"`
            - `"one-minus-src"`
            - `"one-minus-src1"`
            - `"one-minus-src-alpha"`
            - `"one-minus-src1-alpha"`
            - `"one-minus-dst-alpha"`
            - `"one-minus-constant"`
            - `"src"`
            - `"src1"`
            - `"src-alpha"`
            - `"src1-alpha"`
            - `"src-alpha-saturated"`
            - `"zero"`

            اگر حذف شود، `dstFactor` پیش‌فرض `"zero"` است.

            > [!NOTE]
            > برای استفاده موفقیت‌آمیز از عملیات factor ترکیب `src1`، `one-minus-src1`، `src1-alpha` و `one-minus-src1-alpha`، باید [feature](/en-US/docs/Web/API/GPUSupportedFeatures) `dual-source-blending` فعال باشد. در غیر این صورت، یک {{domxref("GPUValidationError")}} تولید می‌شود.

        - `operation` {{optional_inline}}
          - : یک مقدار شمار