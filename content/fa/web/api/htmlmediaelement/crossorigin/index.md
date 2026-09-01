---
title: "HTMLMediaElement: crossOrigin property"
short-title: crossOrigin
slug: Web/API/HTMLMediaElement/crossOrigin
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.crossOrigin
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLMediaElement.crossOrigin`** تنظیمات CORS برای این عنصر رسانهای است. برای جزئیات بیشتر به [ویژگیهای تنظیمات CORS](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin) مراجعه کنید.

## مقدار

رشتهای از یک کلیدواژه که حالت CORS را هنگام دریافت منبع مشخص میکند. مقادیر ممکن عبارتند از:

- `anonymous` یا رشتهٔ خالی (`""`)
  - : درخواستهای ارسالی توسط {{domxref("HTMLMediaElement")}} از حالت `cors` {{domxref("Request.mode", "mode", "", "nocode")}} و حالت `same-origin` {{domxref("Request.credentials", "credentials", "", "nocode")}} استفاده خواهند کرد. این بدان معناست که CORS فعال است و اعتبارنامهها _فقط در صورتی_ ارسال میشوند که منبع از همان مبدأیی که سند از آن بارگذاری شده دریافت شود.
- `use-credentials`
  - : درخواستهای ارسالی توسط {{domxref("HTMLMediaElement")}} از حالت `cors` {{domxref("Request.mode", "mode", "", "nocode")}} و حالت `include` {{domxref("Request.credentials", "credentials", "", "nocode")}} استفاده خواهند کرد. تمام درخواستهای منابع توسط عنصر، بدون توجه به دامنهای که دریافت از آن انجام میشود، از CORS استفاده خواهند کرد.

اگر ویژگی `crossOrigin` با هر مقدار دیگری مشخص شود، همانند مشخص کردن `anonymous` خواهد بود.

اگر ویژگی `crossOrigin` مشخص نشده باشد، منبع بدون CORS دریافت میشود (حالت `no-cors` {{domxref("Request.mode", "mode", "", "nocode")}} و حالت `same-origin` {{domxref("Request.credentials", "credentials", "", "nocode")}}).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLImageElement.crossOrigin")}}
- {{domxref("HTMLLinkElement.crossOrigin")}}
- {{domxref("HTMLScriptElement.crossOrigin")}}