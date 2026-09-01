---
title: "FontData: fullName property"
short-title: fullName
slug: Web/API/FontData/fullName
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.FontData.fullName
---

{{APIRef("Local Font Access API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`fullName`** در رابط {{domxref("FontData")}} نام کامل قلم (font face) را برمی‌گرداند. این نام معمولاً یک نام قابل‌خواندن برای انسان است که برای شناسایی قلم استفاده می‌شود، مانند «Optima Bold».

مثال‌ها شامل موارد زیر هستند:

- Apple SD Gothic Neo UltraLight
- Arial Black
- Avenir Next Heavy
- Katari Medium Italic
- YuMincho +36p Kana Extrabold

## مقدار

یک رشته (string).

## مثال‌ها

قطعه کد زیر همه قلم‌های موجود را جستجو کرده و فراداده‌های آنها را ثبت می‌کند. این می‌تواند برای مثال برای پر کردن یک کنترل انتخاب‌کننده قلم استفاده شود.

```js
async function logFontData() {
  try {
    const availableFonts = await window.queryLocalFonts();
    for (const fontData of availableFonts) {
      console.log(fontData.postscriptName);
      console.log(fontData.fullName);
      console.log(fontData.family);
      console.log(fontData.style);
    }
  } catch (err) {
    console.error(err.name, err.message);
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از تایپوگرافی پیشرفته با قلم‌های محلی](https://developer.chrome.com/docs/capabilities/web-apis/local-fonts)
- {{cssxref("@font-face")}}