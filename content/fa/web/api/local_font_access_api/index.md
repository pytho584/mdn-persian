---
title: Local Font Access API
slug: Web/API/Local_Font_Access_API
page-type: web-api-overview
status:
  - experimental
browser-compat: api.Window.queryLocalFonts
spec-urls: https://wicg.github.io/local-font-access/
---

{{SeeCompatTable}}{{DefaultAPISidebar("Local Font Access API")}}

**API دسترسی به فونت‌های محلی (Local Font Access API)** مکانیزمی برای دسترسی به داده‌های فونت‌های نصب‌شده روی سیستم کاربر فراهم می‌کند — این داده‌ها شامل جزئیات سطح بالا مانند نام‌ها، سبک‌ها و خانواده‌ها، و همچنین بایت‌های خام فایل‌های فونت زیرین است.

## مفاهیم و کاربرد

[فونت‌های وب (Web fonts)](/en-US/docs/Learn_web_development/Core/Text_styling/Web_fonts) در امکان‌پذیر کردن تایپوگرافی در وب انقلابی ایجاد کردند، زیرا به طراحان وب اجازه می‌دهند تا فونت‌های سفارشی را برای استفاده در یک سند وب ارائه دهند. یک فونت وب با استفاده از قانون at-rule {{cssxref("@font-face")}} مشخص می‌شود و می‌تواند از یک URL که در تابع `url()` ارائه شده است بارگیری شود.

`@font-face` دارای چندین ویژگی مفید دیگر است. به طور خاص، می‌توانید نام کامل یا نام پست‌اسکریپت (Postscript) فونت را در داخل تابع `local()` مشخص کنید تا به مرورگر بگویید اگر کاربر آن فونت را روی رایانه خود نصب کرده است، از یک نسخه محلی استفاده کند. این کار بدون مشکل نیست — `local()` به عنوان یک [بردار اثر انگشت (fingerprinting vector)](https://developer.chrome.com/docs/capabilities/web-apis/local-fonts#local_fonts_as_fingerprint_vector) بدنام شده است.

علاوه بر این، ابزارهای طراحی سطح بالا (high-end design tools) به طور تاریخی به دلیل چالش‌های موجود در شمارش دقیق فونت‌ها و دسترسی به داده‌های سطح پایین فونت (به عنوان مثال برای اعمال فیلترها و تبدیل‌ها) به سختی در وب ارائه می‌شدند. برنامه‌های فعلی اغلب به راه‌حل‌های جایگزین مانند درخواست از کاربران برای آپلود فونت‌های خود در سروری که در آنجا پردازش می‌شوند تا داده‌های بایت خام را دریافت کنند، یا نصب یک برنامه محلی جداگانه برای ارائه قابلیت‌های اضافی، متکی هستند.

API دسترسی به فونت‌های محلی برای حل این مشکلات ایجاد شده است.

متود {{domxref("Window.queryLocalFonts()")}} دسترسی به آرایه‌ای از فونت‌های نصب‌شده محلی را فراهم می‌کند که هر کدام توسط یک نمونه از شی {{domxref("FontData")}} نمایش داده می‌شوند. {{domxref("FontData")}} دارای چندین ویژگی است که به نام‌ها، سبک‌ها و خانواده‌ها دسترسی می‌دهد، و همچنین یک متود {{domxref("FontData.blob", "blob()")}} دارد که دسترسی به یک {{domxref("Blob")}} حاوی بایت‌های خام فایل فونت زیرین را فراهم می‌کند.

از نظر حریم خصوصی و امنیت:

- API دسترسی به فونت‌های محلی به گونه‌ای طراحی شده است که تنها به داده‌های مورد نیاز برای حل مشکلات فوق دسترسی دهد. همچنین هیچ الزامی برای مرورگرها وجود ندارد که فهرست کامل فونت‌های محلی موجود را ارائه دهند، یا داده‌ها را به همان ترتیبی که روی دیسک ظاهر می‌شوند، ارائه کنند.
- هنگامی که {{domxref("Window.queryLocalFonts()")}} فراخوانی می‌شود، از کاربر برای دسترسی به فونت‌های محلی خود اجازه خواسته می‌شود. وضعیت این مجوز را می‌توان از طریق [API مجوزها (Permissions API)](/en-US/docs/Web/API/Permissions_API) (مجوز `local-fonts`) پرس‌وجو کرد.
- می‌توانید دسترسی به این ویژگی را با استفاده از یک {{httpheader("Permissions-Policy/local-fonts", "local-fonts")}} [سیاست مجوزها (Permissions Policy)](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) کنترل کنید.

## رابط‌ها

- {{domxref("FontData")}}
  - : یک وجه فونت محلی واحد را نمایش می‌دهد.

## افزونه‌هایی به سایر رابط‌ها

- {{domxref("Window.queryLocalFonts()")}}
  - : یک {{jsxref("Promise")}} را برمی‌گرداند که با آرایه‌ای از اشیاء {{domxref("FontData")}}، که نمایانگر وجه‌های فونت موجود به صورت محلی هستند، تکمیل می‌شود.

## مثال‌ها

برای یک نمایش زنده و عملی، [دموی API دسترسی به فونت‌های محلی](https://mdn.github.io/dom-examples/local-font-access/) ما را ببینید.

### تشخیص ویژگی

```js
if ("queryLocalFonts" in window) {
  // The Local Font Access API is supported
}
```

### شمارش فونت‌ها

قطعه کد زیر تمام فونت‌های موجود را پرس‌وجو می‌کند و فراداده (metadata) را ثبت می‌کند. این می‌تواند برای مثال برای پر کردن یک کنترل انتخاب فونت (font-picker) استفاده شود.

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

متود {{domxref("FontData.blob", "blob()")}} دسترسی به داده‌های سطح پایین [SFNT](https://en.wikipedia.org/wiki/SFNT) را فراهم می‌کند — این یک فرمت فایل فونت است که می‌تواند شامل سایر فرمت‌های فونت مانند PostScript، TrueType، OpenType یا فرمت فونت باز وب (WOFF) باشد.

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

## مشخصات‌نامه‌ها

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [استفاده از تایپوگرافی پیشرفته با فونت‌های محلی](https://developer.chrome.com/docs/capabilities/web-apis/local-fonts)
- {{cssxref("@font-face")}}
- دستورالعمل {{httpheader("Permissions-Policy/local-fonts", "local-fonts")}} [سیاست مجوزها (Permissions Policy)](/en-US/docs/Web/HTTP/Guides/Permissions_Policy)