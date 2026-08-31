---
title: "CanvasRenderingContext2D: globalAlpha property"
short-title: globalAlpha
slug: Web/API/CanvasRenderingContext2D/globalAlpha
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.globalAlpha
---

{{APIRef("Canvas API")}}

ویژگی **`CanvasRenderingContext2D.globalAlpha`** در Canvas 2D API مقدار آلفا (شفافیت) را مشخص می‌کند که قبل از رسم اشکال و تصاویر روی بوم، به آن‌ها اعمال می‌شود.

> [!NOTE]
> همچنین به فصل [استفاده از استایل‌ها و رنگ‌ها](/en-US/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors) در [آموزش Canvas](/en-US/docs/Web/API/Canvas_API/Tutorial) مراجعه کنید.

## مقدار

عددی بین `0.0` (کاملاً شفاف) و `1.0` (کاملاً مات)، شامل این دو مقدار. مقدار پیش‌فرض `1.0` است. مقادیر خارج از این محدوده، از جمله {{jsxref("Infinity")}} و {{jsxref("NaN")}}، تنظیم نخواهند شد و `globalAlpha` مقدار قبلی خود را حفظ خواهد کرد.

## مثال‌ها

### رسم اشکال نیمه‌شفاف

در این مثال از ویژگی `globalAlpha` برای رسم دو مستطیل نیمه‌شفاف استفاده شده است.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.globalAlpha = 0.5;

ctx.fillStyle = "blue";
ctx.fillRect(10, 10, 100, 100);

ctx.fillStyle = "red";
ctx.fillRect(50, 50, 100, 100);
```

#### نتیجه

{{ EmbedLiveSample('Drawing_translucent_shapes', 700, 180) }}

### روی هم قرار دادن اشکال شفاف

این مثال تأثیر روی هم قرار دادن چندین شکل شفاف را نشان می‌دهد. ابتدا یک پس‌زمینهٔ توپر متشکل از چهار مربع با رنگ‌های متفاوت رسم می‌کنیم. سپس ویژگی `globalAlpha` را روی `0.2` (20% کدورت) تنظیم می‌کنیم؛ این سطح آلفا روی تمام اشکال شفاف ما اعمال خواهد شد. بعد از آن، با یک حلقهٔ `for` مجموعه‌ای از دایره‌ها با شعاع‌های رو به افزایش رسم می‌کنیم.

با هر دایرهٔ جدید، کدورت دایره‌های قبلی که زیر آن قرار دارند، عملاً افزایش می‌یابد. اگر تعداد گام‌ها را زیاد کنیم (و بنابراین دایره‌های بیشتری رسم کنیم)، در نهایت پس‌زمینه کاملاً از مرکز تصویر ناپدید می‌شود.

```html hidden
<canvas id="canvas" width="150" height="150"></canvas>
```

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// Draw background
ctx.fillStyle = "#ffdd00";
ctx.fillRect(0, 0, 75, 75);
ctx.fillStyle = "#66cc00";
ctx.fillRect(75, 0, 75, 75);
ctx.fillStyle = "#0099ff";
ctx.fillRect(0, 75, 75, 75);
ctx.fillStyle = "#ff3300";
ctx.fillRect(75, 75, 75, 75);
ctx.fillStyle = "white";

// Set transparency value
ctx.globalAlpha = 0.2;

// Draw transparent circles
for (let i = 0; i < 7; i++) {
  ctx.beginPath();
  ctx.arc(75, 75, 10 + 10 * i, 0, Math.PI * 2, true);
  ctx.fill();
}
```

{{EmbedLiveSample("Overlaying_transparent_shapes", "", "180")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

### یادداشت‌های مخصوص Gecko

- از Gecko 5.0 به بعد، مشخص کردن مقادیر نامعتبر برای `globalAlpha` دیگر استثنای `SYNTAX_ERR` را پرتاب نمی‌کند؛ این مقادیر اکنون به‌درستی و در سکوت نادیده گرفته می‌شوند.

### یادداشت‌های مخصوص WebKit/Blink

- در مرورگرهای مبتنی بر WebKit و Blink، علاوه بر این ویژگی، متد غیراستاندارد و منسوخ `ctx.setAlpha()` نیز پیاده‌سازی شده است.

## همچنین ببینید

- رابط تعریف‌کنندهٔ این ویژگی: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.globalCompositeOperation")}}