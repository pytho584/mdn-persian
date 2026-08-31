---
title: CanvasRenderingContext2D
slug: Web/API/CanvasRenderingContext2D
page-type: web-api-interface
browser-compat: api.CanvasRenderingContext2D
---

{{APIRef("Canvas API")}}

رابط **`CanvasRenderingContext2D`** که بخشی از [Canvas API](/en-US/docs/Web/API/Canvas_API) است، زمینهٔ رندر دوبعدی را برای سطح ترسیم یک عنصر {{HTMLElement("canvas")}} فراهم می‌کند. از این رابط برای ترسیم شکل‌ها، متن، تصاویر و سایر اشیا استفاده می‌شود.

ویژگی‌ها و متدهای این رابط در بخش مرجع این صفحه شرح داده شده‌اند. [آموزش Canvas](/en-US/docs/Web/API/Canvas_API/Tutorial) نیز توضیحات، مثال‌ها و منابع بیشتری را ارائه می‌دهد.

برای [`OffscreenCanvas`](/en-US/docs/Web/API/OffscreenCanvas) یک رابط معادل وجود دارد که زمینهٔ رندر را فراهم می‌کند. این زمینهٔ رندر خارج از صفحه، بیشتر ویژگی‌ها و متدهای مشابه `CanvasRenderingContext2D` را به ارث می‌برد و در صفحهٔ مرجع {{domxref("OffscreenCanvasRenderingContext2D")}} با جزئیات بیشتری توضیح داده شده است.

## مثال پایه

برای به دست آوردن یک نمونه از `CanvasRenderingContext2D`، ابتدا باید یک عنصر HTML `<canvas>` برای کار داشته باشید:

```html
<canvas id="my-house" width="300" height="300"></canvas>
```

برای به دست آوردن زمینهٔ رندر دوبعدی canvas، متد {{domxref("HTMLCanvasElement.getContext()", "getContext()")}} را روی عنصر `<canvas>` فراخوانی کنید و آرگومان `'2d'` را به آن بدهید:

```js
const canvas = document.getElementById("my-house");
const ctx = canvas.getContext("2d");
```

حالا که زمینه را دارید، می‌توانید هر چیزی که دوست دارید بکشید. این کد یک خانه ترسیم می‌کند:

```js
// تنظیم عرض خط
ctx.lineWidth = 10;

// دیوار
ctx.strokeRect(75, 140, 150, 110);

// در
ctx.fillRect(130, 190, 40, 60);

// سقف
ctx.beginPath();
ctx.moveTo(50, 140);
ctx.lineTo(150, 60);
ctx.lineTo(250, 140);
ctx.closePath();
ctx.stroke();
```

نتیجهٔ ترسیم به این شکل است:

{{EmbedLiveSample("Basic_example", 700, 330)}}

## مرجع

### زمینه (Context)

- {{domxref("CanvasRenderingContext2D.getContextAttributes()")}}
  - : یک شیء شامل ویژگی‌های زمینه‌ای که مرورگر استفاده می‌کند را برمی‌گرداند. این ویژگی‌ها را می‌توان هنگام استفاده از {{domxref("HTMLCanvasElement.getContext()")}} برای ایجاد زمینهٔ دوبعدی درخواست کرد.
- {{domxref("CanvasRenderingContext2D.isContextLost()")}}
  - : اگر زمینهٔ رندر از دست رفته باشد، مقدار `true` را برمی‌گرداند.

### ترسیم مستطیل‌ها

سه متد وجود دارند که بلافاصله مستطیل‌ها را روی canvas ترسیم می‌کنند.

- {{domxref("CanvasRenderingContext2D.clearRect()")}}
  - : تمام پیکسل‌های مستطیل تعریف‌شده با نقطهٔ شروع _(x, y)_ و اندازه _(width, height)_ را به رنگ سیاه شفاف تنظیم می‌کند و محتوای قبلاً ترسیم‌شده را پاک می‌کند.
- {{domxref("CanvasRenderingContext2D.fillRect()")}}
  - : یک مستطیل پر شده در موقعیت _(x, y)_ با اندازه‌ای که توسط _width_ و _height_ تعیین می‌شود ترسیم می‌کند.
- {{domxref("CanvasRenderingContext2D.strokeRect()")}}
  - : یک مستطیل با نقطهٔ شروع در _(x, y)_ و عرض _w_ و ارتفاع _h_ را با استفاده از استایل stroke فعلی روی canvas می‌کشد.

### ترسیم متن

متدهای زیر متن را ترسیم می‌کنند. همچنین به شیء {{domxref("TextMetrics")}} برای ویژگی‌های متن مراجعه کنید.

- {{domxref("CanvasRenderingContext2D.fillText()")}}
  - : یک متن داده شده را در موقعیت (x, y) داده شده (پر می‌کند) ترسیم می‌کند.
- {{domxref("CanvasRenderingContext2D.strokeText()")}}
  - : یک متن داده شده را در موقعیت (x, y) داده شده (با stroke) ترسیم می‌کند.
- {{domxref("CanvasRenderingContext2D.measureText()")}}
  - : یک شیء {{domxref("TextMetrics")}} برمی‌گرداند.

### استایل‌های خط

متدها و ویژگی‌های زیر نحوهٔ ترسیم خطوط را کنترل می‌کنند.

- {{domxref("CanvasRenderingContext2D.lineWidth")}}
  - : عرض خطوط. پیش‌فرض `1.0`.
- {{domxref("CanvasRenderingContext2D.lineCap")}}
  - : نوع انتهای خطوط. مقادیر ممکن: `butt` (پیش‌فرض)، `round`، `square`.
- {{domxref("CanvasRenderingContext2D.lineJoin")}}
  - : نوع گوشه‌ها را در محل برخورد دو خط تعریف می‌کند. مقادیر ممکن: `round`، `bevel`، `miter` (پیش‌فرض).
- {{domxref("CanvasRenderingContext2D.miterLimit")}}
  - : نسبت حد miter. پیش‌فرض `10`.
- {{domxref("CanvasRenderingContext2D.getLineDash()")}}
  - : الگوی خط چین فعلی را به صورت آرایه‌ای شامل تعداد زوجی از اعداد غیرمنفی برمی‌گرداند.
- {{domxref("CanvasRenderingContext2D.setLineDash()")}}
  - : الگوی خط چین فعلی را تنظیم می‌کند.
- {{domxref("CanvasRenderingContext2D.lineDashOffset")}}
  - : مشخص می‌کند که یک آرایهٔ خط چین از کجا روی خط شروع شود.

### استایل‌های متن

ویژگی‌های زیر نحوهٔ چیدمان متن را کنترل می‌کنند.

- {{domxref("CanvasRenderingContext2D.font")}}
  - : تنظیمات فونت. مقدار پیش‌فرض `"10px sans-serif"`.
- {{domxref("CanvasRenderingContext2D.textAlign")}}
  - : تنظیم تراز متن. مقادیر ممکن: `start` (پیش‌فرض)، `end`، `left`، `right`، `center`.
- {{domxref("CanvasRenderingContext2D.textBaseline")}}
  - : تنظیم خط پایه. مقادیر ممکن: `top`، `hanging`، `middle`، `alphabetic` (پیش‌فرض)، `ideographic`، `bottom`.
- {{domxref("CanvasRenderingContext2D.direction")}}
  - : جهت‌گیری. مقادیر ممکن: `ltr`، `rtl`، `inherit` (پیش‌فرض).
- {{domxref("CanvasRenderingContext2D.letterSpacing")}}
  - : فاصلهٔ حروف. پیش‌فرض: `0px`.
- {{domxref("CanvasRenderingContext2D.fontKerning")}}
  - : کرنینگ فونت. مقادیر ممکن: `auto` (پیش‌فرض)، `normal`، `none`.
- {{domxref("CanvasRenderingContext2D.fontStretch")}}
  - : کشیدگی فونت. مقادیر ممکن: `ultra-condensed`، `extra-condensed`، `condensed`، `semi-condensed`، `normal` (پیش‌فرض)، `semi-expanded`، `expanded`، `extra-expanded`، `ultra-expanded`.
- {{domxref("CanvasRenderingContext2D.fontVariantCaps")}}
  - : نوع حروف بزرگ فونت. مقادیر ممکن: `normal` (پیش‌فرض)، `small-caps`، `all-small-caps`، `petite-caps`، `all-petite-caps`، `unicase`، `titling-caps`.
- {{domxref("CanvasRenderingContext2D.textRendering")}}
  - : رندر متن. مقادیر ممکن: `auto` (پیش‌فرض)، `optimizeSpeed`، `optimizeLegibility`، `geometricPrecision`.
- {{domxref("CanvasRenderingContext2D.wordSpacing")}}
  - : فاصلهٔ کلمات. مقدار پیش‌فرض: `0px`
- {{domxref("CanvasRenderingContext2D.lang")}}
  - : زبان زمینهٔ ترسیم canvas را دریافت یا تنظیم می‌کند.

### استایل‌های پر کردن (Fill) و stroke

استایل پر کردن برای رنگ‌ها و استایل‌های داخل اشکال و استایل stroke برای خطوط دور اشکال استفاده می‌شود.

- {{domxref("CanvasRenderingContext2D.fillStyle")}}
  - : رنگ یا استایل برای استفاده درون اشکال. پیش‌فرض `black` است.
- {{domxref("CanvasRenderingContext2D.strokeStyle")}}
  - : رنگ یا استایل برای خطوط دور اشکال. پیش‌فرض `black` است.

### گرادیان‌ها و الگوها

- {{domxref("CanvasRenderingContext2D.createConicGradient()")}}
  - : یک گرادیان مخروطی حول یک نقطه که توسط مختصات داده شده با پارامترها مشخص می‌شود، ایجاد می‌کند.
- {{domxref("CanvasRenderingContext2D.createLinearGradient()")}}
  - : یک گرادیان خطی در امتداد خطی که توسط مختصات داده شده با پارامترها مشخص می‌شود، ایجاد می‌کند.
- {{domxref("CanvasRenderingContext2D.createRadialGradient()")}}
  - : یک گرادیان شعاعی با توجه به مختصات دو دایره که توسط پارامترها مشخص می‌شوند، ایجاد می‌کند.
- {{domxref("CanvasRenderingContext2D.createPattern()")}}
  - : یک الگو با استفاده از تصویر مشخص شده ایجاد می‌کند. این الگو منبع را در جهت‌های مشخص شده توسط آرگومان تکرار تکرار می‌کند. این متد یک {{domxref("CanvasPattern")}} برمی‌گرداند.

### سایه‌ها

- {{domxref("CanvasRenderingContext2D.shadowBlur")}}
  - : میزان محو شدگی را مشخص می‌کند. پیش‌فرض: `0`.
- {{domxref("CanvasRenderingContext2D.shadowColor")}}
  - : رنگ سایه. پیش‌فرض: سیاه کاملاً شفاف.
- {{domxref("CanvasRenderingContext2D.shadowOffsetX")}}
  - : فاصلهٔ افقی جابجایی سایه. پیش‌فرض: `0`.
- {{domxref("CanvasRenderingContext2D.shadowOffsetY")}}
  - : فاصلهٔ عمودی جابجایی سایه. پیش‌فرض: `0`.

### مسیرها (Paths)

متدهای زیر را می‌توان برای دستکاری مسیرهای اشیا استفاده کرد.

- {{domxref("CanvasRenderingContext2D.beginPath()")}}
  - : با خالی کردن لیست زیرمسیرها یک مسیر جدید شروع می‌کند. این متد را زمانی که می‌خواهید یک مسیر جدید ایجاد کنید، فراخوانی کنید.
- {{domxref("CanvasRenderingContext2D.closePath()")}}
  - : باعث می‌شود نقطهٔ قلم به ابتدای زیرمسیر فعلی برگردد. سعی می‌کند یک خط مستقیم از نقطهٔ فعلی به نقطهٔ شروع بکشد. اگر شکل قبلاً بسته شده باشد یا فقط یک نقطه داشته باشد، این تابع کاری انجام نمی‌دهد.
- {{domxref("CanvasRenderingContext2D.moveTo()")}}
  - : نقطهٔ شروع یک زیرمسیر جدید را به مختصات (x, y) منتقل می‌کند.
- {{domxref("CanvasRenderingContext2D.lineTo()")}}
  - : آخرین نقطه در زیرمسیر فعلی را با یک خط مستقیم به مختصات (x, y) مشخص شده متصل می‌کند.
- {{domxref("CanvasRenderingContext2D.bezierCurveTo()")}}
  - : یک منحنی Bézier مکعبی به مسیر فعلی اضافه می‌کند.
- {{domxref("CanvasRenderingContext2D.quadraticCurveTo()")}}
  - : یک منحنی Bézier درجه دوم به مسیر فعلی اضافه می‌کند.
- {{domxref("CanvasRenderingContext2D.arc()")}}
  - : یک کمان دایره‌ای به مسیر فعلی اضافه می‌کند.
- {{domxref("CanvasRenderingContext2D.arcTo()")}}
  - : یک کمان با نقاط کنترل و شعاع داده شده به مسیر فعلی اضافه می‌کند که با یک خط مستقیم به نقطهٔ قبلی متصل می‌شود.
- {{domxref("CanvasRenderingContext2D.ellipse()")}}
  - : یک کمان بیضوی به مسیر فعلی اضافه می‌کند.
- {{domxref("CanvasRenderingContext2D.rect()")}}
  - : یک مسیر برای یک مستطیل در موقعیت (x, y) با اندازه‌ای که توسط _width_ و _height_ تعیین می‌شود ایجاد می‌کند.
- {{domxref("CanvasRenderingContext2D.roundRect()")}}
  - : یک مسیر برای یک مستطیل گرد با موقعیت، عرض، ارتفاع و شعاع گوشه‌های مشخص شده ایجاد می‌کند.

### ترسیم مسیرها

- {{domxref("CanvasRenderingContext2D.fill()")}}
  - : زیرمسیرهای فعلی را با استایل fill فعلی پر می‌کند.
- {{domxref("CanvasRenderingContext2D.stroke()")}}
  - : زیرمسیرهای فعلی را با استایل stroke فعلی ترسیم می‌کند.
- {{domxref("CanvasRenderingContext2D.drawFocusIfNeeded()")}}
  - : اگر یک عنصر داده شده دارای فوکوس باشد، این متد یک حلقهٔ فوکوس دور مسیر فعلی می‌کشد.
- {{domxref("CanvasRenderingContext2D.clip()")}}
  - : یک مسیر برش از زیرمسیرهای فعلی ایجاد می‌کند. هر چیزی که بعد از فراخوانی `clip()` ترسیم شود، فقط درون مسیر برش ظاهر می‌شود. برای مثال، به [مسیرهای برش](/en-US/docs/Web/API/Canvas_API/Tutorial/Compositing) در آموزش Canvas مراجعه کنید.
- {{domxref("CanvasRenderingContext2D.isPointInPath()")}}
  - : گزارش می‌دهد که آیا نقطهٔ مشخص شده درون مسیر فعلی قرار دارد یا خیر.
- {{domxref("CanvasRenderingContext2D.isPointInStroke()")}}
  - : گزارش می‌دهد که آیا نقطهٔ مشخص شده درون ناحیهٔ تحت پوشش stroke یک مسیر قرار دارد یا خیر.

### تبدیل‌ها (Transformations)

اشیاء در زمینهٔ رندر `CanvasRenderingContext2D` یک ماتریس تبدیل فعلی و متدهایی برای دستکاری آن دارند. این ماتریس تبدیل هنگام ایجاد مسیر پیش‌فرض فعلی، ترسیم متن، اشکال و اشیاء {{domxref("Path2D")}} اعمال می‌شود. متدهای ذکر شده در زیر به دلایل تاریخی و سازگاری باقی مانده‌اند، زیرا اشیاء {{domxref("DOMMatrix")}} در حال حاضر در بیشتر بخش‌های API استفاده می‌شوند و در آینده به جای آنها استفاده خواهند شد.

- {{domxref("CanvasRenderingContext2D.getTransform()")}}
  - : ماتریس تبدیل فعلی اعمال شده به context را بازیابی می‌کند.
- {{domxref("CanvasRenderingContext2D.rotate()")}}
  - : یک چرخش به ماتریس تبدیل اضافه می‌کند. آرگومان زاویه، یک زاویه چرخش در جهت عقربه‌های ساعت است که بر حسب رادیان بیان می‌شود.
- {{domxref("CanvasRenderingContext2D.scale()")}}
  - : یک تبدیل مقیاس به واحدهای canvas به صورت افقی به اندازه x و عمودی به اندازه y اضافه می‌کند.
- {{domxref("CanvasRenderingContext2D.translate()")}}
  - : یک تبدیل انتقالی با جابجایی canvas و مبدأ آن به صورت افقی x و عمودی y روی شبکه اضافه می‌کند.
- {{domxref("CanvasRenderingContext2D.transform()")}}
  - : ماتریس تبدیل فعلی را در ماتریس توصیف شده توسط آرگومان‌هایش ضرب می‌کند.
- {{domxref("CanvasRenderingContext2D.setTransform()")}}
  - : تبدیل فعلی را به ماتریس همانی بازنشانی می‌کند و سپس متد `transform()` را با همان آرگومان‌ها فراخوانی می‌کند.
- {{domxref("CanvasRenderingContext2D.resetTransform()")}}
  - : تبدیل فعلی را با ماتریس همانی بازنشانی می‌کند.

### ترکیب (Compositing)

- {{domxref("CanvasRenderingContext2D.globalAlpha")}}
  - : مقدار آلفایی که قبل از ترکیب شدن بر روی canvas به اشکال و تصاویر اعمال می‌شود. پیش‌فرض `1.0` (کدر).
- {{domxref("CanvasRenderingContext2D.globalCompositeOperation")}}
  - : با اعمال `globalAlpha`، نحوهٔ ترسیم اشکال و تصاویر روی بیت‌مپ موجود را تنظیم می‌کند.

### ترسیم تصاویر

- {{domxref("CanvasRenderingContext2D.drawImage()")}}
  - : تصویر مشخص شده را ترسیم می‌کند. این متد در چندین قالب موجود است و انعطاف‌پذیری زیادی در استفاده از آن فراهم می‌کند.

### دستکاری پیکسل

همچنین به شیء {{domxref("ImageData")}} مراجعه کنید.

- {{domxref("CanvasRenderingContext2D.createImageData()")}}
  - : یک شیء {{domxref("ImageData")}} جدید و خالی با ابعاد مشخص شده ایجاد می‌کند. تمام پیکسل‌های شیء جدید سیاه شفاف هستند.
- {{domxref("CanvasRenderingContext2D.getImageData()")}}
  - : یک شیء {{domxref("ImageData")}} شامل داده‌های پیکسل زیرین برای ناحیه‌ای از canvas را که با مستطیلی که از _(sx, sy)_ شروع می‌شود و عرض _sw_ و ارتفاع _sh_ دارد، برمی‌گرداند.
- {{domxref("CanvasRenderingContext2D.putImageData()")}}
  - : داده‌های حاصل از شیء {{domxref("ImageData")}} داده شده را روی بیت‌مپ اعمال می‌کند. اگر یک مستطیل کثیف (dirty rectangle) ارائه شود، فقط پیکسل‌های آن مستطیل اعمال می‌شوند.

### هموارسازی تصویر

- {{domxref("CanvasRenderingContext2D.imageSmoothingEnabled")}}
  - : حالت هموارسازی تصویر؛ اگر غیرفعال شود، تصاویر در صورت تغییر اندازه هموار نمی‌شوند.
- {{domxref("CanvasRenderingContext2D.imageSmoothingQuality")}}
  - : به شما امکان می‌دهد کیفیت هموارسازی تصویر را تنظیم کنید.

### وضعیت canvas

زمینهٔ رندر `CanvasRenderingContext2D` شامل حالات مختلف استایل ترسیم (ویژگی‌های استایل خط، استایل پر کردن، استایل سایه، استایل متن) است. متدهای زیر به شما در کار با این وضعیت کمک می‌کنند:

- {{domxref("CanvasRenderingContext2D.save()")}}
  - : وضعیت فعلی استایل ترسیم را با استفاده از یک پشته ذخیره می‌کند تا بتوانید هر تغییری که در آن ایجاد کرده‌اید را با استفاده از `restore()` برگردانید.
- {{domxref("CanvasRenderingContext2D.restore()")}}
  - : وضعیت استایل ترسیم را به آخرین عنصر در 'پشته وضعیت' که توسط `save()` ذخیره شده است، بازمی‌گرداند.
- {{domxref("CanvasRenderingContext2D.canvas")}}
  - : یک ارجاع برگشتی فقط خواندنی به {{domxref("HTMLCanvasElement")}}. اگر با یک عنصر {{HTMLElement("canvas")}} مرتبط نباشد، ممکن است [`null`](/en-US/docs/Web/JavaScript/Reference/Operators/null) باشد.
- {{domxref("CanvasRenderingContext2D.getContextAttributes()")}}
  - : یک شیء شامل ویژگی‌های زمینه‌ای که مرورگر استفاده می‌کند را برمی‌گرداند. این ویژگی‌ها را می‌توان هنگام استفاده از {{domxref("HTMLCanvasElement.getContext()")}} برای ایجاد زمینهٔ دوبعدی درخواست کرد.
- {{domxref("CanvasRenderingContext2D.reset()")}}
  - : زمینهٔ رندر، از جمله بافر پشتیبان، پشته وضعیت ترسیم، مسیر و استایل‌ها را بازنشانی می‌کند.
- {{domxref("CanvasRenderingContext2D.isContextLost()")}} {{Experimental_Inline}}
  - : اگر زمینهٔ رندر از دست رفته باشد، مقدار `true` را برمی‌گرداند.

### فیلترها

- {{domxref("CanvasRenderingContext2D.filter")}}
  - : یک فیلتر CSS یا SVG را به canvas اعمال می‌کند، مثلاً برای تغییر روشنایی یا تاری آن.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLCanvasElement")}}
- {{HTMLElement("canvas")}}
- {{domxref("OffscreenCanvas")}}