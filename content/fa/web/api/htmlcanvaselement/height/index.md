---
title: "HTMLCanvasElement: height property"
short-title: height
slug: Web/API/HTMLCanvasElement/height
page-type: web-api-instance-property
browser-compat: api.HTMLCanvasElement.height
---

{{APIRef("Canvas API")}}

خاصیت **`HTMLCanvasElement.height`** یک `integer` مثبت است که منعکس‌کنندهٔ ویژگی HTML [`height`](/en-US/docs/Web/HTML/Reference/Elements/canvas#height) عنصر {{HTMLElement("canvas")}} است که بر حسب پیکسل‌های CSS تفسیر می‌شود. وقتی این ویژگی مشخص نشده باشد، یا اگر مقدار نامعتبری مانند یک عدد منفی به آن داده شود، مقدار پیش‌فرض `150` استفاده می‌شود.

تنظیم خاصیت `height` کل بافت رندرینگ (rendering context) را به حالت پیش‌فرض خود بازنشانی می‌کند. این شامل پاک کردن بوم (بافر پشتیبان)، بازنشانی مسیر جاری (current path)، و بازنشانی _همه_ ویژگی‌هایی مانند `fillStyle` و `globalCompositeOperation` می‌شود. این بازنشانی برای همه انواع بافت رخ می‌دهد، و حتی زمانی که `height` را به مقدار فعلی خود تنظیم کنید نیز اتفاق می‌افتد. برای بازیابی محتوای قبلی پس از تغییر ارتفاع، از {{domxref("CanvasRenderingContext2D.getImageData()")}} و {{domxref("CanvasRenderingContext2D.putImageData()")}} استفاده کنید. ویژگی‌های بافت باید به‌طور جداگانه ردیابی و بازیابی شوند.

این یکی از دو خاصیتی است که دیگری {{domxref("HTMLCanvasElement.width")}} می‌باشد، و اندازهٔ بوم را کنترل می‌کنند.

## مقدار

یک عدد.

## مثال‌ها

با توجه به این عنصر {{HTMLElement("canvas")}}:

```html
<canvas id="canvas" width="300" height="300"></canvas>
```

می‌توانید ارتفاع بوم را با کد زیر بدست آورید:

```js
const canvas = document.getElementById("canvas");
console.log(canvas.height); // 300
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLCanvasElement")}}: رابط (interface) مورد استفاده برای تعریف خاصیت `HTMLCanvasElement.height`
- {{domxref("HTMLCanvasElement.width")}}: خاصیت دیگر برای کنترل اندازهٔ بوم
- {{domxref("HTMLEmbedElement.height")}}
- {{domxref("HTMLIFrameElement.height")}}
- {{domxref("HTMLImageElement.height")}}
- {{domxref("HTMLObjectElement.height")}}
- {{domxref("HTMLSourceElement.height")}}
- {{domxref("HTMLVideoElement.height")}}