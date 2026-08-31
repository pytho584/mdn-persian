---
title: "CanvasRenderingContext2D: createLinearGradient() method"
---

---
title: "CanvasRenderingContext2D: createLinearGradient() method"
short-title: createLinearGradient()
slug: Web/API/CanvasRenderingContext2D/createLinearGradient
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.createLinearGradient
---

{{APIRef("Canvas API")}}

متد **`CanvasRenderingContext2D.createLinearGradient()`** از Canvas 2D API، یک گرادیان را در امتداد خطی که دو مختصات داده‌شده را به هم متصل می‌کند، ایجاد می‌کند.

![گرادیان رنگ‌ها را در امتداد خط گرادیان تغییر می‌دهد؛ از نقطه x0، y0 شروع شده و به x1، y1 می‌رود، حتی اگر این نقاط خط گرادیان را فراتر از لبه‌های عنصری که گرادیان روی آن رسم می‌شود، امتداد دهند.](mdn-canvas-lineargradient.png)

این متد یک {{domxref("CanvasGradient")}} خطی برمی‌گرداند. برای اعمال آن روی یک شکل، ابتدا باید گرادیان به ویژگی‌های {{domxref("CanvasRenderingContext2D.fillStyle", "fillStyle")}} یا {{domxref("CanvasRenderingContext2D.strokeStyle", "strokeStyle")}} اختصاص داده شود.

> [!NOTE]
> مختصات گرادیان سراسری هستند، یعنی نسبت به فضای مختصات جاری. وقتی روی یک شکل اعمال می‌شوند، این مختصات هیچ نسبتی با مختصات خودِ شکل ندارند.

## نحو

```js-nolint
createLinearGradient(x0, y0, x1, y1)
```

متد `createLinearGradient()` با چهار پارامتر تعریف می‌شود که نقطه شروع و پایان خط گرادیان را مشخص می‌کنند.

### پارامترها

- `x0`
  - : مختصات محور x نقطه شروع.
- `y0`
  - : مختصات محور y نقطه شروع.
- `x1`
  - : مختصات محور x نقطه پایان.
- `y1`
  - : مختصات محور y نقطه پایان.

### مقدار بازگشتی

یک {{domxref("CanvasGradient")}} خطی که با خط مشخص‌شده مقداردهی اولیه شده است.

### استثناها

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر مقادیر نامتناهی (non-finite) به‌عنوان پارامتر ارسال شوند، این استثنا پرتاب می‌شود.

## مثال‌ها

### پر کردن یک مستطیل با گرادیان خطی

این مثال با استفاده از متد `createLinearGradient()` یک گرادیان خطی مقداردهی اولیه می‌کند. سپس سه نقطه توقف رنگ (color stop) بین نقطه شروع و پایان گرادیان ایجاد می‌شود. در پایان، گرادیان به کانتکست بوم اختصاص داده می‌شود و به‌صورت یک مستطیل پر شده رندر می‌شود.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// Create a linear gradient
// The start gradient point is at x=20, y=0
// The end gradient point is at x=220, y=0
const gradient = ctx.createLinearGradient(20, 0, 220, 0);

// Add three color stops
gradient.addColorStop(0, "green");
gradient.addColorStop(0.5, "cyan");
gradient.addColorStop(1, "green");

// Set the fill style and draw a rectangle
ctx.fillStyle = gradient;
ctx.fillRect(20, 20, 200, 100);
```

#### نتیجه

{{ EmbedLiveSample('Filling_a_rectangle_with_a_linear_gradient', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- رابطی که این متد را تعریف می‌کند: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.createRadialGradient()")}}
- {{domxref("CanvasRenderingContext2D.createConicGradient()")}}