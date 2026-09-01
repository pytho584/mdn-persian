---
title: "HTMLScriptElement: crossOrigin property"
short-title: crossOrigin
slug: Web/API/HTMLScriptElement/crossOrigin
page-type: web-api-instance-property
browser-compat: api.HTMLScriptElement.crossOrigin
---

{{APIRef("HTML DOM")}}

ویژگی **`crossOrigin`** در رابط {{domxref("HTMLScriptElement")}} بازتابی از تنظیمات {{Glossary("CORS", "اشتراک منابع بین‌دامنه (CORS)")}} برای عنصر اسکریپت است. برای اسکریپت‌های کلاسیک که از [ریشه‌های](/en-US/docs/Glossary/Origin) دیگر می‌آیند، این ویژگی تعیین می‌کند که آیا اطلاعات کامل خطا در معرض دید قرار می‌گیرد یا خیر. برای اسکریپت‌های ماژولار، این ویژگی هم بر خود اسکریپت و هم بر هر اسکریپتی که ایمپورت می‌کند تأثیر می‌گذارد. برای جزئیات بیشتر به [ویژگی‌های تنظیمات CORS](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin) مراجعه کنید.

## مقدار

یک رشته شامل یک کلیدواژه که حالت CORS مورد استفاده هنگام دریافت منبع را مشخص می‌کند. مقادیر ممکن عبارتند از:

- `anonymous` یا یک رشته خالی (`""`)
  - : درخواست‌هایی که توسط {{domxref("HTMLScriptElement")}} ارسال می‌شوند از حالت `cors` برای {{domxref("Request.mode", "mode", "", "nocode")}} و حالت `same-origin` برای {{domxref("Request.credentials", "credentials", "", "nocode")}} استفاده می‌کنند. این بدان معناست که CORS فعال است و اعتبارنامه‌ها _فقط در صورتی_ ارسال می‌شوند که منبع از همان ریشه‌ای دریافت شود که سند از آن بارگذاری شده است.
- `use-credentials`
  - : درخواست‌هایی که توسط {{domxref("HTMLScriptElement")}} ارسال می‌شوند از حالت `cors` برای {{domxref("Request.mode", "mode", "", "nocode")}} و حالت `include` برای {{domxref("Request.credentials", "credentials", "", "nocode")}} استفاده می‌کنند. همه درخواست‌های منابع توسط این عنصر از CORS استفاده می‌کنند، صرف‌نظر از اینکه دریافت از کدام دامنه انجام می‌شود.

اگر ویژگی `crossOrigin` با هر مقدار دیگری مشخص شود، همانند این است که مقدار `anonymous` تعیین شده باشد.

اگر ویژگی `crossOrigin` مشخص نشود، منبع بدون CORS دریافت می‌شود (حالت `no-cors` برای {{domxref("Request.mode", "mode", "", "nocode")}} و حالت `same-origin` برای {{domxref("Request.credentials", "credentials", "", "nocode")}}).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLImageElement.crossOrigin")}}
- {{domxref("HTMLLinkElement.crossOrigin")}}
- {{domxref("HTMLMediaElement.crossOrigin")}}