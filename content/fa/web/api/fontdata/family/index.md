---
title: "FontData: family property"
---

---
title: "FontData: family property"
short-title: family
slug: Web/API/FontData/family
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.FontData.family
---

{{APIRef("Local Font Access API")}}{{SeeCompatTable}}

ویژگیِ فقط‌خواندنی **`family`** در رابط {{domxref("FontData")}} خانوادهٔ فونت را برمی‌گرداند.

این نامی است که هنگام ارجاع به خانوادهٔ فونت از کد استفاده می‌شود؛ برای مثال در ویژگی {{cssxref("font-family")}} یا در بخش‌هایی از قاعدهٔ {{cssxref("@font-face")}} مانند تابع `local()`.

برای مثال:

- Apple SD Gothic Neo
- Arial Black
- Avenir Next
- Katari
- YuMincho +36p Kana

## مقدار

یک رشته.

## مثال‌ها

قطعه‌کد زیر همهٔ فونت‌های موجود را پرس‌وجو کرده و فراداده‌های آن‌ها را در لاگ ثبت می‌کند. این کار برای نمونه می‌تواند برای پر کردن یک کنترل انتخاب فونت به کار رود.

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

## جستارهای وابسته

- [استفاده از تایپوگرافی پیشرفته با فونت‌های محلی](https://developer.chrome.com/docs/capabilities/web-apis/local-fonts)
- {{cssxref("@font-face")}}