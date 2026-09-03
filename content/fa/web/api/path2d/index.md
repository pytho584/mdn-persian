---
title: Path2D
slug: Web/API/Path2D
page-type: web-api-interface
browser-compat: api.Path2D
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

رابط **`Path2D`** از Canvas 2D API برای تعریف یک مسیر (path) استفاده می‌شود که سپس می‌توان از آن روی یک شیء {{domxref("CanvasRenderingContext2D")}} استفاده کرد. [روش‌های مسیر](/en-US/docs/Web/API/CanvasRenderingContext2D#paths) رابط `CanvasRenderingContext2D` نیز روی این رابط وجود دارند که این امکان را به شما می‌دهد تا مسیر خود را هر زمان که بخواهید ذخیره و دوباره اجرا کنید.

## سازنده‌ها

- {{domxref("Path2D.Path2D", "Path2D()")}}
  - : سازنده `Path2D`. یک شیء `Path2D` جدید ایجاد می‌کند.

## روش‌های نمونه

- {{domxref("Path2D.addPath()")}}
  - : یک مسیر به مسیر فعلی اضافه می‌کند.
- {{domxref("CanvasRenderingContext2D.closePath", "Path2D.closePath()")}}
  - : باعث می‌شود نقطه قلم به ابتدای زیرمسیر فعلی بازگردد. سعی می‌کند از نقطه فعلی به ابتدا یک خط مستقیم رسم کند. اگر شکل از قبل بسته شده باشد یا فقط یک نقطه داشته باشد، این تابع هیچ کاری انجام نمی‌دهد.
- {{domxref("CanvasRenderingContext2D.moveTo()", "Path2D.moveTo()")}}
  - : نقطه شروع یک زیرمسیر جدید را به مختصات (`x, y`) منتقل می‌کند.
- {{domxref("CanvasRenderingContext2D.lineTo()", "Path2D.lineTo()")}}
  - : آخرین نقطه در زیرمسیر را با یک خط مستقیم به مختصات (`x, y`) متصل می‌کند.
- {{domxref("CanvasRenderingContext2D.bezierCurveTo()", "Path2D.bezierCurveTo()")}}
  - : یک منحنی بزیه مکعبی به مسیر اضافه می‌کند. به سه نقطه نیاز دارد. دو نقطه اول نقاط کنترل و نقطه سوم نقطه پایان هستند. نقطه شروع، آخرین نقطه در مسیر فعلی است که می‌توان قبل از ایجاد منحنی بزیه با استفاده از `moveTo()` آن را تغییر داد.
- {{domxref("CanvasRenderingContext2D.quadraticCurveTo()", "Path2D.quadraticCurveTo()")}}
  - : یک منحنی بزیه درجه دوم به مسیر فعلی اضافه می‌کند.
- {{domxref("CanvasRenderingContext2D.arc()", "Path2D.arc()")}}
  - : یک کمان به مسیر اضافه می‌کند که مرکز آن در موقعیت (`x, y`) با شعاع `r` است، از `startAngle` شروع شده و به `endAngle` ختم می‌شود و در جهت مشخص شده توسط `counterclockwise` (پیش‌فرض جهت عقربه‌های ساعت) حرکت می‌کند.
- {{domxref("CanvasRenderingContext2D.arcTo()", "Path2D.arcTo()")}}
  - : یک کمان دایره‌ای به مسیر با نقاط کنترل و شعاع داده شده اضافه می‌کند که با یک خط مستقیم به نقطه قبلی متصل می‌شود.
- {{domxref("CanvasRenderingContext2D.ellipse()", "Path2D.ellipse()")}}
  - : یک کمان بیضوی به مسیر اضافه می‌کند که مرکز آن در موقعیت (`x, y`) با شعاع‌های `radiusX` و `radiusY` است، از `startAngle` شروع شده و به `endAngle` ختم می‌شود و در جهت مشخص شده توسط `counterclockwise` (پیش‌فرض جهت عقربه‌های ساعت) حرکت می‌کند.
- {{domxref("CanvasRenderingContext2D.rect()", "Path2D.rect()")}}
  - : یک مسیر برای یک مستطیل در موقعیت (`x, y`) با اندازه‌ای که توسط `width` و `height` تعیین می‌شود ایجاد می‌کند.
- {{domxref("CanvasRenderingContext2D.roundRect()", "Path2D.roundRect()")}}
  - : یک مسیر برای یک مستطیل گرد در موقعیت (`x, y`) با اندازه‌ای که توسط `width` و `height` تعیین می‌شود ایجاد می‌کند و شعاع‌های کمان دایره‌ای که برای گوشه‌های مستطیل استفاده می‌شود توسط `radii` تعیین می‌شود.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CanvasRenderingContext2D")}}