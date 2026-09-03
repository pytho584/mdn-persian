---
title: "PaintRenderingContext2D"
source: "https://developer.mozilla.org/en-US/docs/Web/API/PaintRenderingContext2D"
---

---
title: PaintRenderingContext2D
slug: Web/API/PaintRenderingContext2D
page-type: web-api-interface
browser-compat: api.PaintRenderingContext2D
---

{{APIRef("CSS Painting API")}}

**`PaintRenderingContext2D`** اینترفیس [CSS Painting API](/en-US/docs/Web/API/CSS_Painting_API) است و به عنوان بافت رندر (rendering context) این API برای ترسیم روی بیت‌مپ (bitmap) عمل می‌کند. این اینترفیس زیرمجموعه‌ای از API مربوط به {{domxref("CanvasRenderingContext2D")}} را پیاده‌سازی می‌کند، با این استثناها:

- متدهای [`CanvasImageData` برای دستکاری پیکسل‌ها](/en-US/docs/Web/API/CanvasRenderingContext2D#pixel_manipulation)، [`CanvasUserInterface` برای فوکوس](/en-US/docs/Web/API/CanvasRenderingContext2D/drawFocusIfNeeded)، [`CanvasText` برای ترسیم متن](/en-US/docs/Web/API/CanvasRenderingContext2D)، و [`CanvasTextDrawingStyles` برای سبک متن](/en-US/docs/Web/API/CanvasRenderingContext2D#text_styles) را پیاده‌سازی نمی‌کند.
- اندازه بیت‌مپ خروجی، به اندازه شیءای است که روی آن رندر انجام می‌شود.
- مقدار `currentColor`، وقتی به عنوان یک رنگ استفاده شود، به عنوان رنگ مشکی مات (opaque black) در نظر گرفته می‌شود.

این اینترفیس فقط در {{domxref("PaintWorkletGlobalScope")}} در دسترس است.

## ویژگی‌ها و متدهای نمونه

_`PaintRenderingContext2D` زیرمجموعه‌ای از API مربوط به {{domxref("CanvasRenderingContext2D")}} را پیاده‌سازی می‌کند، و همه ویژگی‌ها و متدهای آن همان کاربرد مشابه در `CanvasRenderingContext2D` را دارند._

### Context

- {{domxref("CanvasRenderingContext2D.isContextLost()")}}
  - : اگر بافت رندر از بین رفته باشد، مقدار `true` برمی‌گرداند.

### State

- {{domxref("CanvasRenderingContext2D.save()")}}
  - : وضعیت جاری سبک ترسیم را با استفاده از یک پشته (stack) ذخیره می‌کند تا بتوانید هر تغییری که در آن ایجاد می‌کنید را با استفاده از `restore()` بازگردانید.
- {{domxref("CanvasRenderingContext2D.restore()")}}
  - : وضعیت سبک ترسیم را به آخرین عنصر در 'پشته وضعیت' که توسط `save()` ذخیره شده است، بازمی‌گرداند.
- {{domxref("CanvasRenderingContext2D.reset()")}}
  - : وضعیت جاری سبک ترسیم را به مقادیر پیش‌فرض بازنشانی می‌کند.

### Transformations

- {{domxref("CanvasRenderingContext2D.getTransform()")}}
  - : ماتریس تبدیل جاری اعمال‌شده روی بافت را به عنوان یک {{domxref("DOMMatrix")}} بازمی‌گرداند.
- {{domxref("CanvasRenderingContext2D.rotate()")}}
  - : یک چرخش به ماتریس تبدیل اضافه می‌کند. آرگومان زاویه، زاویه چرخش در جهت عقربه‌های ساعت را نشان می‌دهد و بر حسب رادیان بیان می‌شود.
- {{domxref("CanvasRenderingContext2D.scale()")}}
  - : یک تبدیل مقیاس‌گذاری به واحدهای بوم (canvas) به اندازه x در جهت افقی و y در جهت عمودی اضافه می‌کند.
- {{domxref("CanvasRenderingContext2D.translate()")}}
  - : با جابجایی بوم و مبدأ آن به اندازه x در جهت افقی و y در جهت عمودی روی شبکه، یک تبدیل انتقال (translation) اضافه می‌کند.
- {{domxref("CanvasRenderingContext2D.transform()")}}
  - : ماتریس تبدیل جاری را در ماتریسی که توسط آرگومان‌هایش توصیف می‌شود ضرب می‌کند.
- {{domxref("CanvasRenderingContext2D.setTransform()")}}
  - : تبدیل جاری را به ماتریس همانی (identity matrix) بازنشانی می‌کند و سپس متد `transform()` را با همان آرگومان‌ها فراخوانی می‌کند.
- {{domxref("CanvasRenderingContext2D.resetTransform()")}}
  - : تبدیل جاری را با ماتریس همانی بازنشانی می‌کند.

### Compositing

- {{domxref("CanvasRenderingContext2D.globalAlpha")}}
  - : مقدار آلفا (alpha) که قبل از ترکیب اشکال و تصاویر روی بوم، روی آن‌ها اعمال می‌شود.
- {{domxref("CanvasRenderingContext2D.globalCompositeOperation")}}
  - : با اعمال `globalAlpha`، نحوه ترسیم اشکال و تصاویر روی بیت‌مپ موجود را تعیین می‌کند.

### Image smoothing

- {{domxref("CanvasRenderingContext2D.imageSmoothingEnabled")}}
  - : حالت هموارسازی تصویر؛ اگر غیرفعال باشد، تصاویر هنگام مقیاس‌گذاری هموار نمی‌شوند.
- {{domxref("CanvasRenderingContext2D.imageSmoothingQuality")}}
  - : به شما امکان می‌دهد کیفیت هموارسازی تصویر را تنظیم کنید.

### Fill and stroke styles

- {{domxref("CanvasRenderingContext2D.fillStyle")}}
  - : رنگ یا سبکی که برای داخل اشکال استفاده می‌شود.
- {{domxref("CanvasRenderingContext2D.strokeStyle")}}
  - : رنگ یا سبکی که برای خطوط دور اشکال استفاده می‌شود.

### Gradients and patterns

- {{domxref("CanvasRenderingContext2D.createConicGradient()")}}
  - : یک گرادیان مخروطی (conic gradient) حول یک نقطه که توسط مختصات پارامترها تعیین می‌شود ایجاد می‌کند.
- {{domxref("CanvasRenderingContext2D.createLinearGradient()")}}
  - : یک گرادیان خطی در امتداد خطی که توسط مختصات پارامترها تعیین می‌شود ایجاد می‌کند.
- {{domxref("CanvasRenderingContext2D.createRadialGradient()")}}
  - : یک گرادیان شعاعی (radial gradient) که توسط مختصات دو دایره پارامترها تعیین می‌شود ایجاد می‌کند.
- {{domxref("CanvasRenderingContext2D.createPattern()")}}
  - : یک الگوی {{domxref("CanvasPattern")}} از تصویر مشخص‌شده ایجاد می‌کند که در جهت‌های تعیین‌شده توسط آرگومان تکرار (repetition) تکرار می‌شود.

### Shadows

- {{domxref("CanvasRenderingContext2D.shadowBlur")}}
  - : میزان محو بودن (blur) را به عنوان یک عدد مشخص می‌کند.
- {{domxref("CanvasRenderingContext2D.shadowColor")}}
  - : رنگ سایه را به عنوان یک CSS {{cssxref("&lt;color&gt;")}} مشخص می‌کند.
- {{domxref("CanvasRenderingContext2D.shadowOffsetX")}}
  - : فاصله افقی جابجایی سایه را به عنوان یک عدد مشخص می‌کند.
- {{domxref("CanvasRenderingContext2D.shadowOffsetY")}}
  - : فاصله عمودی جابجایی سایه را به عنوان یک عدد مشخص می‌کند.

### Drawing rectangles

- {{domxref("CanvasRenderingContext2D.clearRect()")}}
  - : پیکسل‌های مستطیل داده‌شده را پاک می‌کند و آن‌ها را به رنگ مشکی شفاف (transparent black) تبدیل می‌کند.
- {{domxref("CanvasRenderingContext2D.fillRect()")}}
  - : پیکسل‌های مستطیل داده‌شده را با سبک پر کردن جاری رنگ‌آمیزی می‌کند.
- {{domxref("CanvasRenderingContext2D.strokeRect()")}}
  - : خط دور مستطیل داده‌شده را با استفاده از سبک خط (stroke) جاری رنگ‌آمیزی می‌کند.

### Drawing paths

- {{domxref("CanvasRenderingContext2D.beginPath()")}}
  - : یک مسیر جدید شروع می‌کند و لیست زیرمسیرها را خالی می‌کند. وقتی می‌خواهید یک مسیر جدید ایجاد کنید، این متد را فراخوانی کنید.
- {{domxref("CanvasRenderingContext2D.fill()")}}
  - : زیرمسیرهای مسیر جاری را با سبک پر کردن جاری پر می‌کند.
- {{domxref("CanvasRenderingContext2D.stroke()")}}
  - : زیرمسیرهای مسیر جاری را با سبک خط جاری خط می‌کشد (stroke).
- {{domxref("CanvasRenderingContext2D.clip()")}}
  - : مسیر جاری یا داده‌شده را به ناحیه برش جاری تبدیل می‌کند، با استفاده از قانون پر کردن داده‌شده برای تعیین اینکه کدام نقاط در مسیر هستند. تغییرات بعدی مسیر فقط در داخل مسیر برش ظاهر می‌شوند.
- {{domxref("CanvasRenderingContext2D.isPointInPath()")}}
  - : یک مقدار بولی که اگر نقطه مشخص‌شده در مسیر جاری یا مسیر مشخص‌شده باشد، مقدار آن `true` است.
- {{domxref("CanvasRenderingContext2D.isPointInStroke()")}}
  - : یک مقدار بولی که اگر نقطه داخل ناحیه‌ای باشد که توسط خط کشیدن یک مسیر احاطه شده است، مقدار آن `true` است.

### Drawing images

- {{domxref("CanvasRenderingContext2D.drawImage()")}}
  - : تصویر داده‌شده یا بخش مشخص‌شده از آن را ترسیم می‌کند، به صورت اختیاری با اندازه و موقعیت مشخص.

### Line styles

- {{domxref("CanvasRenderingContext2D.lineWidth")}}
  - : عددی که عرض خط را، بر حسب واحدهای فضای مختصات، مشخص می‌کند.
- {{domxref("CanvasRenderingContext2D.lineCap")}}
  - : نوع انتهای خطوط. مقادیر احتمالی: `butt` (پیش‌فرض)، `round`، `square`.
- {{domxref("CanvasRenderingContext2D.lineJoin")}}
  - : نوع گوشه‌هایی را که دو خط به هم می‌رسند تعریف می‌کند. مقادیر احتمالی: `round`، `bevel`، `miter` (پیش‌فرض).
- {{domxref("CanvasRenderingContext2D.miterLimit")}}
  - : عددی که نسبت حد میتر (miter limit ratio) را، بر حسب واحدهای فضای مختصات، مشخص می‌کند.
- {{domxref("CanvasRenderingContext2D.getLineDash()")}}
  - : الگوی خط‌چین جاری را به عنوان یک [`Array`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) از اعداد برمی‌گرداند که طول خطوط و فاصله‌های متناوب را بر حسب واحدهای فضای مختصات مشخص می‌کنند.
- {{domxref("CanvasRenderingContext2D.setLineDash()")}}
  - : لیست فاصله‌های خط و خط‌چین را به عنوان الگوی خط‌چین جاری تنظیم می‌کند (همانطور که هنگام خط کشیدن استفاده می‌شود).
- {{domxref("CanvasRenderingContext2D.lineDashOffset")}}
  - : مشخص می‌کند که آرایه خط‌چین از کجا روی یک خط شروع شود.

### Paths

- {{domxref("CanvasRenderingContext2D.closePath()")}}
  - : زیرمسیر جاری را به عنوان بسته علامت‌گذاری می‌کند، یک خط مستقیم از نقطه جاری به نقطه شروع می‌کشد، و یک زیرمسیر جدید با نقطه‌ای همانند نقطه شروع و پایان زیرمسیر تازه بسته‌شده شروع می‌کند. اگر شکل قبلاً بسته شده باشد یا فقط یک نقطه داشته باشد، این تابع هیچ کاری انجام نمی‌دهد.
- {{domxref("CanvasRenderingContext2D.moveTo()")}}
  - : نقطه شروع یک زیرمسیر جدید را به مختصات (x, y) منتقل می‌کند.
- {{domxref("CanvasRenderingContext2D.lineTo()")}}
  - : آخرین نقطه در زیرمسیر جاری را با یک خط مستقیم به مختصات (x, y) مشخص‌شده متصل می‌کند.
- {{domxref("CanvasRenderingContext2D.bezierCurveTo()")}}
  - : یک منحنی Bézier مکعبی به مسیر جاری اضافه می‌کند.
- {{domxref("CanvasRenderingContext2D.quadraticCurveTo()")}}
  - : یک منحنی Bézier درجه دوم به مسیر جاری اضافه می‌کند.
- {{domxref("CanvasRenderingContext2D.arc()")}}
  - : یک کمان دایره‌ای به مسیر جاری اضافه می‌کند.
- {{domxref("CanvasRenderingContext2D.arcTo()")}}
  - : یک کمان به مسیر جاری با نقاط کنترل و شعاع داده‌شده اضافه می‌کند که با یک خط مستقیم به نقطه قبلی متصل می‌شود.
- {{domxref("CanvasRenderingContext2D.ellipse()")}}
  - : یک کمان بیضی‌شکل به مسیر جاری اضافه می‌کند.
- {{domxref("CanvasRenderingContext2D.rect()")}}
  - : یک مسیر برای یک مستطیل در موقعیت (x, y) با اندازه‌ای که توسط _width_ و _height_ تعیین می‌شود ایجاد می‌کند.
- {{domxref("CanvasRenderingContext2D.roundRect()")}}
  - : یک مسیر برای یک مستطیل با گوشه‌های گرد در موقعیت (x, y) با اندازه‌ای که توسط _width_ و _height_ و شعاع‌هایی که توسط _radii_ تعیین می‌شود ایجاد می‌کند.

### Filters

- {{domxref("CanvasRenderingContext2D.filter")}} {{Non-standard_Inline}}
  - : یک فیلتر CSS یا SVG را روی بوم اعمال می‌کند، به عنوان مثال برای تغییر روشنایی یا تار بودن آن.

## مثال‌ها

مثال‌های کامل را در [CSS Painting API](/en-US/docs/Web/API/CSS_Painting_API) مشاهده کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از CSS Painting API](/en-US/docs/Web/API/CSS_Painting_API/Guide)
- [CSS Painting API](/en-US/docs/Web/API/CSS_Painting_API)
- [APIهای Houdini](/en-US/docs/Web/API/Houdini_APIs)