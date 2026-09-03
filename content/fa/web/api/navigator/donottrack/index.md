---
title: "Navigator: doNotTrack property"
short-title: doNotTrack
slug: Web/API/Navigator/doNotTrack
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.Navigator.doNotTrack
---

{{ApiRef("HTML DOM")}}{{Deprecated_header}}{{non-standard_header}}

**`Navigator.doNotTrack`** ویژگی تنظیمات «Do Not Track» کاربر را بازمی‌گرداند؛ تنظیماتی که نشان می‌دهد آیا کاربر از وب‌سایت‌ها و تبلیغ‌کنندگان می‌خواهد که او را ردیابی نکنند.

مقدار این ویژگی، همان مقدار هدر HTTP {{httpheader("DNT")}} را بازتاب می‌دهد؛ یعنی مقادیر `"1"`، `"0"` یا `null`.

کل مشخصات DNT (Do Not Track) متوقف شده است. طراحی این سازوکار معیوب بود، زیرا یک ویژگی مشارکتی بین کاربران، وب‌سایت‌ها و مرورگرها بود. ایده این بود که کاربر به _وب‌سایت_ می‌گوید او را ردیابی نکند و _وب‌سایت_ نیز از این درخواست پیروی می‌کرد. با این حال، هیچ اجرای سخت‌گیرانه‌ای برای این سیاست وجود نداشت، بنابراین وب‌سایت‌های تبلیغاتی هدر DNT را نادیده می‌گرفتند و همچنان کاربران را ردیابی می‌کردند. بنابراین این ویژگی بی‌فایده است. علاوه بر این، مضر نیز هست، زیرا [اثر انگشت (fingerprint)](/en-US/docs/Glossary/Fingerprinting) بیشتری از کاربر را در هدر باقی می‌گذارد، که می‌تواند برای ردیابی بیشتر کاربران مورد استفاده قرار گیرد.

مرورگرها در حال بررسی ویژگی‌های حریم خصوصی دیگری هستند که قابلیت اجرای بیشتری دارند، مانند [کنترل حریم خصوصی سراسری (global privacy control)](/en-US/docs/Web/API/Navigator/globalPrivacyControl)، محدودسازی کوکی‌های شخص ثالث و موارد دیگر.

## مقدار

یک رشته (`string`) یا `null`.

## نمونه‌ها

```js
console.log(navigator.doNotTrack);
// prints "1" if DNT is enabled; "0" if the user opted-in for tracking; otherwise null
```

## مشخصات

بخشی از مشخصات منسوخ‌شده‌ی [Tracking Preference Expression (DNT)](https://w3c.github.io/dnt/drafts/tracking-dnt.html#dom-navigator-donottrack).

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- هدر HTTP {{httpheader("DNT")}}