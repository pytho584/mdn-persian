---
title: "CanvasRenderingContext2D: font property"
short-title: font
slug: Web/API/CanvasRenderingContext2D/font
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.font
---

{{APIRef("Canvas API")}}

خاصیت **`CanvasRenderingContext2D.font`** از Canvas 2D API سبک متن فعلی را برای رسم متن مشخص می‌کند. این رشته از همان نحو (syntax) مشخص‌کننده [CSS font](/en-US/docs/Web/CSS/Reference/Properties/font) استفاده می‌کند.

## مقدار

یک رشته که به عنوان مقدار CSS {{cssxref("font")}} تجزیه می‌شود. فونت پیش‌فرض `10px sans-serif` است.

## مثال‌ها

### استفاده از یک فونت سفارشی

در این مثال از خاصیت `font` برای تعیین وزن، اندازه و خانواده فونت سفارشی استفاده می‌کنیم.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.font = "bold 48px serif";
ctx.strokeText("Hello world", 50, 100);
```

#### نتیجه

{{ EmbedLiveSample('Using_a_custom_font', 700, 180) }}

### بارگذاری فونت‌ها با استفاده از CSS Font Loading API

با کمک API {{domxref("FontFace")}} می‌توانید فونت‌ها را قبل از استفاده در canvas به صراحت بارگذاری کنید.

```js
let f = new FontFace("test", "url(x)");

f.load().then(() => {
  // آماده استفاده از فونت در زمینه canvas
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این خاصیت: {{domxref("CanvasRenderingContext2D")}}