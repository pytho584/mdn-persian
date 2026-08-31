---
title: CanvasGradient
slug: Web/API/CanvasGradient
page-type: web-api-interface
browser-compat: api.CanvasGradient
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

رابط **`CanvasGradient`** نمایانگر یک [شیء مات](https://en.wikipedia.org/wiki/Opaque_data_type) است که یک گرادیان را توصیف می‌کند. این رابط توسط متدهای {{domxref("CanvasRenderingContext2D.createLinearGradient()")}}، {{domxref("CanvasRenderingContext2D.createConicGradient()")}} یا {{domxref("CanvasRenderingContext2D.createRadialGradient()")}} بازگردانده می‌شود.

می‌توان از آن به عنوان `fillStyle` یا `strokeStyle` استفاده کرد.

## ویژگی‌های نمونه

_به عنوان یک شیء مات، هیچ ویژگی آشکاری وجود ندارد._

## متدهای نمونه

- {{domxref("CanvasGradient.addColorStop()")}}
  - یک توقف جدید را که توسط یک `offset` و یک `color` تعریف می‌شود، به گرادیان اضافه می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- متدهای ایجادکننده در {{domxref("CanvasRenderingContext2D")}}.
- عنصر {{HTMLElement("canvas")}} و رابط مرتبط با آن، {{domxref("HTMLCanvasElement")}}.