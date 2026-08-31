---
title: "CanvasGradient: addColorStop() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/CanvasGradient/addColorStop"
translated_by: "n8n + AI"
---

---
title: "CanvasGradient: addColorStop() method"
short-title: addColorStop()
slug: Web/API/CanvasGradient/addColorStop
page-type: web-api-instance-method
browser-compat: api.CanvasGradient.addColorStop
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

متد **`CanvasGradient.addColorStop()`** یک ایستگاه رنگی جدید، که توسط یک `offset` و یک `color` تعریف می‌شود، به یک گرادیان بوم اضافه می‌کند.

## نحو

```js-nolint
addColorStop(offset, color)
```

### پارامترها

- `offset`
  - : عددی بین `0` و `1`، به‌صورت شامل، که موقعیت ایستگاه رنگی را نشان می‌دهد. `0` شروع گرادیان و `1` پایان آن را نشان می‌دهد.
- `color`
  - : یک مقدار [CSS](/en-US/docs/Web/CSS) {{cssxref("&lt;color&gt;")}} که رنگ ایستگاه را نشان می‌دهد.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `IndexSizeError` {{domxref("DOMException")}}
  - : اگر `offset` بین 0 و 1 (هر دو شامل) نباشد، پرتاب می‌شود.
- `SyntaxError` {{domxref("DOMException")}}
  - : اگر `color` نتواند به‌عنوان یک مقدار CSS {{cssxref("&lt;color&gt;")}} تجزیه شود، پرتاب می‌شود.

## مثال‌ها

### افزودن ایستگاه‌ها به یک گرادیان

این مثال از متد `addColorStop` برای افزودن ایستگاه‌ها به یک شیء خطی از نوع {{domxref("CanvasGradient")}} استفاده می‌کند. سپس گرادیان برای پر کردن یک مستطیل استفاده می‌شود.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### جاوااسکریپت

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

let gradient = ctx.createLinearGradient(0, 0, 200, 0);
gradient.addColorStop(0, "green");
gradient.addColorStop(0.7, "white");
gradient.addColorStop(1, "pink");
ctx.fillStyle = gradient;
ctx.fillRect(10, 10, 200, 100);
```

#### نتیجه

{{ EmbedLiveSample('Adding_stops_to_a_gradient', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این متد: {{domxref("CanvasGradient")}}
- {{domxref("CanvasRenderingContext2D.createLinearGradient()")}}
- {{domxref("CanvasRenderingContext2D.createRadialGradient()")}}