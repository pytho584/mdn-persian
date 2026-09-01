---
title: "FontData: postscriptName property"
short-title: postscriptName
slug: Web/API/FontData/postscriptName
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.FontData.postscriptName
---

{{APIRef("Local Font Access API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`postscriptName`** در رابط {{domxref("FontData")}}، نام PostScript چهرهٔ قلم را برمی‌گرداند.

این نام برای شناسایی یکتای قلم PostScript استفاده می‌شود و معمولاً دنباله‌ای پیوسته از نویسه‌هاست که نام و سبک قلم را شامل می‌شود.

نمونه‌ها عبارت‌اند از:

- AppleSDGothicNeo-UltraLight
- Arial-Black
- AvenirNext-Heavy
- Katari-MediumItalic
- YuMin_36pKn-Extrabold

## مقدار

یک رشته (string).

## مثال‌ها

قطعه‌کد زیر همهٔ قلم‌های موجود را جستجو کرده و فرادادهٔ آن‌ها را در کنسول ثبت می‌کند. برای مثال، می‌توان از آن برای پر کردن یک کنترل انتخاب قلم استفاده کرد.

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

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از تایپوگرافی پیشرفته با فونت‌های محلی](https://developer.chrome.com/docs/capabilities/web-apis/local-fonts)
- {{cssxref("@font-face")}}