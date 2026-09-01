---
title: "FontFace: FontFace() constructor"
---

{{APIRef("CSS Font Loading API")}}{{AvailableInWorkers}}

سازنده‌ی **`FontFace()`** یک شیء جدید از {{domxref("FontFace")}} می‌سازد.

## Syntax

```js-nolint
new FontFace(family, source)
new FontFace(family, source, descriptors)
```

### پارامترها

- `family`
  - : یک نام خانوادگی فونت را مشخص می‌کند که می‌توان برای تطبیق با این font face (چهره فونت) هنگام استایل‌دهی عناصر استفاده کرد. همان نوع مقادیر توصیف‌کننده‌ی {{cssxref("@font-face/font-family", "font-family")}} در {{cssxref("@font-face")}} را می‌پذیرد. این مقدار را می‌توان با استفاده از ویژگی [`FontFace.family`](/en-US/docs/Web/API/FontFace/family) نیز خواند و تنظیم کرد.

- `source`
  - : منبع فونت. این می‌تواند یکی از موارد زیر باشد:
    - یک URL به یک فایل فونت.
    - داده‌های باینری فونت در یک [`ArrayBuffer`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer) یا یک [`TypedArray`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypedArray).

- `descriptors` {{optional_inline}}
  - : مجموعه‌ای از توصیف‌کننده‌های اختیاری که به صورت یک شیء ارسال می‌شوند. می‌تواند هر یک از توصیف‌کننده‌های موجود برای `@font-face` را شامل شود:
    - `ascentOverride`
      - : با یک مقدار مجاز برای {{cssxref("@font-face/ascent-override")}}.
    - `descentOverride`
      - : با یک مقدار مجاز برای {{cssxref("@font-face/descent-override")}}.
    - `display`
      - : با یک مقدار مجاز برای {{cssxref("@font-face/font-display")}}.
    - `featureSettings`
      - : با یک مقدار مجاز برای {{cssxref("font-feature-settings")}}.
    - `lineGapOverride`
      - : با یک مقدار مجاز برای {{cssxref("@font-face/line-gap-override")}}.
    - `stretch`
      - : با یک مقدار مجاز برای {{cssxref("@font-face/font-stretch")}}.
    - `style`
      - : با یک مقدار مجاز برای {{cssxref("@font-face/font-style")}}.
    - `unicodeRange`
      - : با یک مقدار مجاز برای {{cssxref("@font-face/unicode-range")}}.
    - `variationSettings`
      - : با یک مقدار مجاز برای {{cssxref("@font-face/font-variation-settings")}}.
    - `weight`
      - : با یک مقدار مجاز برای {{cssxref("@font-face/font-weight")}}.

### استثناها

- `SyntaxError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که یک رشته‌ی توصیف‌کننده با دستور زبان توصیف‌کننده‌ی متناظر {{cssxref("@font-face")}} مطابقت نداشته باشد، یا منبع باینری مشخص‌شده قابل بارگیری نباشد. این خطا باعث می‌شود {{domxref("FontFace.status")}} روی `error` تنظیم شود.

## مثال‌ها

```js
async function loadFonts() {
  const font = new FontFace("my-font", 'url("my-font.woff")', {
    style: "normal",
    weight: "400",
    stretch: "condensed",
  });
  // wait for font to be loaded
  await font.load();
  // add font to document
  document.fonts.add(font);
  // enable font with CSS class
  document.body.classList.add("fonts-loaded");
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{cssxref("@font-face")}}