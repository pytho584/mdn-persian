---
title: "<img> HTML image embed element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/img"
translated_by: "n8n + AI"
---

# عنصر `<img>` در HTML

عنصر **`<img>`** در HTML یک تصویر را داخل سند جاسازی می‌کند.

مثال زیر کاربرد این عنصر را نشان می‌دهد:

```html
<img
  class="fit-picture"
  src="/shared-assets/images/examples/grapefruit-slice.jpg"
  alt="Grapefruit slice atop a pile of other slices" />
```

```css
.fit-picture {
  width: 250px;
}
```

در مثال بالا:

- ویژگی `src` مسیر تصویری را که می‌خواهید نمایش دهید نگه می‌دارد. این ویژگی در صورتی که ویژگی `srcset` موجود باشد اجباری نیست؛ اما حداقل یکی از `src` یا `srcset` باید حتماً ارائه شود.
- ویژگی `alt` یک متن جایگزین برای تصویر است. این ویژگی اجباری و برای دسترس‌پذیری **بسیار مفید** است — صفحه‌خوان‌ها (screen reader) مقدار این ویژگی را برای کاربرانشان می‌خوانند تا بدانند تصویر چه معنایی دارد. همچنین اگر تصویر به هر دلیلی بارگذاری نشود — مثلاً به خاطر خطای شبکه، مسدود شدن محتوا یا خراب شدن لینک — متن `alt` در صفحه نمایش داده می‌شود.

ویژگی‌های زیادی برای اهداف مختلف وجود دارند:

- کنترل [Referrer](/en-US/docs/Web/HTTP/Reference/Headers/Referrer-Policy) و {{glossary("CORS")}} برای امنیت و حریم خصوصی: به [`crossorigin`](#crossorigin) و [`referrerpolicy`](#referrerpolicy) مراجعه کنید.
- از [`width`](#width) و [`height`](#height) برای تعیین اندازه ذاتی تصویر استفاده کنید تا قبل از بارگذاری، فضای لازم را اشغال کند و از جابه‌جایی چیدمان محتوا (content layout shifts) جلوگیری شود.
- برای تصاویر واکنش‌گرا از [`sizes`](#sizes) و [`srcset`](#srcset) استفاده کنید (همچنین به عنصر {{htmlelement("picture")}} و آموزش [تصاویر واکنش‌گرا](/en-US/docs/Web/HTML/Guides/Responsive_images) مراجعه کنید).

## فرمت‌های تصویر پشتیبانی‌شده

استاندارد HTML فهرست مشخصی از فرمت‌های تصویر را اجباری نمی‌کند؛ بنابراین هر {{glossary("user agent","user agent")}} ممکن است از فرمت‌های متفاوتی پشتیبانی کند.

> [!NOTE]
> راهنمای [فرمت‌ها و انواع فایل تصویری](/en-US/docs/Web/Media/Guides/Formats/Image_types) اطلاعات کاملی درباره فرمت‌های تصویر و پشتیبانی آن‌ها در مرورگرها ارائه می‌دهد. این بخش فقط یک خلاصه است.

فرمت‌هایی که بیشتر در وب استفاده می‌شوند عبارتند از:

- [APNG (Animated Portable Network Graphics)](/en-US/docs/Web/Media/Guides/Formats/Image_types#apng_animated_portable_network_graphics) — انتخاب خوبی برای انیمیشن بدون اتلاف کیفیت (GIF کارایی کمتری دارد).
- [AVIF (AV1 Image File Format)](/en-US/docs/Web/Media/Guides/Formats/Image_types#avif_image) — به دلیل کارایی بالا، انتخابی عالی برای تصاویر ثابت و متحرک است.
- [GIF (Graphics Interchange Format)](/en-US/docs/Web/Media/Guides/Formats/Image_types#gif_graphics_interchange_format) — انتخاب خوبی برای تصاویر و انیمیشن‌های _ساده_.
- [JPEG (Joint Photographic Expert Group image)](/en-US/docs/Web/Media/Guides/Formats/Image_types#jpeg_joint_photographic_experts_group_image) — انتخاب خوبی برای فشرده‌سازی با اتلاف تصاویر ثابت (در حال حاضر محبوب‌ترین فرمت).
- [PNG (Portable Network Graphics)](/en-US/docs/Web/Media/Guides/Formats/Image_types#png_portable_network_graphics) — انتخاب خوبی برای فشرده‌سازی بدون اتلاف تصاویر ثابت (کیفیت کمی بهتر از JPEG).
- [SVG (Scalable Vector Graphics)](/en-US/docs/Web/Media/Guides/Formats/Image_types#svg_scalable_vector_graphics) — فرمت برداری. برای تصاویری که باید در اندازه‌های مختلف با دقت نمایش داده شوند مناسب است.
- [WebP (Web Picture format)](/en-US/docs/Web/Media/Guides/Formats/Image_types#webp_image) — انتخابی عالی برای تصاویر ثابت و متحرک.

فرمت‌هایی مانند [WebP](/en-US/docs/Web/Media/Guides/Formats/Image_types#webp_image) و [AVIF](/en-US/docs/Web/Media/Guides/Formats/Image_types#avif_image) توصیه می‌شوند، زیرا برای تصاویر ثابت و متحرک عملکرد بسیار بهتری نسبت به PNG، JPEG و GIF دارند.

SVG همچنان فرمت پیشنهادی برای تصاویری است که باید در اندازه‌های مختلف با دقت ترسیم شوند.

## خطاهای بارگذاری تصویر

اگر هنگام بارگذاری یا رندر تصویر خطایی رخ دهد و یک event handler با نام `onerror` برای رویداد `error` تنظیم شده باشد، آن event handler فراخوانی می‌شود. این اتفاق در چند موقعیت ممکن است رخ دهد، از جمله:

- attributeهای `src` یا `srcset` خالی (`""`) یا `null` باشند.
- URL مربوط به `src` همان URL صفحه‌ای باشد که کاربر در آن قرار دارد.
- تصویر به نحوی خراب باشد که بارگذاری آن ممکن نباشد.
- متادیتای تصویر به شکلی خراب باشد که دریافت ابعاد تصویر غیرممکن باشد و ابعادی هم در attributeهای element `<img>` مشخص نشده باشد.
- فرمت تصویر توسط user agent پشتیبانی نشود.

## Attributes

این element شامل [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- `alt`
  - : متنی را تعریف می‌کند که می‌تواند جایگزین تصویر در صفحه شود.

    > [!NOTE]
    > مرورگرها همیشه تصاویر را نمایش نمی‌دهند. موقعیت‌های مختلفی وجود دارد که ممکن است مرورگر تصویر را نمایش ندهد، مانند:
    >
    > - مرورگرهای غیرتصویری (مانند مرورگرهایی که افراد دارای اختلال بینایی استفاده می‌کنند)
    > - کاربر ترجیح دهد تصاویر را نمایش ندهد (برای صرفه‌جویی در پهنای باند یا دلایل حریم خصوصی)
    > - تصویر نامعتبر باشد یا از نوع [پشتیبانی‌نشده](#supported_image_formats) باشد.
    >
    > در این موارد، مرورگر ممکن است تصویر را با متن موجود در attribute `alt` آن element جایگزین کند. به این دلایل و دلایل دیگر، هر زمان که امکان دارد یک مقدار مفید برای `alt` در نظر بگیرید.

    تنظیم این attribute روی رشته خالی (`alt=""`) نشان می‌دهد که این تصویر _بخش کلیدی_ محتوا نیست (تزئینی است یا یک پیکسل ردیابی) و مرورگرهای غیرتصویری ممکن است آن را در rendering نادیده بگیرند. اگر `alt` خالی باشد و تصویر نمایش داده نشود، مرورگرهای تصویری نیز آیکون تصویر شکسته را مخفی می‌کنند.

    این attribute همچنین هنگام کپی و چسباندن تصویر به صورت متن، یا ذخیره کردن یک تصویر لینک‌شده به عنوان نشانک (bookmark) استفاده می‌شود.

- `attributionsrc` (منسوخ) (غیراستاندارد)
  - : مشخص می‌کند که می‌خواهید مرورگر یک هدر `Attribution-Reporting-Eligible` همراه با درخواست تصویر ارسال کند.

    در سمت سرور، از این هدر برای راه‌اندازی ارسال هدر `Attribution-Reporting-Register-Source` یا `Attribution-Reporting-Register-Trigger` در پاسخ استفاده می‌شود، به ترتیب برای ثبت یک [attribution source](/en-US/docs/Web/API/Attribution_Reporting_API/Registering_sources#html-based_event_sources) مبتنی بر تصویر یا [attribution trigger](/en-US/docs/Web/API/Attribution_Reporting_API/Registering_triggers#html-based_attribution_triggers). اینکه کدام هدر پاسخ باید برگردانده شود، به مقدار هدر `Attribution-Reporting-Eligible` بستگی دارد که باعث ثبت شده است.

    هنگامی که مرورگر پاسخ حاوی فایل تصویر را دریافت کند، رویداد منبع یا trigger متناظر فعال می‌شود.

    > [!NOTE]
    > برای جزئیات بیشتر به [Attribution Reporting API](/en-US/docs/Web/API/Attribution_Reporting_API) مراجعه کنید.

    این attribute دو نسخه دارد که می‌توانید تنظیم کنید:
    - بولی؛ یعنی فقط نام `attributionsrc`. این مشخص می‌کند که می‌خواهید هدر `Attribution-Reporting-Eligible` به همان سروری ارسال شود که attribute `src` به آن اشاره می‌کند. این زمانی مناسب است که ثبت attribution source یا trigger را روی همان سرور انجام می‌دهید. هنگام ثبت یک attribution trigger این ویژگی اختیاری است و اگر حذف شود، یک مقدار بولی استفاده خواهد شد.
    - مقداری شامل یک یا چند URL، برای مثال:

    ```html
    <img
      src="image-file.png"
      alt="My image file description"
      attributionsrc="https://a.example/register-source
                         https://b.example/register-source" />
    ```

این قابلیت در مواردی مفید است که منبع درخواست‌شده روی سروری که کنترل آن را ندارید قرار ندارد، یا فقط می‌خواهید ثبت منبع انتساب را روی سرور دیگری مدیریت کنید. در چنین حالتی، می‌توانید یک یا چند URL را به‌عنوان مقدار `attributionsrc` مشخص کنید. وقتی درخواست منبع انجام می‌شود، هدر `Attribution-Reporting-Eligible` علاوه بر مبدأ منبع، به URL(های) مشخص‌شده در `attributionSrc` ارسال می‌شود. این URLها می‌توانند با هدر `Attribution-Reporting-Register-Source` یا `Attribution-Reporting-Register-Trigger` پاسخ دهند و فرایند ثبت را کامل کنند.

> [!NOTE]
> تعیین چند URL به این معنی است که می‌توان چند منبع انتساب را روی یک قابلیت ثبت کرد. برای مثال، ممکن است کمپین‌های متفاوتی داشته باشید که می‌خواهید موفقیت آن‌ها را اندازه بگیرید و این کمپین‌ها گزارش‌های متفاوتی روی داده‌های مختلف تولید می‌کنند.

- [`crossorigin`](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin)
  - : مشخص می‌کند که آیا دریافت تصویر باید با درخواست CORS انجام شود یا خیر. داده‌های تصویری که از یک [CORS-enabled image](/en-US/docs/Web/HTML/How_to/CORS_enabled_image) و در پاسخ به درخواست CORS برگردانده شده‌اند، می‌توانند بدون اینکه «[tainted](/en-US/docs/Web/HTML/How_to/CORS_enabled_image#security_and_tainted_canvases)» علامت‌گذاری شوند، در عنصر `<canvas>` استفاده شوند.

    اگر ویژگی `crossorigin` _تنظیم نشده باشد_، درخواست غیر-CORS ارسال می‌شود (بدون هدر درخواست `Origin`) و مرورگر تصویر را به‌عنوان tainted علامت‌گذاری کرده و دسترسی به داده‌های تصویر را محدود می‌کند و در نتیجه استفاده از آن در عناصر `<canvas>` را جلوگیری می‌کند.

    اگر ویژگی `crossorigin` _تنظیم شده باشد_، درخواست CORS ارسال می‌شود (با هدر درخواست `Origin`)؛ اما اگر سرور با اجازه‌دادن به دسترسی cross-origin به داده‌های تصویر برای سایت مبدأ موافقت نکند (با ارسال نکردن هیچ هدر پاسخ `Access-Control-Allow-Origin`، یا با درج نکردن مبدأ سایت در هدرهای پاسخ `Access-Control-Allow-Origin` که ارسال می‌کند)، مرورگر بارگذاری تصویر را مسدود کرده و خطای CORS را در کنسول devtools ثبت می‌کند.

    مقادیر مجاز:
    - `anonymous`
      - : درخواست CORS بدون credentials ارسال می‌شود (یعنی بدون کوکی، گواهینامهٔ X.509 یا هدر درخواست `Authorization`).
    - `use-credentials`
      - : درخواست CORS با همهٔ credentials ارسال می‌شود (یعنی کوکی‌ها، گواهینامه‌های X.509 و هدر درخواست `Authorization`). اگر سرور با اشتراک‌گذاری credentials با سایت مبدأ موافقت نکند (با ارسال هدر پاسخ `Access-Control-Allow-Credentials: true`)، مرورگر تصویر را tainted علامت‌گذاری کرده و دسترسی به داده‌های تصویر را محدود می‌کند.

    اگر مقدار ویژگی نامعتبر باشد، مرورگرها طوری رفتار می‌کنند که گویی مقدار `anonymous` استفاده شده است. برای اطلاعات بیشتر به [CORS settings attributes](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin) مراجعه کنید.

- `decoding`
  - : این ویژگی به مرورگر پیشنهاد می‌دهد که آیا رمزگشایی تصویر را همراه با رندر سایر محتوای DOM در یک مرحله ارائه انجام دهد که به نظر «درست‌تر» می‌رسد (`sync`)، یا ابتدا سایر محتوای DOM را رندر و نمایش دهد، سپس تصویر را رمزگشایی و بعداً نمایش دهد (`async`). در عمل، `async` به این معنی است که `paint` بعدی منتظر رمزگشایی تصویر نمی‌ماند.

اغلب اوقات دیدن تأثیر قابل‌توجهی هنگام استفاده از `decoding` روی عناصر `<img>` ایستا سخت است. این تصاویر احتمالاً ابتدا به‌صورت خالی رندر می‌شوند در حالی که فایل تصویر (از شبکه یا حافظهٔ نهان) دریافت می‌شود و سپس به‌طور مستقل مدیریت می‌شوند، بنابراین «همگام‌سازی» به‌روزرسانی‌های محتوا کمتر مشخص است. با این حال، مسدود شدن رندر در حین دیکد کردن (decoding) — هرچند اغلب بسیار کوچک است — _قابل اندازه‌گیری_ است، حتی اگر مشاهده آن با چشم انسان دشوار باشد. برای تحلیل دقیق‌تر به [What does the image decoding attribute actually do?](https://www.tunetheweb.com/blog/what-does-the-image-decoding-attribute-actually-do/) مراجعه کنید (tunetheweb.com, 2023).

استفاده از انواع مختلف `decoding` می‌تواند هنگام درج پویای عناصر `<img>` در DOM از طریق JavaScript تفاوت‌های محسوس‌تری ایجاد کند — برای جزئیات بیشتر به {{domxref("HTMLImageElement.decoding")}} مراجعه کنید.

مقادیر مجاز:

- `sync`
  - : تصویر را هم‌زمان با رندر محتوای DOM دیگر دیکد کرده و همه را با هم نمایش دهید.
- `async`
  - : تصویر را به‌صورت ناهم‌زمان (asynchronous) و پس از رندر و نمایش محتوای DOM دیگر دیکد کنید.
- `auto`
  - : ترجیحی برای حالت دیکد وجود ندارد؛ مرورگر تصمیم می‌گیرد چه چیزی برای کاربر بهترین است. این مقدار پیش‌فرض است.

- [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming)
  - : تصویر را برای مشاهده توسط API {{domxref("PerformanceElementTiming")}} علامت‌گذاری می‌کند. مقدار داده شده شناسه‌ای برای عنصر تصویر تحت نظر می‌شود. همچنین به صفحهٔ attribute [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming) مراجعه کنید.

- [`fetchpriority`](/en-US/docs/Web/HTML/Reference/Attributes/fetchpriority)
  - : راهنمایی برای اولویت نسبی هنگام دریافت (fetch) تصویر ارائه می‌دهد. مقادیر مجاز:
    - `high`
      - : تصویر را با اولویت بالا نسبت به تصاویر دیگر دریافت کنید.
    - `low`
      - : تصویر را با اولویت پایین نسبت به تصاویر دیگر دریافت کنید.
    - `auto`
      - : اولویت واکشی را تنظیم نکنید. این مقدار پیش‌فرض است. اگر مقداری تنظیم نشود یا مقدار نامعتبر باشد، استفاده می‌شود.

- `height`
  - : ارتفاع ذاتی تصویر بر حسب پیکسل. باید یک عدد صحیح بدون واحد باشد.

    > [!NOTE]
    > درج `height` و [`width`](#width) به مرورگر امکان می‌دهد تا نسبت ابعاد (aspect ratio) تصویر را قبل از بارگذاری تصویر محاسبه کند. این نسبت ابعاد برای ذخیره فضای لازم برای نمایش تصویر استفاده می‌شود و در نتیجه تغییر چیدمان (layout shift) هنگام دانلود و رنگ‌آمیزی تصویر بر روی صفحه کاهش می‌یابد یا حتی از آن جلوگیری می‌کند. کاهش تغییر چیدمان یکی از مؤلفه‌های اصلی تجربه کاربری خوب و عملکرد وب است.

- `ismap`
  - : این attribute از نوع Boolean نشان می‌دهد که تصویر بخشی از یک [نقشه سمت سرور (server-side map)](https://en.wikipedia.org/wiki/Image_map#Server-side) است. اگر چنین باشد، مختصات جایی که کاربر روی تصویر کلیک کرده به سرور ارسال می‌شود.

    > [!NOTE]
    > این attribute فقط زمانی مجاز است که عنصر `<img>` فرزند یک عنصر {{htmlelement("a")}} با [`href`](/en-US/docs/Web/HTML/Reference/Elements/a#href) معتبر باشد. این کار به کاربرانی که دستگاه‌های اشاره‌گر (pointing devices) ندارند یک مقصد جایگزین می‌دهد.

- `loading`
  - : نحوه بارگذاری تصویر توسط مرورگر را مشخص می‌کند:
    - `eager`
      - : تصویر را بلافاصله بارگذاری می‌کند، صرف‌نظر از اینکه تصویر در حال حاضر درون {{glossary("visual viewport")}} قرار دارد یا خیر (این مقدار پیش‌فرض است).
    - `lazy`
      - : بارگذاری تصویر را تا رسیدن به فاصله محاسبه‌شده از viewport (مطابق تعریف مرورگر) به تأخیر می‌اندازد.

        بارگذاری تنبل (lazy loading) از پهنای باند شبکه و فضای ذخیره‌سازی لازم برای مدیریت تصویر جلوگیری می‌کند تا زمانی که مطمئن شود تصویر تقریباً مورد نیاز خواهد بود. این کار عملکرد را در اکثر موارد استفاده معمولی بهبود می‌بخشد.

هرچند برای همه تصاویر توصیه می‌شود که attributeهای صریح [`width`](#width) و [`height`](#height) را برای جلوگیری از جابجایی چیدمان (layout shift) تعیین کنید، این کار برای تصاویر با بارگذاری تنبل (lazy-loaded) اهمیت بیشتری دارد. تصاویر lazy-loaded اگر با بخش قابل مشاهده از یک element برخورد نکنند هرگز بارگذاری نمی‌شوند، حتی اگر بارگذاری آن‌ها این وضعیت را تغییر دهد؛ زیرا تصاویر بارگذاری‌نشده دارای `width` و `height` برابر با `0` هستند. این موضوع وقتی محتوای قابل مشاهده در viewport در وسط مطالعه بازچینی (reflow) شود، تجربه کاربری بسیار بدتری ایجاد می‌کند.

تصاویر lazy-loaded که در viewport بصری قرار دارند ممکن است هنوز قابل مشاهده نباشند وقتی رویداد `load` پنجره (Window) رخ می‌دهد. دلیل این است که این رویداد بر اساس تصاویری که بلافاصله بارگذاری می‌شوند (eager-loaded) رخ می‌دهد؛ تصاویر lazy-loaded حتی اگر در بارگذاری اولیه صفحه در viewport بصری باشند، در نظر گرفته نمی‌شوند.

بارگذاری فقط زمانی به تأخیر می‌افتد که JavaScript فعال باشد. این یک اقدام ضد ردیابی (anti-tracking) است؛ زیرا اگر user agent در حالی که اسکریپت غیرفعال است از lazy loading پشتیبانی کند، سایت می‌تواند با قرار دادن تصاویر به شکلی هدفمند در مارکاپ صفحه، موقعیت تقریبی اسکرول کاربر را در طول یک نشست ردیابی کند؛ به این صورت که سرور می‌تواند تعداد تصاویر درخواستی و زمان آن‌ها را ردیابی کند.

- `referrerpolicy`
  - : رشته‌ای که مشخص می‌کند هنگام واکشی منبع (resource) از کدام referrer استفاده شود:
    - `no-referrer`: هدر {{HTTPHeader("Referer")}} ارسال نخواهد شد.
    - `no-referrer-when-downgrade`: هدر {{HTTPHeader("Referer")}} به {{Glossary("origin")}}هایی که فاقد {{Glossary("TLS")}} ({{Glossary("HTTPS")}}) هستند ارسال نمی‌شود.
    - `origin`: referrer ارسالی به origin صفحه ارجاع‌دهنده محدود می‌شود: [scheme](/en-US/docs/Learn_web_development/Howto/Web_mechanics/What_is_a_URL)، {{Glossary("host")}} و {{Glossary("port")}}.
    - `origin-when-cross-origin`: referrer ارسالی به سایر originها به scheme، host و port محدود می‌شود. ناوبری‌های هم‌origin همچنان شامل path خواهند بود.
    - `same-origin`: برای {{Glossary("Same-origin policy", "same origin")}} یک referrer ارسال می‌شود، اما درخواست‌های cross-origin هیچ اطلاعات referrer ندارند.
    - `strict-origin`: فقط زمانی origin سند را به عنوان referrer ارسال کن که سطح امنیت پروتکل یکسان بماند (HTTPS→HTTPS)، اما به مقصد امن‌تر (HTTPS→HTTP) ارسال نکن.
    - `strict-origin-when-cross-origin` (پیش‌فرض): برای درخواست هم‌origin یک URL کامل ارسال کن، فقط زمانی origin را ارسال کن که سطح امنیت پروتکل یکسان باشد (HTTPS→HTTPS)، و به مقصد امن‌تر هیچ هدری ارسال نکن.
    - `unsafe-url`: referrer شامل origin _و_ path می‌شود (اما [fragment](/en-US/docs/Web/API/HTMLAnchorElement/hash)، [password](/en-US/docs/Web/API/HTMLAnchorElement/password) یا [username](/en-US/docs/Web/API/HTMLAnchorElement/username) را شامل نمی‌شود). **این مقدار ناامن است**، زیرا origin و path را از منابع محافظت‌شده با TLS به originهای ناامن نشت می‌دهد.

- `sizes`
  - : یک یا چند مقدار که با کاما از هم جدا می‌شوند؛ این مقادیر می‌توانند source size یا کلیدواژه `auto` باشند. مشخصات فنی (spec) الزام می‌کند که attribute `sizes` فقط زمانی وجود داشته باشد که `srcset` از width descriptor استفاده کند.
    - **source size**
      - : یک **source size** شامل این موارد است:
        1. یک [media condition](/en-US/docs/Web/CSS/Guides/Media_queries/Using#syntax)، که برای آخرین مورد در لیست حذف می‌شود.
        2. یک مقدار source size.

        برای مثال، source size زیر پیشنهاد می‌دهد اگر عرض _viewport_ برابر ۵۰۰px یا کمتر بود، از منبع تصویری با عرض `1000px` استفاده شود.

        ```css
        (width <= 500px) 1000px
        ```

        Media conditionها ویژگی‌های _viewport_ را توصیف می‌کنند، نه _تصویر_ را.
        چون یک توصیفگر source size عرض مورد استفاده برای تصویر در طول layout را مشخص می‌کند، media condition معمولاً (نه لزوماً) بر اساس `@media/width` است.

### مقدار `sizes`

مقادیر اندازه منبع (source size) اندازه نمایشی مورد نظر تصویر را مشخص می‌کنند.  
عامل‌های کاربر (user agents) از اندازه منبع جاری برای انتخاب یکی از منابع ارائه‌شده در attribute `srcset` استفاده می‌کنند، زمانی که آن منابع با توصیف‌کننده‌های عرض (`w`) توصیف شده‌باشند.  
مقدار `w` تعریف‌شده در `sizes`، عرض پیش‌فرض layout تصویر را تعیین می‌کند.  
در نبود CSS، مرورگر تصویر را در این اندازه رندر می‌کند، صرف‌نظر از ابعاد پیکسل فیزیکی فایل دانلودشده.

یک مقدار اندازه منبع می‌تواند هر [طول (length)](/en-US/docs/Web/CSS/Reference/Values/length) غیرمنفی باشد.  
نباید از توابع CSS غیر از [توابع ریاضی (math functions)](/en-US/docs/Web/CSS/Reference/Values/Functions#math_functions) استفاده کند.  
واحدها همانطور که در [media queries](/en-US/docs/Web/CSS/Guides/Media_queries) تفسیر می‌شوند، تفسیر می‌شوند؛ یعنی همه واحدهای طول نسبی (relative length) نسبت به ریشه سند (document root) هستند، نه نسبت به عنصر `<img>`. مثلاً مقدار `em` نسبت به اندازه فونت ریشه است، نه اندازه فونت تصویر. [مقادیر درصدی (percentage)](/en-US/docs/Web/CSS/Reference/Values/percentage) مجاز نیستند. اگر attribute `sizes` ارائه نشود، مقدار پیش‌فرض آن `100vw` (عرض viewport) است.

- `auto`
  - کلیدواژه `auto` نشان می‌دهد که مرورگر باید از عرض layout مورد انتظار عنصر برای انتخاب تصویر نمایشی استفاده کند. یعنی باید از [اندازه واقعی (concrete size)](/en-US/docs/Web/CSS/Reference/Values/image#concrete_size) تصویر استفاده کند، که پس از اعمال layout از HTML و CSS محاسبه می‌شود. این تنها زمانی معتبر است که با `loading="lazy"` ترکیب شود، زیرا انتظار می‌رود تا زمان بارگذاری تصویر، CSS و سایر اطلاعات layout موجود باشند.

    استفاده از `auto` شما را از دوبار مشخص کردن شرایط media layout نجات می‌دهد: یک بار برای layout و یک بار برای انتخاب تصویر مناسب برای دریافت و نمایش.

    اگر `auto` نتواند resolve شود — چه به دلیل عدم پشتیبانی مرورگر، چه به دلیل نداشتن اندازه layout برای تصویر — مرورگر به ترتیب به موارد زیر برمی‌گردد:  
    1. اندازه‌های منبع (source sizes) در لیست `sizes`   
    2. attribute‌های `width`/`height` تعریف‌شده روی عنصر  
    3. اندازه ذاتی پیش‌فرض عناصر `<img>` در stylesheet پیش‌فرض user agent (300px در 150px)

    برای سازگاری بهتر با مرورگرهایی که `auto` را پشتیبانی نمی‌کنند، می‌توانید پس از `auto` در attribute `sizes` اندازه‌های fallback قرار دهید. همچنین باید attribute‌های `width` و `height` عنصر را به ابعاد ذاتی بزرگ‌ترین تصویر در `srcset` خود تنظیم کنید تا مرورگر بتواند با نسبت ابعاد صحیح فضا رزرو کند:

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

### `src`

URL تصویر. برای یک عنصر `<img>` حداقل یکی از `src` و [`srcset`](#srcset) الزامی است. اگر [`srcset`](#srcset) مشخص شده باشد، `src` به یکی از دو روش استفاده می‌شود:

- به عنوان fallback برای مرورگرهایی که `srcset` را پشتیبانی نمی‌کنند.
- اگر `srcset` از توصیف‌کننده "x" استفاده کند، آنگاه `src` معادل یک منبع با توصیف‌کننده چگالی `1x` است؛ یعنی تصویر مشخص‌شده توسط `src` در صفحه‌نمایش‌های با چگالی پایین (مانند نمایشگرهای معمولی 72 DPI یا 96 DPI) استفاده می‌شود.

### `srcset`

یک یا چند رشته که با کاما از هم جدا شده‌اند و منابع تصویر ممکن را برای استفاده عامل کاربر (user agent) نشان می‌دهند.

هر رشته از این‌ها تشکیل شده:

1. یک {{glossary("URL")}} به تصویر
2. به‌صورت اختیاری، فاصلهٔ خالی و سپس یکی از این دو:
   - توصیف‌کنندهٔ عرض (یک عدد صحیح مثبت که بلافاصله با `w` همراه است). این عدد **باید** با عرض ذاتی تصویر مرتبط مطابقت داشته باشد. توصیف‌کنندهٔ عرض بر اندازهٔ منبع داده‌شده در ویژگی `sizes` تقسیم می‌شود تا چگالی پیکسل مؤثر محاسبه شود. مثلاً برای ارائه یک تصویر وقتی رندرر به تصویری با عرض ۴۵۰ پیکسل نیاز دارد، از توصیف‌کنندهٔ عرض `450w` استفاده کنید. وقتی `srcset` شامل توصیف‌کننده‌های "w" باشد، مرورگر از آن‌ها به‌همراه ویژگی `sizes` برای انتخاب منبع استفاده می‌کند.
   - توصیف‌کنندهٔ چگالی پیکسل (یک عدد اعشاری مثبت که بلافاصله با `x` همراه است). مشخص می‌کند که در چه شرایطی از تصویر مرتبط استفاده شود، بر اساس چگالی پیکسل نمایشگر. مثلاً اگر چگالی پیکسل دوبرابر استاندارد باشد، از توصیف‌کنندهٔ `2x` یا `2.0x` استفاده کنید.

اگر هیچ توصیف‌کننده‌ای مشخص نشود، منبع به‌طور پیش‌فرض توصیف‌کنندهٔ `1x` دریافت می‌کند. ترکیب توصیف‌کننده‌های عرض و چگالی پیکسل در یک ویژگی `srcset` اشتباه است. همچنین توصیف‌کننده‌های تکراری (مثلاً دو منبع در یک `srcset` که هر دو با `2x` توصیف شده‌اند) نامعتبر هستند.

فاصله‌های خالی، به‌جز آنچه بین URL و توصیف‌کنندهٔ شرطی قرار دارد، نادیده گرفته می‌شوند؛ این شامل فاصله‌های ابتدا و انتها و همچنین فاصله قبل یا بعد از هر کاما است. اما اگر یک رشتهٔ تصویر کاندید هیچ توصیف‌کننده‌ای و هیچ فاصله‌ای بعد از URL نداشته باشد، رشتهٔ بعدی (اگر وجود داشته باشد) باید با یک یا چند فاصله شروع شود، در غیر این صورت کاما بخشی از URL در نظر گرفته می‌شود.

وقتی ویژگی `srcset` عنصر `<img>` از توصیف‌کننده‌های `x` استفاده می‌کند، مرورگر URL موجود در ویژگی `src` (در صورت وجود) را نیز به‌عنوان یک کاندید در نظر می‌گیرد و به آن توصیف‌کنندهٔ پیش‌فرض `1x` اختصاص می‌دهد. از سوی دیگر، اگر `srcset` از توصیف‌کننده‌های عرض استفاده کند، `src` در نظر گرفته نمی‌شود و به‌جای آن از ویژگی `sizes` استفاده می‌شود.

عامل کاربر (user agent) هر یک از منابع موجود را به صلاحدید خود انتخاب می‌کند. این به مرورگر انعطاف زیادی می‌دهد تا بر اساس عواملی مانند ترجیحات کاربر یا شرایط {{glossary("bandwidth")}} انتخاب خود را تنظیم کند. برای مثال می‌توانید به آموزش [تصاویر واکنش‌گرا](/en-US/docs/Web/HTML/Guides/Responsive_images) مراجعه کنید.

- `width`
  - : عرض ذاتی تصویر بر حسب پیکسل. باید یک عدد صحیح بدون واحد باشد.
- `usemap`
  - : بخشی از {{glossary("URL")}} (که با `#` شروع می‌شود) مربوط به یک [نقشه تصویر](/en-US/docs/Web/HTML/Reference/Elements/map) که با عنصر مرتبط است.

    > [!NOTE]
    > اگر عنصر `<img>` داخل یک عنصر {{htmlelement("a")}} یا {{HTMLElement("button")}} قرار دارد، نمی‌توانید از این ویژگی استفاده کنید.

### ویژگی‌های منسوخ‌شده

- `align` {{deprecated_inline}}
  - : تصویر را نسبت به محتوای اطرافش تراز می‌کند. به‌جای این ویژگی از خصوصیات {{cssxref('float')}} و/یا {{cssxref('vertical-align')}} در {{glossary("CSS")}} استفاده کنید. مقادیر مجاز:
    - `top`
      - : معادل `vertical-align: top` یا `vertical-align: text-top`
    - `middle`
      - : معادل `vertical-align: -moz-middle-with-baseline`
    - `bottom`
      - : مقدار پیش‌فرض، معادل `vertical-align: unset` یا `vertical-align: initial`
    - `left`
      - : معادل `float: left`
    - `right`
      - : معادل `float: right`

- `border` (منسوخ)
  - : عرض حاشیه‌ای دور تصویر. این ویژگی منسوخ است؛ به جای آن از خصوصیت CSS `border` استفاده کنید.

- `hspace` (منسوخ)
  - : تعداد پیکسل‌های فضای سفید در چپ و راست تصویر. این ویژگی منسوخ است؛ به جای آن از خصوصیت CSS `margin` استفاده کنید.

- `longdesc` (منسوخ)
  - : پیوندی به توضیح دقیق‌تر تصویر. مقادیر ممکن شامل یک `URL` یا [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) یک المان است.

  > [!NOTE]
  > این ویژگی در [مشخصات HTML](https://html.spec.whatwg.org/multipage/obsolete.html#element-attrdef-img-longdesc) منسوخ در نظر گرفته شده است. آیندهٔ آن نامشخص است؛ نویسندگان باید از جایگزین WAI-ARIA مانند [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) یا [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details) استفاده کنند.

- `name` (منسوخ)
  - : نامی برای المان. این ویژگی منسوخ است؛ به جای آن از ویژگی [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) استفاده کنید.

- `vspace` (منسوخ)
  - : تعداد پیکسل‌های فضای سفید بالا و پایین تصویر. این ویژگی منسوخ است؛ به جای آن از خصوصیت CSS `margin` استفاده کنید.

## استایل‌دهی با CSS

`<img>` یک “replaced element” است؛ به‌طور پیش‌فرض مقدار `display` آن `inline` است، اما ابعاد پیش‌فرض آن توسط مقادیر ذاتی تصویر تعیین می‌شود، گویی `inline-block` است. می‌توانید خصوصیت‌هایی مانند `border`/`border-radius`، `padding`/`margin`، `width`، `height` و غیره را روی تصویر تنظیم کنید.

`<img>` خط پایه (baseline) ندارد؛ بنابراین وقتی تصاویر در یک بافت قالب‌بندی درون‌خطی (inline formatting context) با `vertical-align: baseline` استفاده می‌شوند، پایین تصویر روی خط پایهٔ متن قرار می‌گیرد.

می‌توانید از خصوصیت `object-position` برای جای‌گذاری تصویر در جعبهٔ المان استفاده کنید، و از خصوصیت `object-fit` برای تنظیم اندازهٔ تصویر درون جعبه (مثلاً اینکه تصویر در جعبه جا شود یا آن را پر کند حتی اگر برش لازم باشد) استفاده کنید.

بسته به نوع تصویر، ممکن است عرض و ارتفاع ذاتی داشته باشد. با این حال، برای برخی انواع تصویر، ابعاد ذاتی لازم نیست. برای مثال، تصاویر SVG اگر المان ریشهٔ `<svg>` آن‌ها دارای `width` یا `height` تنظیم‌شده نباشد، ابعاد ذاتی ندارند.

## دسترس‌پذیری

### نوشتن توضیحات جایگزین معنادار

مقدار ویژگی `alt` باید جایگزین متنی واضح و مختصر برای محتوای تصویر باشد. نباید حضور خود تصویر یا نام فایل تصویر را توصیف کند. اگر ویژگی `alt` به‌عمد حذف شده است زیرا تصویر معادل متنی ندارد، روش‌های جایگزین برای ارائهٔ آنچه تصویر سعی در انتقال آن دارد در نظر بگیرید.

#### نمونهٔ نامناسب

```html example-bad
<img alt="image" src="penguin.jpg" />
```

#### نمونهٔ مناسب

```html example-good
<img alt="A Penguin on a beach." src="penguin.jpg" />
```

یک آزمایش دسترس‌پذیری مهم این است که محتوای ویژگی `alt` را همراه با متن قبلی بخوانید تا ببینید آیا همان معنای تصویر را منتقل می‌کند. برای مثال، اگر قبل از تصویر جملهٔ "On my travels, I saw a cute little animal:" آمده باشد، نمونهٔ _Don't_ توسط صفحه‌خوان به صورت "On my travels, I saw a cute little animal: image" خوانده می‌شود که بی‌معناست. نمونهٔ _Do_ به صورت "On my travels, I saw a cute little animal: A Penguin on a beach." خوانده می‌شود که معنادار است.

برای تصاویری که برای اجرای یک عمل استفاده می‌شوند — مثلاً تصاویری که داخل یک `element` مانند `<a>` یا `<button>` قرار دارند — بهتر است در مقدار `alt` attribute عملی که با کلیک روی تصویر انجام می‌شود را توصیف کنید. برای مثال، می‌توانید به جای `alt="arrow right"` بنویسید `alt="next page"`. همچنین می‌توانید یک توضیح تکمیلی اختیاری در `title` attribute اضافه کنید؛ این توضیح ممکن است در صورت درخواست کاربر توسط صفحه‌خوان‌ها خوانده شود.

اگر تصویری `alt` attribute نداشته باشد، بعضی صفحه‌خوان‌ها نام فایل تصویر را به جای آن اعلام می‌کنند. اگر نام فایل نمایانگر محتوای تصویر نباشد، این موضوع می‌تواند تجربه‌ای گیج‌کننده ایجاد کند.

- [درخت تصمیم `alt` — آموزش‌های دسترس‌پذیری وب WAI](https://www.w3.org/WAI/tutorials/images/decision-tree/)
- [متن‌های جایگزین: راهنمای نهایی — Axess Lab](https://axesslab.com/alt-texts/)
- [چگونه متن جایگزین خوبی طراحی کنیم؟ — Deque](https://www.deque.com/blog/great-alt-text-introduction/)
- [توضیحات MDN در مورد درک WCAG، معیار ۱.۱](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable#guideline_1.1_—_providing_text_alternatives_for_non-text_content)
- [درک معیار موفقیت ۱.۱.۱ | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/text-equiv-all.html)

### شناسایی SVG به‌عنوان تصویر

به دلیل یک [باگ در VoiceOver](https://webkit.org/b/216364)، VoiceOver تصاویر SVG را به‌درستی به‌عنوان تصویر اعلام نمی‌کند. برای اینکه فناوری‌های کمکی بتوانند SVG را به‌درستی به‌عنوان محتوای تصویر تشخیص دهند، [`role="img"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/img_role) را به تمام `element`های `<img>` که از فایل SVG استفاده می‌کنند اضافه کنید.

```html
<img src="mdn.svg" alt="MDN" role="img" />
```

### `title` attribute

`title` attribute جایگزین مناسبی برای `alt` attribute نیست. همچنین از تکرار مقدار `alt` در `title` روی همان تصویر خودداری کنید. این کار ممکن است باعث شود برخی صفحه‌خوان‌ها همان متن را دو بار اعلام کنند و تجربه‌ای گیج‌کننده ایجاد شود.

`title` attribute نباید به‌عنوان اطلاعات تکمیلیِ شبیه زیرنویس در کنار توصیف `alt` تصویر استفاده شود. اگر تصویر به زیرنویس نیاز دارد، از `element`های [`figure`](/en-US/docs/Web/HTML/Reference/Elements/figure) و [`figcaption`](/en-US/docs/Web/HTML/Reference/Elements/figcaption) استفاده کنید.

مقدار `title` attribute معمولاً به‌صورت tooltip به کاربر نمایش داده می‌شود؛ tooltip کمی پس از توقف مکان‌نما روی تصویر ظاهر می‌شود. اگرچه این امکان وجود دارد که اطلاعات بیشتری در اختیار کاربر قرار دهد، اما نباید فرض کنید کاربر حتماً آن را می‌بیند. کاربر ممکن است فقط از صفحه‌کلید یا صفحه‌لمسی استفاده کند. اگر اطلاعاتی دارید که برای کاربر اهمیت زیادی دارد، به‌جای استفاده از `title`، آن را به‌صورت درون‌خطی با یکی از روش‌هایی که در بالا ذکر شد ارائه دهید.

- [استفاده از HTML title attribute — به‌روزرسانی‌شده | Vispero](https://vispero.com/resources/using-the-html-title-attribute-updated/)

## مثال‌ها

### متن جایگزین

مثال زیر یک تصویر را در صفحه قرار می‌دهد و برای دسترس‌پذیری، متن جایگزینی در نظر گرفته است.

```html
<img src="/shared-assets/images/examples/favicon144.png" alt="MDN" />
```

### پیوند تصویری

این مثال بر اساس مثال قبلی ساخته شده و نشان می‌دهد چگونه می‌توان تصویر را به پیوند تبدیل کرد. برای این کار، تگ `<img>` را داخل `<a>` قرار دهید. متن جایگزین باید منبعی را که پیوند به آن اشاره می‌کند توصیف کند، همان‌طور که اگر به‌جای تصویر از یک پیوند متنی استفاده می‌کردید.

```html
<a href="https://developer.mozilla.org">
  <img
    src="/shared-assets/images/examples/favicon144.png"
    alt="Visit the MDN site" />
</a>
```

### استفاده از `srcset` attribute

در این مثال، یک attribute به نام `srcset` همراه با ارجاع به نسخه‌ی پرجزئیات‌تر لوگو قرار داده‌ایم؛ این نسخه در دستگاه‌های با وضوح بالا به جای تصویر `src` بارگذاری می‌شود. تصویری که در attribute مربوط به `src` ارجاع داده شده است، در user agents که از `srcset` پشتیبانی می‌کنند به عنوان یک کاندیدای `1x` حساب می‌شود.

```html
<img
  src="/shared-assets/images/examples/favicon72.png"
  alt="MDN"
  srcset="/shared-assets/images/examples/favicon144.png 2x" />
```

### استفاده از attribute های srcset و sizes

در user agents که از `srcset` پشتیبانی می‌کنند و توصیفگرهای `w` شامل شده باشند، attribute مربوط به `src` نادیده گرفته می‌شود. وقتی شرط رسانه‌ای `(width <= 600px)` برقرار باشد، تصویر با عرض ۲۰۰ پیکسل بارگذاری می‌شود (چون این تصویر نزدیک‌ترین تطابق را با `200px` دارد)؛ در غیر این صورت، تصویر دیگر بارگذاری می‌شود.

```html
<img
  src="clock-demo-200px.png"
  alt="The time is 12:45."
  srcset="clock-demo-200px.png 200w, clock-demo-400px.png 400w"
  sizes="(width <= 600px) 200px, 50vw" />
```

> [!NOTE]
> برای مشاهده‌ی تغییر اندازه در عمل، مثال را در یک صفحه‌ی جداگانه باز کنید تا بتوانید واقعاً اندازه‌ی ناحیه‌ی محتوا را تغییر دهید.

## نگرانی‌های امنیتی و حریم خصوصی

اگرچه عناصر `<img>` کاربردهای بی‌خطری دارند، اما می‌توانند پیامدهای ناخواسته‌ای برای امنیت و حریم خصوصی کاربران داشته باشند. برای اطلاعات بیشتر و راه‌های کاهش ریسک، به [Referer header: نگرانی‌های امنیتی و حریم خصوصی](/en-US/docs/Web/Privacy/Guides/Referer_header:_privacy_and_security_concerns) مراجعه کنید.

| ویژگی | مقدار |
| --- | --- |
| دسته‌های محتوا | در دسته‌های [Flow content](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، [phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content)، [embedded content](/en-US/docs/Web/HTML/Guides/Content_categories#embedded_content) و [palpable content](/en-US/docs/Web/HTML/Guides/Content_categories#palpable_content) قرار می‌گیرد. اگر element دارای attribute `usemap` باشد، در دسته interactive content نیز قرار می‌گیرد. |
| محتوای مجاز | هیچ؛ این یک void element است. |
| حذف تگ | باید تگ شروع داشته باشد و نباید تگ پایانی داشته باشد. |
| والدهای مجاز | هر element که embedded content بپذیرد. |
| نقش ARIA ضمنی | <ul><li>با attribute `alt` غیرخالی یا بدون attribute `alt`: [`img`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/img_role)</li><li>با attribute `alt` خالی: [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role)</li></ul> |
| نقش‌های ARIA مجاز | <ul><li>با attribute `alt` غیرخالی:<ul><li>[`button`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role)</li><li>[`checkbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role)</li><li>[`link`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/link_role)</li><li>[`menuitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role)</li><li>[`menuitemcheckbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role)</li><li>[`menuitemradio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role)</li><li>[`option`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role)</li><li>[`progressbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/progressbar_role)</li><li>[`scrollbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/scrollbar_role)</li><li>[`separator`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/separator_role)</li><li>[`slider`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role)</li><li>[`switch`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/switch_role)</li><li>[`tab`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role)</li><li>[`treeitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treeitem_role)</li></ul></li><li>با attribute `alt` خالی: [`none`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role) یا [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role)</li><li>بدون attribute `alt`: هیچ `role` مجاز نیست.</li></ul> |
| رابط DOM | `HTMLImageElement` |

## مشخصات

## سازگاری مرورگرها

## همچنین ببینید

- عناصر `<picture>`، `<object>` و `<embed>`
- خصوصیات CSS مرتبط با تصویر: `object-fit`، `object-position`، `image-orientation`، `image-rendering` و `image-resolution`
- اینترفیس `HTMLImageElement` برای این عنصر
- [تصاویر HTML](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_images)
- [راهنمای نوع فایل و فرمت تصویر](/en-US/docs/Web/Media/Guides/Formats/Image_types)
- [تصاویر واکنش‌گرا](/en-US/docs/Web/HTML/Guides/Responsive_images)