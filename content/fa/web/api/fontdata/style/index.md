```
---
title: "FontData: style property"
short-title: style
slug: Web/API/FontData/style
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.FontData.style
---

{{APIRef("Local Font Access API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`style`** در رابط {{domxref("FontData")}}، سبک قلم را برمی‌گرداند.

این مقداری است که برای انتخاب سبک قلم مورد نظر خود استفاده می‌کنید، برای مثال در ویژگی {{cssxref("font-style")}}.

نمونه‌ها عبارتند از:

- UltraLight
- Regular
- Heavy
- Medium Italic
- Extrabold

## مقدار

یک رشته.

## مثال‌ها

قطعه کد زیر همه قلم‌های موجود را جستجو می‌کند و فراداده‌های آن را در کنسول ثبت می‌کند. برای مثال، می‌توان از آن برای پر کردن یک کنترل انتخاب قلم استفاده کرد.

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

- [استفاده از تایپوگرافی پیشرفته با قلم‌های محلی](https://developer.chrome.com/docs/capabilities/web-apis/local-fonts)
- {{cssxref("@font-face")}}
```