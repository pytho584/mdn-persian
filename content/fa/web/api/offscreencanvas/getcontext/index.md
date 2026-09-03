---
title: "OffscreenCanvas: getContext() method"
short-title: getContext()
slug: Web/API/OffscreenCanvas/getContext
page-type: web-api-instance-method
browser-compat: api.OffscreenCanvas.getContext
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

متد **`OffscreenCanvas.getContext()`** یک context ترسیم برای یک بوم خارج از صفحه (offscreen canvas) برمی‌گرداند. اگر شناسهٔ context پشتیبانی نشود، یا اگر بوم خارج از صفحه از قبل در حالت context متفاوتی قرار گرفته باشد، [`null`](/en-US/docs/Web/JavaScript/Reference/Operators/null) برگردانده می‌شود.

## سینتکس

```js-nolint
getContext(contextType, contextAttributes)
```

### پارامترها

- `contextType`
  - : رشته‌ای حاوی شناسهٔ context است که context ترسیم مرتبط با بوم را تعریف می‌کند. مقادیر ممکن عبارت‌اند از:
    - `2d`
      - : یک شیء {{domxref("OffscreenCanvasRenderingContext2D")}} می‌سازد که یک context رندر دوبعدی را نشان می‌دهد.
    - `webgl`
      - : یک شیء {{domxref("WebGLRenderingContext")}} می‌سازد که یک context رندر سه‌بعدی را نشان می‌دهد. این context فقط در مرورگرهایی در دسترس است که [WebGL](/en-US/docs/Web/API/WebGL_API) نسخهٔ ۱ (OpenGL ES 2.0) را پیاده‌سازی می‌کنند.
    - `webgl2`
      - : یک شیء {{domxref("WebGL2RenderingContext")}} می‌سازد که یک context رندر سه‌بعدی را نشان می‌دهد. این context فقط در مرورگرهایی در دسترس است که [WebGL](/en-US/docs/Web/API/WebGL_API) نسخهٔ ۲ (OpenGL ES 3.0) را پیاده‌سازی می‌کنند.
    - `"webgpu"`
      - : یک شیء {{domxref("GPUCanvasContext")}} می‌سازد که یک context رندر سه‌بعدی برای خط لولهٔ رندر WebGPU را نشان می‌دهد. این context فقط در مرورگرهایی در دسترس است که [WebGPU API](/en-US/docs/Web/API/WebGPU_API) را پیاده‌سازی می‌کنند.
    - `bitmaprenderer`
      - : یک {{domxref("ImageBitmapRenderingContext")}} می‌سازد که تنها قابلیت جایگزینی محتوای بوم با یک {{domxref("ImageBitmap")}} معین را فراهم می‌کند.

    > [!NOTE]
    > شناسه‌های **`"experimental-webgl"`** و **`"experimental-webgl2"`** نیز در پیاده‌سازی‌های WebGL استفاده می‌شوند. این پیاده‌سازی‌ها هنوز به مطابقت با مجموعهٔ آزمون (test suite) نرسیده‌اند یا وضعیت درایورهای گرافیکی در پلتفرم هنوز پایدار نیست.
    > [گروه Khronos](https://www.khronos.org/) پیاده‌سازی‌های WebGL را طبق [قوانین سازگاری](https://registry.khronos.org/webgl/sdk/tests/CONFORMANCE_RULES.txt) تأیید می‌کند.

- `contextAttributes` {{optional_inline}}
  - : هنگام ایجاد context رندر خود می‌توانید از چندین ویژگی (attribute) استفاده کنید، برای مثال:

    ```js
    const gl = canvas.getContext("webgl", {
      antialias: false,
      depth: false,
    });
    ```

    ویژگی‌های context دوبعدی:
    - `alpha`
      - : یک مقدار بولین که نشان می‌دهد بوم شامل کانال آلفا است یا خیر. اگر روی `false` تنظیم شود، مرورگر می‌داند که پس‌زمینه همیشه مات است؛ این کار می‌تواند ترسیم محتوا و تصاویر شفاف را سرعت ببخشد.
    - `colorSpace` {{optional_inline}}
      - : فضای رنگی context رندر را مشخص می‌کند. مقادیر ممکن عبارت‌اند از:
        - `"srgb"` فضای رنگی [sRGB](https://en.wikipedia.org/wiki/SRGB) را انتخاب می‌کند. این مقدار پیش‌فرض است.
        - `"display-p3"` فضای رنگی [display-p3](https://en.wikipedia.org/wiki/DCI-P3) را انتخاب می‌کند.
    - `colorType` {{optional_inline}}
      - : نوع رنگ context رندر را مشخص می‌کند. مقادیر ممکن عبارت‌اند از:
        - `"unorm8"` کانال‌های رنگ را روی مقادیر بدون علامت ۸ بیتی تنظیم می‌کند. این مقدار پیش‌فرض است.
        - `"float16"` کانال‌های رنگ را روی مقادیر ممیز شناور ۱۶ بیتی تنظیم می‌کند.
    - `desynchronized`
      - : یک مقدار بولین که به عامل کاربر (user agent) پیشنهاد می‌کند با ازهمگام‌سازی چرخهٔ نقاشی بوم از حلقهٔ رویداد، تأخیر را کاهش دهد.
    - `willReadFrequently`
      - : یک مقدار بولین که نشان می‌دهد آیا عملیات بازخوانی (read-back) زیادی برنامه‌ریزی شده است یا خیر. این کار باعث می‌شود از بوم دوبعدی نرم‌افزاری (به‌جای شتاب‌دهی‌شده با سخت‌افزار) استفاده شود و هنگام فراخوانی مکرر {{domxref("CanvasRenderingContext2D.getImageData", "getImageData()")}} می‌تواند در مصرف حافظه صرفه‌جویی کند.

    ویژگی‌های context WebGL:
    - `alpha`
      - : یک مقدار بولین که نشان می‌دهد بوم شامل بافر آلفا باشد یا خیر.
    - `depth`
      - : یک مقدار بولین که نشان می‌دهد بافر ترسیم باید بافر عمق با حداقل ۱۶ بیت داشته باشد.
    - `stencil`
      - : یک مقدار بولین که نشان می‌دهد بافر ترسیم باید بافر استنسیل با حداقل ۸ بیت داشته باشد.
    - `desynchronized`
      - : یک مقدار بولین که به عامل کاربر پیشنهاد می‌کند با ازهمگام‌سازی چرخهٔ نقاشی بوم از حلقهٔ رویداد، تأخیر را کاهش دهد.
    - `antialias`
      - : یک مقدار بولین که نشان می‌دهد در صورت امکان ضدآلیاسینگ (anti-aliasing) انجام شود یا خیر.
    - `failIfMajorPerformanceCaveat`
      - : یک مقدار بولین که نشان می‌دهد اگر کارایی سیستم پایین باشد یا GPU سخت‌افزاری در دسترس نباشد، context ساخته خواهد شد یا خیر.
    - `powerPreference`
      - : راهنمایی برای عامل کاربر دربارهٔ اینکه کدام پیکربندی GPU برای context WebGL مناسب است. مقادیر ممکن عبارت‌اند از:
        - `"default"`
          - : به عامل کاربر اجازه می‌دهد تصمیم بگیرد کدام پیکربندی GPU مناسب‌تر است. این مقدار پیش‌فرض است.
        - `"high-performance"`
          - : کارایی رندر را بر مصرف انرژی مقدم می‌شمارد.
        - `"low-power"`
          - : صرفه‌جویی در مصرف انرژی را بر کارایی رندر مقدم می‌شمارد.

    - `premultipliedAlpha`
      - : یک مقدار بولین که نشان می‌دهد ترکیب‌کنندهٔ صفحه فرض می‌کند بافر ترسیم شامل رنگ‌هایی با آلفای پیش‌ضرب‌شده (pre-multiplied alpha) است.
    - `preserveDrawingBuffer`
      - : اگر مقدار `true` باشد، بافرها پاک نمی‌شوند و مقادیر خود را تا زمانی که توسط نویسنده پاک یا بازنویسی شوند حفظ می‌کنند.
    - `xrCompatible`
      - : یک مقدار بولین که به عامل کاربر پیشنهاد می‌کند از یک آداپتور گرافیکی سازگار برای یک [دستگاه XR همه‌جانبه](/en-US/docs/Web/API/WebXR_Device_API) استفاده کند. تنظیم این پرچم همروند (synchronous) هنگام ایجاد context توصیه نمی‌شود؛ در عوض، به محض اینکه قصد شروع یک نشست XR را دارید، متد ناهمزمان {{domxref("WebGLRenderingContext.makeXRCompatible()")}} را فراخوانی کنید.

    > [!NOTE]
    > مشخصات WebGPU هیچ ویژگی context خاصی برای `getContext()` تعریف نمی‌کند. در عوض، گزینه‌های پیکربندی را از طریق متد {{domxref("GPUCanvasContext.configure()")}} فراهم می‌کند.

### مقدار بازگشتی

یک context رندر که یکی از موارد زیر است:

- {{domxref("OffscreenCanvasRenderingContext2D")}} برای `"2d"`،
- {{domxref("WebGLRenderingContext")}} برای `"webgl"` و `"experimental-webgl"`،
- {{domxref("WebGL2RenderingContext")}} برای `"webgl2"` و `"experimental-webgl2"`،
- {{domxref("GPUCanvasContext")}} برای `"webgpu"`،
- {{domxref("ImageBitmapRenderingContext")}} برای `"bitmaprenderer"`.

اگر شناسهٔ context پشتیبانی نشود، یا اگر بوم از قبل در حالت context متفاوتی قرار گرفته باشد، `null` برگردانده می‌شود.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر بوم به حوزهٔ context دیگری (مثلاً به worker) منتقل شده باشد، پرتاب می‌شود.

## مثال‌ها

```js
const offscreen = new OffscreenCanvas(256, 256);
const gl = offscreen.getContext("webgl");

gl; // WebGLRenderingContext
gl.canvas; // OffscreenCanvas
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- رابطی که این متد را تعریف می‌کند: {{domxref("OffscreenCanvas")}}
- {{domxref("HTMLCanvasElement.getContext()")}}
- contextهای رندر موجود: {{domxref("CanvasRenderingContext2D")}}، {{domxref("WebGLRenderingContext")}}، {{domxref("WebGL2RenderingContext")}}، {{domxref("ImageBitmapRenderingContext")}} و {{domxref("OffscreenCanvasRenderingContext2D")}}