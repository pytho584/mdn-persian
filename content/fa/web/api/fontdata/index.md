---
title: FontData
slug: Web/API/FontData
page-type: web-api-interface
status:
  - experimental
browser-compat: api.FontData
---

{{APIRef("Local Font Access API")}}{{SeeCompatTable}}

رابطه‌ی **`FontData`** در {{domxref("Local Font Access API", "Local Font Access API", "", "nocode")}} یک قلم‌رو (font face) محلی را نمایش می‌دهد.

## ویژگی‌های نمونه

- {{domxref('FontData.family')}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : خانواده‌ی قلم‌رو را برمی‌گرداند.
- {{domxref('FontData.fullName')}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : نام کامل قلم‌رو را برمی‌گرداند.
- {{domxref('FontData.postscriptName')}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : نام PostScript قلم‌رو را برمی‌گرداند.
- {{domxref('FontData.style')}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : سبک قلم‌رو را برمی‌گرداند.

## متدهای نمونه

- {{domxref('FontData.blob()')}} {{Experimental_Inline}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که با یک {{domxref("Blob")}} شامل بایت‌های خام فایل قلمِ زیرین تکمیل می‌شود.

## مثال‌ها

برای یک مثال زنده، به [دموی Local Font Access API](https://mdn.github.io/dom-examples/local-font-access/) مراجعه کنید.

### شمارش قلم‌ها

قطعه‌کد زیر همه‌ی قلم‌های موجود را جستجو می‌کند و فراداده‌ها را در کنسول ثبت می‌کند. به‌عنوان مثال می‌توان از آن برای پر کردن یک کنترل انتخاب‌گر قلم استفاده کرد.

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

### دسترسی به داده‌های سطح پایین

متد {{domxref("FontData.blob", "blob()")}} به داده‌های سطح پایین [SFNT](https://en.wikipedia.org/wiki/SFNT) دسترسی می‌دهد — این یک فرمت فایل قلم است که می‌تواند شامل سایر فرمت‌های قلم مانند PostScript، TrueType، OpenType یا Web Open Font Format (WOFF) باشد.

```js
async function computeOutlineFormat() {
  try {
    const availableFonts = await window.queryLocalFonts({
      postscriptNames: ["ComicSansMS"],
    });
    for (const fontData of availableFonts) {
      // `blob()` returns a Blob containing valid and complete
      // SFNT-wrapped font data.
      const sfnt = await fontData.blob();
      // Slice out only the bytes we need: the first 4 bytes are the SFNT
      // version info.
      // Spec: https://learn.microsoft.com/en-us/typography/opentype/spec/otff#organization-of-an-opentype-font
      const sfntVersion = await sfnt.slice(0, 4).text();

      let outlineFormat = "UNKNOWN";
      switch (sfntVersion) {
        case "\x00\x01\x00\x00":
        case "true":
        case "typ1":
          outlineFormat = "truetype";
          break;
        case "OTTO":
          outlineFormat = "cff";
          break;
      }
      console.log("Outline format:", outlineFormat);
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