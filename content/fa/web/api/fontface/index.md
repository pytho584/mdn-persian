---
title: "FontFace"
slug: Web/API/FontFace
page-type: web-api-interface
browser-compat: api.FontFace
---

{{APIRef("CSS Font Loading API")}}{{AvailableInWorkers}}

رابط **`FontFace`** از [API بارگذاری فونت CSS](/en-US/docs/Web/API/CSS_Font_Loading_API) نشان‌دهنده‌ی یک قلم (font face) قابل استفاده است.

این رابط منبع یک قلم را تعریف می‌کند، خواه یک URL به یک منبع خارجی یا یک بافر (buffer) باشد، و همچنین ویژگی‌های قلم مانند `style`، `weight` و غیره را مشخص می‌کند. برای منابع قلم مبتنی بر URL، به نویسندگان امکان می‌دهد تا زمان واکشی و بارگذاری قلم از راه دور را تعیین کرده و وضعیت بارگذاری را پیگیری کنند.

## سازنده

- {{domxref("FontFace.FontFace", "FontFace()")}}
  - : یک شیء جدید `FontFace` می‌سازد و برمی‌گرداند که از یک منبع خارجی توصیف‌شده توسط یک URL یا از یک {{jsxref("ArrayBuffer")}} ساخته شده است.

## ویژگی‌های نمونه

- {{domxref("FontFace.ascentOverride")}}
  - : یک رشته که معیار بالای (ascent metric) قلم را بازیابی یا تنظیم می‌کند. معادل توصیفگر {{cssxref("@font-face/ascent-override", "ascent-override")}} است.
- {{domxref("FontFace.descentOverride")}}
  - : یک رشته که معیار پایین (descent metric) قلم را بازیابی یا تنظیم می‌کند. معادل توصیفگر {{cssxref("@font-face/descent-override", "descent-override")}} است.
- {{domxref("FontFace.display")}}
  - : یک رشته که نحوه نمایش قلم را بر اساس اینکه آیا بارگذاری شده و آماده استفاده است تعیین می‌کند.
- {{domxref("FontFace.family")}}
  - : یک رشته که خانواده (family) قلم را بازیابی یا تنظیم می‌کند. معادل توصیفگر {{cssxref("@font-face/font-family", "font-family")}} است.
- {{domxref("FontFace.featureSettings")}}
  - : یک رشته که ویژگی‌های کم‌استفاده قلم را که از طریق ویژگی‌های variant در دسترس نیستند، بازیابی یا تنظیم می‌کند. معادل ویژگی CSS {{cssxref("font-feature-settings")}} است.
- {{domxref("FontFace.lineGapOverride")}}
  - : یک رشته که معیار فاصله خط (line-gap metric) قلم را بازیابی یا تنظیم می‌کند. معادل توصیفگر {{cssxref("@font-face/line-gap-override", "line-gap-override")}} است.
- {{domxref("FontFace.loaded")}} {{ReadOnlyInline}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که وقتی قلم مشخص‌شده در سازنده‌ی شیء بارگذاری کامل شود، با شیء `FontFace` فعلی حل می‌شود (resolve) و در صورت خطا با یک `SyntaxError` {{domxref("DOMException")}} رد می‌شود (reject).
- {{domxref("FontFace.status")}} {{ReadOnlyInline}}
  - : یک مقدار شمارشی (enumerated) برمی‌گرداند که وضعیت قلم را نشان می‌دهد، یکی از `"unloaded"`، `"loading"`، `"loaded"` یا `"error"`.
- {{domxref("FontFace.stretch")}}
  - : یک رشته که نحوه‌ی کشیدگی (stretch) قلم را بازیابی یا تنظیم می‌کند. معادل توصیفگر {{cssxref("@font-face/font-stretch", "font-stretch")}} است.
- {{domxref("FontFace.style")}}
  - : یک رشته که سبک (style) قلم را بازیابی یا تنظیم می‌کند. معادل توصیفگر {{cssxref("@font-face/font-style", "font-style")}} است.
- {{domxref("FontFace.unicodeRange")}}
  - : یک رشته که محدوده نقاط کد یونیکد (unicode code points) پوشش‌دهنده قلم را بازیابی یا تنظیم می‌کند. معادل توصیفگر {{cssxref("@font-face/unicode-range", "unicode-range")}} است.
- {{domxref("FontFace.variant")}} {{non-standard_inline}}
  - : یک رشته که نوع (variant) قلم را بازیابی یا تنظیم می‌کند.
- {{domxref("FontFace.variationSettings")}}
  - : یک رشته که تنظیمات تغییرات (variation settings) قلم را بازیابی یا تنظیم می‌کند. معادل توصیفگر {{cssxref("@font-face/font-variation-settings", "font-variation-settings")}} است.
- {{domxref("FontFace.weight")}}
  - : یک رشته که وزن (weight) قلم را بازیابی یا تنظیم می‌کند. معادل توصیفگر {{cssxref("@font-face/font-weight", "font-weight")}} است.
- {{domxref("FontFace.load()")}}
  - : یک قلم را بر اساس نیازهای ارسال‌شده به سازنده‌ی شیء فعلی (شامل یک مکان یا بافر منبع) بارگذاری می‌کند و یک {{jsxref('Promise')}} برمی‌گرداند که با شیء FontFace فعلی حل می‌شود.

## مثال‌ها

کد زیر یک قلم را با استفاده از داده‌های موجود در URL "my-font.woff" به همراه چند توصیفگر قلم تعریف می‌کند. فقط برای نشان دادن نحوه کار، سپس توصیفگر `stretch` را با استفاده از یک ویژگی تعریف می‌کنیم.

```js
// Define a FontFace
const font = new FontFace("my-font", 'url("my-font.woff")', {
  style: "italic",
  weight: "400",
});

font.stretch = "condensed";
```

سپس قلم را با استفاده از {{domxref("FontFace.load()")}} بارگذاری می‌کنیم و از promise بازگشتی برای پیگیری اتمام یا گزارش خطا استفاده می‌کنیم.

```js
// Load the font
font.load().then(
  () => {
    // Resolved - add font to document.fonts
  },
  (err) => {
    console.error(err);
  },
);
```

برای استفاده‌ی واقعی از قلم، باید آن را به یک {{domxref("FontFaceSet")}} اضافه کنیم. می‌توانیم این کار را قبل یا بعد از بارگذاری قلم انجام دهیم.

برای مثال‌های بیشتر به [CSS Font Loading API > Examples](/en-US/docs/Web/API/CSS_Font_Loading_API#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{cssxref("@font-face")}}