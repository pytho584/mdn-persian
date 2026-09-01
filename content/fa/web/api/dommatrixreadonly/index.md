---
title: "DOMMatrixReadOnly"
source: "https://developer.mozilla.org/en-US/docs/Web/API/DOMMatrixReadOnly"
---

---
title: DOMMatrixReadOnly
slug: Web/API/DOMMatrixReadOnly
page-type: web-api-interface
browser-compat: api.DOMMatrixReadOnly
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

رابطهٔ **`DOMMatrixReadOnly`** یک ماتریس ۴×۴ فقط‌خواندنی را نشان می‌دهد که برای عملیات دوبعدی و سه‌بعدی مناسب است. رابط {{domxref("DOMMatrix")}} که بر پایهٔ `DOMMatrixReadOnly` ساخته شده، [قابلیت تغییرپذیری](https://en.wikipedia.org/wiki/Immutable_object) را اضافه می‌کند و به شما اجازه می‌دهد پس از ایجاد ماتریس، آن را تغییر دهید.

این رابط باید در [web workers](/en-US/docs/Web/API/Web_Workers_API) در دسترس باشد، هرچند برخی پیاده‌سازی‌ها هنوز آن را مجاز نمی‌دانند.

## سازنده

- {{domxref("DOMMatrixReadOnly.DOMMatrixReadOnly", "DOMMatrixReadOnly()")}}
  - : یک شیء جدید `DOMMatrixReadOnly` ایجاد می‌کند.

## ویژگی‌های نمونه

_این رابط هیچ ویژگی‌ای را به ارث نمی‌برد._

- {{domxref("DOMMatrixReadOnly.is2D")}} {{ReadOnlyInline}}
  - : یک پرچم بولی که مقدار آن `true` است اگر ماتریس به‌عنوان ماتریس دوبعدی مقداردهی شده باشد. اگر `false` باشد، ماتریس سه‌بعدی است.
- {{domxref("DOMMatrixReadOnly.isIdentity")}} {{ReadOnlyInline}}
  - : یک بولی که مقدار آن `true` است اگر ماتریس یک [ماتریس همانی](https://en.wikipedia.org/wiki/Identity_matrix) باشد.
- `m11`, `m12`, `m13`, `m14`, `m21`, `m22`, `m23`, `m24`, `m31`, `m32`, `m33`, `m34`, `m41`, `m42`, `m43`, `m44`
  - : مقادیر ممیز شناور با دقت دوگانه که هر مؤلفهٔ یک ماتریس ۴×۴ را نشان می‌دهند؛ به‌طوری که `m11` تا `m14` ستون اول، `m21` تا `m24` ستون دوم و به همین ترتیب هستند.
- `a`, `b`, `c`, `d`, `e`, `f`
  - : مقادیر ممیز شناور با دقت دوگانه که مؤلفه‌های موردنیاز یک ماتریس ۴×۴ را برای انجام چرخش‌ها و انتقال‌های دوبعدی نشان می‌دهند. این‌ها نام‌های مستعار برای مؤلفه‌های خاصی از ماتریس ۴×۴ هستند، همان‌طور که در زیر نشان داده شده است.

    | 2D  | معادل 3D |
    | --- | ------------- |
    | `a` | `m11`         |
    | `b` | `m12`         |
    | `c` | `m21`         |
    | `d` | `m22`         |
    | `e` | `m41`         |
    | `f` | `m42`         |

## روش‌های نمونه

_این رابط هیچ روشی را به ارث نمی‌برد. هیچ‌یک از روش‌های زیر ماتریس اصلی را تغییر نمی‌دهند._

- {{domxref("DOMMatrixReadOnly.flipX()")}}
  - : یک {{domxref("DOMMatrix")}} جدید برمی‌گرداند که با چرخاندن ماتریس منبع حول محور X آن ایجاد شده است. این معادل ضرب ماتریس در `DOMMatrix(-1, 0, 0, 1, 0, 0)` است. ماتریس اصلی تغییر نمی‌کند.
- {{domxref("DOMMatrixReadOnly.flipY()")}}
  - : یک {{domxref("DOMMatrix")}} جدید برمی‌گرداند که با چرخاندن ماتریس منبع حول محور Y آن ایجاد شده است. این معادل ضرب ماتریس در `DOMMatrix(1, 0, 0, -1, 0, 0)` است. ماتریس اصلی تغییر نمی‌کند.
- {{domxref("DOMMatrixReadOnly.inverse()")}}
  - : یک {{domxref("DOMMatrix")}} جدید برمی‌گرداند که با معکوس کردن ماتریس منبع ایجاد شده است. ماتریس اصلی تغییر نمی‌کند.
- {{domxref("DOMMatrixReadOnly.multiply()")}}
  - : یک {{domxref("DOMMatrix")}} جدید برمی‌گرداند که با محاسبهٔ ضرب داخلی ماتریس منبع و ماتریس مشخص‌شده ایجاد شده است. ماتریس اصلی تغییر نمی‌کند.
- {{domxref("DOMMatrixReadOnly.rotateAxisAngle()")}}
  - : یک {{domxref("DOMMatrix")}} جدید برمی‌گرداند که با چرخاندن ماتریس منبع به اندازهٔ زاویهٔ داده‌شده حول بردار مشخص‌شده ایجاد شده است. ماتریس اصلی تغییر نمی‌کند.
- {{domxref("DOMMatrixReadOnly.rotate()")}}
  - : یک {{domxref("DOMMatrix")}} جدید برمی‌گرداند که با چرخاندن ماتریس منبع حول هر یک از محورهای آن به اندازهٔ درجه‌های مشخص‌شده ایجاد شده است. ماتریس اصلی تغییر نمی‌کند.
- {{domxref("DOMMatrixReadOnly.rotateFromVector()")}}
  - : یک {{domxref("DOMMatrix")}} جدید برمی‌گرداند که با چرخاندن ماتریس منبع به اندازهٔ زاویهٔ بین بردار مشخص‌شده و `(1, 0)` ایجاد شده است. ماتریس اصلی تغییر نمی‌کند.
- {{domxref("DOMMatrixReadOnly.scale()")}}
  - : یک {{domxref("DOMMatrix")}} جدید برمی‌گرداند که با مقیاس‌دهی ماتریس منبع به اندازهٔ مشخص‌شده برای هر محور، حول مبدأ داده‌شده ایجاد شده است. به‌طور پیش‌فرض، محورهای X و Z با ضریب `1` مقیاس می‌خورند و محور Y مقدار پیش‌فرض مقیاس ندارد. مبدأ پیش‌فرض `(0, 0, 0)` است. ماتریس اصلی تغییر نمی‌کند.
- {{domxref("DOMMatrixReadOnly.scale3d()")}}
  - : یک {{domxref("DOMMatrix")}} جدید برمی‌گرداند که با مقیاس‌دهی ماتریس سه‌بعدی منبع به اندازهٔ ضریب داده‌شده در امتداد همهٔ محورهای آن، حول نقطهٔ مبدأ مشخص‌شده ایجاد شده است. مبدأ پیش‌فرض `(0, 0, 0)` است. ماتریس اصلی تغییر نمی‌کند.
- {{domxref("DOMMatrixReadOnly.scaleNonUniform()")}} {{deprecated_inline}}
  - : یک {{domxref("DOMMatrix")}} جدید برمی‌گرداند که با اعمال مقیاس مشخص‌شده بر محورهای X، Y و Z، حول مبدأ داده‌شده ایجاد شده است. به‌طور پیش‌فرض، ضرایب مقیاس محورهای Y و Z هر دو `1` هستند، اما ضریب مقیاس برای X باید مشخص شود. مبدأ پیش‌فرض `(0, 0, 0)` است. ماتریس اصلی تغییر نمی‌کند.
- {{domxref("DOMMatrixReadOnly.skewX()")}}
  - : یک {{domxref("DOMMatrix")}} جدید برمی‌گرداند که با اعمال تبدیل کج‌سازی مشخص‌شده به ماتریس منبع در امتداد محور X آن ایجاد شده است. ماتریس اصلی تغییر نمی‌کند.
- {{domxref("DOMMatrixReadOnly.skewY()")}}
  - : یک {{domxref("DOMMatrix")}} جدید برمی‌گرداند که با اعمال تبدیل کج‌سازی مشخص‌شده به ماتریس منبع در امتداد محور Y آن ایجاد شده است. ماتریس اصلی تغییر نمی‌کند.
- {{domxref("DOMMatrixReadOnly.toFloat32Array()")}}
  - : یک {{jsxref("Float32Array")}} جدید از اعداد ممیز شناور تک‌دقت برمی‌گرداند که شامل هر ۱۶ عنصر تشکیل‌دهندهٔ ماتریس است.
- {{domxref("DOMMatrixReadOnly.toFloat64Array()")}}
  - : یک {{jsxref("Float64Array")}} جدید از اعداد ممیز شناور دوگانه‌دقت برمی‌گرداند که شامل هر ۱۶ عنصر تشکیل‌دهندهٔ ماتریس است.
- {{domxref("DOMMatrixReadOnly.toJSON()")}}
  - : یک نمایش JSON از شیء `DOMMatrixReadOnly` برمی‌گرداند.
- {{domxref("DOMMatrixReadOnly.toString()")}}
  - : یک نمایش رشته‌ای از ماتریس در نحو ماتریس CSS، با استفاده از نمادگذاری ماتریس CSS مناسب، ایجاد و برمی‌گرداند.
- {{domxref("DOMMatrixReadOnly.transformPoint()")}}
  - : نقطهٔ مشخص‌شده را با استفاده از ماتریس تبدیل می‌کند و یک شیء {{domxref("DOMPoint")}} جدید حاوی نقطهٔ تبدیل‌شده برمی‌گرداند. نه ماتریس و نه نقطهٔ اصلی تغییر نمی‌کنند.
- {{domxref("DOMMatrixReadOnly.translate()")}}
  - : یک {{domxref("DOMMatrix")}} جدید شامل ماتریسی برمی‌گرداند که با انتقال ماتریس منبع با استفاده از بردار مشخص‌شده محاسبه شده است. به‌طور پیش‌فرض، بردار `(0, 0, 0)` است. ماتریس اصلی تغییر نمی‌کند.

## روش‌های ایستا

- {{domxref("DOMMatrixReadOnly.fromFloat32Array_static", "fromFloat32Array()")}}
  - : یک شیء جدید `DOMMatrixReadOnly` با دریافت یک {{jsxref("Float32Array")}} شامل ۶ یا ۱۶ مقدار ممیز شناور تک‌دقت (۳۲ بیتی) ایجاد می‌کند.
- {{domxref("DOMMatrixReadOnly.fromFloat64Array_static", "fromFloat64Array()")}}
  - : یک شیء جدید `DOMMatrixReadOnly` با دریافت یک {{jsxref("Float64Array")}} شامل ۶ یا ۱۶ مقدار ممیز شناور دوگانه‌دقت (۶۴ بیتی) ایجاد می‌کند.
- {{domxref("DOMMatrixReadOnly.fromMatrix_static", "fromMatrix()")}}
  - : یک شیء جدید `DOMMatrixReadOnly` با دریافت یک ماتریس موجود یا یک شیء که مقادیر ویژگی‌های آن را فراهم می‌کند ایجاد می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- نوع ماتریس تغییرپذیر، {{domxref("DOMMatrix")}}، که بر پایهٔ همین نوع ساخته شده است.
- نمادگذاری تابعی CSS {{cssxref("transform-function/matrix", "matrix()")}} و {{cssxref("transform-function/matrix3d", "matrix3d()")}} که می‌توانند از این رابط تولید شوند و در {{cssxref("transform")}} CSS استفاده شوند.