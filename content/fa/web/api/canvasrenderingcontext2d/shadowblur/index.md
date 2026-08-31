---
title: "CanvasRenderingContext2D: shadowBlur property"
short-title: shadowBlur
slug: Web/API/CanvasRenderingContext2D/shadowBlur
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.shadowBlur
---

{{APIRef("Canvas API")}}

ویژگی
**`CanvasRenderingContext2D.shadowBlur`**
در API Canvas 2D میزان محو شدن سایه‌ها را مشخص می‌کند. مقدار پیش‌فرض آن
`0` (بدون محو شدگی) است.

> [!NOTE]
> سایه‌ها تنها زمانی رسم می‌شوند که ویژگی
> {{domxref("CanvasRenderingContext2D.shadowColor", "shadowColor")}} روی یک مقدار غیرشفاف تنظیم شده باشد.
> همچنین یکی از ویژگی‌های `shadowBlur`،
> {{domxref("CanvasRenderingContext2D.shadowOffsetX", "shadowOffsetX")}} یا
> {{domxref("CanvasRenderingContext2D.shadowOffsetY", "shadowOffsetY")}} باید غیر از صفر باشد.

## مقدار

یک عدد اعشاری نامنفی که میزان محو شدگی سایه را مشخص می‌کند؛ `0` به معنای بدون محو شدگی و اعداد بزرگ‌تر به معنای محو شدگی بیشتر است. این مقدار با تعداد پیکسل‌ها متناظر نیست و تحت تأثیر ماتریس تبدیل فعلی قرار نمی‌گیرد. مقدار پیش‌فرض `0` است. مقادیر منفی، {{jsxref("Infinity")}} و {{jsxref("NaN")}} نادیده گرفته می‌شوند.

## نمونه‌ها

### افزودن سایه به یک شکل

این مثال یک سایه‌ی محو شده به یک مستطیل اضافه می‌کند. ویژگی `shadowColor`
رنگ آن را تنظیم می‌کند و `shadowBlur` میزان محو شدگی آن را مشخص می‌کند.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### جاوااسکریپت

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// سایه
ctx.shadowColor = "red";
ctx.shadowBlur = 15;

// مستطیل
ctx.fillStyle = "blue";
ctx.fillRect(20, 20, 150, 100);
```

#### نتیجه

{{ EmbedLiveSample('Adding_a_shadow_to_a_shape', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

### نکات ویژه WebKit/Blink

در مرورگرهای مبتنی بر WebKit و Blink، متد غیراستاندارد و منسوخ‌شده
`ctx.setShadow()` علاوه بر این ویژگی پیاده‌سازی شده است.

```js
setShadow(width, height, blur, color, alpha);
setShadow(width, height, blur, graylevel, alpha);
setShadow(width, height, blur, r, g, b, a);
setShadow(width, height, blur, c, m, y, k, a);
```

## همچنین ببینید

- رابط تعریف‌کننده این ویژگی: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.shadowColor")}}