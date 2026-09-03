---
title: OffscreenCanvasRenderingContext2D
slug: Web/API/OffscreenCanvasRenderingContext2D
page-type: web-api-interface
browser-compat: api.OffscreenCanvasRenderingContext2D
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

رابط **`OffscreenCanvasRenderingContext2D`** یک زمینهٔ رندرگیری (rendering context) از نوع {{domxref("CanvasRenderingContext2D")}} است که برای رسم روی bitmap یک شیء `OffscreenCanvas` به کار می‌رود. این رابط مشابه شیء `CanvasRenderingContext2D` است، با این تفاوت‌ها:

- از ویژگی‌های رابط کاربری (`drawFocusIfNeeded`) پشتیبانی نمی‌کند.
- ویژگی `canvas` آن به یک شیء `OffscreenCanvas` اشاره می‌کند، نه به یک عنصر {{HtmlElement("canvas")}}.
- bitmap مربوط به عنصر {{HtmlElement("canvas")}} جایگزین (placeholder) که متعلق به شیء `OffscreenCanvas` است، هنگام به‌روزرسانی رندرِ `Window` یا `Worker` مالک آن `OffscreenCanvas` به‌روزرسانی می‌شود.

## مثال

قطعه کد زیر یک شیء {{domxref("Worker")}} را با استفاده از سازندهٔ {{domxref("Worker.Worker", "Worker()")}} می‌سازد. از متد `transferControlToOffscreen()` برای دریافت یک شیء `OffscreenCanvas` از عنصر {{HtmlElement("canvas")}} استفاده می‌شود تا بتوان آن را به worker منتقل کرد:

```js
const canvas = document.getElementById("canvas");
const offscreen = canvas.transferControlToOffscreen();
const worker = new Worker("worker.js");
worker.postMessage({ canvas: offscreen }, [offscreen]);
```

در نخ worker می‌توانیم از `OffscreenCanvasRenderingContext2D` برای رسم روی bitmap شیء `OffscreenCanvas` استفاده کنیم:

```js
onmessage = (event) => {
  const canvas = event.data.canvas;
  const offCtx = canvas.getContext("2d");
  // draw to the offscreen canvas context
  offCtx.fillStyle = "red";
  offCtx.fillRect(0, 0, 100, 100);
};
```

برای مشاهدهٔ یک مثال کامل، [مثال OffscreenCanvas worker](https://github.com/mdn/dom-examples/tree/main/web-workers/offscreen-canvas-worker) را ببینید ([اجرای OffscreenCanvas worker](https://mdn.github.io/dom-examples/web-workers/offscreen-canvas-worker/)).

## متدهای اضافی

متد زیر در رابط `OffscreenCanvasRenderingContext2D` جدید است و در رابط `CanvasRenderingContext2D` وجود ندارد:

- {{domxref("OffscreenCanvasRenderingContext2D.commit()", "commit()")}} {{deprecated_inline}} {{non-standard_inline}}
  - : تصویر رندر شده را به عنصر {{HtmlElement("canvas")}} جایگزین مربوط به شیء `OffscreenCanvas` همان context ارسال می‌کند.

## ویژگی‌های پشتیبانینشده

متد رابط کاربری زیر توسط رابط `OffscreenCanvasRenderingContext2D` **پشتیبانی نمی‌شود**:

- {{domxref("CanvasRenderingContext2D.drawFocusIfNeeded()")}}
  - : اگر یک عنصر مشخص فوکوس داشته باشد، این متد یک قاب فوکوس دور مسیر فعلی رسم می‌کند.

## خصوصیات و متدهای به‌ارث‌رسیده

خصوصیات و متدهای زیر از {{domxref("CanvasRenderingContext2D")}} به ارث رسیده‌اند. کاربرد آن‌ها دقیقاً مانند `CanvasRenderingContext2D` است.

### Context

- {{domxref("CanvasRenderingContext2D.getContextAttributes()")}} {{experimental_inline}}
  - : یک شیء شامل ویژگی‌های واقعی context را برمی‌گرداند. ویژگی‌های context را می‌توان با {{domxref("OffscreenCanvas.getContext()")}} درخواست کرد.
- {{domxref("CanvasRenderingContext2D.isContextLost()")}}
  - : اگر زمینهٔ رندرگیری از دست رفته باشد، `true` برمی‌گرداند.

### رسم مستطیل‌ها

- {{domxref("CanvasRenderingContext2D.clearRect()")}}
  - : تمام پیکسل‌های داخل مستطیلی را که با نقطهٔ شروع _(x, y)_ و اندازهٔ _(width, height)_ تعریف می‌شود به سیاهِ شفاف تبدیل می‌کند و هر محتوای قبلاً رسم‌شده را پاک می‌کند.
- {{domxref("CanvasRenderingContext2D.fillRect()")}}
  - : یک مستطیل پُر را در موقعیت _(x, y)_ رسم می‌کند که اندازهٔ آن توسط _width_ و _height_ تعیین می‌شود.
- {{domxref("CanvasRenderingContext2D.strokeRect()")}}
  - : با استفاده از سبک stroke فعلی، مستطیلی را روی canvas رسم می‌کند که نقطهٔ شروع آن _(x, y)_، عرض آن _w_ و ارتفاع آن _h_ است.

### رسم متن

متدها و خصوصیات زیر رسم متن را کنترل می‌کنند. برای ویژگی‌های متن به شیء {{domxref("TextMetrics")}} نیز مراجعه کنید.

- {{domxref("CanvasRenderingContext2D.fillText()")}}
  - : متن داده‌شده را در موقعیت (x, y) رسم (fill) می‌کند.
- {{domxref("CanvasRenderingContext2D.strokeText()")}}
  - : متن داده‌شده را در موقعیت (x, y) رسم (stroke) می‌کند.
- {{domxref("CanvasRenderingContext2D.measureText()")}}
  - : یک شیء {{domxref("TextMetrics")}} برمی‌گرداند.
- {{domxref("CanvasRenderingContext2D.textRendering")}}
  - : رندر متن. مقادیر ممکن: `auto` (پیش‌فرض)، `optimizeSpeed`، `optimizeLegibility`،

### سبک‌های خط

متدها و خصوصیات زیر نحوهٔ رسم خط‌ها را کنترل می‌کنند.

- {{domxref("CanvasRenderingContext2D.lineWidth")}}
  - : عرض خط‌ها. پیش‌فرض: `1.0`.
- {{domxref("CanvasRenderingContext2D.lineCap")}}
  - : نوع انتهای خط‌ها. مقادیر ممکن: `butt` (پیش‌فرض)، `round`، `square`.
- {{domxref("CanvasRenderingContext2D.lineJoin")}}
  - : نوع گوشه‌هایی را که دو خط به هم می‌رسند تعریف می‌کند. مقادیر ممکن: `round`، `bevel`، `miter` (پیش‌فرض).
- {{domxref("CanvasRenderingContext2D.miterLimit")}}
  - : نسبت حد miter. پیش‌فرض: `10`.
- {{domxref("CanvasRenderingContext2D.getLineDash()")}}
  - : آرایهٔ الگوی خط‌چین فعلی را برمی‌گرداند؛ آرایه‌ای شامل تعداد زوجی عدد نامنفی.
- {{domxref("CanvasRenderingContext2D.setLineDash()")}}
  - : الگوی خط‌چین فعلی را تنظیم می‌کند.
- {{domxref("CanvasRenderingContext2D.lineDashOffset")}}
  - : مشخص می‌کند که یک آرایهٔ خط‌چین روی خط از کجا شروع شود.

### سبک‌های متن

خصوصیات زیر نحوهٔ چیدمان متن را کنترل می‌کنند.

- {{domxref("CanvasRenderingContext2D.font")}}
  - : تنظیم فونت. مقدار پیش‌فرض: `10px sans-serif`.
- {{domxref("CanvasRenderingContext2D.textAlign")}}
  - : تنظیم تراز متن. مقادیر ممکن: `start` (پیش‌فرض)، `end`، `left`، `right`، `center`.
- {{domxref("CanvasRenderingContext2D.textBaseline")}}
  - : تنظیم تراز خط پایه (baseline). مقادیر ممکن: `top`، `hanging`، `middle`، `alphabetic` (پیش‌فرض)، `ideographic`، `bottom`.
- {{domxref("CanvasRenderingContext2D.direction")}}
  - : جهت نوشتار. مقادیر ممکن: `ltr`، `rtl`، `inherit` (پیش‌فرض).
- {{domxref("CanvasRenderingContext2D.letterSpacing")}}
  - : فاصلهٔ حروف. پیش‌فرض: `0px`.
- {{domxref("CanvasRenderingContext2D.fontKerning")}}
  - : کرنینگ فونت. مقادیر ممکن: `auto` (پیش‌فرض)، `normal`، `none`.
- {{domxref("CanvasRenderingContext2D.fontStretch")}}
  - : کشیدگی فونت. مقادیر ممکن: `ultra-condensed`، `extra-condensed`، `condensed`، `semi-condensed`، `normal` (پیش‌فرض)، `semi-expanded`، `expanded`، `extra-expanded`، `ultra-expanded`.
- {{domxref("CanvasRenderingContext2D.fontVariantCaps")}}
  - : حالت حروف بزرگ فونت. مقادیر ممکن: `normal` (پیش‌فرض)، `small-caps`، `all-small-caps`، `petite-caps`، `all-petite-caps`، `unicase`، `titling-caps`.
- {{domxref("CanvasRenderingContext2D.textRendering")}} {{experimental_inline}}
  - : رندر متن. مقادیر ممکن: `auto` (پیش‌فرض)، `optimizeSpeed`، `optimizeLegibility`، `geometricPrecision`.
- {{domxref("CanvasRenderingContext2D.wordSpacing")}}
  - : فاصلهٔ بین واژه‌ها. مقدار پیش‌فرض: `0px`.
- {{domxref("CanvasRenderingContext2D.lang")}}
  - : زبان context رسم canvas را دریافت یا تنظیم می‌کند.

### سبک‌های fill و stroke

سبک‌دهی fill برای رنگ‌ها و سبک‌های داخل اشکال استفاده می‌شود و سبک‌دهی stroke برای خط‌های دور اشکال به کار می‌رود.

- {{domxref("CanvasRenderingContext2D.fillStyle")}}
  - : رنگ یا سبکی که داخل اشکال استفاده می‌شود. پیش‌فرض: `black`.
- {{domxref("CanvasRenderingContext2D.strokeStyle")}}
  - : رنگ یا سبکی که برای خط‌های دور اشکال استفاده می‌شود. پیش‌فرض: `black`.

### گرادیان‌ها و الگوها

- {{domxref("CanvasRenderingContext2D.createConicGradient()")}}
  - : یک گرادیان مخروطی (conic) حول نقطه‌ای که مختصات آن توسط پارامترها داده شده است می‌سازد.
- {{domxref("CanvasRenderingContext2D.createLinearGradient()")}}
  - : یک گرادیان خطی در امتداد خطی که مختصات آن توسط پارامترها داده شده است می‌سازد.
- {{domxref("CanvasRenderingContext2D.createRadialGradient()")}}
  - : یک گرادیان شعاعی بر اساس مختصات دو دایره‌ای که توسط پارامترها مشخص می‌شوند می‌سازد.
- {{domxref("CanvasRenderingContext2D.createPattern()")}}
  - : با استفاده از تصویر مشخص‌شده یک الگو می‌سازد. این الگو، تصویر منبع را در جهت‌های تعیین‌شده توسط آرگومان تکرار، تکرار می‌کند. این متد یک {{domxref("CanvasPattern")}} برمی‌گرداند.

### سایه‌ها

- {{domxref("CanvasRenderingContext2D.shadowBlur")}}
  - : میزان تاری (blur) را مشخص می‌کند. پیش‌فرض: `0`.
- {{domxref("CanvasRenderingContext2D.shadowColor")}}
  - : رنگ سایه. پیش‌فرض: سیاهِ کاملاً شفاف.
- {{domxref("CanvasRenderingContext2D.shadowOffsetX")}}
  - : فاصلهٔ افقی جابه‌جایی سایه. پیش‌فرض: `0`.
- {{domxref("CanvasRenderingContext2D.shadowOffsetY")}}
  - : فاصلهٔ عمودی جابه‌جایی سایه. پیش‌فرض: `0`.

### مسیرها

متدهای زیر را می‌توان برای دستکاری مسیر اشیا استفاده کرد.

- {{domxref("CanvasRenderingContext2D.beginPath()")}}
  - : با خالی کردن فهرست زیرمسیرها، یک مسیر جدید شروع می‌کند. وقتی می‌خواهید مسیر جدیدی بسازید، این متد را فراخوانی کنید.
- {{domxref("CanvasRenderingContext2D.closePath()")}}
  - : باعث می‌شود نقطهٔ قلم به شروع زیرمسیر فعلی بازگردد. این متد سعی می‌کند از نقطهٔ فعلی به نقطهٔ شروع، یک خط راست رسم کند. اگر شکل قبلاً بسته شده باشد یا فقط یک نقطه داشته باشد، این تابع کاری انجام نمی‌دهد.
- {{domxref("CanvasRenderingContext2D.moveTo()")}}
  - : نقطهٔ شروع یک زیرمسیر جدید را به مختصات (x, y) منتقل می‌کند.
- {{domxref("CanvasRenderingContext2D.lineTo()")}}
  - : آخرین نقطهٔ زیرمسیر فعلی را با یک خط راست به مختصات (x, y) مشخص‌شده متصل می‌کند.
- {{domxref("CanvasRenderingContext2D.bezierCurveTo()")}}
  - : یک منحنی بزیهٔ مکعبی به مسیر فعلی اضافه می‌کند.
- {{domxref("CanvasRenderingContext2D.quadraticCurveTo()")}}
  - : یک منحنی بزیهٔ درجه دوم به مسیر فعلی اضافه می‌کند.
- {{domxref("CanvasRenderingContext2D.arc()")}}
  - : یک کمان دایره‌ای به مسیر فعلی اضافه می‌کند.
- {{domxref("CanvasRenderingContext2D.arcTo()")}}
  - : یک کمان با نقطه‌های کنترل و شعاع داده‌شده به مسیر فعلی اضافه می‌کند که با یک خط راست به نقطهٔ قبلی متصل می‌شود.
- {{domxref("CanvasRenderingContext2D.ellipse()")}}
  - : یک کمان بیضوی به مسیر فعلی اضافه می‌کند.
- {{domxref("CanvasRenderingContext2D.rect()")}}
  - : برای یک مستطیل در موقعیت (x, y) با اندازه‌ای که توسط _width_ و _height_ تعیین می‌شود، مسیر می‌سازد.
- {{domxref("CanvasRenderingContext2D.roundRect()")}}
  - : برای یک مستطیل با گوشه‌های گرد در موقعیت (x, y) مسیر می‌سازد؛ اندازهٔ آن توسط _width_ و _height_ و شعاع گوشه‌ها توسط _radii_ تعیین می‌شود.

### رسم مسیرها

- {{domxref("CanvasRenderingContext2D.fill()")}}
  - : زیرمسیرهای فعلی را با سبک fill فعلی پر می‌کند.
- {{domxref("CanvasRenderingContext2D.stroke()")}}
  - : زیرمسیرهای فعلی را با سبک stroke فعلی خط می‌کشد.
- {{domxref("CanvasRenderingContext2D.clip()")}}
  - : از زیرمسیرهای فعلی یک مسیر برش (clipping path) می‌سازد. هر چیزی که پس از فراخوانی `clip()` رسم شود فقط در داخل مسیر برش دیده می‌شود. برای مثال، بخش [Clipping paths](/en-US/docs/Web/API/Canvas_API/Tutorial/Compositing) در آموزش Canvas را ببینید.
- {{domxref("CanvasRenderingContext2D.isPointInPath()")}}
  - : گزارش می‌دهد که آیا نقطهٔ مشخص‌شده درون مسیر فعلی قرار دارد یا نه.
- {{domxref("CanvasRenderingContext2D.isPointInStroke()")}}
  - : گزارش می‌دهد که آیا نقطهٔ مشخص‌شده درون ناحیهٔ حاصل از خط‌کشی (stroke) یک مسیر قرار دارد یا نه.

### تبدیل‌ها

اشیای موجود در زمینهٔ رندرگیری `CanvasRenderingContext2D` دارای ماتریس تبدیل فعلی و متدهایی برای دستکاری آن هستند. ماتریس تبدیل هنگام ساخت مسیر پیش‌فرض فعلی، رسم متن، اشکال و اشیای {{domxref("Path2D")}} اعمال می‌شود. متدهای فهرست‌شده در زیر به دلایل تاریخی و سازگاری باقی مانده‌اند؛ زیرا امروزه در بیشتر بخش‌های این API از اشیای {{domxref("DOMMatrix")}} استفاده می‌شود و در آینده نیز به‌جای این متدها به کار خواهند رفت.

- {{domxref("CanvasRenderingContext2D.getTransform()")}}
  - : ماتریس تبدیلی را که در حال حاضر روی context اعمال می‌شود بازیابی می‌کند.
- {{domxref("CanvasRenderingContext2D.rotate()")}}
  - : یک چرخش به ماتریس تبدیل اضافه می‌کند. آرگومان زاویه، زاویهٔ چرخش در جهت عقربه‌های ساعت را نشان می‌دهد و بر حسب رادیان بیان می‌شود.
- {{domxref("CanvasRenderingContext2D.scale()")}}
  - : یک تبدیل مقیاس‌بندی با ضریب x در جهت افقی و ضریب y در جهت عمودی به واحدهای canvas اضافه می‌کند.
- {{domxref("CanvasRenderingContext2D.translate()")}}
  - : یک تبدیل انتقال اضافه می‌کند؛ به این صورت که canvas و مبدأ آن را روی شبکه به اندازهٔ x در جهت افقی و y در جهت عمودی جابه‌جا می‌کند.
- {{domxref("CanvasRenderingContext2D.transform()")}}
  - : ماتریس تبدیل فعلی را در ماتریسی که توسط آرگومان‌هایش توصیف شده است ضرب می‌کند.
- {{domxref("CanvasRenderingContext2D.setTransform()")}}
  - : تبدیل فعلی را به ماتریس همانی بازنشانی می‌کند و سپس متد `transform()` را با همان آرگومان‌ها فراخوانی می‌کند.
- {{domxref("CanvasRenderingContext2D.resetTransform()")}}
  - : تبدیل فعلی را با ماتریس همانی بازنشانی می‌کند.

### ترکیب (Compositing)

- {{domxref("CanvasRenderingContext2D.globalAlpha")}}
  - : مقدار آلفایی که پیش از ترکیب شدن اشکال و تصاویر روی canvas به آن‌ها اعمال می‌شود. پیش‌فرض: `1.0` (کاملاً غیرشفاف).
- {{domxref("CanvasRenderingContext2D.globalCompositeOperation")}}
  - : همراه با `globalAlpha` تعیین می‌کند که اشکال و تصاویر چگونه روی bitmap موجود رسم شوند.

### رسم تصاویر

- {{domxref("CanvasRenderingContext2D.drawImage()")}}
  - : تصویر مشخص‌شده را رسم می‌کند. این متد در چند قالب (overload) در دسترس است و انعطاف زیادی در استفاده از آن فراهم می‌کند.

### دستکاری پیکسل‌ها

به شیء {{domxref("ImageData")}} نیز مراجعه کنید.

- {{domxref("CanvasRenderingContext2D.createImageData()")}}
  - : یک شیء جدید و خالی {{domxref("ImageData")}} با ابعاد مشخص‌شده می‌سازد. تمام پیکسل‌های شیء جدید سیاهِ شفاف هستند.
- {{domxref("CanvasRenderingContext2D.getImageData()")}}
  - : یک شیء {{domxref("ImageData")}} برمی‌گرداند که داده‌های پیکسلی ناحیهٔ canvas را نشان می‌دهد؛ ناحیه‌ای که توسط مستطیلی با شروع از _(sx, sy)_ و عرض _sw_ و ارتفاع _sh_ مشخص شده است.
- {{domxref("CanvasRenderingContext2D.putImageData()")}}
  - : داده‌های شیء {{domxref("ImageData")}} داده‌شده را روی bitmap می‌نویسد. اگر یک ناحیهٔ کثیف (dirty rectangle) مشخص شده باشد، فقط پیکسل‌های همان ناحیه نوشته می‌شوند.

### هموارسازی تصویر

- {{domxref("CanvasRenderingContext2D.imageSmoothingEnabled")}}
  - : حالت هموارسازی تصویر؛ اگر غیرفعال باشد، هنگام تغییر مقیاس تصاویر هموار نمی‌شوند.
- {{domxref("CanvasRenderingContext2D.imageSmoothingQuality")}}
  - : به شما امکان می‌دهد کیفیت هموارسازی تصویر را تنظیم کنید.

### وضعیت canvas

زمینهٔ رندرگیری `CanvasRenderingContext2D` شامل انواع حالت‌های سبک رسم است (ویژگی‌هایی برای سبک خط، سبک fill، سبک سایه و سبک متن). متدهای زیر به شما در کار با این حالت کمک می‌کنند:

- {{domxref("CanvasRenderingContext2D.save()")}}
  - : وضعیت فعلی سبک رسم را با استفاده از یک پشته ذخیره می‌کند تا بتوانید هر تغییری را که روی آن اعمال کرده‌اید با `restore()` بازگردانید.
- {{domxref("CanvasRenderingContext2D.restore()")}}
  - : وضعیت سبک رسم را به آخرین عنصر موجود در «پشتهٔ حالت» که توسط `save()` ذخیره شده است بازمی‌گرداند.
- {{domxref("CanvasRenderingContext2D.canvas")}}
  - : یک ارجاع فقط‌خواندنی به یک شیء `OffscreenCanvas`.
- {{domxref("CanvasRenderingContext2D.getContextAttributes()")}} {{experimental_inline}}
  - : یک شیء شامل ویژگی‌های واقعی context را برمی‌گرداند. ویژگی‌های context را می‌توان با {{domxref("HTMLCanvasElement.getContext()")}} درخواست کرد.
- {{domxref("CanvasRenderingContext2D.reset()")}}
  - : وضعیت فعلی سبک رسم را به مقادیر پیش‌فرض بازنشانی می‌کند.

### فیلترها

- {{domxref("CanvasRenderingContext2D.filter")}}
  - : یک فیلتر CSS یا SVG روی canvas اعمال می‌کند؛ مثلاً برای تغییر روشنایی یا میزان تاری آن.

## خصوصیات و متدهای پشتیبانینشده

متد زیر در رابط `OffscreenCanvasRenderingContext2D` **پشتیبانی نمی‌شود**:

- {{domxref("CanvasRenderingContext2D.drawFocusIfNeeded()")}}
  - : اگر یک عنصر مشخص فوکوس داشته باشد، این متد یک قاب فوکوس دور مسیر فعلی رسم می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLCanvasElement")}}
- {{HTMLElement("canvas")}}