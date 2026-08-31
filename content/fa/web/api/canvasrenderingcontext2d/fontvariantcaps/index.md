---
title: "CanvasRenderingContext2D: fontVariantCaps property"
short-title: fontVariantCaps
slug: Web/API/CanvasRenderingContext2D/fontVariantCaps
page-type: web-api-instance-property
browser-compat: api.CanvasRenderingContext2D.fontVariantCaps
---

{{APIRef("Canvas API")}}

ویژگی **`CanvasRenderingContext2D.fontVariantCaps`** از [Canvas API](/en-US/docs/Web/API/Canvas_API) یک حالت بزرگ‌نمایی جایگزین برای متن نمایش‌داده‌شده مشخص می‌کند.

این ویژگی معادل ویژگی CSS {{cssxref("font-variant-caps")}} است.

## مقدار

مقدار حالت بزرگ‌نمایی جایگزین قلم، که یکی از موارد زیر است:

- `normal` (پیش‌فرض)
  - استفاده از گلیف‌های جایگزین را غیرفعال می‌کند.
- `small-caps`
  - نمایش حروف بزرگ کوچک (small capitals) را فعال می‌کند (ویژگی OpenType: `smcp`).
    گلیف‌های حروف بزرگ کوچک معمولاً از شکل حروف بزرگ استفاده می‌کنند اما به اندازه حروف کوچک کاهش می‌یابند.
- `all-small-caps`
  - نمایش حروف بزرگ کوچک را برای هر دو حرف بزرگ و کوچک فعال می‌کند (ویژگی‌های OpenType: `c2sc`, `smcp`).
- `petite-caps`
  - نمایش حروف بزرگ ریز (petite capitals) را فعال می‌کند (ویژگی OpenType: `pcap`).
- `all-petite-caps`
  - نمایش حروف بزرگ ریز را برای هر دو حرف بزرگ و کوچک فعال می‌کند (ویژگی‌های OpenType: `c2pc`, `pcap`).
- `unicase`
  - نمایش ترکیبی از حروف بزرگ کوچک برای حروف بزرگ با حروف کوچک معمولی را فعال می‌کند (ویژگی OpenType: `unic`).
- `titling-caps`
  - نمایش حروف بزرگ عنوان (titling capitals) را فعال می‌کند (ویژگی OpenType: `titl`).
    گلیف‌های حروف بزرگ اغلب برای استفاده با حروف کوچک طراحی شده‌اند.
    هنگامی که در دنباله‌های تمام‌بزرگ عنوان استفاده می‌شوند، ممکن است بیش از حد قوی به نظر برسند.
    حروف بزرگ عنوان به طور خاص برای این وضعیت طراحی شده‌اند.

از این ویژگی می‌توان برای دریافت یا تنظیم مقدار بزرگ‌نمایی قلم استفاده کرد.

توجه داشته باشید که برخی از این موارد نگرانی‌های دسترسی‌پذیری دارند که در مبحث مربوطه [`font-variant-caps`](/en-US/docs/Web/CSS/Reference/Properties/font-variant-caps#accessibility) توضیح داده شده‌اند.

## مثال‌ها

در این مثال متن "Hello World" را با استفاده از هر یک از مقادیر پشتیبانی‌شده ویژگی `fontVariantCaps` نمایش می‌دهیم.
مقدار نیز برای هر مورد با خواندن ویژگی نمایش داده می‌شود.

### HTML

```html
<canvas id="canvas" width="700" height="220"></canvas>
```

### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
ctx.font = "20px serif";

// Default (normal)
ctx.fillText(`Hello world (default: ${ctx.fontVariantCaps})`, 5, 20);

// Capitalization: small-caps
ctx.fontVariantCaps = "small-caps";
ctx.fillText(`Hello world (${ctx.fontVariantCaps})`, 5, 50);

// Capitalization: all-small-caps
ctx.fontVariantCaps = "all-small-caps";
ctx.fillText(`Hello world (${ctx.fontVariantCaps})`, 5, 80);

// Capitalization: petite-caps
ctx.fontVariantCaps = "petite-caps";
ctx.fillText(`Hello world (${ctx.fontVariantCaps})`, 5, 110);

// Capitalization: all-petite-caps
ctx.fontVariantCaps = "all-petite-caps";
ctx.fillText(`Hello world (${ctx.fontVariantCaps})`, 5, 140);

// Capitalization: unicase
ctx.fontVariantCaps = "unicase";
ctx.fillText(`Hello world (${ctx.fontVariantCaps})`, 5, 170);

// Capitalization: titling-caps
ctx.fontVariantCaps = "titling-caps";
ctx.fillText(`Hello world (${ctx.fontVariantCaps})`, 5, 200);
```

### نتیجه

{{ EmbedLiveSample('Examples', 700, 230) }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}