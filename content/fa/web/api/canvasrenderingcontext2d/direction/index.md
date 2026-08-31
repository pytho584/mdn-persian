```markdown
---
title: "CanvasRenderingContext2D: direction property"
short-title: direction
slug: Web/API/CanvasRenderingContext2D/direction
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.direction
---

{{APIRef("Canvas API")}}

ویژگی
**`CanvasRenderingContext2D.direction`**
از Canvas 2D API جهت فعلی متن را برای رسم متن مشخص می‌کند.

## مقدار

مقادیر ممکن:

- `"ltr"`
  - : جهت متن از چپ به راست است.
- `"rtl"`
  - : جهت متن از راست به چپ است.
- `"inherit"`
  - : جهت متن از عنصر {{HTMLElement("canvas")}} یا {{domxref("Document")}} به‌طور مناسب به ارث برده می‌شود. مقدار پیش‌فرض.

مقدار پیش‌فرض `"inherit"` است.

## مثال‌ها

### تغییر جهت متن

این مثال دو قطعه متن رسم می‌کند. اولی از چپ به راست و دومی از راست به چپ است. توجه داشته باشید که «سلام!» در حالت `ltr` در حالت `rtl` به «!سلام» تبدیل می‌شود.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.font = "48px serif";
ctx.fillText("Hi!", 150, 50);
ctx.direction = "rtl";
ctx.fillText("Hi!", 150, 130);
```

#### نتیجه

{{ EmbedLiveSample('Changing_text_direction', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کننده این ویژگی: {{domxref("CanvasRenderingContext2D")}}
```