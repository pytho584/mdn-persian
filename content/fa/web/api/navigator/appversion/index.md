---
title: "Navigator: appVersion property"
short-title: appVersion
slug: Web/API/Navigator/appVersion
page-type: web-api-instance-property
browser-compat: api.Navigator.appVersion
---

{{APIRef("HTML DOM")}}

خاصیت فقط خواندنی **`Navigator.appVersion`** از رابط {{domxref("Navigator")}} رشته‌ای را برمی‌گرداند که اطلاعات نسخه مرورگر را نشان می‌دهد.

## مقدار

یک رشته.

## توضیحات

خاصیت `appVersion` اطلاعاتی را برمی‌گرداند که نسخه مرورگر را نشان می‌دهد.

توجه داشته باشید که اطلاعات برگردانده شده بسته به مرورگر بسیار متفاوت است. در برخی مرورگرها مانند Chrome، این مقدار تقریباً مشابه مقداری است که توسط {{domxref("Navigator.userAgent")}} برگردانده می‌شود، با این تفاوت که پیشوند `Mozilla/` حذف شده است. به عنوان مثال:

```plain
5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/143.0.0.0 Safari/537.36
```

در مرورگرهای دیگر مانند Firefox، این مقدار به یک رشته کوتاه که به پلتفرم/سیستم عامل اشاره دارد، کاهش می‌یابد. به عنوان مثال:

```plain
5.0 (Macintosh)
```

از نظر تئوری، این اطلاعات برای تشخیص مرورگر و ارائه کد برای دور زدن باگ‌های خاص مرورگر یا عدم پشتیبانی از ویژگی‌ها مفید است. با این حال، این روش **غیرقابل اعتماد** است و **توصیه نمی‌شود** به دلایلی که در [کاهش User-Agent](/en-US/docs/Web/HTTP/Guides/User-agent_reduction) و [تشخیص مرورگر با استفاده از user agent](/en-US/docs/Web/HTTP/Guides/Browser_detection_using_the_user_agent) ذکر شده است.

[تشخیص ویژگی](/en-US/docs/Learn_web_development/Extensions/Testing/Feature_detection) یک استراتژی بسیار قابل اعتمادتر است.

## مثال‌ها

```js
console.log(navigator.appVersion);
// در Chrome، چیزی شبیه به این لاگ می‌کند: "5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/143.0.0.0 Safari/537.36" (رشته UA کاهش یافته)

// در Firefox، چیزی شبیه به این لاگ می‌کند: "5.0 (Macintosh)"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Navigator.userAgent")}}
- هدر HTTP {{HTTPHeader("User-agent")}}