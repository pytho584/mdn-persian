---
title: "Registering attribution sources"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Attribution_Reporting_API/Registering_sources"
translated_by: "n8n + AI"
---

---
title: Registering attribution sources
slug: Web/API/Attribution_Reporting_API/Registering_sources
page-type: guide
status:
  - deprecated
---

{{DefaultAPISidebar("Attribution Reporting API")}}{{deprecated_header}}

این مقاله نحوه ثبت منبع‌های انتساب را هنگام استفاده از [Attribution Reporting API](/en-US/docs/Web/API/Attribution_Reporting_API) توضیح می‌دهد.

## روش‌شناسی پایه

منبع‌های انتساب به شکل پیوندها، تصاویر یا اسکریپت‌هایی هستند که در محتوایی قرار دارند که می‌خواهید تعاملات با آن‌ها را اندازه‌گیری کنید (مثلاً ممکن است تبلیغاتی باشند که می‌خواهید تبدیل‌های آن‌ها را اندازه‌گیری کنید). این‌ها باعث می‌شوند مرورگر داده‌های منبع را در حافظهٔ پنهان محلی خصوصی (که فقط مرورگر به آن دسترسی دارد) زمانی که تعاملات خاص کاربر رخ می‌دهد ذخیره کند. انواع مختلف منبع انتساب به روش‌های مختلفی ثبت می‌شوند و تعاملات را نشان می‌دهند — به این صورت تفکیک می‌شوند:

- **منابع ناوبری**، که باعث می‌شوند مرورگر داده‌های منبع را در پاسخ به ناوبری ذخیره کند — برای مثال وقتی کاربر روی یک پیوند کلیک می‌کند یا آن را با صفحه‌کلید فعال می‌کند، یا زمانی که در نتیجه یک فراخوانی {{domxref("Window.open()")}} ناوبری رخ می‌دهد. برای مثال‌ها به [منابع انتساب مبتنی بر ناوبری](#navigation-based_attribution_sources) مراجعه کنید.
- **منابع رویدادی**، که باعث می‌شوند مرورگر داده‌های منبع را در پاسخ به رخ دادن رویدادها ذخیره کند. برای مثال‌ها به [منابع انتساب مبتنی بر رویداد](#event-based_attribution_sources) مراجعه کنید.

آنچه در پشت صحنه برای ثبت منبع‌ها و بازیابی و ذخیره داده‌های منبع اتفاق می‌افتد، در هر دو مورد یکسان است:

1. وقتی کاربر با یک منبع انتساب تعامل می‌کند، یک هدر {{httpheader("Attribution-Reporting-Eligible")}} در یک درخواست به سروری که تعاملات را اندازه‌گیری می‌کند (معمولاً سرور تبلیغ‌کننده) ارسال می‌شود که نشان می‌دهد پاسخ واجد شرایط ثبت یک منبع است. برای مثال:

   ```http
   Attribution-Reporting-Eligible: navigation-source
   ```

2. وقتی سرور درخواستی دریافت می‌کند که شامل هدر `Attribution-Reporting-Eligible` است، می‌تواند یک هدر {{httpheader("Attribution-Reporting-Register-Source")}} را همراه با پاسخ برای تکمیل ثبت منبع اضافه کند. مقدار آن یک رشته JSON است که اطلاعاتی را که مرورگر باید درباره منبع انتسابی که با آن تعامل شده است ذخیره کند، فراهم می‌کند. اطلاعات موجود در این هدر همچنین تعیین می‌کند که مرورگر چه نوع گزارش‌هایی تولید خواهد کرد:

   - مثال زیر باعث می‌شود وقتی یک [ماشه](/en-US/docs/Web/API/Attribution_Reporting_API/Registering_triggers) به یک منبع تطبیق داده می‌شود، یک [گزارش سطح رویداد](/en-US/docs/Web/API/Attribution_Reporting_API/Generating_reports#event-level_reports) تولید شود:

     ```js
     res.set(
       "Attribution-Reporting-Register-Source",
       JSON.stringify({
         source_event_id: "412444888111012",
         destination: "https://advertiser.example",
         trigger_data: [0, 1, 2, 3, 4],
         trigger_data_matching: "exact",
         expiry: "604800",
         priority: "100",
         debug_key: "122939999",
         event_report_window: "86400",
       }),
     );
     ```

     در این زمینه، تنها فیلد الزامی `destination` است که ۱ تا ۳ سایتی را مشخص می‌کند که انتظار می‌رود یک ماشه در آن‌ها رخ دهد. این‌ها برای تطبیق ماشه انتساب با منبع در زمانی که با یک ماشه تعامل می‌شود استفاده می‌شوند. سایر فیلدهای ذکرشده در بالا کارهای زیر را انجام می‌دهند:

     - `"source_event_id"`: رشته‌ای که یک شناسه برای منبع انتساب را نشان می‌دهد؛ می‌توان از آن برای نگاشت به اطلاعات دیگر هنگام تعامل با منبع انتساب استفاده کرد، یا برای تجمیع اطلاعات در نقطه پایانی گزارش (برای اطلاعات نقطه پایانی به [تولید گزارش‌ها > فرایند پایه](/en-US/docs/Web/API/Attribution_Reporting_API/Generating_reports#basic_process) مراجعه کنید).
     - `"trigger_data"`: آرایه‌ای از اعداد صحیح بدون علامت ۳۲ بیتی که داده‌هایی را نشان می‌دهد که رویدادهای مختلف ماشه را توصیف می‌کند که می‌توانند با این منبع تطبیق یابند. برای مثال، «کاربر موردی را به سبد خرید اضافه کرد» یا «کاربر در فهرست پستی ثبت‌نام کرد» می‌توانند اقداماتی باشند که در سایت ماشه رخ می‌دهند، با این منبع تطبیق می‌یابند و نوعی تبدیل را نشان می‌دهند که تبلیغ‌کننده در تلاش است آن را اندازه‌گیری کند. برای انجام انتساب سطح رویداد، این موارد باید با `"trigger_data"` مشخص‌شده در [ماشه‌ها](/en-US/docs/Web/HTTP/Reference/Headers/Attribution-Reporting-Register-Trigger#trigger_data) تطبیق داده شوند.

       > [!NOTE]
       > مقادیری که برای نمایش هر رویداد استفاده می‌شوند و تعداد عناصر آرایه، کاملاً اختیاری هستند و توسط شما به‌عنوان توسعه‌دهنده تعریف می‌شوند. آرایه ممکن است حاوی مقادیری باشد که استفاده نمی‌شوند، اما برای اینکه مرورگر هنگام ثبت یک ماشه، مقادیر را به منبع نسبت دهد، مقادیر باید در آرایه وجود داشته باشند.

     - `"trigger_data_matching"`: رشته‌ای که مشخص می‌کند چگونه `"trigger_data"` از ماشه با `"trigger_data"` منبع تطبیق داده می‌شود. `"exact"` مقداری است که تقریباً همیشه از آن استفاده خواهید کرد، که مقادیر دقیق را تطبیق می‌دهد.
     - `"expiry"`: رشته‌ای که زمان انقضا را بر حسب ثانیه برای منبع انتساب نشان می‌دهد؛ پس از آن منبع دیگر فعال نخواهد بود (یعنی ماشه‌های بعدی به این منبع قابل انتساب نخواهند بود).
     - `"priority"`: رشته‌ای که مقدار اولویت را برای منبع انتساب نشان می‌دهد. برای اطلاعات بیشتر به [اولویت‌ها و محدودیت‌های گزارش](/en-US/docs/Web/API/Attribution_Reporting_API/Generating_reports#report_priorities_and_limits) مراجعه کنید.
     - `"debug_key"`: یک عدد صحیح بدون علامت ۶۴ بیتی با قالب پایه ۱۰ که یک کلید اشکال‌زدایی را نشان می‌دهد. اگر می‌خواهید یک [گزارش اشکال‌زدایی](/en-US/docs/Web/API/Attribution_Reporting_API/Generating_reports#debug_reports) همراه با گزارش انتساب مربوطه تولید کنید، این مقدار را تنظیم کنید.
     - `"event_report_window"`: رشته‌ای که زمانی را بر حسب ثانیه نشان می‌دهد؛ پس از آن، ماشه‌های بعدی برای هدف تولید گزارش‌های سطح رویداد به این منبع قابل انتساب نخواهند بود.

     برای توضیح دقیق همه فیلدهای موجود در این هدر، به {{httpheader("Attribution-Reporting-Register-Source")}} مراجعه کنید.

   - برای اینکه مرورگر وقتی یک ماشه به یک منبع تطبیق داده می‌شود یک [گزارش خلاصه](/en-US/docs/Web/API/Attribution_Reporting_API/Generating_reports#summary_reports) تولید کند، باید برخی فیلدهای اضافی را _علاوه بر_ فیلدهای لازم برای تولید گزارش سطح رویداد شامل کنید.

     ```js
     res.set(
       "Attribution-Reporting-Register-Source",
       JSON.stringify({
         source_event_id: "412444888111012",
         destination: "https://advertiser.example",
         trigger_data: [0, 1, 2, 3, 4],
         trigger_data_matching: "exact",
         expiry: "604800",
         priority: "100",
         debug_key: "122939999",
         event_report_window: "86400",

         aggregation_keys: {
           campaignCounts: "0x159",
           geoValue: "0x5",
         },
         aggregatable_report_window: "86400",
       }),
     );
     ```

     فیلدهای اضافی در این مثال عبارت‌اند از:

     - `"aggregation_keys"`: یک شیء حاوی کلیدهای ارائه‌شده توسط کاربر که نقاط داده‌ای مختلف را برای تجمیع مقادیر گزارش زیر آن‌ها نشان می‌دهند.
     - `"aggregatable_report_window"`: رشته‌ای که زمانی را بر حسب ثانیه نشان می‌دهد؛ پس از آن داده‌های ماشه دیگر در گزارش‌های قابل تجمیع تولیدشده گنجانده نخواهند شد.

     باز هم، برای توضیح دقیق همه فیلدهای موجود در این هدر به {{httpheader("Attribution-Reporting-Register-Source")}} مراجعه کنید.

3. پس از انجام موفقیت‌آمیز ثبت منبع، مرورگر داده‌های منبع ارائه‌شده را در حافظه پنهان محلی خصوصی خود ذخیره می‌کند.

## منابع انتساب مبتنی بر ناوبری

منابع ناوبری برای اندازه‌گیری تعامل با پیوندها مفید هستند — برای مثال، ممکن است کاربر تبلیغی را در صفحه یک ناشر ببیند و روی آن کلیک کند تا به صفحه تبلیغ‌کننده برود جایی که امید است تبدیلی رخ دهد.

چند نوع مختلف از منابع انتساب مبتنی بر ناوبری (مثلاً کلیک روی یک تبلیغ) وجود دارد که می‌توانند ثبت شوند — آن‌هایی که مبتنی بر HTML هستند (که از ویژگی `attributionsrc` استفاده می‌کنند) و آن‌هایی که مبتنی بر فراخوانی‌های {{domxref("Window.open()")}} هستند (که از ویژگی پنجره `attributionsrc` استفاده می‌کنند).

### منابع ناوبری مبتنی بر HTML

برای ثبت یک منبع انتساب مبتنی بر ناوبری، می‌توانید ویژگی `attributionsrc` را به یک عنصر مناسب {{htmlelement("a")}} اضافه کنید، که مشخص می‌کند درخواست ثبت به کجا ارسال خواهد شد.

اگر مقدار ویژگی را خالی بگذارید، درخواست ثبت به مقصدی که به آن پیوند داده شده ارسال می‌شود. همچنین امکان تعیین یک یا چند URL اضافی در داخل مقدار وجود دارد تا درخواست ثبت به آن‌ها ارسال شود؛ برای جزئیات بیشتر به [تعیین URLها در داخل attributionsrc](#specifying_urls_inside_attributionsrc) مراجعه کنید.

`attributionsrc` را می‌توان به‌صورت اعلانی اضافه کرد:

```html
<a href="https://shop.example" attributionsrc target="_blank">
  Click to visit our shop
</a>
```

یا از طریق ویژگی {{domxref("HTMLAnchorElement.attributionSrc")}}:

```js
const aElem = document.querySelector("a");
aElem.attributionSrc = "";
```

در این حالت، تعامل رخ می‌دهد و باعث می‌شود مرورگر داده‌های منبع مرتبط با منبع انتساب مبتنی بر ناوبری (طبق آنچه در هدر پاسخ {{httpheader("Attribution-Reporting-Register-Source")}} ارائه شده) را زمانی ذخیره کند که کاربر روی پیوند کلیک کند و مرورگر پاسخ را دریافت کند.

### منابع ناوبری مبتنی بر Window.open()

همچنین می‌توانید کلمه کلیدی ویژگی `attributionsrc` را به ویژگی features یک فراخوانی {{domxref("Window.open()")}} اضافه کنید. در این مثال، ما آن را در پاسخ به رخداد یک رویداد `click` اجرا می‌کنیم:

```js
elem.addEventListener("click", () => {
  window.open("https://shop.example", "_blank", "attributionsrc");
});
```

در این حالت، تعامل رخ می‌دهد و مرورگر داده‌های منبع را زمانی ذخیره می‌کند که `Window.open()` فراخوانی شود و مرورگر پاسخ را دریافت کند.

> [!NOTE]
> هنگام راه‌اندازی یک رویداد [`click`](/en-US/docs/Web/API/Element/click_event) مانند مثال بالا، بهتر است آن را روی کنترلی تنظیم کنید که در آن کلیک مورد انتظار است، مانند یک عنصر {{htmlelement("button")}} یا {{htmlelement("a")}}. این کار از نظر معنایی منطقی‌تر است و برای کاربران صفحه‌خوان و صفحه‌کلید در دسترس‌تر است.

> [!NOTE]
> برای ثبت یک منبع انتساب از طریق `open()`، باید آن را با [فعال‌سازی گذرا](/en-US/docs/Glossary/Transient_activation) (یعنی در داخل یک کنترل‌کننده رویداد تعامل کاربر مانند `click`) در عرض پنج ثانیه از تعامل کاربر فراخوانی کرد.

## منابع انتساب مبتنی بر رویداد

منابع انتساب مبتنی بر رویداد باعث می‌شوند مرورگر داده‌های منبع را در پاسخ به رخ دادن نوعی رویداد ذخیره کند، مانند رویداد `load` در مورد یک عنصر `<img>` یا `<script>` (که از ویژگی `attributionsrc` مانند آنچه در بالا با عنصر `<a>` دیدیم استفاده می‌کنند)، یا یک رویداد سفارشی به انتخاب شما که در جاوااسکریپت خود تنظیم کرده‌اید.

### منابع رویدادی مبتنی بر HTML

منابع رویدادی مبتنی بر HTML می‌توانند برای اندازه‌گیری تعامل با صفحه یک ناشر در زمان بارگذاری اولیه آن استفاده شوند — یا به‌طور دقیق‌تر وقتی یک `<img>` یا `<script>` بارگذاری می‌شود. برای ثبت یک منبع انتساب مبتنی بر رویداد از طریق HTML، می‌توانید ویژگی `attributionsrc` را به یک عنصر مناسب — {{htmlelement("img")}} یا {{htmlelement("script")}} اضافه کنید.

اگر مقدار ویژگی را خالی بگذارید، درخواست ثبت به سروری که منبع درخواست‌شده روی آن میزبانی می‌شود ارسال خواهد شد. همچنین امکان تعیین یک یا چند URL اضافی در داخل مقدار وجود دارد تا درخواست ثبت به آن‌ها ارسال شود؛ برای جزئیات بیشتر به [تعیین URLها در داخل attributionsrc](#specifying_urls_inside_attributionsrc) مراجعه کنید.

بیایید به یک مثال عنصر `<img>` نگاه کنیم:

```html
<img src="advertising-image.png" alt="" attributionsrc />
```

همچنین می‌توانید این کار را از طریق ویژگی {{domxref("HTMLImageElement.attributionSrc")}} انجام دهید:

```js
const imgElem = document.querySelector("img");
imgElem.attributionSrc = "";
```

مرورگر داده‌های منبع انتساب را زمانی ذخیره می‌کند که پاسخ حاوی فایل تصویر را دریافت کند (یعنی وقتی رویداد `load` رخ می‌دهد). به خاطر داشته باشید که کاربران ممکن است لزوماً نتوانند تصویر را درک کنند — ممکن است یک پیکسل ردیابی شفاف ۱×۱ باشد که فقط برای گزارش انتساب استفاده می‌شود.

یک مثال {{htmlelement("script")}} ممکن است به این شکل باشد:

```html
<script src="advertising-script.js" attributionsrc></script>
```

یا از طریق ویژگی {{domxref("HTMLScriptElement.attributionSrc")}}:

```js
const scriptElem = document.querySelector("script");
scriptElem.attributionSrc = "";
```

در این حالت، تعامل رخ می‌دهد و مرورگر داده‌های منبع را زمانی ذخیره می‌کند که پاسخ حاوی اسکریپت را دریافت کند.

### منابع رویدادی مبتنی بر JavaScript

منابع انتساب مبتنی بر اسکریپت نسبت به منابع انتساب مبتنی بر HTML انعطاف‌پذیرتر هستند. می‌توانید یک اسکریپت راه‌اندازی کنید تا درخواستی را آغاز کند که واجد شرایط ثبت یک منبع انتساب بر اساس هر درخواستی که با برنامه شما سازگار است باشد. این یک رویکرد منعطف است و زمانی مفید است که بخواهید داده‌های منبع را در پاسخ به تعاملات سفارشی ذخیره کنید، برای مثال، کلیک روی یک عنصر سفارشی یا ارسال یک فرم.

برای راه‌اندازی یک منبع انتساب مبتنی بر اسکریپت، می‌توانید یکی از این کارها را انجام دهید:

- یک درخواست {{domxref("Window/fetch", "fetch()")}} حاوی گزینه `attributionReporting` ارسال کنید:

  ```js
  const attributionReporting = {
    eventSourceEligible: true,
    triggerEligible: false,
  };

  // Optionally set keepalive to ensure the request outlives the page
  function triggerSourceInteraction() {
    fetch("https://shop.example/endpoint", {
      keepalive: true,
      attributionReporting,
    });
  }

  // Associate the interaction trigger with whatever
  // event makes sense for your code (does not have to be a
  // DOM event/user interaction)
  elem.addEventListener("click", triggerSourceInteraction);
  ```

- یک {{domxref("XMLHttpRequest")}} ارسال کنید و {{domxref("XMLHttpRequest.setAttributionReporting", "setAttributionReporting()")}} را روی شیء درخواست فراخوانی کنید:

  ```js
  const attributionReporting = {
    eventSourceEligible: true,
    triggerEligible: false,
  };

  function triggerSourceInteraction() {
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
  // event makes sense for your code (does not have to be a
  // DOM event/user interaction)
  elem.addEventListener("click", triggerSourceInteraction);
  ```

در این حالت، تعامل رخ می‌دهد و مرورگر داده‌های منبع را زمانی ذخیره می‌کند که پاسخ درخواست fetch را دریافت کند.

> [!NOTE]
> درخواست می‌تواند برای هر منبعی باشد. لازم نیست مستقیماً به Attribution Reporting API مرتبط باشد و می‌تواند درخواستی برای JSON، متن ساده، یک Blob تصویر یا هر چیز دیگری باشد که برای برنامه شما منطقی است.

## تعیین URLها در داخل attributionsrc

تا اینجا، در همه مثال‌هایی که دیده‌ایم، ویژگی/ویژگی پنجره `attributionsrc` یا ویژگی `attributionSrc` خالی گذاشته شده و مقدار رشته خالی را گرفته است. این کار در صورتی خوب است که سروری که منبع درخواست‌شده را نگه می‌دارد همان سروری باشد که می‌خواهید ثبت را مدیریت کند، یعنی هدر {{httpheader("Attribution-Reporting-Eligible")}} را دریافت کند و با هدر {{httpheader("Attribution-Reporting-Register-Source")}} پاسخ دهد.

با این حال، ممکن است منبع درخواست‌شده روی سروری که کنترل می‌کنید نباشد، یا فقط بخواهید ثبت منبع انتساب را روی سرور دیگری مدیریت کنید. در چنین مواردی، می‌توانید یک یا چند URL را به‌عنوان مقدار `attributionsrc` مشخص کنید. وقتی درخواست منبع رخ می‌دهد، هدر {{httpheader("Attribution-Reporting-Eligible")}} علاوه بر مبدأ منبع، به URL(های) مشخص‌شده در `attributionsrc` ارسال خواهد شد؛ سپس این URLها می‌توانند با {{httpheader("Attribution-Reporting-Register-Source")}} پاسخ دهند تا منبع را ثبت کنند.

برای مثال، در مورد یک عنصر `<a>` می‌توانید URL(ها) را در ویژگی `attributionsrc` اعلام کنید:

```html
<a
  href="https://shop.example"
  attributionsrc="https://a.example/register-source">
  Click to visit our shop
</a>
```

یا در جاوااسکریپت از طریق ویژگی `attributionSrc`:

```js
// encode the URLs in case they contain special characters
// such as '=' that would be improperly parsed.
const encodedUrlA = encodeURIComponent("https://a.example/register-source");
const encodedUrlB = encodeURIComponent("https://b.example/register-source");

const aElem = document.querySelector("a");
aElem.attributionSrc = `${encodedUrlA} ${encodedUrlB}`;
```

در مورد یک فراخوانی {{domxref("Window.open()")}}، URLهای مختلف باید به‌عنوان چند ویژگی جداگانه `attributionsrc` در پارامتر [`windowFeatures`](/en-US/docs/Web/API/Window/open#windowfeatures) فهرست شوند که با کاما یا فاصله از هم جدا شده‌اند:

```js
// encode the URLs in case they contain special characters
// such as '=' that would be improperly parsed.
const encodedUrlA = encodeURIComponent("https://a.example/register-source");
const encodedUrlB = encodeURIComponent("https://b.example/register-source");

elem.addEventListener("click", () => {
  window.open(
    "https://ourshop.example",
    "_blank",
    `attributionsrc=${encodedUrlA},attributionsrc=${encodedUrlB}`,
  );
});
```

> [!NOTE]
> تعیین چندین URL به این معناست که چندین منبع انتساب می‌توانند روی همان ویژگی ثبت شوند. برای مثال، ممکن است کمپین‌های مختلفی داشته باشید که می‌خواهید موفقیت آن‌ها را اندازه‌گیری کنید، که شامل تولید گزارش‌های مختلف روی داده‌های مختلف است.

## همچنین ببینید

- [Attribution Reporting Header Validation tool](https://wicg.github.io/attribution-reporting-api/validate-headers)