---
title: OES_draw_buffers_indexed
slug: Web/API/OES_draw_buffers_indexed
page-type: web-api-interface
browser-compat: api.OES_draw_buffers_indexed
---

{{APIRef("WebGL")}}

افزونهٔ **`OES_draw_buffers_indexed`** بخشی از [API WebGL](/en-US/docs/Web/API/WebGL_API) است و امکان استفاده از گزینه‌های مختلف ترکیب (blend) را هنگام نوشتن همزمان در چندین بافر رنگی فراهم می‌کند.

افزونه‌های WebGL با استفاده از روش {{domxref("WebGLRenderingContext.getExtension()")}} در دسترس هستند. برای اطلاعات بیشتر، به [استفاده از افزونه‌ها](/en-US/docs/Web/API/WebGL_API/Using_Extensions) در [آموزش WebGL](/en-US/docs/Web/API/WebGL_API/Tutorial) مراجعه کنید.

> [!NOTE]
> این افزونه فقط در زمینه‌های {{domxref("WebGL2RenderingContext", "WebGL2", "", 1)}} در دسترس است.

## روش‌های نمونه

- {{DOMxRef("OES_draw_buffers_indexed.blendEquationiOES()")}}
  - : معادلهٔ ترکیب (blend equation) RGB و آلفا را برای یک بافر ترسیم خاص تنظیم می‌کند.
- {{DOMxRef("OES_draw_buffers_indexed.blendEquationSeparateiOES()")}}
  - : معادلهٔ ترکیب RGB و آلفا را به‌طور جداگانه برای یک بافر ترسیم خاص تنظیم می‌کند.
- {{DOMxRef("OES_draw_buffers_indexed.blendFunciOES()")}}
  - : تابعی را که هنگام ترکیب پیکسل‌ها برای یک بافر ترسیم خاص استفاده می‌شود، تعریف می‌کند.
- {{DOMxRef("OES_draw_buffers_indexed.blendFuncSeparateiOES()")}}
  - : تابعی را که هنگام ترکیب پیکسل‌ها برای مؤلفه‌های RGB و آلفا به‌طور جداگانه برای یک بافر ترسیم خاص استفاده می‌شود، تعریف می‌کند.
- {{DOMxRef("OES_draw_buffers_indexed.colorMaskiOES()")}}
  - : مشخص می‌کند کدام مؤلفه‌های رنگی هنگام رسم یا رندر کردن برای یک بافر ترسیم خاص فعال یا غیرفعال شوند.
- {{DOMxRef("OES_draw_buffers_indexed.disableiOES()")}}
  - : ترکیب (blending) را برای یک بافر ترسیم خاص غیرفعال می‌کند.
- {{DOMxRef("OES_draw_buffers_indexed.enableiOES()")}}
  - : ترکیب را برای یک بافر ترسیم خاص فعال می‌کند.

## مثال‌ها

### استفاده از افزونهٔ `OES_draw_buffers_indexed`

افزونه را با فراخوانی {{domxref("WebGLRenderingContext.getExtension()")}} فعال کنید.

```js
const ext = gl.getExtension("OES_draw_buffers_indexed");
```

اکنون می‌توانید ترکیب (blending) را فعال کنید، معادلهٔ ترکیب، تابع ترکیب، و ماسک رنگی را برای یک بافر ترسیم خاص تنظیم کنید.

```js
// برای gl.DRAW_BUFFER0
ext.enableiOES(gl.BLEND, 0);
ext.blendEquationiOES(0, gl.FUNC_ADD);
ext.blendFunciOES(0, gl.ONE, gl.ONE);
ext.colorMaskiOES(0, 1, 0, 0, 0);

// برای gl.DRAW_BUFFER1
ext.enableiOES(gl.BLEND, 1);
ext.blendEquationSeparateiOES(1, gl.FUNC_ADD, gl.FUNC_SUBTRACT);
ext.blendFuncSeparateiOES(
  1,
  gl.SRC_ALPHA,
  gl.ONE_MINUS_SRC_ALPHA,
  gl.ZERO,
  gl.ZERO,
);
ext.colorMaskiOES(1, 0, 1, 0, 0);
```

برای بازیابی تنظیمات یک بافر ترسیم خاص، از {{domxref("WebGL2RenderingContext.getIndexedParameter()")}} استفاده کنید.

```js
// برای gl.DRAW_BUFFER0
gl.getIndexedParameter(gl.BLEND_EQUATION_RGB, 0);
gl.getIndexedParameter(gl.BLEND_EQUATION_ALPHA, 0);
gl.getIndexedParameter(gl.BLEND_SRC_RGB, 0);
gl.getIndexedParameter(gl.BLEND_SRC_ALPHA, 0);
gl.getIndexedParameter(gl.BLEND_DST_RGB, 0);
gl.getIndexedParameter(gl.BLEND_DST_ALPHA, 0);
gl.getIndexedParameter(gl.COLOR_WRITEMASK, 0);

// برای gl.DRAW_BUFFER1
gl.getIndexedParameter(gl.BLEND_EQUATION_RGB, 1);
gl.getIndexedParameter(gl.BLEND_EQUATION_ALPHA, 1);
gl.getIndexedParameter(gl.BLEND_SRC_RGB, 1);
gl.getIndexedParameter(gl.BLEND_SRC_ALPHA, 1);
gl.getIndexedParameter(gl.BLEND_DST_RGB, 1);
gl.getIndexedParameter(gl.BLEND_DST_ALPHA, 1);
gl.getIndexedParameter(gl.COLOR_WRITEMASK, 1);
```

می‌توانید از {{domxref("WebGLRenderingContext.getParameter()")}} برای مشاهدهٔ تعداد بافرهای ترسیم موجود استفاده کنید.

```js
const maxDrawBuffers = gl.getParameter(gl.MAX_DRAW_BUFFERS);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}