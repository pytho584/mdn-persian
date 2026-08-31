---
title: "CanvasRenderingContext2D: restore() method"
short-title: restore()
slug: Web/API/CanvasRenderingContext2D/restore
page-type: web-api-instance-method
browser-compat: api.CanvasRenderingContext2D.restore
---

{{APIRef("Canvas API")}}

متد
**`CanvasRenderingContext2D.restore()`**
از API بوم ۲ بعدی (Canvas 2D)، آخرین حالت ذخیره‌شدهٔ بوم را با خارج کردن ورودی بالایی از پشتهٔ حالت‌های رسم بازیابی می‌کند. اگر حالتی ذخیره نشده باشد، این متد هیچ کاری انجام نمی‌دهد.

برای اطلاعات بیشتر دربارهٔ [حالت رسم](/en-US/docs/Web/API/CanvasRenderingContext2D/save#description)، به {{domxref("CanvasRenderingContext2D.save()")}} مراجعه کنید.

## نحو (Syntax)

```js-nolint
restore()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### بازیابی یک حالت ذخیره‌شده

این مثال از متد `save()` برای ذخیرهٔ حالت فعلی و از `restore()` برای بازیابی بعدی آن استفاده می‌کند، تا بتوانید بعداً یک مستطیل را با حالت فعلی رسم کنید.

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### جاوااسکریپت

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// ذخیرهٔ حالت فعلی
ctx.save();

ctx.fillStyle = "green";
ctx.fillRect(10, 10, 100, 100);

// بازگشت به حالتی که در آخرین فراخوانی save() ذخیره شده بود
ctx.restore();

ctx.fillRect(150, 40, 100, 100);
```

#### نتیجه

{{ EmbedLiveSample('Restoring_a_saved_state', 700, 180) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط تعریف‌کنندهٔ این متد: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.save()")}}