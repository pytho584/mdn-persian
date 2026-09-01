---
title: "File: lastModifiedDate property"
short-title: lastModifiedDate
slug: Web/API/File/lastModifiedDate
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.File.lastModifiedDate
---

{{APIRef("File API")}}{{AvailableInWorkers}}{{Deprecated_Header}}{{Non-standard_Header}}

خاصیت فقط‌خواندنی **`lastModifiedDate`** در رابط {{domxref("File")}}، تاریخ آخرین تغییر فایل را برمی‌گرداند. فایل‌هایی که تاریخ آخرین تغییر مشخصی ندارند، تاریخ جاری را برمی‌گردانند.

## مقدار

یک شیء {{JSXRef("Global_Objects/Date", "Date")}} که تاریخ و زمان آخرین تغییر فایل را نشان می‌دهد.

## نمونه‌ها

```js
// fileInput is a HTMLInputElement: <input type="file" multiple id="my-file-input">
const fileInput = document.getElementById("my-file-input");

for (const file of fileInput.files) {
  console.log(
    `${file.name} has a last modified date of ${file.lastModifiedDate}`,
  );
}
```

## دقت زمانی کاهش‌یافته

برای محافظت در برابر حملات زمان‌بندی و [اثر انگشت دیجیتال](/en-US/docs/Glossary/Fingerprinting)، ممکن است دقت `someFile.lastModifiedDate` بسته به تنظیمات مرورگر گرد شود. در فایرفاکس، ترجیح `privacy.reduceTimerPrecision` به‌طور پیش‌فرض فعال است و مقدار آن به‌طور پیش‌فرض ۲ میلی‌ثانیه است. همچنین می‌توانید `privacy.resistFingerprinting` را فعال کنید که در این صورت دقت، ۱۰۰ میلی‌ثانیه یا مقدار `privacy.resistFingerprinting.reduceTimerPrecision.microseconds` (هرکدام بزرگ‌تر باشد) خواهد بود.

برای مثال، با دقت زمانی کاهش‌یافته، نتیجه `someFile.lastModifiedDate.getTime()` همیشه مضربی از ۲، یا با فعال بودن `privacy.resistFingerprinting` مضربی از ۱۰۰ (یا `privacy.resistFingerprinting.reduceTimerPrecision.microseconds`) خواهد بود.

```js
// reduced time precision (2ms) in Firefox 60
someFile.lastModifiedDate.getTime();
// Might be:
// 1519211809934
// 1519211810362
// 1519211811670
// …

// reduced time precision with `privacy.resistFingerprinting` enabled
someFile.lastModifiedDate.getTime();
// Might be:
// 1519129853500
// 1519129858900
// 1519129864400
// …
```

## مشخصات

_اگرچه این خاصیت در پیش‌نویس اولیه مشخصات File API وجود داشت، از آن حذف شده و اکنون غیراستاندارد است. به جای آن از {{domxref("File.lastModified")}} استفاده کنید._

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("File")}}