---
title: "CanvasRenderingContext2D: getTransform() method"
---

---
title: "CanvasRenderingContext2D: getTransform() method"
short-title: getTransform()
slug: Web/API/CanvasRenderingContext2D/getTransform
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.getTransform
---

{{APIRef("Canvas API")}}

متد **`CanvasRenderingContext2D.getTransform()`** از Canvas 2D API، ماتریس تبدیل فعلیِ اعمال‌شده بر بافت (context) را بازیابی می‌کند.

## نحو

```js-nolint
getTransform()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء {{domxref("DOMMatrix")}}.

ماتریس تبدیل با عبارت زیر توصیف می‌شود:

<!-- prettier-ignore-start -->
<math display="block">
  <semantics><mrow><mo>[</mo><mtable columnalign="center center center" rowspacing="0.5ex"><mtr><mtd><mi>a</mi></mtd><mtd><mi>c</mi></mtd><mtd><mi>e</mi></mtd></mtr><mtr><mtd><mi>b</mi></mtd><mtd><mi>d</mi></mtd><mtd><mi>f</mi></mtd></mtr><mtr><mtd><mn>0</mn></mtd><mtd><mn>0</mn></mtd><mtd><mn>1</mn></mtd></mtr></mtable><mo>]</mo></mrow><annotation encoding="TeX">\left[ \begin{array}{ccc} a & c & e \\ b & d & f \\ 0 & 0 & 1 \end{array} \right]</annotation></semantics>
</math>
<!-- prettier-ignore-end -->

> [!NOTE]
> شیء بازگردانده‌شده زنده (live) نیست؛ بنابراین به‌روزرسانی آن تأثیری بر ماتریس تبدیل فعلی نخواهد داشت و به‌روزرسانی ماتریس تبدیل فعلی نیز تأثیری بر `DOMMatrix` که قبلاً بازگردانده شده، نخواهد داشت.

## مثال‌ها

در مثال زیر، دو عنصر {{htmlelement("canvas")}} داریم. با استفاده از {{domxref("CanvasRenderingContext2D.setTransform()")}} یک تبدیل روی بافت عنصر اول اعمال و یک مربع روی آن رسم می‌کنیم؛ سپس ماتریس را با `getTransform()` از آن بازیابی می‌کنیم.

سپس ماتریس بازیابی‌شده را با ارسال مستقیم شیء `DOMMatrix` به `setTransform()` روی بافت بوم دوم اعمال و یک دایره روی آن رسم می‌کنیم.

### HTML

```html
<canvas width="240"></canvas> <canvas width="240"></canvas>
```

### CSS

```css
canvas {
  border: 1px solid black;
}
```

### JavaScript

```js
const canvases = document.querySelectorAll("canvas");
const ctx1 = canvases[0].getContext("2d");
const ctx2 = canvases[1].getContext("2d");

ctx1.setTransform(1, 0.2, 0.8, 1, 0, 0);
ctx1.fillRect(25, 25, 50, 50);

let storedTransform = ctx1.getTransform();
console.log(storedTransform);

ctx2.setTransform(storedTransform);
ctx2.beginPath();
ctx2.arc(50, 50, 50, 0, 2 * Math.PI);
ctx2.fill();
```

### نتیجه

{{ EmbedLiveSample('Examples', "100%", 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- رابط تعریف‌کنندهٔ این متد: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.transform()")}}