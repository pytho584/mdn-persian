---
title: "Generating attribution reports"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Attribution_Reporting_API/Generating_reports"
translated_by: "n8n + AI"
---

---
title: Generating attribution reports
slug: Web/API/Attribution_Reporting_API/Generating_reports
page-type: guide
status:
  - deprecated
---

{{DefaultAPISidebar("Attribution Reporting API")}}{{deprecated_header}}

این مقاله توضیح می‌دهد که چگونه گزارش‌های [API گزارش‌دهی انتساب](/en-US/docs/Web/API/Attribution_Reporting_API) — چه گزارش‌های انتساب و چه گزارش‌های اشکال‌زدایی — تولید می‌شوند و چگونه می‌توانید گزارش‌های تولید شده را کنترل کنید. این شامل مدیریت نویز، اولویت‌بندی گزارش‌ها، فیلتر کردن گزارش‌ها و تولید گزارش‌های اشکال‌زدایی است.

## فرآیند پایه

هنگامی که یک تطابق بین یک محرک و یک منبع رخ می‌دهد، مرورگر یک گزارش تولید کرده و آن را از طریق یک درخواست [`POST`](/en-US/docs/Web/HTTP/Reference/Methods/POST) بدون اعتبارنامه به یک نقطه پایانی خاص در مبدأ گزارش‌دهی ارسال می‌کند:

- برای گزارش‌های سطح رویداد، این نقطه پایانی `<reporting-origin>/.well-known/attribution-reporting/report-event-attribution` است.
- برای گزارش‌های خلاصه، این نقطه پایانی `<reporting-origin>/.well-known/attribution-reporting/report-aggregate-attribution` است.

`<reporting-origin>` با مبدأی که منبع و محرک را ثبت کرده است، هم‌ریشه خواهد بود.

داده‌های گزارش در یک ساختار JSON قرار دارند.

## گزارش‌های سطح رویداد

گزارش‌های سطح رویداد در پایان **پنجره گزارش** مربوطه خود تولید و زمان‌بندی ارسال می‌شوند. طول پنجره گزارش توسط مقادیر تعیین شده در فیلد [`"event_report_window"`](/en-US/docs/Web/HTTP/Reference/Headers/Attribution-Reporting-Register-Source#event_report_window) یا [`"event_report_windows"`](/en-US/docs/Web/HTTP/Reference/Headers/Attribution-Reporting-Register-Source#event_report_windows) که در هدر {{httpheader("Attribution-Reporting-Register-Source")}} منبع تنظیم شده است، تعیین می‌شود.

اگر هیچ‌یک از این فیلدها مشخص نشده باشند، پنجره گزارش به موارد پیش‌فرض زیر بازمی‌گردد:

- برای [منابع مبتنی بر رویداد](/en-US/docs/Web/API/Attribution_Reporting_API/Registering_sources#event-based_attribution_sources)، پنجره گزارش پیش‌فرض در زمان انقضای منبع به پایان می‌رسد، که در فیلد `"expiry"` هدر `Attribution-Reporting-Register-Source` تنظیم شده است. در صورت عدم تنظیم صریح، این مقدار به طور پیش‌فرض ۳۰ روز پس از ثبت است.
- برای [منابع مبتنی بر پیمایش](/en-US/docs/Web/API/Attribution_Reporting_API/Registering_sources#navigation-based_attribution_sources)، پنجره‌های گزارش پیش‌فرض ۲ روز، ۷ روز و `"expiry"` منبع هستند.

برای جزئیات بیشتر به [پنجره‌های گزارش سفارشی](https://privacysandbox.google.com/private-advertising/attribution-reporting/custom-report-windows) مراجعه کنید.

هنگامی که یک گزارش سطح رویداد در نقطه پایانی مناسب دریافت شد، نحوه پردازش، ذخیره و نمایش داده‌ها کاملاً به عهده توسعه‌دهنده است. یک گزارش سطح رویداد معمولی ممکن است به صورت زیر باشد:

```json
{
  "attribution_destination": "https://advertiser.example",
  "source_event_id": "412444888111012",
  "trigger_data": "4",
  "report_id": "123e4567-e89b-12d3-a456-426614174000",
  "source_type": "navigation",
  "randomized_trigger_rate": 0.34,
  "scheduled_report_time": "1692255696",
  "source_debug_key": 647775351539539,
  "trigger_debug_key": 647776891539539
}
```

ویژگی‌ها به شرح زیر هستند:

- `"attribution_destination"`
  - : یک رشته، یا یک آرایه از ۲ تا ۳ رشته، بسته به اینکه منبع با چندین مقصد ثبت شده باشد یا خیر. این رشته‌ها نشان‌دهنده سایت(های) انتساب [`"destination"`](/en-US/docs/Web/HTTP/Reference/Headers/Attribution-Reporting-Register-Source#destination) هستند که در ثبت منبع از طریق هدر پاسخ {{httpheader("Attribution-Reporting-Register-Source")}} مرتبط تنظیم شده‌اند.
- `"source_event_id"`
  - : یک رشته نشان‌دهنده شناسه منبع انتساب. این مقدار برابر با [`"source_event_id"`](/en-US/docs/Web/HTTP/Reference/Headers/Attribution-Reporting-Register-Source#source_event_id) تنظیم شده در ثبت منبع (از طریق هدر پاسخ {{httpheader("Attribution-Reporting-Register-Source")}} مرتبط) است.
- `"trigger_data"`
  - : یک رشته نشان‌دهنده داده‌های حاصل از محرک انتساب، که در ثبت محرک (مقدار [`"trigger_data"`](/en-US/docs/Web/HTTP/Reference/Headers/Attribution-Reporting-Register-Trigger#trigger_data) تنظیم شده از طریق هدر پاسخ {{httpheader("Attribution-Reporting-Register-Trigger")}} مرتبط) تنظیم شده است.
- `"report_id"`
  - : یک رشته نشان‌دهنده یک [شناسه یکتای جهانی (UUID)](/en-US/docs/Glossary/UUID) برای این گزارش که می‌تواند برای جلوگیری از شمارش تکراری استفاده شود.
- `"source_type"`
  - : یک رشته برابر با `"navigation"` یا `"event"` که به ترتیب نشان می‌دهد منبع انتساب مرتبط [مبتنی بر پیمایش](/en-US/docs/Web/API/Attribution_Reporting_API/Registering_sources#navigation-based_attribution_sources) است یا [مبتنی بر رویداد](/en-US/docs/Web/API/Attribution_Reporting_API/Registering_sources#event-based_attribution_sources).
- `"randomized_trigger_rate"`
  - : یک عدد تصادفی بین ۰ و ۱ که نشان می‌دهد چند وقت یکبار [نویز](#adding_noise_to_reports) برای این پیکربندی منبع خاص اعمال می‌شود.
- `"scheduled_report_time"`
  - : یک رشته نشان‌دهنده تعداد ثانیه‌های سپری شده از مبدأ Unix تا زمانی که مرورگر در ابتدا گزارش را برای ارسال زمان‌بندی کرده است (برای جلوگیری از عدم دقت ناشی از گزارش‌دهی دیرهنگام دستگاه‌های آفلاین).
- `"source_debug_key"` {{optional_inline}}
  - : یک عدد صحیح ۶۴ بیتی بدون علامت نشان‌دهنده کلید اشکال‌زدایی برای منبع انتساب. این مقدار منعکس‌کننده مقدار تنظیم شده در فیلد [`"debug_key"`](/en-US/docs/Web/HTTP/Reference/Headers/Attribution-Reporting-Register-Source#debug_key) هدر {{httpheader("Attribution-Reporting-Register-Source")}} مرتبط است. برای اطلاعات بیشتر به [گزارش‌های اشکال‌زدایی](#debug_reports) مراجعه کنید.
- `"trigger_debug_key"` {{optional_inline}}
  - : یک عدد صحیح ۶۴ بیتی بدون علامت نشان‌دهنده کلید اشکال‌زدایی برای محرک انتساب. این مقدار منعکس‌کننده مقدار تنظیم شده در فیلد `"debug_key"` هدر {{httpheader("Attribution-Reporting-Register-Trigger")}} مرتبط است. برای اطلاعات بیشتر به [گزارش‌های اشکال‌زدایی](#debug_reports) مراجعه کنید.

## گزارش‌های خلاصه

یک گزارش خلاصه از چندین گزارش قابل تجمیع که در نقطه پایانی مناسب دریافت شده‌اند ایجاد می‌شود و سپس برای آماده‌سازی جهت پردازش توسط یک [سرویس تجمیع](https://privacysandbox.google.com/private-advertising/aggregation-service) [دسته‌بندی](https://privacysandbox.google.com/private-advertising/attribution-reporting/summary-reports-intro#batching) می‌شود. هنگامی که این اتفاق افتاد، نحوه پردازش، ذخیره و نمایش داده‌ها کاملاً به عهده توسعه‌دهنده است.

یک گزارش قابل تجمیع به طور پیش‌فرض پس از تعامل با یک محرک تولید و با تأخیر تصادفی برای کمک به محو کردن زمان‌بندی‌ها و بهبود حریم خصوصی، زمان‌بندی ارسال می‌شود. برای یک منبع انتساب ثبت‌شده، رویدادهای منبع انتساب از زمان ثبت تا زمان انقضای منبع ثبت می‌شوند - این به عنوان **پنجره گزارش** نامیده می‌شود.

زمان انقضا توسط مقدار `expiry` تنظیم شده در هدر {{httpheader("Attribution-Reporting-Register-Source")}} مرتبط تعریف می‌شود که در صورت عدم تنظیم صریح، به طور پیش‌فرض ۳۰ روز پس از ثبت است. به خاطر داشته باشید که طول پنجره گزارش می‌تواند با تنظیم یک مقدار `aggregatable_report_window` در هدر `Attribution-Reporting-Register-Source` بیشتر تغییر کند. برای جزئیات بیشتر به [پنجره‌های گزارش سفارشی](https://privacysandbox.google.com/private-advertising/attribution-reporting/custom-report-windows) مراجعه کنید.

> [!NOTE]
> برای محافظت بیشتر از حریم خصوصی کاربر، مقادیر گزارش خلاصه مرتبط با هر منبع انتساب دارای یک مقدار کل محدود هستند — این **بودجه مشارکت** نامیده می‌شود. این مقدار ممکن است در پیاده‌سازی‌های مختلف API متفاوت باشد؛ در کروم این مقدار ۶۵۵۳۶ است. هر تبدیلی که باعث تولید گزارش‌هایی با مقادیر بیش از این حد شود، ثبت نمی‌شود. مطمئن شوید که بودجه را پیگیری کرده و آن را بین معیارهای مختلفی که می‌خواهید اندازه‌گیری کنید، به اشتراک بگذارید.

یک گزارش قابل تجمیع معمولی ممکن است به صورت زیر باشد:

```json
{
  "shared_info": "{\"api\":\"attribution-reporting\",\"attribution_destination\":\"https://advertiser.example\",\"report_id\":\"123e4567-e89b-12d3-a456-426614174000\",\"reporting_origin\":\"https://reporter.example\",\"scheduled_report_time\":\"1692255696\",\"source_registration_time\":\"1692230400\",\"version\":\"3\"}",
  "aggregation_service_payloads": [
    {
      "payload": "[base64-encoded HPKE encrypted data readable only by the aggregation service]",
      "key_id": "[string identifying public key used to encrypt payload]",
      "debug_cleartext_payload": "[base64-encoded unencrypted payload]"
    }
  ],
  "aggregation_coordinator_origin": "https://publickeyservice.aws.privacysandboxservices.com",
  "source_debug_key": 647775351539539,
  "trigger_debug_key": 647776891539539
}
```

ویژگی‌ها به شرح زیر هستند:

- `"shared_info"`
  - : این یک شیء JSON سریال‌سازی شده است که اطلاعاتی را ارائه می‌دهد که سرویس تجمیع از آن برای تهیه یک گزارش خلاصه استفاده خواهد کرد. این داده‌ها برای جلوگیری از دستکاری با استفاده از [AEAD](https://en.wikipedia.org/wiki/Authenticated_encryption) [رمزگذاری](/en-US/docs/Glossary/Encryption) شده‌اند. ویژگی‌های زیر در رشته سریال‌سازی شده نشان داده شده‌اند:
    - `"api"`
      - : یک مقدار شمارشی نشان‌دهنده API که تولید گزارش را فعال کرده است. در حال حاضر این مقدار همیشه برابر با `"attribution-reporting"` خواهد بود، اما ممکن است در آینده با مقادیر اضافی برای پشتیبانی از APIهای دیگر گسترش یابد.
    - `"attribution_destination"`
      - : یک رشته نشان‌دهنده URL [`"destination"`](/en-US/docs/Web/HTTP/Reference/Headers/Attribution-Reporting-Register-Source#destination) انتساب تنظیم شده در ثبت منبع (از طریق هدر پاسخ {{httpheader("Attribution-Reporting-Register-Source")}} مرتبط).
    - `"report_id"`
      - : یک رشته نشان‌دهنده یک [شناسه یکتای جهانی (UUID)](/en-US/docs/Glossary/UUID) برای این گزارش که می‌تواند برای جلوگیری از شمارش تکراری استفاده شود.
    - `"reporting_origin"`
      - : مبدأی که تولید گزارش را فعال کرده است.
    - `"scheduled_report_time"`
      - : یک رشته نشان‌دهنده تعداد ثانیه‌های سپری شده از مبدأ Unix تا زمانی که مرورگر در ابتدا گزارش را برای ارسال زمان‌بندی کرده است (برای جلوگیری از عدم دقت ناشی از گزارش‌دهی دیرهنگام دستگاه‌های آفلاین).
    - `"source_registration_time"`
      - : یک رشته نشان‌دهنده تعداد ثانیه‌های سپری شده از مبدأ Unix تا زمانی که منبع انتساب ثبت شده است، که به پایین‌ترین روز کامل گرد شده است.
    - `"version"`
      - : یک رشته نشان‌دهنده نسخه API مورد استفاده برای تولید گزارش.
- `"aggregation_service_payloads"`
  - : یک آرایه از اشیاء نشان‌دهنده اشیاء بار (payload) حاوی مشارکت‌های هیستوگرام که توسط سرویس تجمیع برای جمع‌آوری داده‌های موجود در گزارش استفاده می‌شود. در حال حاضر، تنها یک بار در هر گزارش پشتیبانی می‌شود که توسط مرورگر پیکربندی شده است. در آینده، ممکن است بارهای متعدد و قابل تنظیم پشتیبانی شوند. هر شیء بار می‌تواند شامل ویژگی‌های زیر باشد:
    - `"payload"`
      - : یک نقشه [CBOR](https://cbor.io/) که از طریق [HPKE](https://datatracker.ietf.org/doc/rfc9180/) رمزگذاری شده و سپس با [base64](/en-US/docs/Glossary/Base64) کدگذاری شده است، با ساختار زیر (با استفاده از JSON فقط برای نمادگذاری):

        ```json
        {
          "operation": "histogram",
          "data": [
            {
              "bucket": "<Encoded as a 16-byte (i.e. 128-bit) big-endian bytestring>",
              "value": "<Encoded as a 4-byte (i.e. 32-bit) big-endian bytestring>"
            }
            // …
          ]
        }
        ```

        `operation` همیشه `"histogram"` است؛ این امکان را فراهم می‌کند که سرویس در آینده از عملیات‌های دیگر پشتیبانی کند.

    - `"key_id"`
      - : یک رشته شناسایی‌کننده کلید عمومی مورد استفاده برای رمزگذاری بار.
    - `"debug_cleartext_payload"` {{optional_inline}}
      - : اطلاعات اشکال‌زدایی اختیاری.

- `"aggregation_coordinator_origin"`
  - : گزینه استقرار برای سرویس تجمیع.
- `"source_debug_key"` {{optional_inline}}
  - : یک عدد صحیح ۶۴ بیتی بدون علامت نشان‌دهنده کلید اشکال‌زدایی برای منبع انتساب. این مقدار منعکس‌کننده مقدار تنظیم شده در فیلد [`"debug_key"`](/en-US/docs/Web/HTTP/Reference/Headers/Attribution-Reporting-Register-Source#debug_key) هدر {{httpheader("Attribution-Reporting-Register-Source")}} مرتبط است. برای اطلاعات بیشتر به [گزارش‌های اشکال‌زدایی](#debug_reports) مراجعه کنید.
- `"trigger_debug_key"` {{optional_inline}}
  - : یک عدد صحیح ۶۴ بیتی بدون علامت نشان‌دهنده کلید اشکال‌زدایی برای محرک انتساب. این مقدار منعکس‌کننده مقدار تنظیم شده در فیلد `"debug_key"` هدر {{httpheader("Attribution-Reporting-Register-Trigger")}} مرتبط است. برای اطلاعات بیشتر به [گزارش‌های اشکال‌زدایی](#debug_reports) مراجعه کنید.

## افزودن نویز به گزارش‌ها

<!--
THIS INFORMATION IS NOT COMPLETE; WE HAVE PARKED IT FOR NOW SO THAT WE CAN GET THIS DOCUMENTATION PUBLISHED, AND WE WILL DO MORE WORK ON ARA NOISE ON A FUTURE DATE, IF/WHEN THE DEMAND IS THERE

In the case of event-level reports, this is done using a randomized response algorithm, which works like so:

1. When an attribution source is stored, the browser generates a list of all possible sets of reports that could originate from the source's configuration (including the set consisting of no reports).
2. In a small percentage of cases, the browser prevents the source from being attributed and instead picks a random member of that list to use as the source's reports. The probability of this happening is based on the size of that list, the browser's implementation-specific privacy parameters, and the source's chosen [`"event_level_epsilon"`](/en-US/docs/Web/HTTP/Reference/Headers/Attribution-Reporting-Register-Source#event_level_epsilon).

Typical settings in the {{httpheader("Attribution-Reporting-Register-Source")}} header might look like so:

```json
{
  ...,
  "trigger_data": [0, 1, 2, 3, 4],
  "trigger_data_matching": "exact",
  ...,
}
```

The source `"trigger_data"` can have a maximum of 32 values. Increasing the number of values and `"event_report_windows"` increases the number of elements in the overall report set.

A matching {{httpheader("Attribution-Reporting-Register-Trigger")}} could contain the following:

```json
{
  ...,
  "event_trigger_data": [
    {
      // The value 4 is contained in the source data, therefore a match is possible
      "trigger_data": "4"
    },
  ],
  ...,
}
```

It is however still possible that a match may not occur, based on the randomized response algorithm described above.
-->

نویز به گزارش‌ها اضافه می‌شود تا خروجی مرتبط با یک منبع خاص مبهم شود و در نتیجه حریم خصوصی کاربر محافظت شود. داده‌های دقیق منبع قابل شناسایی و نسبت دادن به کاربران فردی نیستند، اما الگوهای کلی گرفته شده از داده‌ها همچنان همان معنی را ارائه می‌دهند.

برای اطلاعات در مورد نحوه عملکرد نویز در گزارش‌دهی انتساب، به موارد زیر مراجعه کنید:

- [درک نویز در گزارش‌های خلاصه](https://privacysandbox.google.com/private-advertising/attribution-reporting/understanding-noise).
- [محدودیت‌های داده و نویز](https://github.com/WICG/attribution-reporting-api/blob/main/EVENT.md#data-limits-and-noise)
- [کار با نویز](https://privacysandbox.google.com/private-advertising/attribution-reporting/working-with-noise)

## اولویت‌ها و محدودیت‌های گزارش

به طور پیش‌فرض، همه منابع انتساب دارای اولویت یکسانی هستند و مدل انتساب آخرین لمس است، به این معنی که یک تبدیل به آخرین رویداد منبع منطبق نسبت داده می‌شود. برای هر دو گزارش سطح رویداد و قابل تجمیع، می‌توانید اولویت منبع را با تنظیم یک مقدار جدید برای فیلد `"priority"` در هدر {{httpheader("Attribution-Reporting-Register-Source")}} مرتبط تغییر دهید. مقدار پیش‌فرض `0` است؛ اگر مقدار `"priority"` برابر `1` را روی یک منبع خاص تنظیم کنید، آن منبع ابتدا مطابقت داده می‌شود، قبل از هر منبع با اولویت `0`. منابع با `"priority": "2"` قبل از منابع `"priority": "1"` مطابقت داده می‌شوند و به همین ترتیب.

اولویت‌های محرک انتساب نیز به همین صورت کار می‌کنند؛ همچنین می‌توانید با افزودن یک فیلد `"priority"` به هدر {{httpheader("Attribution-Reporting-Register-Trigger")}} مرتبط، اولویت‌های محرک را تنظیم کنید، اما فقط برای گزارش‌های سطح رویداد.

انواع مختلف منبع دارای محدودیت‌های پیش‌فرض متفاوتی هستند:

- [منابع انتساب مبتنی بر پیمایش](/en-US/docs/Web/API/Attribution_Reporting_API/Registering_sources#navigation-based_attribution_sources) به طور پیش‌فرض دارای محدودیت سه گزارش هستند. به عنوان مثال، فرض کنید یک کاربر روی یک تبلیغ کلیک می‌کند و چهار بار تبدیل می‌کند: از صفحه اصلی سایت تبلیغ‌کننده بازدید می‌کند، سپس از صفحه محصول بازدید می‌کند، در خبرنامه ثبت نام می‌کند و در نهایت خرید می‌کند. گزارش خرید حذف می‌شود، زیرا از چهارمین تبدیل می‌آید.
- [منابع انتساب مبتنی بر رویداد](/en-US/docs/Web/API/Attribution_Reporting_API/Registering_sources#event-based_attribution_sources) به طور پیش‌فرض دارای محدودیت یک گزارش هستند.

> [!NOTE]
> محدودیت گزارش را می‌توان با تنظیم تعداد متفاوتی از `"end_times"` در فیلدهای [`"event_report_windows"`](/en-US/docs/Web/HTTP/Reference/Headers/Attribution-Reporting-Register-Source#event_report_windows) هدر `Attribution-Reporting-Register-Source` مرتبط تنظیم کرد.

هنگامی که یک انتساب برای یک رویداد منبع مشخص فعال می‌شود، اگر حداکثر تعداد انتساب‌ها (سه تا برای کلیک‌ها، یک تا برای تصاویر/اسکریپت‌ها) برای این منبع به دست آمده باشد، مرورگر موارد زیر را انجام می‌دهد:

- اولویت گزارش جدید را با اولویت‌های گزارش‌های زمان‌بندی شده موجود برای همان منبع مقایسه می‌کند.
- گزارش با کمترین اولویت را حذف می‌کند تا گزارش جدید را جایگزین کند. اگر گزارش جدید دارای کمترین اولویت باشد، نادیده گرفته می‌شود و آن را دریافت نخواهید کرد.

اگر هیچ اولویتی تنظیم نشده باشد، مرورگر به رفتار پیش‌فرض خود بازمی‌گردد: هر تبدیلی که بعد از سومین تبدیل برای کلیک‌ها یا اولین تبدیل برای بازدیدها رخ دهد، حذف می‌شود.

## فیلترها

می‌توانید قوانینی را برای تعیین اینکه کدام تبدیل‌ها گزارش تولید می‌کنند، با استفاده از فیلترها تعریف کنید. به عنوان مثال، می‌توانید انتخاب کنید که فقط تبدیل‌های یک دسته محصول خاص شمارش شوند و تبدیل‌های سایر دسته‌ها فیلتر شوند.

برای اعلام فیلترها:

1. در ثبت منبع، یک فیلد `filter_data` به هدر {{httpheader("Attribution-Reporting-Register-Source")}} اضافه کنید که کلیدهای فیلتری را که برای فیلتر کردن تبدیل‌ها در سمت محرک استفاده خواهید کرد، تعریف می‌کند. این فیلدها کاملاً سفارشی هستند. برای مثال، برای مشخص کردن فقط تبدیل‌ها در زیردامنه‌های خاص و برای محصولات خاص:

   ```json
   {
     "filter_data": {
       "conversion_subdomain": [
         "electronics.megastore",
         "electronics2.megastore"
       ],
       "product": ["1234"]
     }
   }
   ```

2. در ثبت محرک، یک فیلد `filters` به هدر {{httpheader("Attribution-Reporting-Register-Trigger")}} اضافه کنید. برای مثال، موارد زیر باعث می‌شود که تعاملات محرک با ثبت منبع فوق مطابقت داشته باشند، زیرا هر دو حاوی فیلد `"conversion_subdomain"` برابر `"electronics.megastore"` هستند. از طرف دیگر، فیلتر `"directory"` زمانی که تطابق تلاش می‌شود نادیده گرفته می‌شود، زیرا در ثبت منبع فوق گنجانده نشده است.

   ```json
   {
     "filters": {
       "conversion_subdomain": ["electronics.megastore"],
       "directory": ["/store/electronics"]
     }
   }
   ```

اگر فیلدهای `"filter_data"` و `"filters"` حاوی زیرفیلدهای منطبق (مانند `"conversion_subdomain"` در مثال بالا) باشند اما هیچ‌یک از مقادیر زیرفیلد مطابقت نداشته باشد، محرک نادیده گرفته می‌شود و در نتیجه هیچ تطابقی رخ نمی‌دهد.

### فیلتر کردن داده‌های محرک

فیلد `event_trigger_data` در هدر {{httpheader("Attribution-Reporting-Register-Trigger")}} می‌تواند برای انجام فیلتر انتخابی برای تنظیم `trigger_data`، `priority` یا `deduplication_key`، بر اساس `filter_data` تعریف شده در هدر {{httpheader("Attribution-Reporting-Register-Source")}} گسترش یابد.

به عنوان مثال:

```json
{
  "event_trigger_data": [
    {
      "trigger_data": "2",
      "filters": { "source_type": ["navigation"] }
    },
    {
      "trigger_data": "1",
      "filters": { "source_type": ["event"] }
    }
  ]
}
```

> [!NOTE]
> `"source_type"` یک فیلد به طور خودکار پر شده است که در `"filter_data"` منبع موجود است.

> [!NOTE]
> `not_filters`، که با نفی فیلتر می‌کند، نیز پشتیبانی می‌شود.

در این زمینه، `filters` می‌تواند یک شیء یا یک آرایه از اشیاء باشد. هنگامی که یک لیست مشخص شده است، فقط یک دیکشنری باید مطابقت داشته باشد تا محرک در نظر گرفته شود.

```json
{
  "event_trigger_data": [
    {
      "trigger_data": "2",
      "filters": [
        {
          "product": ["1234"],
          "conversion_subdomain": ["electronics.megastore"]
        },
        {
          "product": ["4321"],
          "conversion_subdomain": ["electronics4.megastore"]
        }
      ]
    }
  ]
}
```

اگر فیلترها برای هیچ‌یک از محرک‌های رویداد مطابقت نداشته باشند، هیچ گزارش سطح رویدادی ایجاد نخواهد شد. اگر فیلترها برای چندین محرک رویداد مطابقت داشته باشند، اولین محرک رویداد منطبق استفاده می‌شود.

## گزارش‌های اشکال‌زدایی

می‌توانید گزارش‌های اشکال‌زدایی را برای بازگرداندن اطلاعات عیب‌یابی درباره گزارش‌های انتساب خود فعال کنید. این موارد می‌توانند، برای مثال، برای بررسی اینکه تنظیمات شما به درستی کار می‌کنند و درک شکاف‌ها در نتایج اندازه‌گیری بین پیاده‌سازی قدیمی مبتنی بر کوکی و پیاده‌سازی جدید گزارش‌دهی انتساب استفاده شوند. گزارش‌های اشکال‌زدایی بلافاصله ارسال می‌شوند؛ آنها مشمول همان زمان‌بندی گزارش‌های سطح رویداد و خلاصه نیستند.

دو نوع مختلف گزارش اشکال‌زدایی وجود دارد:

- **گزارش‌های اشکال‌زدایی موفقیت** تولید موفق یک گزارش انتساب خاص را ردیابی می‌کنند. گزارش‌های اشکال‌زدایی موفقیت به محض ثبت محرک مربوطه تولید و ارسال می‌شوند.
- **گزارش‌های اشکال‌زدایی مفصل** دید بیشتری به شما در مورد رویدادهای منبع انتساب و رویدادهای محرک انتساب مرتبط با یک گزارش انتساب می‌دهند. آنها به شما امکان می‌دهند اطمینان حاصل کنید که منابع با موفقیت ثبت شده‌اند، یا گزارش‌های از دست رفته را ردیابی کنید و دلیل فقدان آنها را تعیین کنید (به عنوان مثال به دلیل شکست در ثبت رویداد منبع یا محرک یا شکست در ارسال یا تولید گزارش). گزارش‌های اشکال‌زدایی مفصل بلافاصله پس از ثبت منبع یا محرک ارسال می‌شوند.

> [!NOTE]
> برای استفاده از گزارش‌های اشکال‌زدایی، مبدأ گزارش‌دهی باید یک کوکی تنظیم کند. اگر مبدأ پیکربندی شده برای دریافت گزارش‌ها شخص ثالث باشد، این کوکی یک [کوکی شخص ثالث](/en-US/docs/Web/Privacy/Guides/Third-party_cookies) خواهد بود، به این معنی که گزارش‌های اشکال‌زدایی در مرورگرهایی که کوکی‌های شخص ثالث غیرفعال/در دسترس نیستند، در دسترس نخواهند بود.

### استفاده از گزارش‌های اشکال‌زدایی

برای استفاده از گزارش‌های اشکال‌زدایی، باید:

1. کوکی `ar_debug` را در مبدأ گزارش‌دهی خود تنظیم کنید. این باید در طول ثبت منبع و محرک وجود داشته باشد:

   ```http
   Set-Cookie: ar_debug=1; SameSite=None; Secure; Path=/; HttpOnly
   ```

2. فیلد `debug_key` را در هر هدر پاسخ {{httpheader("Attribution-Reporting-Register-Source")}} و {{httpheader("Attribution-Reporting-Register-Trigger")}} مرتبط با گزارش‌های انتسابی که می‌خواهید اطلاعات اشکال‌زدایی را برای آنها افشا کنید، تنظیم کنید. هر مقدار `debug_key` باید یک عدد صحیح ۶۴ بیتی بدون علامت باشد که به عنوان یک رشته پایه ۱۰ قالب‌بندی شده است. هر کلید اشکال‌زدایی را یک شناسه منحصر به فرد کنید — به عنوان مثال می‌توانید هر کدام را به عنوان شناسه کوکی + مهر زمانی منبع/محرک تنظیم کنید (و اگر می‌خواهید این دو را مقایسه کنید، همان مهر زمانی را در سیستم قدیمی مبتنی بر کوکی خود ثبت کنید).

   ```json
   {
     "debug_key": "647775351539539"
   }
   ```

   > [!NOTE]
   > کلید اشکال‌زدایی سمت منبع را با `source_event_id` متفاوت کنید، تا بتوانید گزارش‌های فردی را که دارای شناسه رویداد منبع یکسانی هستند، متمایز کنید.

3. به صورت اختیاری، فیلد `debug_reporting` را روی `true`، در هر دو هدر `Attribution-Reporting-Register-Source` و `Attribution-Reporting-Register-Trigger` تنظیم کنید. اگر این کار را انجام دهید، یک گزارش اشکال‌زدایی مفصل تولید خواهد شد. اگر این کار را انجام ندهید، یک گزارش اشکال‌زدایی موفقیت تولید می‌شود که نوع گزارش انتسابی را که تولید می‌کنید (سطح رویداد یا قابل تجمیع) منعکس می‌کند.

   ```json
   {
     "debug_key": "647775351539539",
     "debug_reporting": true
   }
   ```

4. نقاط پایانی مناسب را برای دریافت گزارش‌های اشکال‌زدایی که می‌خواهید تولید کنید، راه‌اندازی کنید. گزارش‌های اشکال‌زدایی به سه نقطه پایانی جداگانه در مبدأ گزارش‌دهی ارسال می‌شوند:
   - نقطه پایانی برای گزارش‌های اشکال‌زدایی موفقیت سطح رویداد: `<reporting-origin>/.well-known/attribution-reporting/debug/report-event-attribution`
   - نقطه پایانی برای گزارش‌های اشکال‌زدایی موفقیت قابل تجمیع: `<reporting-origin>/.well-known/attribution-reporting/debug/report-aggregate-attribution`
   - نقطه پایانی برای گزارش‌های اشکال‌زدایی مفصل: `<reporting-origin>/.well-known/attribution-reporting/debug/verbose`

گزارش‌های اشکال‌زدایی موفقیت تولید شده با گزارش‌های انتساب یکسان هستند و حاوی کلیدهای اشکال‌زدایی سمت منبع و سمت محرک، به ترتیب در فیلدهای `"source_debug_key"` و `"trigger_debug_key"` هستند.

برای اطلاعات بیشتر و مثال‌ها، به موارد زیر مراجعه کنید:

- [مقدمه‌ای بر گزارش‌های اشکال‌زدایی](https://privacysandbox.google.com/private-advertising/attribution-reporting/attribution-reporting-debugging/) در privacysandbox.google.com (2023)
- [راه‌اندازی گزارش‌های اشکال‌زدایی](https://privacysandbox.google.com/private-advertising/attribution-reporting/attribution-reporting-debugging/part-2/) در privacysandbox.google.com (2023)
- [کتاب آشپزی اشکال‌زدایی](https://privacysandbox.google.com/private-advertising/attribution-reporting/attribution-reporting-debugging/part-3/) در privacysandbox.google.com (2023)