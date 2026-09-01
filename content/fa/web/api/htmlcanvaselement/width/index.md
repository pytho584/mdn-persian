---
title: "HTMLCanvasElement: width property"
short-title: width
slug: Web/API/HTMLCanvasElement/width
page-type: web-api-instance-property
browser-compat: api.HTMLCanvasElement.width
---

{{APIRef("Canvas API")}}

خاصیت **`HTMLCanvasElement.width`** یک `integer` مثبت است که منعکس‌کنندهٔ ویژگی HTML [`width`](/en-US/docs/Web/HTML/Reference/Elements/canvas#width) عنصر {{HTMLElement("canvas")}} است که به پیکسل‌های CSS تفسیر می‌شود. وقتی ویژگی مشخص نشده باشد یا به مقدار نامعتبری (مانند منفی) تنظیم شود، مقدار پیش‌فرض `300` استفاده می‌شود.

تنظیم خاصیت `width` کل بافت رندرینگ را به حالت پیش‌فرض خود بازنشانی می‌کند. این شامل پاک کردن بوم (بافر پشتیبان)، بازنشانی مسیر فعلی، و بازنشانی _همه_ خصوصیات مانند `fillStyle` و `globalCompositeOperation` می‌شود. این بازنشانی برای همه انواع بافت رخ می‌دهد، و حتی زمانی که `width` را به مقدار فعلی آن تنظیم کنید نیز اتفاق می‌افتد. برای بازیابی محتوای قبلی پس از تغییر عرض، از {{domxref("CanvasRenderingContext2D.getImageData()")}} و {{domxref("CanvasRenderingContext2D.putImageData()")}} استفاده کنید. خصوصیات بافت باید جداگانه ردیابی و بازیابی شوند.

این یکی از دو خاصیتی است که دیگری {{domxref("HTMLCanvasElement.height")}} می‌باشد و اندازهٔ بوم را کنترل می‌کنند.

## مقدار

یک عدد.

## مثال‌ها

با توجه به این عنصر {{HTMLElement("canvas")}}:

```html
<canvas id="canvas" width="300" height="300"></canvas>
```

می‌توانید عرض بوم را با کد زیر بدست آورید:

```js
const canvas = document.getElementById("canvas");
console.log(canvas.width); // 300
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLCanvasElement")}}: رابطی که برای تعریف خاصیت `HTMLCanvasElement.width` استفاده می‌شود
- {{domxref("HTMLCanvasElement.height")}}: خاصیت دیگر برای کنترل اندازهٔ بوم
- {{domxref("HTMLEmbedElement.width")}}
- {{domxref("HTMLIFrameElement.width")}}
- {{domxref("HTMLImageElement.width")}}
- {{domxref("HTMLObjectElement.width")}}
- {{domxref("HTMLSourceElement.width")}}
- {{domxref("HTMLVideoElement.width")}}