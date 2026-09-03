---
title: NavigatorUAData
slug: Web/API/NavigatorUAData
page-type: web-api-interface
status:
  - experimental
browser-compat: api.NavigatorUAData
---

{{APIRef("User-Agent Client Hints API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

رابط **`NavigatorUAData`** از {{domxref("User-Agent Client Hints API", "", "", "nocode")}} اطلاعاتی درباره مرورگر و سیستم‌عامل کاربر بازمی‌گرداند.

یک نمونه از این شیء با فراخوانی {{domxref("Navigator.userAgentData")}} یا {{domxref("WorkerNavigator.userAgentData")}} بازگردانده می‌شود. بنابراین، این رابط سازنده‌ای ندارد.

> [!NOTE]
> اصطلاحات _آنتروپی بالا_ و _آنتروپی پایین_ به میزان اطلاعاتی اشاره دارند که این مقادیر درباره مرورگر فاش می‌کنند. مقادیر بازگردانده شده به عنوان ویژگی‌ها، [آنتروپی پایین](/en-US/docs/Web/HTTP/Guides/Client_hints#low_entropy_hints) در نظر گرفته می‌شوند که بعید است کاربر را شناسایی کنند. از {{domxref("NavigatorUAData.getHighEntropyValues()")}} می‌توان برای درخواست مقادیر [آنتروپی بالا](/en-US/docs/Web/HTTP/Guides/Client_hints#high_entropy_hints) اضافی استفاده کرد که ممکن است اطلاعات شناسایی‌کننده بیشتری را فاش کنند. بنابراین این مقادیر از طریق یک {{jsxref("Promise")}} بازیابی می‌شوند تا به مرورگر زمان دهد برای درخواست اجازه کاربر یا انجام بررسی‌های دیگر.

## ویژگی‌های نمونه

- {{domxref("NavigatorUAData.brands")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک آرایه از اطلاعات برند شامل نام و نسخه مرورگر بازمی‌گرداند.
- {{domxref("NavigatorUAData.mobile")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : اگر عامل کاربر روی یک دستگاه تلفن‌همراه در حال اجرا باشد، `true` بازمی‌گرداند.
- {{domxref("NavigatorUAData.platform")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : برند سکویی که عامل کاربر روی آن اجرا می‌شود را بازمی‌گرداند.

## روش‌های نمونه

- {{domxref("NavigatorUAData.getHighEntropyValues()")}} {{Experimental_Inline}}
  - : یک {{jsxref("Promise")}} بازمی‌گرداند که با یک شیء فرهنگ‌واره حاوی اطلاعات آنتروپی پایین و اطلاعات آنتروپی بالای درخواست‌شده درباره مرورگر حل می‌شود.
- {{domxref("NavigatorUAData.toJSON()")}} {{Experimental_Inline}}
  - : یک _سریالایزر_ که یک نمایش JSON از ویژگی‌های _آنتروپی پایین_ شیء `NavigatorUAData` بازمی‌گرداند.

## مثال‌ها

### دریافت برندها

مثال زیر مقدار {{domxref("NavigatorUAData.brands")}} را در کنسول چاپ می‌کند.

```js
console.log(navigator.userAgentData.brands);
```

### بازگرداندن مقادیر آنتروپی بالا

در مثال زیر، تعدادی راهنما با استفاده از روش {{domxref("NavigatorUAData.getHighEntropyValues()")}} درخواست می‌شود. هنگامی که وعده حل می‌شود، این اطلاعات در کنسول چاپ می‌شوند.

```js
navigator.userAgentData
  .getHighEntropyValues([
    "architecture",
    "model",
    "platform",
    "platformVersion",
    "fullVersionList",
  ])
  .then((ua) => {
    console.log(ua);
  });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [بهبود حریم خصوصی کاربر و تجربه توسعه‌دهنده با User-Agent Client Hints](https://developer.chrome.com/docs/privacy-security/user-agent-client-hints)