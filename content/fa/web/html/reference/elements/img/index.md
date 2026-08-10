---
title: "<img> HTML image embed element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/img"
translated_by: "n8n + AI"
---

عنصر **`<img>`** در [HTML](/en-US/docs/Web/HTML) یک تصویر را درون سند جاسازی می‌کند.

```html interactive-example
<img
  class="fit-picture"
  src="/shared-assets/images/examples/grapefruit-slice.jpg"
  alt="Grapefruit slice atop a pile of other slices" />
```

```css interactive-example
.fit-picture {
  width: 250px;
}
```

مثال بالا نحوه استفاده از عنصر `<img>` را نشان می‌دهد:

- ویژگی `src` مسیر تصویری که می‌خواهید جاسازی کنید را نگه می‌دارد. اگر ویژگی [srcset](/en-US/docs/Web/API/HTMLImageElement/srcset) موجود باشد، اجباری نیست. با این حال، حداقل یکی از ویژگی‌های `src` یا `srcset` باید ارائه شود.
- ویژگی `alt` یک جایگزین متنی برای تصویر در خود دارد که اجباری است و **بسیار مفید** برای دسترسی‌پذیری — صفحه‌خوان‌ها مقدار ویژگی را برای کاربرانشان می‌خوانند تا بدانند مفهوم تصویر چیست. متن جایگزین همچنین در صفحه نمایش داده می‌شود اگر تصویر به هر دلیلی بارگذاری نشود: برای مثال، خطاهای شبکه، مسدود شدن محتوا، یا خرابی لینک‌ها.

ویژگی‌های بسیار دیگری هم برای اهداف مختلف وجود دارد:

- کنترل [Referrer](/en-US/docs/Web/HTTP/Reference/Headers/Referrer-Policy)/CORS برای امنیت و حریم خصوصی: به [`crossorigin`](#crossorigin) و [`referrerpolicy`](#referrerpolicy) مراجعه کنید.
- از هر دو [`width`](#width) و [`height`](#height) برای تنظیم اندازهٔ ذاتی تصویر استفاده کنید، تا پیش از بارگذاری فضا اشغال کند و از جابه‌جایی محتوای طرح جلوگیری شود.
- نکات تصاویر واکنش‌گرا با [`sizes`](#sizes) و [`srcset`](#srcset) (همچنین به عنصر `<picture>` و آموزش [تصاویر واکنش‌گرا](/en-US/docs/Web/HTML/Guides/Responsive_images) مراجعه کنید).

## قالب‌های تصویر پشتیبانی‌شده

استاندارد HTML لیستی از قالب‌های تصویر پشتیبانی‌شده ارائه نمی‌دهد، بنابراین {{glossary("user agent","عامل‌های کاربر")}} ممکن است از قالب‌های متفاوتی پشتیبانی کنند.

> [!NOTE]
> راهنمای [انواع و قالب‌های فایل تصویر](/en-US/docs/Web/Media/Guides/Formats/Image_types) اطلاعات جامعی دربارهٔ قالب‌های تصویر و پشتیبانی مرورگرهای وب ارائه می‌دهد. این بخش تنها یک خلاصه است!

قالب‌های فایل تصویری که بیشترین استفاده را در وب دارند عبارت‌اند از:

- [APNG (Animated Portable Network Graphics)](/en-US/docs/Web/Media/Guides/Formats/Image_types#apng_animated_portable_network_graphics) — انتخاب خوبی برای توالی‌های انیمیشن بدون اتلاف (GIF کارایی کمتری دارد)
- [AVIF (AV1 Image File Format)](/en-US/docs/Web/Media/Guides/Formats/Image_types#avif_image) — انتخابی خوب برای تصاویر و تصاویر متحرک به دلیل عملکرد بالا.
- [GIF (Graphics Interchange Format)](/en-US/docs/Web/Media/Guides/Formats/Image_types#gif_graphics_interchange_format) — انتخاب خوبی برای تصاویر و انیمیشن‌های _ساده_.
- [JPEG (Joint Photographic Expert Group image)](/en-US/docs/Web/Media/Guides/Formats/Image_types#jpeg_joint_photographic_experts_group_image) — انتخاب خوبی برای فشرده‌سازی با اتلاف تصاویر ثابت (در حال حاضر محبوب‌ترین).
- [PNG (Portable Network Graphics)](/en-US/docs/Web/Media/Guides/Formats/Image_types#png_portable_network_graphics) — انتخاب خوبی برای فشرده‌سازی بدون اتلاف تصاویر ثابت (کیفیت کمی بهتر از JPEG).
- [SVG (Scalable Vector Graphics)](/en-US/docs/Web/Media/Guides/Formats/Image_types#svg_scalable_vector_graphics) — قالب تصویر برداری. برای تصاویری که باید در اندازه‌های مختلف با دقت ترسیم شوند استفاده کنید.
- [WebP (Web Picture format)](/en-US/docs/Web/Media/Guides/Formats/Image_types#webp_image) — انتخابی عالی برای تصاویر و تصاویر متحرک

قالب‌هایی مانند [WebP](/en-US/docs/Web/Media/Guides/Formats/Image_types#webp_image) و [AVIF](/en-US/docs/Web/Media/Guides/Formats/Image_types#avif_image) توصیه می‌شوند زیرا عملکرد بسیار بهتری نسبت به PNG، JPEG و GIF هم برای تصاویر ثابت و هم متحرک دارند.

SVG همچنان قالب توصیه‌شده برای تصاویری است که باید در اندازه‌های مختلف با دقت رسم شوند.

## خطاهای بارگذاری تصویر

اگر هنگام بارگذاری یا رندر تصویر خطایی رخ دهد و یک کنترل‌کننده رویداد `onerror` برای رویداد {{domxref("HTMLElement/error_event", "error")}} تنظیم شده باشد، آن کنترل‌کننده فراخوانی می‌شود. این اتفاق ممکن است در چند موقعیت رخ دهد:

- ویژگی‌های `src` یا `srcset` خالی (`""`) یا `null` باشند.
- `src` {{glossary("URL")}} همان URL صفحه‌ای باشد که کاربر در حال مشاهدهٔ آن است.
- تصویر به‌نحوی خراب شده باشد که امکان بارگذاری آن وجود نداشته باشد.
- ابردادهٔ تصویر به‌گونه‌ای خراب باشد که نتوان ابعاد آن را بازیابی کرد و ابعادی نیز در ویژگی‌های عنصر `<img>` مشخص نشده باشد.
- قالب تصویر توسط {{Glossary("user agent")}} پشتیبانی نشود.

## ویژگی‌ها

این عنصر از [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) پشتیبانی می‌کند.

- `alt`
  - : متنی را تعریف می‌کند که می‌تواند جایگزین تصویر در صفحه شود.

    > [!NOTE]
    > مرورگرها همیشه تصاویر را نمایش نمی‌دهند. موقعیت‌های مختلفی وجود دارد که ممکن است مرورگر تصویر را نشان ندهد، مانند:
    >
    > - مرورگرهای غیردیداری (مانند مرورگرهایی که افراد دارای اختلالات بینایی استفاده می‌کنند)
    > - کاربر تصمیم می‌گیرد تصاویر را نمایش ندهد (برای صرفه‌جویی در پهنای باند یا به دلایل حریم خصوصی)
    > - تصویر نامعتبر است یا [نوع پشتیبانی‌نشده](#supported_image_formats)‌ای دارد
    >
    > در این موارد، مرورگر ممکن است تصویر را با متن موجود در ویژگی `alt` عنصر جایگزین کند. به این دلایل و دلایل دیگر، هر زمان که امکان دارد یک مقدار مفید برای `alt` در نظر بگیرید.

    تنظیم این ویژگی روی یک رشتهٔ خالی (`alt=""`) نشان می‌دهد که این تصویر _بخش کلیدی_ محتوا نیست (تزئینی یا یک پیکسل ردیابی است) و مرورگرهای غیردیداری می‌توانند آن را از {{glossary("Engine/Rendering", "rendering")}} حذف کنند. مرورگرهای دیداری نیز اگر ویژگی `alt` خالی باشد و تصویر بارگذاری نشود، نماد تصویر خراب را پنهان می‌کنند.

    این ویژگی همچنین هنگام کپی و چسباندن تصویر به متن، یا ذخیرهٔ یک تصویر پیوندشده در بوکمارک استفاده می‌شود.

- `attributionsrc` {{deprecated_inline}} {{non-standard_inline}}
  - : مشخص می‌کند که می‌خواهید مرورگر یک سرآیند {{httpheader("Attribution-Reporting-Eligible")}} همراه با درخواست تصویر ارسال کند.

    در سمت سرور، از این برای راه‌اندازی ارسال یک سرآیند {{httpheader("Attribution-Reporting-Register-Source")}} یا {{httpheader("Attribution-Reporting-Register-Trigger")}} در پاسخ استفاده می‌شود تا به‌ترتیب یک [منبع انتساب](/en-US/docs/Web/API/Attribution_Reporting_API/Registering_sources#html-based_event_sources) یا [محرک انتساب](/en-US/docs/Web/API/Attribution_Reporting_API/Registering_triggers#html-based_attribution_triggers) مبتنی بر تصویر ثبت شود. اینکه کدام سرآیند پاسخ باید بازگردانده شود به مقدار سرآیند `Attribution-Reporting-Eligible` که ثبت را فعال کرده بستگی دارد.

    رویداد منبع یا محرک متناظر زمانی فعال می‌شود که مرورگر پاسخ حاوی فایل تصویر را دریافت کند.

    > [!NOTE]
    > برای جزئیات بیشتر به [Attribution Reporting API](/en-US/docs/Web/API/Attribution_Reporting_API) مراجعه کنید.

    دو نسخه از این ویژگی قابل تنظیم است:
    - بولی، یعنی فقط نام `attributionsrc`. این مشخص می‌کند که می‌خواهید سرآیند {{httpheader("Attribution-Reporting-Eligible")}} به همان سروری که ویژگی `src` به آن اشاره دارد ارسال شود. این حالت برای زمانی مناسب است که ثبت منبع یا محرک انتساب را در همان سرور انجام می‌دهید. هنگام ثبت یک محرک انتساب، این ویژگی اختیاری است و در صورت حذف، مقدار بولی استفاده خواهد شد.
    - مقداری شامل یک یا چند URL، برای نمونه:

    ```html
    <img
      src="image-file.png"
      alt="My image file description"
      attributionsrc="https://a.example/register-source
                         https://b.example/register-source" />
    ```

این قابلیت در مواقعی مفید است که منبع درخواستی روی سروری که تحت کنترل شما نیست قرار دارد، یا صرفاً می‌خواهید فرآیند ثبت منبع انتساب (attribution source) را روی یک سرور دیگر مدیریت کنید. در این حالت می‌توانید یک یا چند URL را به عنوان مقدار `attributionsrc` مشخص کنید. هنگامی که درخواست منبع انجام می‌شود، header `Attribution-Reporting-Eligible` علاوه بر مبدأ منبع، به URL(های) مشخص‌شده در `attributionSrc` نیز ارسال می‌شود. سپس این URLها می‌توانند با ارسال header مناسب `Attribution-Reporting-Register-Source` یا `Attribution-Reporting-Register-Trigger` پاسخ دهند تا ثبت تکمیل شود.

> [!NOTE]
> تعیین چندین URL به این معنی است که می‌توان چندین منبع انتساب را برای یک ویژگی یکسان ثبت کرد. برای مثال ممکن است کمپین‌های مختلفی داشته باشید که می‌خواهید موفقیت آن‌ها را اندازه‌گیری کنید و هر کدام شامل تولید گزارش‌های متفاوتی بر اساس داده‌های مختلف است.

- [`crossorigin`](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin)
  - : مشخص می‌کند که دریافت تصویر باید با استفاده از یک درخواست CORS انجام شود یا خیر. داده‌های تصویری که از یک [تصویر فعال‌شده برای CORS](/en-US/docs/Web/HTML/How_to/CORS_enabled_image) و با یک درخواست CORS دریافت می‌شود، می‌توانند در المان {{HTMLElement("canvas")}} استفاده شوند بدون آنکه به‌عنوان «[آلوده](/en-US/docs/Web/HTML/How_to/CORS_enabled_image#security_and_tainted_canvases)» (tainted) علامت‌گذاری شوند.

    اگر ویژگی `crossorigin` تعیین نشده باشد، یک درخواست غیر CORS ارسال می‌شود (بدون header درخواست `Origin`) و مرورگر تصویر را آلوده (tainted) علامت‌گذاری کرده و دسترسی به داده‌های تصویر را محدود می‌کند و از استفاده از آن در المان‌های {{HTMLElement("canvas")}} جلوگیری می‌کند.

    اگر ویژگی `crossorigin` تعیین شود، یک درخواست CORS ارسال می‌شود (همراه با header درخواست `Origin`)؛ اما اگر سرور اجازه دسترسی cross-origin به داده‌های تصویر را برای سایت مبدأ صادر نکند (با ارسال نکردن هیچ header پاسخ `Access-Control-Allow-Origin`، یا با قرار ندادن مبدأ سایت در header پاسخ `Access-Control-Allow-Origin` که ارسال می‌کند)، آنگاه مرورگر از بارگذاری تصویر جلوگیری کرده و یک خطای CORS را در کنسول ابزارهای توسعه‌دهنده ثبت می‌کند.

    مقادیر مجاز:
    - `anonymous`
      - : یک درخواست CORS بدون اطلاعات کاربری ارسال می‌شود (یعنی بدون cookies، [گواهی‌های X.509](https://datatracker.ietf.org/doc/html/rfc5280) یا header درخواست `Authorization`).
    - `use-credentials`
      - : درخواست CORS همراه با اطلاعات کاربری ارسال می‌شود (یعنی cookies، گواهی‌های X.509 و header درخواست `Authorization`). اگر سرور با ارسال header پاسخ `Access-Control-Allow-Credentials: true` اجازه به اشتراک‌گذاری اطلاعات کاربری با سایت مبدأ را ندهد، مرورگر تصویر را آلوده علامت‌گذاری کرده و دسترسی به داده‌های آن را محدود می‌کند.

    اگر این ویژگی دارای مقدار نامعتبری باشد، مرورگرها آن را مانند مقدار `anonymous` در نظر می‌گیرند. برای اطلاعات بیشتر به [ویژگی‌های تنظیمات CORS](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin) مراجعه کنید.

- `decoding`
  - : این ویژگی یک راهنمایی به مرورگر می‌دهد که آیا رمزگشایی تصویر همراه با رندر سایر محتوای DOM در یک گام نمایشی واحد که «صحیح‌تر» به نظر می‌رسد انجام شود (`sync`)، یا اینکه ابتدا سایر محتوای DOM رندر و نمایش داده شوند و سپس تصویر رمزگشایی و بعداً نمایش داده شود (`async`). در عمل، `async` به این معنی است که رندر بعدی (next paint) منتظر رمزگشایی تصویر نمی‌ماند.

معمولاً تشخیص تأثیر ویژگی `decoding` روی عناصر `<img>` ایستا دشوار است. این تصاویر در حین دریافت فایل (از شبکه یا حافظهٔ نهان) احتمالاً ابتدا به‌صورت تصویر خالی رندر می‌شوند و سپس به‌طور مستقل مدیریت می‌شوند، بنابراین «هم‌گام‌سازی» به‌روزرسانی محتوا کمتر به چشم می‌آید. با این حال، مسدود شدن رندر هنگام رمزگشایی – اگرچه اغلب بسیار اندک است – قابل اندازه‌گیری است، حتی اگر با چشم انسان به‌سختی دیده شود. برای تحلیل دقیق‌تر، [What does the image decoding attribute actually do?](https://www.tunetheweb.com/blog/what-does-the-image-decoding-attribute-actually-do/) را ببینید (tunetheweb.com، ۲۰۲۳).

استفاده از انواع مختلف `decoding` می‌تواند هنگام درج پویای عناصر `<img>` در DOM با جاوااسکریپت، تفاوت‌های محسوس‌تری ایجاد کند – برای جزئیات بیشتر به {{domxref("HTMLImageElement.decoding")}} مراجعه کنید.

مقادیر مجاز:
- `sync`
  - : تصویر را هم‌گام با رندر سایر محتوای DOM رمزگشایی کن و همه را با هم ارائه بده.
- `async`
  - : تصویر را بعد از رندر و نمایش سایر محتوای DOM، به‌صورت ناهمگام رمزگشایی کن.
- `auto`
  - : هیچ اولویتی برای حالت رمزگشایی تعیین نمی‌شود؛ مرورگر تصمیم می‌گیرد چه چیزی برای کاربر بهتر است. این مقدار پیش‌فرض است.

- [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming)
  - : تصویر را برای مشاهده توسط API {{domxref("PerformanceElementTiming")}} نشانه‌گذاری می‌کند. مقدار داده‌شده به یک شناسه برای عنصر تصویر مشاهده‌شده تبدیل می‌شود. همچنین صفحهٔ ویژگی [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming) را ببینید.

- [`fetchpriority`](/en-US/docs/Web/HTML/Reference/Attributes/fetchpriority)
  - : اشاره‌ای دربارهٔ اولویت نسبی واکشی تصویر ارائه می‌دهد. مقادیر مجاز:
    - `high`
      - : تصویر با اولویت بالا نسبت به سایر تصاویر واکشی می‌شود.
    - `low`
      - : تصویر با اولویت پایین نسبت به سایر تصاویر واکشی می‌شود.
    - `auto`
      - : هیچ اولویتی برای واکشی تعیین نمی‌شود.
        این مقدار پیش‌فرض است.
        اگر هیچ مقداری تنظیم نشود یا مقدار نامعتبری داده شود، استفاده می‌شود.
- `height`
  - : ارتفاع ذاتی تصویر به پیکسل. باید یک عدد صحیح بدون واحد باشد.

    > [!NOTE]
    > وجود `height` و [`width`](#width) به مرورگر امکان می‌دهد پیش از بارگذاری تصویر، {{glossary("aspect ratio")}} آن را محاسبه کند. این نسبت برای رزرو فضای مورد نیاز نمایش تصویر استفاده می‌شود و از جابه‌جایی layout هنگام دریافت و ترسیم تصویر روی صفحه می‌کاهد یا حتی آن را حذف می‌کند. کاهش جابه‌جایی layout یکی از عوامل اصلی تجربهٔ کاربری خوب و عملکرد وب است.

- `ismap`
  - : این ویژگی Boolean نشان می‌دهد که تصویر بخشی از یک [نقشهٔ سمت سرور](https://en.wikipedia.org/wiki/Image_map#Server-side) است. در این صورت مختصات جایی که کاربر روی تصویر کلیک کرده به سرور ارسال می‌شود.

    > [!NOTE]
    > این ویژگی فقط زمانی مجاز است که عنصر `<img>` نوادهٔ یک عنصر {{htmlelement("a")}} با ویژگی [`href`](/en-US/docs/Web/HTML/Reference/Elements/a#href) معتبر باشد. این کار یک مقصد جایگزین برای کاربرانی که دستگاه اشاره‌گر ندارند فراهم می‌کند.

- `loading`
  - : نحوهٔ بارگذاری تصویر توسط مرورگر را مشخص می‌کند:
    - `eager`
      - : تصویر را بدون توجه به اینکه در حال حاضر در {{glossary("visual viewport")}} قرار دارد یا خیر، بلافاصله بارگذاری می‌کند (این مقدار پیش‌فرض است).
    - `lazy`
      - : بارگذاری تصویر را تا زمانی که به فاصلهٔ محاسبه‌شده‌ای از viewport برسد، طبق تعریف مرورگر به تعویق می‌اندازد.

        بارگذاری تنبلانه (lazy loading) پهنای باند شبکه و فضای ذخیره‌سازی لازم برای پردازش تصویر را تا زمانی که تقریباً مطمئن باشیم به آن نیاز داریم، ذخیره می‌کند. این کار در بیشتر موارد به بهبود عملکرد می‌انجامد.

اگرچه توصیه می‌شود برای همه تصاویر ویژگی‌های `width` و `height` را به‌صورت صریح مشخص کنید تا از تغییر چیدمان (layout shift) جلوگیری شود، این موضوع برای تصاویر lazy-loaded اهمیت بیشتری دارد. تصاویر lazy-loaded اگر با بخش قابل مشاهده از یک المان هم‌پوشانی نداشته باشند هرگز بارگذاری نمی‌شوند، حتی اگر بارگذاری آن‌ها بتواند آن وضعیت را تغییر دهد؛ چون تصاویر بارگذاری‌نشده `width` و `height`شان `0` است. این اتفاق زمانی که محتوای قابل مشاهده در viewport وسط خواندن کاربر جابه‌جا می‌شود، تجربه کاربری را به شدت مختل می‌کند.

تصاویر lazy-loaded که در visual viewport قرار دارند ممکن است هنگام اجرای رویداد `load` پنجره (Window) هنوز دیده نشوند. دلیل آن این است که این رویداد بر اساس تصاویر eager-loaded فعال می‌شود — تصاویر lazy-loaded حتی اگر در بارگذاری اولیه صفحه در visual viewport باشند، در نظر گرفته نمی‌شوند.

بارگذاری تنها زمانی به تعویق می‌افتد که جاوااسکریپت فعال باشد. این یک اقدام ضد ردیابی است، زیرا اگر user agent از lazy loading در حالت غیرفعال بودن اسکریپت پشتیبانی کند، همچنان امکان ردیابی موقعیت تقریبی اسکرول کاربر در طول یک نشست وجود خواهد داشت؛ به این صورت که تصاویر به‌طور راهبردی در نشانه‌گذاری صفحه قرار داده شوند تا سرور بتواند تعداد تصاویر درخواستی و زمان آن‌ها را ردیابی کند.

- `referrerpolicy`
  - : یک رشته که مشخص می‌کند هنگام واکشی منبع از کدام referrer استفاده شود:
    - `no-referrer`: هدر `Referer` ارسال نخواهد شد.
    - `no-referrer-when-downgrade`: هدر `Referer` به `origin` های بدون TLS (HTTPS) ارسال نخواهد شد.
    - `origin`: Referrer ارسالی محدود به origin صفحه ارجاع‌دهنده خواهد بود: شامل scheme، host و port آن.
    - `origin-when-cross-origin`: Referrer ارسالی به origin های دیگر محدود به scheme، host و port خواهد بود. درخواست‌های same-origin همچنان شامل path نیز می‌شوند.
    - `same-origin`: برای same origin یک referrer ارسال می‌شود، اما درخواست‌های cross-origin هیچ اطلاعات referrer ندارند.
    - `strict-origin`: تنها زمانی origin سند را به‌عنوان referrer ارسال می‌کند که سطح امنیتی پروتکل یکسان باقی بماند (HTTPS→HTTPS)؛ اما به مقصدی با امنیت پایین‌تر (HTTPS→HTTP) ارسال نمی‌شود.
    - `strict-origin-when-cross-origin` (پیش‌فرض): در درخواست‌های same-origin یک URL کامل ارسال می‌کند؛ اگر سطح امنیتی پروتکل یکسان باشد (HTTPS→HTTPS) فقط origin ارسال می‌شود؛ و به مقصدی با امنیت پایین‌تر (HTTPS→HTTP) هیچ هدری ارسال نمی‌شود.
    - `unsafe-url`: Referrer شامل origin و path خواهد بود (اما fragment، password یا username را شامل نمی‌شود). **این مقدار ناامن است**، چون origin ها و path های منابع محافظت‌شده با TLS را به origin های ناامن درز می‌دهد.

- `sizes`
  - : یک یا چند مقدار جداشده با کاما که می‌تواند source size یا کلیدواژه `auto` باشد.
    طبق مشخصات، ویژگی `sizes` تنها زمانی باید حضور داشته باشد که `srcset` از توصیف‌گرهای عرض (width descriptors) استفاده کند.
    - **source size**
      - : یک **source size** شامل موارد زیر است:
        1. یک media condition (که برای آخرین آیتم لیست حذف می‌شود).
        2. یک مقدار source size.

        برای مثال، source size زیر پیشنهاد می‌دهد که اگر عرض `viewport` برابر با 500px یا کمتر باشد، از یک تصویر با عرض 1000px استفاده شود.

        ```css
        (width <= 500px) 1000px
        ```

        media condition ها ویژگی‌های viewport را توصیف می‌کنند، نه تصویر را.
        از آن‌جا که یک توصیف‌گر source size عرضی را مشخص می‌کند که برای تصویر در زمان چیدمان استفاده می‌شود، media condition معمولاً (اما نه الزاماً) بر پایه `@media/width` است.

مقادیر source size اندازهٔ نمایشی مورد نظر تصویر را مشخص می‌کنند.  
عامل‌های کاربر (user agents) از اندازهٔ source جاری برای انتخاب یکی از منابع ارائه‌شده توسط ویژگی `srcset` استفاده می‌کنند، زمانی که آن منابع با توصیف‌گرهای عرض (`w`) توصیف شده باشند. مقدار `w` تعریف‌شده در `sizes`، پهنای پیش‌فرض طرح‌بندی تصویر را تعیین می‌کند.  
در نبود {{glossary("CSS")}}، مرورگر تصویر را در همین اندازه نمایش می‌دهد، بدون توجه به ابعاد پیکسلی فیزیکی فایل دانلودشده.

یک مقدار source size می‌تواند هر [طول](/en-US/docs/Web/CSS/Reference/Values/length) غیرمنفی‌ای باشد.  
نباید از توابع CSS به جز [توابع ریاضی](/en-US/docs/Web/CSS/Reference/Values/Functions#math_functions) استفاده کند.  
واحدها به همان شکلی که در [media queries](/en-US/docs/Web/CSS/Guides/Media_queries) تفسیر می‌شوند، تفسیر می‌شوند؛ یعنی تمام واحدهای طول نسبی نسبت به ریشهٔ سند محاسبه می‌شوند، نه عنصر `<img>`. برای مثال، مقدار `em` نسبت به اندازهٔ قلم ریشه است، نه اندازهٔ قلم تصویر.  
مقادیر [درصدی](/en-US/docs/Web/CSS/Reference/Values/percentage) مجاز نیستند.  
اگر ویژگی `sizes` ارائه نشود، مقدار پیش‌فرض آن `100vw` (عرض viewport) است.

- `auto`
  - : کلیدواژهٔ `auto` نشان می‌دهد که مرورگر باید از عرض طرح‌بندی مورد انتظار عنصر برای انتخاب تصویر جهت نمایش استفاده کند.  
    به‌عبارت دیگر، باید از [concrete size](/en-US/docs/Web/CSS/Reference/Values/image#concrete_size) تصویر استفاده کند که پس از اعمال طرح‌بندی HTML و CSS محاسبه می‌شود.  
    این فقط زمانی معتبر است که همراه با `loading="lazy"` استفاده شود، زیرا انتظار می‌رود صفحه تا زمان بارگذاری تصویر، CSS و سایر اطلاعات طرح‌بندی را داشته باشد.  

    استفاده از `auto` شما را از تکرار شرط‌های media طرح‌بندی بی‌نیاز می‌کند: یک بار برای طرح‌بندی و بار دیگر برای انتخاب تصویر مناسب برای دریافت و نمایش.  

    اگر `auto` نتواند حل شود — چه به این دلیل که مرورگر از آن پشتیبانی نمی‌کند، چه به این دلیل که تصویر هنوز اندازهٔ طرح‌بندی‌ای ندارد — مرورگر به ترتیب به *source size*های موجود در لیست مراجعه می‌کند تا عرض را تعیین کند، سپس به ویژگی‌های `width`/`height` تعریف‌شده روی عنصر، و در نهایت به اندازهٔ ذاتی پیش‌فرض عنصر `<img>` که در stylesheet عامل کاربر تعریف شده است (300px در 150px).  

    برای سازگاری بهتر با مرورگرهایی که از `auto` پشتیبانی نمی‌کنند، می‌توانید بعد از `auto` در ویژگی `sizes`، اندازه‌های جایگزین قرار دهید.  
    همچنین بهتر است ویژگی‌های `width` و `height` عنصر را به ابعاد ذاتی بزرگ‌ترین تصویر در `srcset` تنظیم کنید تا مرورگر بتواند فضا را با نسبت تصویر درست رزرو کند:

    ```html
    <img
      loading="lazy"
      width="200"
      height="200"
      sizes="auto, (max-width: 30em) 100vw, (max-width: 50em) 50vw, calc(33vw - 100px)"
      srcset="
        swing-200.jpg   200w,
        swing-400.jpg   400w,
        swing-800.jpg   800w,
        swing-1600.jpg 1600w
      "
      src="swing-400.jpg"
      alt="Kettlebell Swing" />
    ```

- `src`
  - : URL تصویر. حداقل یکی از `src` و [`srcset`](#srcset) برای عنصر `<img>` الزامی است. اگر [`srcset`](#srcset) مشخص شده باشد، `src` به یکی از دو روش زیر استفاده می‌شود:
    - به‌عنوان پشتیبان برای مرورگرهایی که از `srcset` پشتیبانی نمی‌کنند.
    - اگر `srcset` از توصیف‌گر "x" استفاده کند، آن‌گاه `src` معادل منبعی با توصیف‌گر چگالی `1x` است؛ یعنی تصویر مشخص‌شده توسط `src` در نمایشگرهای با چگالی پایین (مانند نمایشگرهای معمولی 72 DPI یا 96 DPI) استفاده می‌شود.

- `srcset`
  - : یک یا چند رشته که با کاما جدا شده‌اند و منابع تصویر ممکن را برای عامل کاربر مشخص می‌کنند.

هر رشته از موارد زیر تشکیل شده است:
1. یک URL به تصویر
2. به صورت اختیاری، یک فضای خالی و سپس یکی از موارد زیر:
   - یک توصیف‌گر عرض (یک عدد صحیح مثبت که بلافاصله پس از آن `w` می‌آید). این توصیف‌گر _باید_ با عرض ذاتی تصویر ارجاع‌شده مطابقت داشته باشد. برای محاسبه‌ی تراکم پیکسلی مؤثر، توصیف‌گر عرض بر اندازه‌ی منبع داده‌شده در ویژگی `sizes` تقسیم می‌شود. برای مثال، برای ارائه‌ی یک منبع تصویر که وقتی نمایش‌دهنده نیاز به تصویری با عرض ۴۵۰ پیکسل دارد استفاده شود، از توصیف‌گر عرض `450w` استفاده کنید. وقتی `srcset` شامل توصیف‌گرهای "w" باشد، مرورگر آن توصیف‌گرها را همراه با ویژگی `sizes` برای انتخاب یک منبع به کار می‌برد.
   - یک توصیف‌گر تراکم پیکسلی (یک عدد اعشاری مثبت که بلافاصله پس از آن `x` می‌آید). شرطی را مشخص می‌کند که در آن باید از منبع تصویر متناظر بر اساس تراکم پیکسلی نمایشگر استفاده شود. برای مثال، برای ارائه‌ی یک منبع تصویر که وقتی تراکم پیکسلی دو برابر تراکم استاندارد است استفاده شود، از توصیف‌گر تراکم پیکسلی `2x` یا `2.0x` استفاده کنید.

اگر هیچ توصیف‌گری مشخص نشود، به منبع توصیف‌گر پیش‌فرض `1x` اختصاص می‌یابد. ترکیب توصیف‌گرهای عرض و توصیف‌گرهای تراکم پیکسلی در یک ویژگی `srcset` اشتباه است. توصیف‌گرهای تکراری (مثلاً دو منبع در یک `srcset` که هر دو با `2x` توصیف شده‌اند) نیز نامعتبر هستند.

کاراکترهای فاصله، به جز فضای خالی که URL و توصیف‌گر شرطی را جدا می‌کند، نادیده گرفته می‌شوند؛ این شامل فضای ابتدا و انتها و همچنین فاصله قبل یا بعد از هر ویرگول می‌شود. با این حال، اگر یک رشته‌ی گزینه‌ی تصویر فاقد توصیف‌گر باشد و هیچ فاصله‌ای پس از URL نداشته باشد، رشته‌ی گزینه‌ی تصویر بعدی (در صورت وجود) باید با یک یا چند فضای خالی آغاز شود، در غیر این صورت ویرگول بخشی از URL در نظر گرفته می‌شود.

زمانی که `srcset` عنصر `<img>` از توصیف‌گرهای `x` استفاده می‌کند، مرورگرها URL درون ویژگی `src` (در صورت وجود) را نیز به‌عنوان یک گزینه در نظر می‌گیرند و توصیف‌گر پیش‌فرض `1x` را به آن اختصاص می‌دهند. از طرف دیگر، اگر ویژگی `srcset` از توصیف‌گرهای عرض استفاده کند، `src` در نظر گرفته نمی‌شود و در عوض از ویژگی `sizes` استفاده می‌شود.

نماینده‌ی کاربر (user agent) هر یک از منابع موجود را بنا به صلاحدید خود انتخاب می‌کند. این امر آزادی عمل قابل‌توجهی برای تطبیق انتخاب بر اساس عواملی مانند ترجیحات کاربر یا شرایط پهنای باند فراهم می‌کند. برای یک نمونه، آموزش [تصاویر واکنش‌گرا](/en-US/docs/Web/HTML/Guides/Responsive_images) را ببینید.

- `width`
  - : عرض ذاتی تصویر به پیکسل. باید یک عدد صحیح بدون واحد باشد.
- `usemap`
  - : بخشی از URL (که با `#` شروع می‌شود) از یک [نقشه‌ی تصویری](/en-US/docs/Web/HTML/Reference/Elements/map) مرتبط با عنصر.

    > [!NOTE]
    > اگر عنصر `<img>` درون یک عنصر `<a>` یا `<button>` باشد، نمی‌توانید از این ویژگی استفاده کنید.

### ویژگی‌های منسوخ‌شده

- `align` {{deprecated_inline}}
  - : تصویر را نسبت به متن اطرافش تراز می‌کند. به‌جای این ویژگی از خصوصیات CSS مانند {{cssxref('float')}} و/یا {{cssxref('vertical-align')}} استفاده کنید. مقادیر مجاز:
    - `top`
      - : معادل `vertical-align: top` یا `vertical-align: text-top`
    - `middle`
      - : معادل `vertical-align: -moz-middle-with-baseline`
    - `bottom`
      - : پیش‌فرض، معادل `vertical-align: unset` یا `vertical-align: initial`
    - `left`
      - : معادل `float: left`
    - `right`
      - : معادل `float: right`

- `border` {{deprecated_inline}}
  - : عرض حاشیهٔ دور تصویر. به‌جای آن از ویژگی {{cssxref('border')}} {{glossary("CSS")}} استفاده کنید.
- `hspace` {{deprecated_inline}}
  - : تعداد پیکسل فضای خالی سمت چپ و راست تصویر. به‌جای آن از ویژگی {{cssxref('margin')}} در CSS استفاده کنید.
- `longdesc` {{deprecated_inline}}
  - : لینکی به توصیف مفصل‌تر تصویر. مقدار مجاز یک {{glossary("URL")}} یا یک [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) از یک عنصر است.

    > [!NOTE]
    > این attribute طبق [HTML spec](https://html.spec.whatwg.org/multipage/obsolete.html#element-attrdef-img-longdesc) منسوخ محسوب می‌شود و آیندهٔ مشخصی ندارد؛ توسعه‌دهندگان باید از جایگزینی مبتنی بر {{glossary("WAI")}}-{{glossary("ARIA")}} مثل [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) یا [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details) استفاده کنند.

- `name` {{deprecated_inline}}
  - : یک نام برای عنصر. به‌جای آن از ویژگی [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) استفاده کنید.
- `vspace` {{deprecated_inline}}
  - : تعداد پیکسل فضای خالی بالا و پایین تصویر. به‌جای آن از ویژگی {{cssxref('margin')}} در CSS استفاده کنید.

## استایل‌دهی با CSS

`<img>` یک {{ glossary("replaced elements", "عنصر جایگزین‌شده")}} است؛ به‌طور پیش‌فرض مقدار {{cssxref("display")}} آن `inline` است، اما ابعاد پیش‌فرض آن بر اساس مقادیر ذاتی تصویر تعیین می‌شود، شبیه به `inline-block`. می‌توانید ویژگی‌هایی مانند {{cssxref("border")}}/{{cssxref("border-radius")}}، {{cssxref("padding")}}/{{cssxref("margin")}}، {{cssxref("width")}}، {{cssxref("height")}} و غیره را روی تصویر تنظیم کنید.

`<img>` خط پایه (baseline) ندارد، بنابراین اگر تصاویر در یک بافت inline با {{cssxref("vertical-align", "vertical-align: baseline")}} استفاده شوند، پایین تصویر روی خط پایهٔ متن قرار می‌گیرد.

می‌توانید با ویژگی {{cssxref("object-position")}} موقعیت تصویر را درون جعبهٔ عنصر تنظیم کنید و با {{cssxref("object-fit")}} اندازه‌بندی تصویر را درون جعبه کنترل کنید (مثلاً اینکه تصویر داخل جعبه جای بگیرد یا حتی با برش، جعبه را پر کند).

بسته به نوع تصویر، ممکن است عرض و ارتفاع ذاتی داشته باشد. اما برای برخی انواع تصویر، ابعاد ذاتی ضروری نیستند. برای نمونه، تصاویر {{glossary("SVG")}} اگر عنصر ریشهٔ {{SVGElement("svg")}} آن‌ها `width` یا `height` نداشته باشد، ابعاد ذاتی ندارند.

## دسترسی‌پذیری

### نوشتن متن‌های جایگزین معنادار

مقدار ویژگی `alt` باید جایگزینی متنی روشن و مختصر برای محتوای تصویر ارائه دهد. این مقدار نباید حضور خود تصویر یا نام فایل آن را توصیف کند. اگر عمداً `alt` را حذف کرده‌اید چون تصویر معادل متنی ندارد، روش‌های جایگزین برای انتقال مفهوم تصویر را در نظر بگیرید.

#### نمونهٔ نامناسب

```html example-bad
<img alt="image" src="penguin.jpg" />
```

#### نمونهٔ مناسب

```html example-good
<img alt="یک پنگوئن در ساحل." src="penguin.jpg" />
```

یک آزمون مهم دسترسی‌پذیری این است که محتوای `alt` را همراه با متن قبل از آن بخوانید و ببینید آیا همان معنای تصویر را منتقل می‌کند. مثلاً اگر قبل از تصویر جملهٔ «در سفرهایم، حیوان کوچک بامزه‌ای دیدم:» باشد، نمونهٔ نامناسب توسط صفحه‌خوان اینطور خوانده می‌شود: «در سفرهایم، حیوان کوچک بامزه‌ای دیدم: image» که معنی ندارد. نمونهٔ مناسب اینطور خوانده می‌شود: «در سفرهایم، حیوان کوچک بامزه‌ای دیدم: یک پنگوئن در ساحل.» که معنی‌دار است.

برای تصاویری که برای اجرای یک عمل استفاده می‌شوند، مثلاً تصاویری که داخل یک `<a>` یا `<button>` قرار دارند، بهتر است عمل انجام‌شده را داخل مقدار attributeِ `alt` توضیح دهید. برای نمونه می‌توانید بنویسید `alt="next page"` به‌جای `alt="arrow right"`. همچنین می‌توانید یک توضیح اضافی اختیاری داخل attributeِ `title` قرار دهید؛ این متن ممکن است توسط screen readerها در صورت درخواست کاربر خوانده شود.

وقتی یک تصویر attributeِ `alt` نداشته باشد، بعضی screen readerها ممکن است نام فایل تصویر را به‌جای آن اعلام کنند. اگر نام فایل بیانگر محتوای تصویر نباشد، این می‌تواند تجربه‌ای گیج‌کننده ایجاد کند.

- [An alt Decision Tree • Images • WAI Web Accessibility Tutorials](https://www.w3.org/WAI/tutorials/images/decision-tree/)
- [Alt-texts: The Ultimate Guide — Axess Lab](https://axesslab.com/alt-texts/)
- [How to Design Great Alt Text: An Introduction | Deque](https://www.deque.com/blog/great-alt-text-introduction/)
- [MDN Understanding WCAG, Guideline 1.1 explanations](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable#guideline_1.1_—_providing_text_alternatives_for_non-text_content)
- [Understanding Success Criterion 1.1.1 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/text-equiv-all.html)

### شناسایی SVG به‌عنوان تصویر

به دلیل یک [باگ VoiceOver](https://webkit.org/b/216364)، VoiceOver تصاویر SVG را به‌درستی به‌عنوان تصویر اعلام نمی‌کند. برای اطمینان از اینکه فناوری‌های کمکی تصاویر SVG را به‌عنوان محتوای تصویری تشخیص دهند، به تمام `<img>`هایی که فایل SVG بارگذاری می‌کنند، [`role="img"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/img_role) اضافه کنید.

```html
<img src="mdn.svg" alt="MDN" role="img" />
```

### attributeِ `title`

attributeِ [`title`](/en-US/docs/Web/HTML/Reference/Global_attributes/title) جایگزین مناسبی برای attributeِ `alt` نیست. همچنین از تکرار مقدار `alt` در attributeِ `title` برای یک تصویر خودداری کنید. این کار ممکن است باعث شود بعضی screen readerها همان متن را دوبار بخوانند که تجربه‌ای گیج‌کننده خواهد بود.

attributeِ `title` همچنین نباید به‌عنوان اطلاعات توضیحی کمکی همراه با متن جایگزین تصویر استفاده شود. اگر تصویری به caption نیاز دارد، از elementهای [`figure`](/en-US/docs/Web/HTML/Reference/Elements/figure) و [`figcaption`](/en-US/docs/Web/HTML/Reference/Elements/figcaption) استفاده کنید.

مقدار attributeِ `title` معمولاً به شکل tooltip به کاربر نمایش داده می‌شود که کمی پس از توقف نشانگر روی تصویر ظاهر می‌شود. گرچه این _می‌تواند_ اطلاعات بیشتری در اختیار کاربر بگذارد، نباید فرض کنید کاربر حتماً آن را می‌بیند: کاربر ممکن است فقط از صفحه‌کلید یا صفحه لمسی استفاده کند. اگر اطلاعاتی دارید که برای کاربر مهم یا ارزشمند است، به‌جای استفاده از `title`، آن را با یکی از روش‌های ذکر‌شده در متن ارائه دهید.

- [Using the HTML title attribute – updated | Vispero](https://vispero.com/resources/using-the-html-title-attribute-updated/)

## مثال‌ها

### متن جایگزین

مثال زیر تصویری را در صفحه قرار می‌دهد و متن جایگزین را برای دسترسی‌پذیری در نظر می‌گیرد.

```html
<img src="/shared-assets/images/examples/favicon144.png" alt="MDN" />
```

### لینک تصویری

این مثال نسخه‌ای از مثال قبلی است که نحوه تبدیل تصویر به لینک را نشان می‌دهد. برای این کار، تگ `<img>` را داخل `<a>` قرار دهید. بهتر است متن جایگزین، منبعی که لینک به آن اشاره می‌کند را توصیف کند، انگار که به‌جای تصویر از یک لینک متنی استفاده می‌کردید.

```html
<a href="https://developer.mozilla.org">
  <img
    src="/shared-assets/images/examples/favicon144.png"
    alt="Visit the MDN site" />
</a>
```

### استفاده از attributeِ srcset

در این مثال یک ویژگی `srcset` با ارجاع به نسخهٔ با وضوح بالای لوگو قرار داده‌ایم؛ این نسخه در دستگاه‌های با وضوح بالا به‌جای تصویر `src` بارگذاری می‌شود. در user agent‌هایی که از `srcset` پشتیبانی می‌کنند، تصویر مشخص‌شده در ویژگی `src` به‌عنوان یک گزینهٔ `1x` در نظر گرفته می‌شود.

```html
<img
  src="/shared-assets/images/examples/favicon72.png"
  alt="MDN"
  srcset="/shared-assets/images/examples/favicon144.png 2x" />
```

### استفاده از ویژگی‌های srcset و sizes

در user agent‌هایی که از `srcset` پشتیبانی می‌کنند، وقتی توصیف‌گرهای `w` حضور داشته باشند، ویژگی `src` نادیده گرفته می‌شود. هنگامی که شرط مدیای `(width <= 600px)` برقرار باشد، تصویری با پهنای ۲۰۰ پیکسل بارگذاری می‌شود (چون نزدیک‌ترین تطابق با `200px` است)؛ در غیر این‌صورت تصویر دیگر بارگذاری خواهد شد.

```html
<img
  src="clock-demo-200px.png"
  alt="The time is 12:45."
  srcset="clock-demo-200px.png 200w, clock-demo-400px.png 400w"
  sizes="(width <= 600px) 200px, 50vw" />
```

> [!NOTE]
> برای دیدن نحوهٔ تغییر اندازه در عمل، مثال را در صفحه‌ای جداگانه باز کنید تا بتوانید اندازهٔ ناحیهٔ محتوا را تغییر دهید.

## نگرانی‌های امنیتی و حریم خصوصی

اگرچه عناصر `<img>` کاربردهای بی‌ضرری دارند، می‌توانند پیامدهای ناخواسته‌ای برای امنیت و حریم خصوصی کاربر داشته باشند. برای اطلاعات بیشتر و راه‌های کاهش خطر، به [Referer header: privacy and security concerns](/en-US/docs/Web/Privacy/Guides/Referer_header:_privacy_and_security_concerns) مراجعه کنید.

## خلاصهٔ فنی

```html
<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories"
          >دسته‌بندی‌های محتوا</a
        >
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >محتوای جریانی</a
        >,
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >محتوای عبارتی</a
        >,
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#embedded_content"
          >محتوای جاسازی‌شده</a
        >,
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#palpable_content"
          >محتوای محسوس</a
        >. اگر عنصر دارای ویژگی <code>usemap</code> باشد، همچنین بخشی از دسته محتوای تعاملی است.
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>مجاز نیست؛ یک عنصر void است.</td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>باید تگ شروع داشته باشد و نباید تگ پایان داشته باشد.</td>
    </tr>
    <tr>
      <th scope="row">والدهای مجاز</th>
      <td>هر عنصری که محتوای جاسازی‌شده را می‌پذیرد.</td>
    </tr>
    <tr>
      <th scope="row">نقش ضمنی ARIA</th>
      <td>
        <ul>
          <li>
            با ویژگی <code>alt</code> غیرخالی یا بدون ویژگی <code>alt</code>:
            <code
              ><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/img_role"
                ><code>img</code></a
              ></code
            >
          </li>
          <li>
            با ویژگی <code>alt</code> خالی:
            <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role"
              ><code>presentation</code></a
            >
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های مجاز ARIA</th>
      <td>
        <ul>
          <li>
            با ویژگی <code>alt</code> غیرخالی:
            <ul>
              <li>
                <code
                  ><a
                    href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role"
                    >button</a
                  ></code
                >
              </li>
              <li>
                <code
                  ><a
                    href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role"
                    >checkbox</a
                  ></code
                >
              </li>
              <li><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/link_role"><code>link</code></a></li>
              <li><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role"><code>menuitem</code></a></li>
              <li><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role"><code>menuitemcheckbox</code></a></li>
              <li><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role"><code>menuitemradio</code></a></li>
              <li><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role"><code>option</code></a></li>
              <li><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/progressbar_role"><code>progressbar</code></a></li>
              <li><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/scrollbar_role"><code>scrollbar</code></a></li>
              <li><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/separator_role"><code>separator</code></a></li>
              <li><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role"><code>slider</code></a></li>
              <li>
                <code
                  ><a
                    href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/switch_role"
                    >switch</a
                  ></code
                >
              </li>
              <li>
                <code
                  ><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role"
                    >tab</a
                  ></code
                >
              </li>
              <li><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treeitem_role"><code>treeitem</code></a></li>
            </ul>
          </li>
          <li>
            با ویژگی <code>alt</code> خالی: <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role"><code>none</code></a>
            یا <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role"><code>presentation</code></a>
          </li>
          <li>
            بدون ویژگی <code>alt</code>، هیچ <code>role</code>‌ای مجاز نیست.
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td>{{domxref("HTMLImageElement")}}</td>
    </tr>
  </tbody>
</table>
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- عناصر {{HTMLElement("picture")}}، {{HTMLElement("object")}} و {{HTMLElement("embed")}}
- {{cssxref("object-fit")}}، {{cssxref("object-position")}}، {{cssxref("image-orientation")}}، {{cssxref("image-rendering")}} و {{cssxref("image-resolution")}}: پراپرتی‌های CSS مرتبط با تصویر
- رابط {{domxref("HTMLImageElement")}} برای این عنصر
- [تصاویر در HTML](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_images)
- [راهنمای انواع فایل و فرمت تصویر](/en-US/docs/Web/Media/Guides/Formats/Image_types)
- [تصاویر واکنش‌گرا](/en-US/docs/Web/HTML/Guides/Responsive_images)