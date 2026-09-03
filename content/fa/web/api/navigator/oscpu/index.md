---
title: "Navigator: oscpu property"
short-title: oscpu
slug: Web/API/Navigator/oscpu
page-type: web-api-instance-property
browser-compat: api.Navigator.oscpu
---

{{ ApiRef("HTML DOM") }}

ویژگی **`Navigator.oscpu`** رشته‌ای را بازمی‌گرداند که سیستم‌عامل فعلی را شناسایی می‌کند.

## مقدار

رشته‌ای که سیستم‌عاملی را که مرورگر روی آن در حال اجرا است مشخص می‌کند.

| سیستم‌عامل                              | قالب رشته `oscpuInfo`                              |
| --------------------------------------- | -------------------------------------------------- |
| OS/2                                    | `OS/2 Warp x (either 3, 4 or 4.5)`                 |
| Windows CE                              | `WindowsCE x.y`                                    |
| ویندوز ۶۴ بیتی (نسخهٔ ۶۴ بیتی)           | `Windows NT x.y; Win64; x64`                       |
| ویندوز ۶۴ بیتی (نسخهٔ ۳۲ بیتی)           | `Windows NT x.y; WOW64`                            |
| ویندوز ۳۲ بیتی                           | `Windows NT x.y`                                   |
| Mac OS X (نسخهٔ PPC)                    | `PowerPC Mac OS X version x.y`                     |
| Mac OS X (نسخهٔ i386/x64)               | `Intel Mac OS X` یا `macOS version x.y`            |
| لینوکس ۶۴ بیتی (نسخهٔ ۳۲ بیتی)           | خروجی `uname -s` به همراه `i686 on x86_64`         |
| لینوکس                                  | خروجی `uname -sm`                                  |

در این جدول `x.y` به نسخهٔ سیستم‌عامل اشاره دارد.

## مثال‌ها

```js
function osInfo() {
  alert(navigator.oscpu);
}

osInfo(); // alerts "Windows NT 6.0" for example
```

## نکات استفاده

مگر اینکه کد شما امتیاز ویژه داشته باشد (chrome یا حداقل دارای امتیاز UniversalBrowserRead باشد)، ممکن است به جای پلتفرم واقعی، مقدار تنظیم `general.oscpu.override` را دریافت کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}