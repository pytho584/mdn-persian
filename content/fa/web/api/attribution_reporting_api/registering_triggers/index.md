---
title: "Registering attribution triggers"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Attribution_Reporting_API/Registering_triggers"
translated_by: "n8n + AI"
---

---
title: Registering attribution triggers
slug: Web/API/Attribution_Reporting_API/Registering_triggers
page-type: guide
status:
  - deprecated
---

{{DefaultAPISidebar("Attribution Reporting API")}}{{deprecated_header}}

این مقاله نحوه ثبت «محرک‌های انتساب» (attribution triggers) را توضیح می‌دهد.

## روش اولیه

پس از اینکه [منابع انتساب را ثبت کردید](/en-US/docs/Web/API/Attribution_Reporting_API/Registering_sources)، باید محرک‌های انتساب را ثبت کنید. این محرک‌ها تعاملاتی در یک سایت هستند که قرار است تبدیل (conversion) در آن‌ها اندازه‌گیری شود (مثلاً کلیک بر دکمه «خرید» در سایت یک تبلیغ‌کننده می‌تواند نشان دهد که یک تبدیل رخ داده است). سپس مرورگر تلاش می‌کند محرک انتساب را با ورودی منبع انتساب ذخیره‌شده در یک پارتیشن محلی خصوصی مطابقت دهد و در صورت یافتن تطابق، [گزارشی تولید کند](/en-US/docs/Web/API/Attribution_Reporting_API/Generating_reports).

انواع مختلف محرک انتساب به روش‌های مختلفی ثبت می‌شوند که در بخش‌های زیر به تفصیل آمده است — به [محرک‌های انتساب مبتنی بر HTML](#html-based_attribution_triggers) و [محرک‌های انتساب مبتنی بر جاوااسکریپت](#javascript-based_attribution_triggers) مراجعه کنید.

با این حال، آنچه در پشت صحنه برای ثبت محرک‌ها، جستجوی تطابق و غیره اتفاق می‌افتد، در همه موارد یکسان است.

1. همه انواع محرک، یک هدر {{httpheader("Attribution-Reporting-Eligible")}} در یک درخواست ارسال می‌کنند که نشان می‌دهد پاسخ واجد شرایط ثبت یک محرک است. به عنوان مثال:

   ```http
   Attribution-Reporting-Eligible: trigger
   ```

2. وقتی سرور درخواستی حاوی هدر `Attribution-Reporting-Eligible` دریافت می‌کند، می‌تواند یک {{httpheader("Attribution-Reporting-Register-Trigger")}} را به همراه پاسخ ارسال کند. مقدار آن یک رشته JSON حاوی داده‌هایی است که می‌توانند در گزارش‌های تولیدشده گنجانده شوند، مانند شناسه محرک، و مقادیر اولویت و حذف تکراری (deduplication).

   مثال زیر برای تطابق با یک منبع انتساب [گزارش سطح رویداد](/en-US/docs/Web/API/Attribution_Reporting_API/Generating_reports#event-level_reports) در نظر گرفته شده است:

   ```js
   res.set(
     "Attribution-Reporting-Register-Trigger",
     JSON.stringify({
       event_trigger_data: [
         {
           trigger_data: "4",
           priority: "1000000000000",
           deduplication_key: "2345698765",
         },
       ],
       debug_key: "1115698977",
     }),
   );
   ```

   فیلدهای مشخص‌شده در اینجا به شرح زیر هستند:

   - `"event_trigger_data"`: شیئی است که داده‌های مربوط به محرک را نشان می‌دهد. این شامل:
     - `"trigger_data"`: داده‌ای مرتبط با محرک که معمولاً برای نشان دادن رویدادهایی مانند «کاربر آیتمی را به سبد خرید اضافه کرد» یا «کاربر در خبرنامه ثبت‌نام کرد» استفاده می‌شود. این مقدار در صورت وجود در گزارش تولیدشده گنجانده خواهد شد، البته بسته به فیلد [`"trigger_data_matching"`](/en-US/docs/Web/HTTP/Reference/Headers/Attribution-Reporting-Register-Source#trigger_data_matching) منبع منتسب ممکن است تغییر کند.
       > [!NOTE]
       > مقادیری که برای نشان دادن هر رویداد استفاده می‌شوند و تعداد عناصر آرایه، کاملاً دلخواه هستند و توسط شما به عنوان توسعه‌دهنده تعریف می‌شوند. آرایه ممکن است حاوی مقادیری باشد که استفاده نشده‌اند، اما مقادیر باید در آرایه حضور داشته باشند تا مرورگر در زمان ثبت محرک، آن‌ها را به منبع نسبت دهد.
     - `"priority"`: رشته‌ای که مقدار اولویت را برای محرک انتساب نشان می‌دهد. برای اطلاعات بیشتر به [Report priorities and limits](/en-US/docs/Web/API/Attribution_Reporting_API/Generating_reports#report_priorities_and_limits) مراجعه کنید.
     - `"deduplication_key"`: رشته‌ای که یک کلید یکتا را نشان می‌دهد و می‌تواند برای جلوگیری از تکرار انتساب‌ها استفاده شود — مثلاً اگر کاربر همان آیتم را چند بار به سبد خرید اضافه کند. برای اطلاعات بیشتر به [Prevent duplication in reports](https://privacysandbox.google.com/private-advertising/attribution-reporting/prevent-duplication) مراجعه کنید.
   - `"debug_key"`: عددی که یک کلید اشکال‌زدایی را نشان می‌دهد. اگر می‌خواهید یک [گزارش اشکال‌زدایی](/en-US/docs/Web/API/Attribution_Reporting_API/Generating_reports#debug_reports) را همراه با گزارش انتساب مربوطه تولید کنید، این مقدار را تنظیم کنید.

   برای توضیح دقیق همه فیلدهای موجود، به {{httpheader("Attribution-Reporting-Register-Trigger")}} مراجعه کنید.

   یک محرک که برای تطابق با منبع انتساب [گزارش خلاصه](/en-US/docs/Web/API/Attribution_Reporting_API/Generating_reports#summary_reports) در نظر گرفته شده است، به فیلدهای زیر نیاز دارد:

   ```js
   res.set(
     "Attribution-Reporting-Register-Trigger",
     JSON.stringify({
       aggregatable_trigger_data: [
         {
           key_piece: "0x400",
           source_keys: ["campaignCounts"],
         },
         {
           key_piece: "0xA80",
           source_keys: ["geoValue", "nonMatchingKeyIdsAreIgnored"],
         },
       ],
       aggregatable_values: {
         campaignCounts: 32768,
         geoValue: 1664,
       },
       debug_key: "1115698977",
     }),
   );
   ```

   فیلدهای این مثال عبارت‌اند از:

   - `"aggregatable_trigger_data"`: آرایه‌ای از اشیاء که هر کدام یک کلید تجمیع را برای اعمال به کلیدهای مختلف منبع تعریف می‌کنند.
   - `"aggregatable_values"`: شیئی حاوی ویژگی‌هایی که مقدار هر نقطه داده تعریف‌شده در `"aggregatable_trigger_data"` را نشان می‌دهند.

   باز هم، برای توضیح دقیق همه فیلدهای موجود به {{httpheader("Attribution-Reporting-Register-Trigger")}} مراجعه کنید.

3. هنگامی که کاربر با محرک انتساب تعامل می‌کند، مرورگر تلاش می‌کند محرک را با هر یک از ورودی‌های منبع انتساب ذخیره‌شده در حافظه پنهان محلی خصوصی مرورگر مطابقت دهد. برای یک تطابق موفق، [`"trigger_data"`](/en-US/docs/Web/HTTP/Reference/Headers/Attribution-Reporting-Register-Trigger#trigger_data) موجود در `Attribution-Reporting-Register-Trigger` باید با یکی از مقادیر ارائه‌شده در [`"trigger_data"`](/en-US/docs/Web/HTTP/Reference/Headers/Attribution-Reporting-Register-Source#trigger_data) موجود در {{httpheader("Attribution-Reporting-Register-Source")}} مطابقت داشته باشد، و سایت (scheme + {{glossary("registrable domain")}}) صفحه سطح بالایی که محرک در آن ثبت می‌شود باید:

   - با سایت حداقل یکی از `destination`های مشخص‌شده در داده‌های مرتبط با منبع مطابقت داشته باشد.
   - با منشأ همان درخواستی که ثبت منبع را مشخص کرده است، هم‌منشأ (same-origin) باشد.

   > [!NOTE]
   > این الزامات محافظت از حریم خصوصی را فراهم می‌کنند، اما همچنین انعطاف‌پذیری نیز دارند — منبع _و_ محرک می‌توانند به طور بالقوه در یک {{htmlelement("iframe")}} جاسازی شوند یا در سایت سطح بالا قرار گیرند.

   عوامل بسیاری دیگری نیز وجود دارند که مانع از نتیجه تطابق موفق می‌شوند؛ برای مثال:

   - فیلترهای محرک با داده‌های فیلتر منبع مطابقت ندارند (برای جزئیات بیشتر به [Filters](/en-US/docs/Web/API/Attribution_Reporting_API/Generating_reports#filters) مراجعه کنید).
   - تنظیم [`"trigger_data_matching"`](/en-US/docs/Web/HTTP/Reference/Headers/Attribution-Reporting-Register-Source#trigger_data_matching) منبع باعث می‌شود هیچ تطابقی رخ ندهد.
   - حداکثر [`"max_event_level_reports"`](/en-US/docs/Web/HTTP/Reference/Headers/Attribution-Reporting-Register-Source#max_event_level_reports) منبع به دست آمده است.
   - یک تطابق موفق به دلیل الگوریتم پاسخ تصادفی مرورگر گزارش نمی‌شود. برای جزئیات بیشتر به [Adding noise to reports](/en-US/docs/Web/API/Attribution_Reporting_API/Generating_reports#adding_noise_to_reports) مراجعه کنید.

4. اگر تطابق موفق پیدا شود، مرورگر بر اساس داده‌های منبع و محرک [گزارشی تولید می‌کند](/en-US/docs/Web/API/Attribution_Reporting_API/Generating_reports) و آن را به یک endpoint گزارش ارسال می‌کند.

> [!NOTE]
> محرک‌های انتساب را نمی‌توان بر روی عناصر {{htmlelement("a")}} یا فراخوانی‌های {{domxref("Window.open()")}} مانند منابع انتساب ثبت کرد.

## محرک‌های انتساب مبتنی بر HTML

محرک‌های انتساب مبتنی بر HTML را می‌توان برای تشخیص تبدیل‌ها در یک صفحه هنگام بارگذاری اولیه آن استفاده کرد — یا به طور دقیق‌تر، زمانی که یک `<img>` یا `<script>` بارگذاری می‌شود. برای مثال، اگر کاربر روی یک پیوند منبع انتساب در صفحه ناشر کلیک کرده باشد و به صفحه تبلیغ‌کننده هدایت شده باشد، می‌توانید محرک انتساب را ثبت کنید و مرورگر را وادار کنید به محض بارگذاری صفحه تبلیغ‌کننده، مطابقت را با ورودی‌های منبع ذخیره‌شده امتحان کند.

شما می‌توانید یک محرک انتساب را با افزودن ویژگی `attributionsrc` به یک عنصر مناسب ثبت کنید. این کار را می‌توان بر روی عناصر {{htmlelement("img")}} و {{htmlelement("script")}} انجام داد.

اگر مقدار ویژگی را خالی بگذارید، درخواست ثبت به سروری که منبع درخواستی روی آن میزبانی می‌شود ارسال خواهد شد. همچنین امکان تعیین یک URL اضافی در داخل مقدار وجود دارد تا درخواست ثبت به آن ارسال شود؛ برای جزئیات بیشتر به [تعیین URL در داخل attributionsrc](#specifying_a_url_inside_attributionsrc) مراجعه کنید.

در اینجا یک مثال از عنصر `<img>` آورده شده است:

```html
<img
  src="https://shop.example/conversion/4rghshdh5"
  alt=""
  width="1"
  height="1"
  attributionsrc />
```

همچنین می‌توانید از طریق ویژگی {{domxref("HTMLImageElement.attributionSrc")}} به این نتیجه برسید:

```js
const imgElem = document.querySelector("img");
imgElem.attributionSrc = "";
```

در این حالت، مرورگر وقتی پاسخ حاوی فایل تصویر را دریافت کند (زمانی که رویداد `load` رخ می‌دهد) تلاش می‌کند محرک را با یک منبع انتساب ذخیره‌شده مطابقت دهد. به خاطر داشته باشید که کاربران ممکن است لزوماً نتوانند تصویر را درک کنند — ممکن است یک پیکسل ردیابی شفاف 1x1 باشد که فقط برای گزارش انتساب استفاده می‌شود.

یک مثال با {{htmlelement("script")}} می‌تواند به شکل زیر باشد:

```html
<script src="advertising-script.js" attributionsrc></script>
```

```js
const scriptElem = document.querySelector("script");
scriptElem.attributionSrc = "";
```

در این حالت، مرورگر وقتی پاسخ حاوی اسکریپت را دریافت کند، تلاش می‌کند محرک را با یک منبع انتساب ذخیره‌شده مطابقت دهد.

## محرک‌های انتساب مبتنی بر جاوااسکریپت

محرک‌های انتساب مبتنی بر جاوااسکریپت نسبت به محرک‌های مبتنی بر HTML انعطاف‌پذیرتر هستند. شما می‌توانید بر اساس یک تعامل سفارشی، مانند کلیک بر روی یک عنصر سفارشی یا ارسال یک فرم، مرورگر را وادار به تلاش برای تطابق با یک منبع ذخیره‌شده کنید.

برای ثبت یک محرک انتساب مبتنی بر اسکریپت، می‌توانید یکی از این دو کار را انجام دهید:

- ارسال یک درخواست {{domxref("Window/fetch", "fetch()")}} که شامل گزینه `attributionReporting` است:

  ```js
  const attributionReporting = {
    eventSourceEligible: false,
    triggerEligible: true,
  };

  // Optionally set keepalive to ensure the request outlives the page
  function triggerMatching() {
    fetch("https://shop.example/endpoint", {
      keepalive: true,
      attributionReporting,
    });
  }

  // Associate the interaction trigger with whatever
  // element and event makes sense for your code
  elem.addEventListener("click", triggerMatching);
  ```

- ارسال یک {{domxref("XMLHttpRequest")}} با فراخوانی {{domxref("XMLHttpRequest.setAttributionReporting", "setAttributionReporting()")}} بر روی شیء درخواست:

  ```js
  const attributionReporting = {
    eventSourceEligible: false,
    triggerEligible: true,
  };

  function triggerMatching() {
    const req = new XMLHttpRequest();
    req.open("GET", "https://shop.example/endpoint");
    // Check availability of setAttributionReporting() before calling
    if (typeof req.setAttributionReporting === "function") {
      req.setAttributionReporting(attributionReporting);
      req.send();
    } else {
      throw new Error("Attribution reporting not available");
      // Include recovery code here as appropriate
    }
  }

  // Associate the interaction trigger with whatever
  // element and event makes sense for your code
  elem.addEventListener("click", triggerMatching);
  ```

در این حالت، مرورگر وقتی پاسخ درخواست fetch را دریافت کند، تلاش می‌کند محرک را با یک منبع انتساب ذخیره‌شده مطابقت دهد.

> [!NOTE]
> درخواست می‌تواند برای هر منبعی باشد. لازم نیست مستقیماً به Attribution Reporting API مرتبط باشد و می‌تواند درخواستی برای JSON، متن ساده، یک بلاب تصویر یا هر چیز دیگری باشد که برای برنامه شما منطقی است.

## تعیین URL در داخل attributionsrc

در مثال‌های بالا، ویژگی `attributionsrc` خالی گذاشته شده است و مقدار آن یک رشته خالی است. این کار در صورتی مناسب است که سروری که منبع درخواستی را نگه می‌دارد، همان سروری باشد که می‌خواهید ثبت را نیز مدیریت کند، یعنی هدر {{httpheader("Attribution-Reporting-Eligible")}} را دریافت کند و با هدر {{httpheader("Attribution-Reporting-Register-Trigger")}} پاسخ دهد.

با این حال، ممکن است منبع درخواستی روی سروری که شما کنترل می‌کنید نباشد، یا فقط بخواهید ثبت محرک انتساب را روی سرور دیگری مدیریت کنید. در چنین مواردی، می‌توانید یک یا چند URL را به عنوان مقدار `attributionsrc` مشخص کنید. وقتی درخواست منبع رخ می‌دهد، هدر {{httpheader("Attribution-Reporting-Eligible")}} علاوه بر منشأ منبع، به URLهای مشخص‌شده در `attributionsrc` نیز ارسال می‌شود؛ سپس آن URLها می‌توانند با {{httpheader("Attribution-Reporting-Register-Trigger")}} پاسخ دهند تا ثبت کامل شود.

برای مثال، در مورد یک عنصر `<