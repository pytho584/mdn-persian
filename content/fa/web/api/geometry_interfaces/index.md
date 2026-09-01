---
title: "Geometry interfaces"
---

---
title: Geometry interfaces
slug: Web/API/Geometry_interfaces
page-type: web-api-overview
browser-compat:
  - api.DOMMatrix
  - api.DOMMatrixReadOnly
  - api.DOMPoint
  - api.DOMPointReadOnly
  - api.DOMQuad
  - api.DOMRect
  - api.DOMRectReadOnly
---

{{DefaultAPISidebar("Geometry Interfaces")}}

**رابط‌های هندسی** یک ماژول CSS است که رابط‌هایی را برای کار با گرافیک سه‌بعدی و دوبعدی فراهم می‌کند — به‌ویژه برای کار با نقاط، مستطیل‌ها، چهارضلعی‌ها و [ماتریس‌های تبدیل](/en-US/docs/Web/API/WebGL_API/Matrix_math_for_the_web#transformation_matrices) (برای عملیات انتقال/جابجایی، تغییر مقیاس، چرخش، اریب‌کردن/کج‌کردن/مورب‌کردن و برگرداندن گرافیک، و همچنین برای ضرب/زنجیره‌کردن و معکوس‌کردن/برگرداندن آن عملیات).

به‌عنوان یک توسعه‌دهنده وب، همیشه مستقیماً از رابط‌های هندسی استفاده نمی‌کنید، بلکه از ویژگی‌های دیگری استفاده می‌کنید که در پس‌زمینه به آن‌ها متکی هستند: بخش‌هایی از [تبدیل‌های CSS](/en-US/docs/Web/CSS/Guides/Transforms)، [رابط Canvas](/en-US/docs/Web/API/Canvas_API)، [رابط WebXR Device](/en-US/docs/Web/API/WebXR_Device_API)، و (به‌طور مستقیم‌تر) {{domxref('VideoFrame.visibleRect')}}، {{domxref('Element.getClientRects()')}} و {{domxref('Element.getBoundingClientRect()')}}.

## رابط‌ها

- {{domxref('DOMMatrix')}}
  - : یک [ماتریس تبدیل](/en-US/docs/Web/API/WebGL_API/Matrix_math_for_the_web#transformation_matrices) را نشان می‌دهد، برای عملیات انتقال/جابجایی، تغییر مقیاس، چرخش، اریب‌کردن/کج‌کردن/مورب‌کردن و برگرداندن گرافیک، و همچنین برای ضرب/زنجیره‌کردن و معکوس‌کردن/برگرداندن آن عملیات.
- {{domxref('DOMMatrixReadOnly')}}
  - : نسخهٔ فقط‌خواندنی {{domxref('DOMMatrix')}}.
- {{domxref('DOMPoint')}}
  - : یک نقطهٔ دوبعدی یا سه‌بعدی را در یک دستگاه مختصات نشان می‌دهد؛ شامل مقادیری برای مختصات در حداکثر سه بُعد و همچنین یک مقدار پرسپکتیو اختیاری است.
- {{domxref('DOMPointReadOnly')}}
  - : نسخهٔ فقط‌خواندنی {{domxref('DOMPoint')}}.
- {{domxref('DOMQuad')}}
  - : مجموعه‌ای از چهار شیء {{domxref('DOMPoint')}} را نشان می‌دهد که گوشه‌های یک [چهارضلعی](https://en.wikipedia.org/wiki/Quadrilateral) را تعریف می‌کنند.
- {{domxref('DOMRect')}}
  - : اندازه و موقعیت یک مستطیل را نشان می‌دهد.
- {{domxref('DOMRectReadOnly')}}
  - : نسخهٔ فقط‌خواندنی {{domxref('DOMRect')}}.

## مثال‌ها

مقالات {{domxref('Path2D.addPath()')}} و {{domxref('CanvasPattern.setTransform()')}} دارای مثال‌هایی هستند که از برخی از رابط‌های هندسی استفاده می‌کنند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref('Path2D.addPath()')}}
- {{domxref('CanvasPattern.setTransform()')}}
- {{domxref('CanvasRenderingContext2D.getTransform()')}}
- {{domxref('CanvasRenderingContext2D.setTransform()')}}
- {{domxref('CSSTransformValue.toMatrix()')}}
- {{domxref('CSSTransformComponent.toMatrix()')}}
- {{domxref('Element.getBoundingClientRect()')}}
- {{domxref('Element.getClientRects()')}}
- {{domxref('VideoFrame.visibleRect')}}
- {{domxref('XRLightEstimate')}}
- {{domxref('XRRigidTransform')}}