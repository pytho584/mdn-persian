---
title: "Canvas API"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API"
translated_by: "n8n + AI"
---

---
title: Canvas API
slug: Web/API/Canvas_API
page-type: web-api-overview
browser-compat: html.elements.canvas
---

{{DefaultAPISidebar("Canvas API")}}

**Canvas API** روشی برای ترسیم گرافیک از طریق [جاوااسکریپت](/en-US/docs/Web/JavaScript) و عنصر {{HtmlElement("canvas")}} در [HTML](/en-US/docs/Web/HTML) فراهم میکند. از جمله کاربردهای آن میتوان به انیمیشن، گرافیک بازی، تجسم دادهها، دستکاری تصاویر و پردازش ویدیوی بلادرنگ اشاره کرد.

Canvas API عمدتاً بر گرافیک دوبعدی تمرکز دارد. [WebGL API](/en-US/docs/Web/API/WebGL_API) که از عنصر `<canvas>` نیز استفاده میکند، گرافیکهای دوبعدی و سهبعدی شتابدهیشده با سختافزار را ترسیم میکند.

## مثال ساده

این مثال ساده یک مستطیل سبز بر روی بوم ترسیم میکند.

### HTML

```html
<canvas id="canvas"></canvas>
```

### جاوااسکریپت

متد {{domxref("Document.getElementById()")}} ارجاعی به عنصر `<canvas>` در HTML دریافت میکند. سپس، متد {{domxref("HTMLCanvasElement.getContext()")}} بافت یا زمینه آن عنصر را دریافت میکند—همان چیزی که ترسیم روی آن انجام میشود.

ترسیم واقعی با استفاده از رابط {{domxref("CanvasRenderingContext2D")}} انجام میشود. ویژگی {{domxref("CanvasRenderingContext2D.fillStyle", "fillStyle")}} مستطیل را سبز میکند. متد {{domxref("CanvasRenderingContext2D.fillRect()", "fillRect()")}} گوشهی بالا-چپ آن را در (۱۰، ۱۰) قرار میدهد و عرض آن را ۱۵۰ واحد و ارتفاع آن را ۱۰۰ واحد تعیین میکند.

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.fillStyle = "green";
ctx.fillRect(10, 10, 150, 100);
```

### نتیجه

{{ EmbedLiveSample('Basic_example', 700, 180) }}

## مرجع

- {{domxref("HTMLCanvasElement")}}
- {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasGradient")}}
- {{domxref("CanvasPattern")}}
- {{domxref("ImageBitmap")}}
- {{domxref("ImageData")}}
- {{domxref("TextMetrics")}}
- {{domxref("OffscreenCanvas")}}
- {{domxref("Path2D")}} {{experimental_inline}}
- {{domxref("ImageBitmapRenderingContext")}} {{experimental_inline}}

> [!NOTE]
> رابطهای مرتبط با `WebGLRenderingContext` در بخش [WebGL](/en-US/docs/Web/API/WebGL_API) مرجع داده شدهاند.

> [!NOTE]
> {{domxref("OffscreenCanvas")}} همچنین در وب ورکرها در دسترس است.

{{domxref("CanvasCaptureMediaStreamTrack")}} یک رابط مرتبط است.

## راهنماها و آموزشها

- [آموزش Canvas](/en-US/docs/Web/API/Canvas_API/Tutorial)
  - : یک آموزش جامع که هم کاربرد پایه Canvas API و هم ویژگی‌های پیشرفته آن را پوشش می‌دهد.
- [HTML5 Canvas Deep Dive](https://joshondesign.com/p/books/canvasdeepdive/title.html)
  - : یک معرفی عملی و کتاب‌گونه به Canvas API و WebGL.
- [راهنمای Canvas](https://bucephalus.org/text/CanvasHandbook/CanvasHandbook.html)
  - : یک مرجع کاربردی برای Canvas API.
- [دستکاری ویدیو با استفاده از canvas](/en-US/docs/Web/API/Canvas_API/Manipulating_video_using_canvas)
  - : ترکیب {{HTMLElement("video")}} و {{HTMLElement("canvas")}} برای دستکاری داده‌های ویدیویی در زمان واقعی.

## کتابخانه‌ها

Canvas API بسیار قدرتمند است، اما همیشه ساده برای استفاده نیست. کتابخانه‌های فهرست‌شده در زیر می‌توانند ایجاد پروژه‌های مبتنی بر canvas را سریع‌تر و آسان‌تر کنند.

- [EaselJS](https://createjs.com/easeljs) یک کتابخانه متن‌باز canvas است که ایجاد بازی‌ها، هنر تولیدی (generative art) و سایر تجربه‌های بسیار گرافیکی را آسان می‌کند.
- [Fabric.js](https://fabricjs.com/) یک کتابخانه متن‌باز canvas با قابلیت‌های تجزیه SVG است.
- [heatmap.js](https://www.patrick-wied.at/static/heatmapjs/) یک کتابخانه متن‌باز برای ایجاد نقشه‌های حرارتی داده مبتنی بر canvas است.
- [JavaScript InfoVis Toolkit](https://philogb.github.io/jit/) تجسم‌های تعاملی داده ایجاد می‌کند.
- [Konva.js](https://konvajs.org/) یک کتابخانه canvas دوبعدی برای برنامه‌های دسکتاپ و موبایل است.
- [p5.js](https://p5js.org/) مجموعه کاملی از قابلیت‌های ترسیم مخصوص هنرمندان، طراحان، مربیان و مبتدیان دارد.
- [Phaser](https://phaser.io/) یک چارچوب متن‌باز سریع، رایگان و سرگرم‌کننده برای بازی‌های مرورگری مبتنی بر Canvas و WebGL است.
- [Pts.js](https://ptsjs.org/) یک کتابخانه برای کدنویسی خلاقانه و تجسم در canvas و SVG است.
- [Rekapi](https://github.com/jeremyckahn/rekapi) یک API کلیدگذاری (key-framing) انیمیشن برای Canvas است.
- [Scrawl-canvas](https://scrawl.rikweb.org.uk/) یک کتابخانه متن‌باز جاوااسکریپت برای ایجاد و دستکاری عناصر canvas دوبعدی است.
- چارچوب [ZIM](https://zimjs.com/) امکانات رفاهی، اجزا و کنترل‌ها برای کدنویسی خلاقانه روی canvas فراهم می‌کند — شامل دسترس‌پذیری و صدها آموزش رنگارنگ است.
- [Sprig](https://github.com/hackclub/sprig) یک کتابخانه توسعه بازی مبتنی بر کاشی، متن‌باز و مناسب مبتدیان است که از Canvas استفاده می‌کند.

> [!NOTE]
> برای کتابخانه‌های 2D و 3D که از WebGL استفاده می‌کنند، به [WebGL API](/en-US/docs/Web/API/WebGL_API) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [WebGL](/en-US/docs/Web/API/WebGL_API)