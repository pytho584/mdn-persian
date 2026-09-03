---
title: "NavigatorUAData: getHighEntropyValues() method"
short-title: getHighEntropyValues()
slug: Web/API/NavigatorUAData/getHighEntropyValues
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.NavigatorUAData.getHighEntropyValues
---

{{APIRef("User-Agent Client Hints API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

متد **`getHighEntropyValues()`** از رابط {{domxref("NavigatorUAData")}} یک {{jsxref("Promise")}} را برمی‌گرداند که با یک شیء دیکشنری شامل اطلاعات آنتروپی پایین (low-entropy) و اطلاعات آنتروپی بالای (high-entropy) درخواست‌شده درباره مرورگر، resolve می‌شود.

شیء resolve شده به‌صورت پیش‌فرض حاوی [ویژگی‌های «آنتروپی پایین»](/en-US/docs/Web/API/NavigatorUAData#instance_properties) است که روی شیء `NavigatorUAData` در دسترس هستند – این مقادیر آنهایی هستند که احتمال کمی برای اثرانگشت‌گذاری کاربر دارند. همچنین شامل زیرمجموعه‌ای از مقادیر «آنتروپی بالا» است که در پارامتر `hints` درخواست شده‌اند و مجوز آن‌ها صادر شده است. این مقادیر آنهایی هستند که احتمال بیشتری برای اثرانگشت‌گذاری دارند. توجه داشته باشید که معنی اصطلاحات [آنتروپی پایین](/en-US/docs/Web/HTTP/Guides/Client_hints#low_entropy_hints) و [آنتروپی بالا](/en-US/docs/Web/HTTP/Guides/Client_hints#high_entropy_hints) همان است که در مکانیزم [نشانه‌های کاربر-عامل (User-Agent Client Hints)](/en-US/docs/Web/HTTP/Guides/Client_hints) HTTP تعریف شده است.

> [!NOTE]
> استفاده از متد `getHighEntropyValues()` برای بازیابی داده‌های کاربر-عامل با آنتروپی بالا می‌تواند از طریق {{HTTPHeader('Permissions-Policy/ch-ua-high-entropy-values', 'ch-ua-high-entropy-values')}} {{HTTPHeader('Permissions-Policy')}} کنترل شود. اگر مجوز داده نشود، متد فقط داده‌های آنتروپی پایین `brands`، `mobile` و `platform` را برمی‌گرداند.

## Syntax

```js-nolint
getHighEntropyValues(hints)
```

### پارامترها

- `hints`
  - : آرایه‌ای حاوی نشانه‌های آنتروپی بالا که باید برگردانده شوند. می‌تواند شامل یک یا چند مورد از موارد زیر باشد:
    - `"architecture"`
    - `"bitness"`
    - `"formFactors"`
    - `"fullVersionList"`
    - `"model"`
    - `"platformVersion"`
    - `"uaFullVersion"` {{Deprecated_Inline}}
    - `"wow64"`

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به یک شیء حاوی برخی یا همه مقادیر زیر (بر اساس نشانه‌های درخواست‌شده و اعطاشده) resolve می‌شود:

- `brands`
  - : آرایه‌ای از اشیاء حاوی `brand` و `version` که مشخص‌کننده نام و نسخه مرورگر است (همان اطلاعاتی که توسط {{domxref("NavigatorUAData.brands")}} ارائه می‌شود). توجه داشته باشید که این اطلاعات می‌تواند در هدر {{HTTPHeader("Sec-CH-UA")}} (یک [نشانه کاربر-عامل با آنتروپی پایین](/en-US/docs/Web/HTTP/Guides/Client_hints#low_entropy_hints)) به سرور ارسال شود.
- `mobile`
  - : اگر کاربر-عامل روی یک دستگاه همراه اجرا شود، `true` برمی‌گرداند (همان اطلاعاتی که توسط {{domxref("NavigatorUAData.mobile")}} ارائه می‌شود). توجه داشته باشید که این اطلاعات می‌تواند در هدر {{HTTPHeader("Sec-CH-UA-Mobile")}} (یک [نشانه کاربر-عامل با آنتروپی پایین](/en-US/docs/Web/HTTP/Guides/Client_hints#low_entropy_hints)) به سرور ارسال شود.
- `platform`
  - : رشته‌ای که پلتفرم اجرای کاربر-عامل را توصیف می‌کند، مانند `"Windows"` (همان اطلاعاتی که توسط {{domxref("NavigatorUAData.platform")}} ارائه می‌شود). توجه داشته باشید که این اطلاعات می‌تواند در هدر {{HTTPHeader("Sec-CH-UA-Platform")}} (یک [نشانه کاربر-عامل با آنتروپی پایین](/en-US/docs/Web/HTTP/Guides/Client_hints#low_entropy_hints)) به سرور ارسال شود.
- `architecture`
  - : رشته‌ای حاوی معماری پلتفرم. به‌عنوان مثال، `"x86"`. توجه داشته باشید که این اطلاعات می‌تواند در هدر {{HTTPHeader("Sec-CH-UA-Arch")}} پس از درخواست صریح سرور در هدر {{HTTPHeader("Accept-CH")}} به سرور ارسال شود.
- `bitness`
  - : رشته‌ای حاوی بیت‌نِس (bitness) معماری. به‌عنوان مثال، `"32"` یا `"64"`. توجه داشته باشید که این اطلاعات می‌تواند در هدر {{HTTPHeader("Sec-CH-UA-Bitness")}} در صورت درخواست صریح سرور در هدر {{HTTPHeader("Accept-CH")}} به سرور ارسال شود.
- `formFactors`
  - : آرایه‌ای از رشته‌ها حاوی فاکتورهای فرم (form-factors) یک دستگاه. به‌عنوان مثال، `["Tablet", "XR"]`. توجه داشته باشید که این اطلاعات می‌تواند در هدر {{HTTPHeader("Sec-CH-UA-Form-Factors")}} در صورت درخواست صریح سرور در هدر {{HTTPHeader("Accept-CH")}} به سرور ارسال شود.
- `fullVersionList`
  - : آرایه‌ای از اشیاء با ویژگی‌های `"brand"` و `"version"` که به ترتیب نام و نسخه کامل مرورگر را نشان می‌دهند. به‌عنوان مثال، `{"brand": "Google Chrome", "version": "103.0.5060.134"}, {"brand": "Chromium", "version": "103.0.5060.134"}`. لطفاً توجه داشته باشید که یک شیء ممکن است عمداً اطلاعات نامعتبر داشته باشد تا از وابستگی سایت‌ها به یک لیست ثابت از مرورگرها جلوگیری کند. توجه داشته باشید که این اطلاعات می‌تواند در هدر {{HTTPHeader("Sec-CH-UA-Full-Version-List")}} در صورت درخواست صریح سرور در هدر {{HTTPHeader("Accept-CH")}} به سرور ارسال شود.
- `model`
  - : رشته‌ای حاوی مدل دستگاه همراه. به‌عنوان مثال، `"Pixel 2XL"`. اگر دستگاه یک دستگاه همراه نباشد یا مدل دستگاه ناشناخته باشد، `model` برابر `""` خواهد بود. توجه داشته باشید که این اطلاعات می‌تواند در هدر {{HTTPHeader("Sec-CH-UA-Model")}} در صورت درخواست صریح سرور در هدر {{HTTPHeader("Accept-CH")}} به سرور ارسال شود.
- `platformVersion`
  - : رشته‌ای حاوی نسخه پلتفرم. نام خود پلتفرم همیشه به‌عنوان یک نشانه آنتروپی پایین به نام `platform` در دسترس است. به‌عنوان مثال، `"10.0"`. توجه داشته باشید که این اطلاعات می‌تواند در هدر {{HTTPHeader("Sec-CH-UA-Platform-Version")}} در صورت درخواست صریح سرور در هدر {{HTTPHeader("Accept-CH")}} به سرور ارسال شود.
- `uaFullVersion` {{Deprecated_Inline}}
  - : رشته‌ای حاوی نسخه کامل مرورگر. به‌عنوان مثال، `"103.0.5060.134"`. این ویژگی منسوخ شده و به جای آن از `fullVersionList` استفاده می‌شود. توجه داشته باشید که این اطلاعات می‌تواند در هدر {{HTTPHeader("Sec-CH-UA-Full-Version")}} در صورت درخواست صریح سرور در هدر {{HTTPHeader("Accept-CH")}} به سرور ارسال شود.
- `wow64`
  - : یک مقدار بولی که نشان می‌دهد آیا باینری کاربر-عامل در حالت ۳۲ بیتی روی ویندوز ۶۴ بیتی اجرا می‌شود یا خیر. توجه داشته باشید که این اطلاعات می‌تواند در هدر {{HTTPHeader("Sec-CH-UA-WoW64")}} در صورت درخواست صریح سرور در هدر {{HTTPHeader("Accept-CH")}} به سرور ارسال شود.

### استثناها

- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر کاربر-عامل تشخیص دهد که یک یا چند نشانه از `hints` درخواست‌شده نباید برگردانده شوند، پرتاب می‌شود.

## مثال‌ها

در مثال زیر، تعدادی نشانه با استفاده از متد `getHighEntropyValues()` درخواست می‌شوند. وقتی promise resolve می‌شود، این اطلاعات در کنسول چاپ می‌شوند.

```js
navigator.userAgentData
  .getHighEntropyValues([
    "architecture",
    "model",
    "platformVersion",
    "fullVersionList",
  ])
  .then((values) => console.log(values));
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- این مقادیر از طریق هدرهای درخواست HTTP نیز در دسترس هستند:
  - [نشانه‌های کاربر-عامل با آنتروپی پایین](/en-US/docs/Web/HTTP/Guides/Client_hints#low_entropy_hints) به‌طور خودکار ارسال می‌شوند:
    - {{HTTPHeader("Sec-CH-UA")}}
    - {{HTTPHeader("Sec-CH-UA-Mobile")}}
    - {{HTTPHeader("Sec-CH-UA-Platform")}}
  - سرورها می‌توانند با استفاده از هدر {{HTTPHeader("Accept-CH")}} درخواست دریافت نشانه‌های کاربر-عامل با آنتروپی بالا در درخواست‌های بعدی را بدهند:
    - {{HTTPHeader("Sec-CH-UA-Arch")}}
    - {{HTTPHeader("Sec-CH-UA-Bitness")}}
    - {{HTTPHeader("Sec-CH-UA-Full-Version")}}
    - {{HTTPHeader("Sec-CH-UA-Model")}}
    - {{HTTPHeader("Sec-CH-UA-Platform-Version")}}