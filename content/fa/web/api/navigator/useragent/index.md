---
title: "Navigator: userAgent property"
short-title: userAgent
slug: Web/API/Navigator/userAgent
page-type: web-api-instance-property
browser-compat: api.Navigator.userAgent
---

{{ApiRef("HTML DOM")}}

خاصیت فقط خواندنی **`Navigator.userAgent`** از رابط {{domxref("Navigator")}}، رشته `User-Agent` (UA) مربوط به مرورگر فعلی را بازمی‌گرداند.

## مقدار

یک رشته.

## توضیحات

خاصیت `userAgent` رشته UA مرورگر فعلی را ارائه می‌دهد. رشته UA بر اساس یک ساختار رسمی ساخته شده است که می‌توان آن را به چند بخش اطلاعاتی تجزیه کرد.

مرورگر همچنین رشته UA را از طریق هدر HTTP {{HTTPHeader("User-Agent")}} ارائه می‌دهد. بخش‌هایی از این اطلاعات در هدرهای {{Glossary("HTTP")}} مانند [راهنمای‌های مشتری User-Agent](/en-US/docs/Web/HTTP/Guides/Client_hints) و سایر ویژگی‌های API مرتبط مانند {{domxref("Navigator.appVersion")}} و {{domxref("Navigator.platform")}} نیز در دسترس هستند.

از نظر تئوری، این اطلاعات برای تشخیص مرورگر و ارائه کد برای رفع اشکالات خاص مرورگر یا عدم پشتیبانی از ویژگی‌ها مفید است. با این حال، این کار **غیرقابل اعتماد** است و **توصیه نمی‌شود** به دلایلی که در [کاهش User-Agent](/en-US/docs/Web/HTTP/Guides/User-agent_reduction) و [تشخیص مرورگر با استفاده از user agent](/en-US/docs/Web/HTTP/Guides/Browser_detection_using_the_user_agent) ذکر شده است.

[تشخیص ویژگی](/en-US/docs/Learn_web_development/Extensions/Testing/Feature_detection) یک استراتژی بسیار قابل اطمینان‌تر است.

## مثال‌ها

```js
console.log(navigator.userAgent);
// On Chrome on macOS, logs something like "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/143.0.0.0 Safari/537.36" (reduced UA string)

// On Firefox on Windows, logs something like "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:124.0) Gecko/20100101 Firefox/124.0"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- هدر HTTP {{httpheader("User-Agent")}}