```
---
title: "HTMLCanvasElement: getContext() method"
short-title: getContext()
slug: Web/API/HTMLCanvasElement/getContext
page-type: web-api-instance-method
browser-compat: api.HTMLCanvasElement.getContext
---

{{APIRef("Canvas API")}}

متد **`HTMLCanvasElement.getContext()`** یک بافت ترسیمی (drawing context) روی بوم برمی‌گرداند؛ یا اگر شناسهٔ بافت پشتیبانی نشود یا بوم از قبل در حالت بافت دیگری قرار گرفته باشد، مقدار [`null`](/en-US/docs/Web/JavaScript/Reference/Operators/null) برمی‌گرداند.

فراخوانی‌های بعدی این متد روی همان عنصر بوم، با آرگومان `contextType` یکسان، همیشه همان نمونهٔ بافت ترسیمی را برمی‌گردانند که در نخستین فراخوانی بازگردانده شده است. به‌دست آوردن یک شیء بافت ترسیمی متفاوت روی یک عنصر بوم مشخص امکان‌پذیر نیست.

## نحو (Syntax)

```js-nolint
getContext(contextType)
getContext(contextType, contextAttributes)
```

### پارامترها

- `contextType`
  - : رشته‌ای شامل شناسهٔ بافت که بافت ترسیمی مرتبط با بوم را تعریف می‌کند. مقادیر ممکن عبارت‌اند از:
    - `"2d"`
      - : یک شیء {{domxref("CanvasRenderingContext2D")}} ایجاد می‌کند که یک بافت رندر دوبعدی را نشان می‌دهد.
    - `"webgl"` (یا `"experimental-webgl"`)
      - : یک شیء {{domxref("WebGLRenderingContext")}} ایجاد می‌کند که یک بافت رندر سه‌بعدی را نشان می‌دهد. این بافت فقط در مرورگرهایی در دسترس است که [WebGL](/en-US/docs/Web/API/WebGL_API) نسخهٔ ۱ (OpenGL ES 2.0) را پیاده‌سازی کرده باشند.
    - `"webgl2"`
      - : یک شیء {{domxref("WebGL2RenderingContext")}} ایجاد می‌کند که یک بافت رندر سه‌بعدی را نشان می‌دهد. این بافت فقط در مرورگرهایی در دسترس است که [WebGL](/en-US/docs/Web/API/WebGL_API) نسخهٔ ۲ (OpenGL ES 3.0) را پیاده‌سازی کرده باشند.
    - `"webgpu"`
      - : یک شیء {{domxref("GPUCanvasContext")}} ایجاد می‌کند که یک بافت رندر سه‌بعدی برای خط لوله‌های رندر WebGPU را نشان می‌دهد. این بافت فقط در مرورگرهایی در دسترس است که [The WebGPU API](/en-US/docs/Web/API/WebGPU_API) را پیاده‌سازی کرده باشند.
    - `"bitmaprenderer"`
      - : یک {{domxref("ImageBitmapRenderingContext")}} ایجاد می‌کند که فقط قابلیت جایگزینی محتوای بوم با یک {{domxref("ImageBitmap")}} داده‌شده را فراهم می‌کند.

    > [!NOTE]
    > شناسهٔ `"experimental-webgl"` در پیاده‌سازی‌های جدیدِ WebGL استفاده می‌شود. این پیاده‌سازی‌ها یا به هم‌خوانی با مجموعه‌آزمون (test suite conformance) نرسیده‌اند، یا درایورهای گرافیکی روی سکو هنوز پایدار نیستند. گروه [Khronos Group](https://www.khronos.org/) پیاده‌سازی‌های WebGL را تحت [قوانین هم‌خوانی](https://registry.khronos.org/webgl/sdk/tests/CONFORMANCE_RULES.txt) خاصی گواهی می‌کند.

- `contextAttributes` {{optional_inline}}
  - : هنگام ایجاد بافت رندر خود می‌توانید چندین ویژگی بافت (context attribute) استفاده کنید، برای مثال:

    ```js
    const gl = canvas.getContext("webgl", {
      antialias: false,
      depth: false,
    });
    ```

    ویژگی‌های بافت 2d:
    - `alpha`
      - : یک مقدار بولی که نشان می‌دهد آیا بوم دارای کانال آلفا است یا خیر. اگر روی `false` تنظیم شود، مرورگر می‌داند که پس‌زمینه همیشه مات است، که می‌تواند ترسیم محتواها و تصاویر شفاف را سرعت بخشد.
    - `colorSpace` {{optional_inline}}
      - : فضای رنگی بافت رندر را مشخص می‌کند. مقادیر ممکن عبارت‌اند از:
        - `"srgb"` فضای رنگی [sRGB](https://en.wikipedia.org/wiki/SRGB) را انتخاب می‌کند. این مقدار پیش‌فرض است.
        - `"display-p3"` فضای رنگی [display-p3](https://en.wikipedia.org/wiki/DCI-P3) را انتخاب می‌کند.
    - `colorType` {{optional_inline}}
      - : نوع رنگ بافت رندر را مشخص می‌کند. مقادیر ممکن عبارت‌اند از:
        - `"unorm8"` کانال‌های رنگ را به مقادیر بدون علامت ۸ بیتی تنظیم می‌کند. این مقدار پیش‌فرض است.
        - `"float16"` کانال‌های رنگ را به مقادیر اعشار شناور ۱۶ بیتی تنظیم می‌کند.
    - `desynchronized`
      - : یک مقدار بولی که به عامل کاربر (user agent) راهنمایی می‌دهد تا با خارج کردن چرخهٔ ترسیم بوم از هم‌گامی با حلقهٔ رویداد (event loop)، تأخیر را کاهش دهد.
    - `willReadFrequently`
      - : یک مقدار بولی که نشان می‌دهد آیا عملیات خواندن مجدد زیادی برنامه‌ریزی شده است یا خیر. این کار استفاده از بوم دوبعدی نرم‌افزاری (به‌جای شتاب‌دهی‌شده با سخت‌افزار) را اجباری می‌کند و هنگام فراخوانی مکرر {{domxref("CanvasRenderingContext2D.getImageData", "getImageData()")}} می‌تواند حافظه را ذخیره کند.

    ویژگی‌های بافت WebGL:
    - `alpha`
      - : یک مقدار بولی که نشان می‌دهد آیا بوم دارای بافر آلفا است یا خیر.
    - `depth`
      - : یک مقدار بولی که نشان می‌دهد درخواست می‌شود بافر ترسیم دارای بافر عمق حداقل ۱۶ بیتی باشد.
    - `stencil`
      - : یک مقدار بولی که نشان می‌دهد درخواست می‌شود بافر ترسیم دارای بافر استنسیل حداقل ۸ بیتی باشد.
    - `desynchronized`
      - : یک مقدار بولی که به عامل کاربر راهنمایی می‌دهد تا با خارج کردن چرخهٔ ترسیم بوم از هم‌گامی با حلقهٔ رویداد، تأخیر را کاهش دهد.
    - `antialias`
      - : یک مقدار بولی که نشان می‌دهد در صورت امکان ضدآلیاسینگ (anti-aliasing) انجام شود یا نه.
    - `failIfMajorPerformanceCaveat`
      - : یک مقدار بولی که نشان می‌دهد آیا اگر کارایی سیستم پایین باشد یا GPU سخت‌افزاری در دسترس نباشد، بافتی ایجاد خواهد شد یا خیر.
    - `powerPreference`
      - : یک راهنمایی به عامل کاربر که نشان می‌دهد چه پیکربندی از GPU برای بافت WebGL مناسب است. مقادیر ممکن عبارت‌اند از:
        - `"default"`
          - : به عامل کاربر اجازه می‌دهد تا تصمیم بگیرد کدام پیکربندی GPU مناسب‌ترین است. این مقدار پیش‌فرض است.
        - `"high-performance"`
          - : کارایی رندر را بر مصرف انرژی اولویت می‌دهد.
        - `"low-power"`
          - : صرفه‌جویی در مصرف انرژی را بر کارایی رندر اولویت می‌دهد.

    - `premultipliedAlpha`
      - : یک مقدار بولی که نشان می‌دهد ترکیب‌کنندهٔ صفحه (page compositor) فرض خواهد کرد بافر ترسیم شامل رنگ‌هایی با آلفای پیش‌ضرب (pre-multiplied alpha) است.
    - `preserveDrawingBuffer`
      - : اگر مقدار درست (true) باشد، بافرها پاک نمی‌شوند و مقادیر خود را حفظ می‌کنند تا زمانی که توسط توسعه‌دهنده پاک یا بازنویسی شوند.
    - `xrCompatible`
      - : یک مقدار بولی که به عامل کاربر راهنمایی می‌دهد برای یک [دستگاه XR فراگیر](/en-US/docs/Web/API/WebXR_Device_API) از آداپتور گرافیکی سازگار استفاده کند. تنظیم این پرچم هم‌زمان هنگام ایجاد بافت توصیه نمی‌شود؛ در عوض، به محض اینکه قصد شروع یک نشست XR را داشتید، متد ناهم‌زمان {{domxref("WebGLRenderingContext.makeXRCompatible()")}} را فراخوانی کنید.

    > [!NOTE]
    > مشخصات WebGPU هیچ ویژگی بافت خاصی برای `getContext()` تعریف نمی‌کند. در عوض، گزینه‌های پیکربندی را از طریق متد {{domxref("GPUCanvasContext.configure()")}} فراهم می‌کند.

### مقدار بازگشتی

یک بافت رندر که یکی از این موارد است:

- {{domxref("CanvasRenderingContext2D")}} برای `"2d"`،
- {{domxref("WebGLRenderingContext")}} برای `"webgl"` و `"experimental-webgl"`،
- {{domxref("WebGL2RenderingContext")}} برای `"webgl2"`،
- {{domxref("GPUCanvasContext")}} برای `"webgpu"`،
- {{domxref("ImageBitmapRenderingContext")}} برای `"bitmaprenderer"`.

اگر شناسهٔ بافت پشتیبانی نشود، یا بوم از قبل در حالت بافت دیگری قرار گرفته باشد، `null` برگردانده می‌شود.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : این خطا پرتاب می‌شود اگر بوم کنترل خود را با فراخوانی {{domxref("HTMLCanvasElement.transferControlToOffscreen()")}} به حالت برون‌صفحه‌ای (offscreen) منتقل کرده باشد.

## مثال‌ها

با توجه به این عنصر {{HTMLElement("canvas")}}:

```html
<canvas id="canvas" width="300" height="300"></canvas>
```

می‌توانید بافت `2d` بوم را با کد زیر دریافت کنید:

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
console.log(ctx); // CanvasRenderingContext2D { /* … */ }
```

اکنون [بافت رندر دوبعدی](/en-US/docs/Web/API/CanvasRenderingContext2D) را برای بوم دارید و می‌توانید درون آن ترسیم کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLCanvasElement")}}: واسطی که برای تعریف متد `HTMLCanvasElement.getContext()` استفاده می‌شود.
- {{domxref("OffscreenCanvas.getContext()")}}
- {{domxref("CanvasRenderingContext2D.getContextAttributes()")}}, {{domxref("WebGLRenderingContext.getContextAttributes()")}}
- {{domxref("CanvasRenderingContext2D")}}، {{domxref("ImageBitmapRenderingContext")}}، {{domxref("WebGLRenderingContext")}}، {{domxref("WebGL2RenderingContext")}}، {{domxref("GPUCanvasContext")}}: بافت‌های رندر موجود
- [فضای رنگی DCI-P3](https://en.wikipedia.org/wiki/DCI-P3) در ویکی‌پدیا
- [فضای رنگی sRGB](https://en.wikipedia.org/wiki/SRGB) در ویکی‌پدیا
```