---
title: "CanvasRenderingContext2D: fontKerning property"
short-title: fontKerning
slug: Web/API/CanvasRenderingContext2D/fontKerning
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.fontKerning
---

{{APIRef("Canvas API")}}

خاصیت **`CanvasRenderingContext2D.fontKerning`** در [Canvas API](/en-US/docs/Web/API/Canvas_API) مشخص می‌کند که چگونه از اطلاعات کرنینگ فونت استفاده شود.

کرنینگ فاصله‌گذاری بین حروف مجاور را در فونت‌های متناسب تنظیم می‌کند و در صورت وجود فضای کافی، به حروف اجازه می‌دهد به محدوده بصری یکدیگر نفوذ کنند.
برای مثال، در فونت‌هایی که کرنینگ خوبی دارند، کاراکترهای `AV`، `Ta` و `We` به هم می‌چسبند و فاصله‌گذاری یکنواخت‌تر و خواناتری نسبت به متن بدون کرنینگ ایجاد می‌کنند.

این خاصیت معادل خاصیت CSS {{cssxref("font-kerning")}} است.

## مقدار

این خاصیت برای دریافت یا تنظیم مقدار استفاده می‌شود.

مقادیر مجاز عبارتند از:

- `auto`
  - : مرورگر تعیین می‌کند که آیا کرنینگ فونت استفاده شود یا خیر.
    برای مثال، برخی مرورگرها کرنینگ را برای فونت‌های کوچک غیرفعال می‌کنند، زیرا اعمال آن می‌تواند خوانایی متن را کاهش دهد.
- `normal`
  - : اطلاعات کرنینگ ذخیره‌شده در فونت باید اعمال شود.
- `none`
  - : اطلاعات کرنینگ ذخیره‌شده در فونت غیرفعال است.

## مثال‌ها

در این مثال، متن «AVA Ta We» را با هر یک از مقادیر پشتیبانی‌شده خاصیت `textRendering` نمایش می‌دهیم.

### HTML

```html
<canvas id="canvas" width="700" height="140"></canvas>
```

### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
ctx.font = "30px serif";

// پیش‌فرض (auto)
ctx.fillText(`AVA Ta We (default: ${ctx.fontKerning})`, 5, 30);

// کرنینگ فونت: normal
ctx.fontKerning = "normal";
ctx.fillText(`AVA Ta We (${ctx.fontKerning})`, 5, 70);

// کرنینگ فونت: none
ctx.fontKerning = "none";
ctx.fillText(`AVA Ta We (${ctx.fontKerning})`, 5, 110);
```

### نتیجه

توجه کنید که در آخرین رشته، کرنینگ فونت غیرفعال است و بنابراین حروف مجاور فاصله‌های یکنواختی دارند.

{{ EmbedLiveSample('Examples', 700, 150) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}