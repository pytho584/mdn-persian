---
title: DOMMatrix
slug: Web/API/DOMMatrix
page-type: web-api-interface
browser-compat: api.DOMMatrix
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

رابط **`DOMMatrix`** ماتریس‌های 4×4 را نشان می‌دهد که برای عملیات دو بعدی و سه بعدی از جمله چرخش و انتقال مناسب هستند. این رابط نسخهٔ تغییرپذیر رابط {{domxref("DOMMatrixReadOnly")}} است.

این رابط در [web workers](/en-US/docs/Web/API/Web_Workers_API) نیز در دسترس است.

**`WebKitCSSMatrix`** و **`SVGMatrix`** نام‌های مستعار **`DOMMatrix`** هستند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("DOMMatrix.DOMMatrix","DOMMatrix()")}}

  - : یک شیء `DOMMatrix` جدید ایجاد و بازمی‌گرداند.

## ویژگی‌های نمونه

_این رابط ویژگی‌هایی را از {{domxref("DOMMatrixReadOnly")}} به ارث می‌برد، اگرچه برخی از این ویژگی‌ها برای تغییرپذیری تغییر یافته‌اند._

- `m11`, `m12`, `m13`, `m14`, `m21`, `m22`, `m23`, `m24`, `m31`, `m32`, `m33`, `m34`, `m41`, `m42`, `m43`, `m44`

  - : مقادیر ممیز شناور با دقت دوگانه که هر مؤلفه از یک ماتریس 4×4 را نشان می‌دهند؛ به‌طوری که `m11` تا `m14` ستون اول، `m21` تا `m24` ستون دوم و به همین ترتیب هستند.

- `a`, `b`, `c`, `d`, `e`, `f`

  - : مقادیر ممیز شناور با دقت دوگانه که مؤلفه‌های لازم یک ماتریس 4×4 برای انجام چرخش و انتقال دوبعدی را نشان می‌دهند. این‌ها نام‌های مستعار برای مؤلفه‌های خاصی از یک ماتریس 4×4 هستند، همان‌طور که در زیر نشان داده شده است.

    | دوبعدی | معادل سه‌بعدی |
    | ------ | ------------ |
    | `a`    | `m11`        |
    | `b`    | `m12`        |
    | `c`    | `m21`        |
    | `d`    | `m22`        |
    | `e`    | `m41`        |
    | `f`    | `m42`        |

## متدهای نمونه

_این رابط شامل متدهای زیر و همچنین متدهایی است که از {{domxref("DOMMatrixReadOnly")}} به ارث می‌برد._

- {{domxref("DOMMatrix.invertSelf()")}}

  - : ماتریس را با معکوس کردن آن تغییر می‌دهد. اگر ماتریس قابل معکوس شدن نباشد، همهٔ مؤلفه‌های آن روی `NaN` تنظیم می‌شوند و [`is2D`](/en-US/docs/Web/API/DOMMatrixReadOnly/is2D) مقدار `false` را برمی‌گرداند.

- {{domxref("DOMMatrix.multiplySelf()")}}

  - : ماتریس را با ضرب آن در `DOMMatrix` مشخص‌شده از سمت راست تغییر می‌دهد. این معادل ضرب نقطه‌ای `A⋅B` است، جایی که ماتریس `A` ماتریس مبدأ و `B` ماتریسی است که به‌عنوان ورودی به متد داده می‌شود. خود ماتریس را برمی‌گرداند.

- {{domxref("DOMMatrix.preMultiplySelf()")}}

  - : ماتریس را با ضرب آن در `DOMMatrix` مشخص‌شده از سمت چپ تغییر می‌دهد. خود ماتریس را برمی‌گرداند.

- {{domxref("DOMMatrix.translateSelf()")}}

  - : ماتریس را با اعمال بردار مشخص‌شده تغییر می‌دهد. بردار پیش‌فرض `[0, 0, 0]` است. خود ماتریس را برمی‌گرداند.

- {{domxref("DOMMatrix.scaleSelf()")}}

  - : ماتریس را با اعمال ضرایب مقیاس مشخص‌شده، با مرکزیت در مبدأ مشخص‌شده، تغییر می‌دهد. همچنین خود ماتریس را برمی‌گرداند. به‌طور پیش‌فرض، ضریب مقیاس برای هر سه محور `1` و مبدأ `(0, 0, 0)` است. خود ماتریس را برمی‌گرداند.

- {{domxref("DOMMatrix.scale3dSelf()")}}

  - : ماتریس را با اعمال ضریب مقیاس مشخص‌شده به هر سه محور، با مرکزیت مبدأ داده‌شده، تغییر می‌دهد. خود ماتریس را برمی‌گرداند.

- {{domxref("DOMMatrix.rotateSelf()")}}

  - : ماتریس را با چرخاندن آن به دور هر محور به اندازهٔ درجهٔ مشخص‌شده تغییر می‌دهد. خود ماتریس را برمی‌گرداند.

- {{domxref("DOMMatrix.rotateAxisAngleSelf()")}}

  - : ماتریس را با چرخاندن آن به اندازهٔ زاویهٔ مشخص‌شده حول بردار داده‌شده تغییر می‌دهد. خود ماتریس را برمی‌گرداند.

- {{domxref("DOMMatrix.rotateFromVectorSelf()")}}

  - : ماتریس را با چرخاندن آن به اندازهٔ زاویه بین بردار مشخص‌شده و `(1, 0)` تغییر می‌دهد. خود ماتریس را برمی‌گرداند.

- {{domxref("DOMMatrix.setMatrixValue()")}}

  - : محتویات ماتریس را با ماتریسی که توسط تبدیل یا تبدیل‌های مشخص‌شده توصیف می‌شود جایگزین می‌کند. خود ماتریس را برمی‌گرداند.

- {{domxref("DOMMatrix.skewXSelf()")}}

  - : ماتریس را با اعمال تبدیل برش (skew) مشخص‌شده در راستای محور X تغییر می‌دهد. خود ماتریس را برمی‌گرداند.

- {{domxref("DOMMatrix.skewYSelf()")}}

  - : ماتریس را با اعمال تبدیل برش مشخص‌شده در راستای محور Y تغییر می‌دهد. خود ماتریس را برمی‌گرداند.

## متدهای ایستا

- {{domxref("DOMMatrix.fromFloat32Array_static", "fromFloat32Array()")}}

  - : با دریافت یک {{jsxref("Float32Array")}} شامل ۶ یا ۱۶ مقدار ممیز شناور تک‌دقت (۳۲ بیتی)، یک شیء `DOMMatrix` جدید می‌سازد.

- {{domxref("DOMMatrix.fromFloat64Array_static", "fromFloat64Array()")}}

  - : با دریافت یک {{jsxref("Float64Array")}} شامل ۶ یا ۱۶ مقدار ممیز شناور با دقت دوگانه (۶۴ بیتی)، یک شیء `DOMMatrix` جدید می‌سازد.

- {{domxref("DOMMatrix.fromMatrix_static", "fromMatrix()")}}

  - : با دریافت یک ماتریس موجود یا شیئی که مقادیر ویژگی‌های آن را فراهم می‌کند، یک شیء `DOMMatrix` جدید می‌سازد.

## نکات استفاده

ماتریس تعریف‌شده توسط رابط `DOMMatrix` از چهار ردیف و چهار ستون تشکیل شده است. اگرچه توضیح ریاضیات مربوطه خارج از حوصلهٔ این مقاله است، این اندازهٔ 4×4 برای توصیف هر تبدیلی که ممکن است روی هندسه‌های دوبعدی یا سه‌بعدی اعمال کنید کافی است.

<!-- prettier-ignore-start -->
<math display="block">
  <semantics><mrow><mo>[</mo><mtable rowspacing="0.5ex"><mtr><mtd><msub><mi>m</mi><mn>11</mn></msub></mtd><mtd><msub><mi>m</mi><mn>21</mn></msub></mtd><mtd><msub><mi>m</mi><mn>31</mn></msub></mtd><mtd><msub><mi>m</mi><mn>41</mn></msub></mtd></mtr><mtr><mtd><msub><mi>m</mi><mn>12</mn></msub></mtd><mtd><msub><mi>m</mi><mn>22</mn></msub></mtd><mtd><msub><mi>m</mi><mn>32</mn></msub></mtd><mtd><msub><mi>m</mi><mn>42</mn></msub></mtd></mtr><mtr><mtd><msub><mi>m</mi><mn>13</mn></msub></mtd><mtd><msub><mi>m</mi><mn>23</mn></msub></mtd><mtd><msub><mi>m</mi><mn>33</mn></msub></mtd><mtd><msub><mi>m</mi><mn>43</mn></msub></mtd></mtr><mtr><mtd><msub><mi>m</mi><mn>14</mn></msub></mtd><mtd><msub><mi>m</mi><mn>24</mn></msub></mtd><mtd><msub><mi>m</mi><mn>34</mn></msub></mtd><mtd><msub><mi>m</mi><mn>44</mn></msub></mtd></mtr></mtable><mo>]</mo></mrow><annotation encoding="TeX">\left [ \begin{matrix} m_{11} & m_{21} & m_{31} & m_{41} \\ m_{12} & m_{22} & m_{32} & m_{42} \\ m_{13} & m_{23} & m_{33} & m_{43} \\ m_{14} & m_{24} & m_{34} & m_{44} \end{matrix} \right ]</annotation></semantics>
</math>
<!-- prettier-ignore-end -->

رابط `DOMMatrix` با این هدف طراحی شده است که برای همهٔ ماتریس‌ها در نشانه‌گذاری (markup) استفاده شود.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMMatrixReadOnly.is2D")}}
- {{domxref("DOMMatrixReadOnly.isIdentity")}}