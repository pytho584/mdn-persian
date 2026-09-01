---
title: "HTMLLinkElement: crossOrigin property"
---

---
title: "HTMLLinkElement: crossOrigin property"
short-title: crossOrigin
slug: Web/API/HTMLLinkElement/crossOrigin
page-type: web-api-instance-property
browser-compat: api.HTMLLinkElement.crossOrigin
---

{{APIRef("HTML DOM")}}

ویژگی **`crossOrigin`** در رابط {{domxref("HTMLLinkElement")}} تنظیمات اشتراک منابع بین‌دامنه‌ای ({{Glossary("CORS")}}) را هنگام بازیابی منبع مشخص می‌کند.

## مقدار

یک رشته شامل یک کلیدواژه که حالت CORS مورد استفاده هنگام واکشی منبع را مشخص می‌کند. مقادیر ممکن عبارت‌اند از:

- `anonymous` یا رشته خالی (`""`)
  - : درخواست‌هایی که توسط {{domxref("HTMLLinkElement")}} ارسال می‌شوند از حالت `cors` {{domxref("Request.mode", "mode", "", "nocode")}} و حالت `same-origin` {{domxref("Request.credentials", "credentials", "", "nocode")}} استفاده خواهند کرد. این یعنی CORS فعال است و اعتبارنامه‌ها تنها _اگر_ منبع از همان مبدأی (origin) که سند از آن بارگذاری شده واکشی شود، ارسال می‌شوند.
- `use-credentials`
  - : درخواست‌های ارسال‌شده توسط {{domxref("HTMLLinkElement")}} از حالت `cors` {{domxref("Request.mode", "mode", "", "nocode")}} و حالت `include` {{domxref("Request.credentials", "credentials", "", "nocode")}} استفاده می‌کنند. تمام درخواست‌های منابع این عنصر، بدون توجه به اینکه واکشی از چه دامنه‌ای انجام شود، از CORS استفاده خواهند کرد.

اگر ویژگی `crossOrigin` با هر مقدار دیگری مشخص شود، همانند این است که مقدار `anonymous` تعیین شده باشد.

اگر ویژگی `crossOrigin` مشخص نشده باشد، منبع بدون CORS واکشی می‌شود (حالت `no-cors` {{domxref("Request.mode", "mode", "", "nocode")}} و حالت `same-origin` {{domxref("Request.credentials", "credentials", "", "nocode")}}).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLImageElement.crossOrigin")}}
- {{domxref("HTMLMediaElement.crossOrigin")}}
- {{domxref("HTMLScriptElement.crossOrigin")}}