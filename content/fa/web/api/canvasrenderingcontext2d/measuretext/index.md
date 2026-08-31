---
title: "CanvasRenderingContext2D: measureText() method"
short-title: measureText()
slug: Web/API/CanvasRenderingContext2D/measureText
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.measureText
---

{{APIRef("Canvas API")}}

متد `CanvasRenderingContext2D.measureText()` یک شیء {{domxref("TextMetrics")}} برمی‌گرداند که شامل اطلاعاتی دربارهٔ متنِ اندازه‌گیری‌شده است (برای مثال، عرض آن).

## نحو

```js-nolint
measureText(text)
```

### پارامترها

- `text`
  - : رشته متنی که باید اندازه‌گیری شود.

### مقدار بازگشتی

یک شیء {{domxref("TextMetrics")}}.

## مثال‌ها

با توجه به این عنصر {{HTMLElement("canvas")}}:

```html
<canvas id="canvas"></canvas>
```

… می‌توانید با استفاده از کد زیر، یک شیء {{domxref("TextMetrics")}} به‌دست آورید:

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

let text = ctx.measureText("Hello world");
console.log(text.width); // 56;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کنندهٔ این متد: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("TextMetrics")}}