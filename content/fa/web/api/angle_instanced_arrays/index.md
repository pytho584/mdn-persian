---
title: "ANGLE_instanced_arrays"
source: "https://developer.mozilla.org/en-US/docs/Web/API/ANGLE_instanced_arrays"
translated_by: "n8n + AI"
---

افزونه **`ANGLE_instanced_arrays`** بخشی از [WebGL API](/en-US/docs/Web/API/WebGL_API) است و امکان رسم یک شیء یا گروه‌هایی از اشیای مشابه را چندین بار فراهم می‌کند، به شرطی که داده‌های vertex، تعداد و نوع primitive یکسانی داشته باشند.

افزونه‌های WebGL با استفاده از متد {{domxref("WebGLRenderingContext.getExtension()")}} در دسترس قرار می‌گیرند. برای اطلاعات بیشتر، بخش [استفاده از افزونه‌ها](/en-US/docs/Web/API/WebGL_API/Using_Extensions) در [آموزش WebGL](/en-US/docs/Web/API/WebGL_API/Tutorial) را نیز ببینید.

> [!NOTE]
> این افزونه فقط در contextهای {{domxref("WebGLRenderingContext", "WebGL1", "", 1)}} در دسترس است. در {{domxref("WebGL2RenderingContext", "WebGL2", "", 1)}}، قابلیت‌های این افزونه به‌صورت پیش‌فرض در context وجود دارد و ثابت‌ها و متدها بدون پسوند `ANGLE_` قابل استفاده هستند.
>
> با وجود نام "ANGLE"، این افزونه روی هر دستگاهی که سخت‌افزار از آن پشتیبانی کند کار می‌کند، نه فقط روی ویندوز یا با کتابخانه ANGLE. "ANGLE" صرفاً نشان‌دهنده این است که این افزونه توسط نویسندگان کتابخانه ANGLE نوشته شده است.

## ثابت‌ها

این افزونه یک ثابت جدید در اختیار می‌گذارد که می‌توان از آن در متد {{domxref("WebGLRenderingContext.getVertexAttrib()", "gl.getVertexAttrib()")}} استفاده کرد:

- `ext.VERTEX_ATTRIB_ARRAY_DIVISOR_ANGLE`
  - : یک {{domxref("WebGL_API/Types", "GLint")}} برمی‌گرداند که مقسوم‌علیه فرکانس (frequency divisor) استفاده شده برای rendering نمونه‌ای (instanced rendering) را توصیف می‌کند. این ثابت هنگام فراخوانی `gl.getVertexAttrib()` به‌عنوان پارامتر `pname` به کار می‌رود.

## متدهای نمونه

این افزونه سه متد جدید ارائه می‌دهد.

- {{domxref("ANGLE_instanced_arrays.drawArraysInstancedANGLE()", "ext.drawArraysInstancedANGLE()")}}
  - : عملکردی مشابه {{domxref("WebGLRenderingContext.drawArrays()", "gl.drawArrays()")}} دارد، با این تفاوت که چندین نمونه از بازه المان‌ها اجرا می‌شود و شمارنده نمونه در هر تکرار افزایش می‌یابد.
- {{domxref("ANGLE_instanced_arrays.drawElementsInstancedANGLE()", "ext.drawElementsInstancedANGLE()")}}
  - : عملکردی مشابه {{domxref("WebGLRenderingContext.drawElements()", "gl.drawElements()")}} دارد، با این تفاوت که چندین نمونه از مجموعه المان‌ها اجرا می‌شود و شمارنده نمونه بین هر مجموعه افزایش می‌یابد.
- {{domxref("ANGLE_instanced_arrays.vertexAttribDivisorANGLE()", "ext.vertexAttribDivisorANGLE()")}}
  - : نرخ پیشروی ویژگی‌های عمومی vertex را هنگام رسم چندین نمونه از primitiveها با استفاده از {{domxref("ANGLE_instanced_arrays.drawArraysInstancedANGLE()", "ext.drawArraysInstancedANGLE()")}} و {{domxref("ANGLE_instanced_arrays.drawElementsInstancedANGLE()", "ext.drawElementsInstancedANGLE()")}} تغییر می‌دهد.

## مثال‌ها

مثال زیر نشان می‌دهد که چگونه یک هندسه مشخص را چندین بار تنها با یک فراخوانی draw رسم کنید.

> [!WARNING]
> کد زیر صرفاً جنبه آموزشی دارد و برای محیط تولید مناسب نیست. به‌طور کلی باید از ساخت داده/بافر در حلقه rendering یا درست قبل از استفاده خودداری کرد.

```js
// enable the extension
const ext = gl.getExtension("ANGLE_instanced_arrays");

// binding the geometry buffer as usual
gl.bindBuffer(gl.ARRAY_BUFFER, geometryVertexBuffer);
gl.enableVertexAttribArray(vertexPositionAttributeLocation);
gl.vertexAttribPointer(
  vertexPositionAttributeLocation,
  3,
  gl.FLOAT,
  false,
  0,
  0,
);

// build position buffer
const instancePositions = [];
for (const instance of instances) {
  instancePositions.push(
    instance.position.x,
    instance.position.y,
    instance.position.z,
  );
}
const instancePositionBuffer = createWebGLBufferFromData(instancePositions);
```

```
// بایند کردن بافر موقعیت نمونه‌ها همانند هر attribute دیگر
gl.bindBuffer(gl.ARRAY_BUFFER, instancePositionBuffer);
gl.enableVertexAttribArray(instancePositionAttributeLocation);
gl.vertexAttribPointer(
  instancePositionAttributeLocation,
  3,
  gl.FLOAT,
  false,
  0,
  0,
);

// علامت‌گذاری attribute به‌عنوان instanced و جلو بردن آن به ازای هر instance (یکی‌یکی) به‌جای هر vertex
ext.vertexAttribDivisorANGLE(instancePositionAttributeLocation, 1);

// رسم هندسه برای هر instance
ext.drawArraysInstancedANGLE(
  gl.TRIANGLES,
  0,
  numGeometryVertices,
  instances.length,
);
```

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- {{domxref("WebGLRenderingContext.getExtension()")}}
- {{domxref("WebGL2RenderingContext.drawArraysInstanced()")}}
- {{domxref("WebGL2RenderingContext.drawElementsInstanced()")}}
- {{domxref("WebGL2RenderingContext.vertexAttribDivisor()")}}