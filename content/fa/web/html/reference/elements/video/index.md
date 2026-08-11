---
title: "<video> HTML video embed element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/video"
translated_by: "n8n + AI"
---

عنصر `<video>` در HTML یک پخش‌کننده رسانه را در سند جاسازی می‌کند که از پخش ویدیو پشتیبانی می‌کند. می‌توانید از `<video>` برای محتوای صوتی هم استفاده کنید، اما عنصر {{HTMLElement("audio")}} ممکن است تجربه کاربری مناسب‌تری ارائه دهد.

در مثال بالا نحوه استفاده از عنصر `<video>` نشان داده شده است. مشابه عنصر {{htmlelement("img")}}، مسیر رسانه‌ای که می‌خواهیم نمایش دهیم را در attribute  `src` قرار می‌دهیم. می‌توانیم attributeهای دیگری مثل عرض و ارتفاع ویدیو، autoplay، loop یا نمایش کنترل‌های پیش‌فرض مرورگر را مشخص کنیم.

محتویات داخل تگ‌های باز و بسته `<video></video>` به عنوان fallback (جایگزین) در مرورگرهایی که از این عنصر پشتیبانی نمی‌کنند نشان داده می‌شود.

## ویژگی‌ها (Attributes)

مانند همه عناصر HTML دیگر، این عنصر از [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) پشتیبانی می‌کند.

- `autoplay`
  - : یک Boolean attribute است. اگر مشخص شود، ویدیو به محض امکان‌پذیری بدون توقف برای بارگذاری کامل داده، به طور خودکار شروع به پخش می‌کند.

    > [!NOTE]
    > مرورگرهای مدرن از autoplay صدا (یا ویدیوهای با صدای قطع‌نشده) جلوگیری می‌کنند، زیرا سایت‌هایی که به طور خودکار صدا پخش می‌کنند ممکن است برای کاربران ناخوشایند باشد. برای اطلاعات بیشتر درباره استفاده صحیح از autoplay به [راهنمای autoplay](/en-US/docs/Web/Media/Guides/Autoplay) مراجعه کنید.

    برای غیرفعال کردن autoplay ویدیو، `autoplay="false"` کار نمی‌کند. اگر attribute در تگ `<video>` وجود داشته باشد، ویدیو autoplay می‌شود. برای حذف autoplay باید attribute را به طور کامل حذف کرد.

    > [!NOTE]
    > ویدیوهایی که [`loading="lazy"`](#loading) دارند، تا زمانی که عنصر نزدیک یا داخل viewport نباشد شروع به دانلود و autoplay نمی‌کنند.

- `controls`
  - : اگر این attribute وجود داشته باشد، مرورگر کنترل‌هایی را برای کاربر فراهم می‌کند تا بتواند پخش ویدیو از جمله صدا، جستجو (seeking) و توقف/ادامه پخش را کنترل کند.
- `controlslist`
  - : attribute  [`controlslist`](https://wicg.github.io/controls-list/explainer.html) به مرورگر کمک می‌کند تا انتخاب کند چه کنترل‌هایی برای عنصر `video` نمایش دهد، زمانی که مرورگر مجموعه کنترل‌های خود را نشان می‌دهد (یعنی وقتی attribute  `controls` مشخص شده است).

    مقادیر مجاز عبارتند از `nodownload`، `nofullscreen` و `noremoteplayback`.

    برای غیرفعال کردن حالت Picture-In-Picture (و کنترل مربوطه) از attribute  [`disablepictureinpicture`](#disablepictureinpicture) استفاده کنید.

- [`crossorigin`](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin)
  - : این ویژگی شمارشی (enumerated) مشخص می‌کند که آیا برای دریافت ویدیوی مربوطه از CORS استفاده شود یا خیر. منابع فعال‌شده با CORS را می‌توان بدون اینکه _آلوده (tainted)_ شوند، در عنصر {{HTMLElement("canvas")}} دوباره استفاده کرد. مقادیر مجاز عبارتند از:
    - `anonymous`
      - : یک درخواست cross-origin بدون credential ارسال می‌کند. به عبارت دیگر، هدر `Origin:` را بدون کوکی، گواهی X.509 یا انجام احراز هویت پایه HTTP می‌فرستد. اگر سرور به سایت مبدأ credential ندهد (با تنظیم نکردن هدر `Access-Control-Allow-Origin:`)، منبع _آلوده_ می‌شود و استفاده از آن محدود می‌گردد.
    - `use-credentials`
      - : یک درخواست cross-origin با credential ارسال می‌کند. یعنی هدر `Origin:` را همراه با کوکی، گواهی یا انجام احراز هویت پایه HTTP می‌فرستد. اگر سرور از طریق هدر `Access-Control-Allow-Credentials:` به سایت مبدأ credential ندهد، منبع _آلوده_ می‌شود و استفاده از آن محدود می‌گردد.

    در صورت عدم وجود این ویژگی، منبع بدون درخواست CORS دریافت می‌شود (یعنی بدون ارسال هدر `Origin:`) که از استفاده غیرآلوده آن در عناصر {{HTMLElement('canvas')}} جلوگیری می‌کند. اگر مقدار نامعتبر باشد، طوری رفتار می‌شود که گویی کلیدواژه `anonymous` استفاده شده است. برای اطلاعات بیشتر به [ویژگی‌های تنظیمات CORS](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin) مراجعه کنید.

- `disablepictureinpicture`
  - : از پیشنهاد منوی زمینه Picture-in-Picture توسط مرورگر یا درخواست خودکار آن در برخی موارد جلوگیری می‌کند.
- `disableremoteplayback`
  - : یک ویژگی Boolean که قابلیت پخش از راه دور را در دستگاه‌های متصل با فناوری‌های سیمی (HDMI، DVI و غیره) و بی‌سیم (Miracast، Chromecast، DLNA، AirPlay و غیره) غیرفعال می‌کند.

    در Safari، می‌توانید از [`x-webkit-airplay="deny"`](https://developer.apple.com/library/archive/documentation/AudioVideo/Conceptual/AirPlayGuide/OptingInorOutofAirPlay/OptingInorOutofAirPlay.html) به عنوان یک جایگزین (fallback) استفاده کنید.

- `height`
  - : ارتفاع ناحیه نمایش ویدیو، بر حسب [پیکسل CSS](https://drafts.csswg.org/css-values/#px) (فقط مقادیر مطلق؛ [بدون درصد](https://html.spec.whatwg.org/multipage/embedded-content.html#dimension-attributes)).

- `loading` {{experimental_inline}}
  - : نحوه بارگذاری ویدیو (شامل هر تصویر پوستر) توسط مرورگر را مشخص می‌کند:
    - `eager`
      - : ویدیو را بلافاصله بارگذاری می‌کند، صرف‌نظر از اینکه ویدیو در حال حاضر درون viewport قابل مشاهده است یا خیر (این مقدار پیش‌فرض است).
    - `lazy`
      - : بارگذاری ویدیو را تا زمانی که به فاصله محاسبه‌شده‌ای از viewport برسد (که توسط مرورگر تعریف می‌شود) به تأخیر می‌اندازد.

        بارگذاری تنبل (lazy loading) از پهنای باند شبکه و ذخیره‌سازی مورد نیاز برای مدیریت ویدیو تا زمانی که اطمینان معقولی از نیاز به آن وجود داشته باشد جلوگیری می‌کند. این کار عملکرد را در اکثر موارد معمول بهبود می‌بخشد.

        اگرچه برای همه ویدیوها توصیه می‌شود که از ویژگی‌های صریح [`width`](#width) و [`height`](#height) برای جلوگیری از جابه‌جایی layout استفاده شود، اما این ویژگی‌ها برای ویدیوهای بارگذاری‌شده با `lazy` اهمیت ویژه‌ای دارند. ویدیوهای بارگذاری‌شده با `lazy` اگر با یک بخش قابل مشاهده از یک عنصر تلاقی نداشته باشند، هرگز بارگذاری نخواهند شد، حتی اگر بارگذاری آن‌ها این وضعیت را تغییر دهد، زیرا ویدیوهای بارگذاری‌نشده `width` و `height` برابر `0` دارند. این موضوع وقتی محتوای قابل مشاهده در viewport در حین مطالعه دوباره چیده می‌شود، تجربه کاربری آزاردهنده‌تری ایجاد می‌کند.

        ویدیوهای بارگذاری‌شده با `lazy` که در viewport بصری قرار دارند ممکن است هنگام رویداد {{domxref("Window.load_event", "load")}} پنجره هنوز قابل مشاهده نباشند. دلیل این است که رویداد بر اساس ویدیوهای بارگذاری‌شده با `eager` فعال می‌شود - ویدیوهای بارگذاری‌شده با `lazy` حتی اگر در بارگذاری اولیه صفحه درون viewport بصری باشند، در نظر گرفته نمی‌شوند.

```markdown
بارگذاری فقط زمانی به تأخیر می‌افتد که جاوااسکریپت فعال باشد. این یک اقدام ضد ردیابی است؛ زیرا اگر user agent در حالی که اسکریپت غیرفعال است از بارگذاری تنبل (lazy loading) پشتیبانی کند، باز هم برای یک سایت امکان‌پذیر است که با قرار دادن راهبردی ویدیوها در مارکاپ صفحه، موقعیت تقریبی اسکرول کاربر را در طول یک نشست ردیابی کند؛ یعنی سرور می‌تواند بفهمد چند ویدیو و در چه زمانی درخواست شده‌اند.

> [!NOTE]
> attribute `loading="lazy"` روی attribute های [`autoplay`](#autoplay)، [`poster`](#poster) و [`preload`](#preload) نیز تأثیر می‌گذارد؛ همانطور که در هر یک از بخش‌های مربوطه در همین صفحه توضیح داده شده است.

- `loop`
  - : یک attribute بولی است؛ اگر مشخص شده باشد، browser پس از رسیدن به پایان ویدیو، به‌طور خودکار به ابتدا برمی‌گردد.

- `muted`
  - : یک attribute بولی است که تنظیم پیش‌فرض بی‌صدا بودن (mute) صدا در ویدیو را مشخص می‌کند. اگر تنظیم شود، صدا در ابتدا قطع خواهد بود. مقدار پیش‌فرض آن `false` است، یعنی هنگام پخش ویدیو صدا شنیده می‌شود.

    > [!NOTE]
    > برای بازگرداندن صدا، تنظیم `muted="false"` کار نخواهد کرد؛ اگر attribute وجود داشته باشد، صدا بی‌صدا می‌ماند. برای بازگرداندن صدا، باید attribute را به‌طور کامل حذف کرد.

- `playsinline`
  - : یک attribute بولی است که نشان می‌دهد ویدیو باید «inline» پخش شود، یعنی در ناحیه پخش همان element. توجه داشته باشید که نبود این attribute _به این معنا نیست_ که ویدیو همیشه تمام‌صفحه پخش می‌شود.

- `poster`
  - : یک URL برای تصویری است که در هنگام دانلود ویدیو نمایش داده می‌شود. اگر این attribute مشخص نشود، هیچ چیزی نمایش داده نمی‌شود تا زمانی که اولین فریم در دسترس باشد؛ سپس اولین فریم به‌عنوان poster frame نمایش داده می‌شود.

    > [!NOTE]
    > ویدیوهایی که attribute [`loading="lazy"`](#loading) را تنظیم کرده‌اند، فقط زمانی منبع `poster` را دانلود می‌کنند که ویدیو به viewport نزدیک یا داخل آن باشد.

- `preload`
  - : این attribute از نوع شمارشی (enumerated) است و هدف آن ارائه یک hint به browser است درباره اینکه نویسنده فکر می‌کند چه چیزی بهترین تجربه کاربری را برای محتوایی که قبل از پخش ویدیو بارگذاری می‌شود، به همراه خواهد داشت. این attribute ممکن است یکی از مقادیر زیر را داشته باشد:
    - `none`: نشان می‌دهد که ویدیو نباید پیش‌بارگذاری شود.
    - `metadata`: نشان می‌دهد که فقط فراداده (metadata) ویدیو واکشی می‌شود (مثلاً طول ویدیو).
    - `auto`: نشان می‌دهد که کل فایل ویدیو می‌تواند دانلود شود، حتی اگر انتظار نرود کاربر از آن استفاده کند.
    - _رشتهٔ خالی_: مترادف مقدار `auto` است.

    مقدار پیش‌فرض در هر browser متفاوت است. توصیه مشخصات (spec) این است که روی `metadata` تنظیم شود.

    > [!NOTE]
    >
    > - ویدیوهایی که attribute [`loading="lazy"`](#loading) روی آن‌ها تنظیم شده است، رفتار `preload` را فقط زمانی اعمال می‌کنند که ویدیو به viewport نزدیک یا داخل آن باشد.
    > - attribute `autoplay` بر `preload` اولویت دارد. اگر `autoplay` مشخص شود، browser به‌وضوح برای پخش باید دانلود ویدیو را شروع کند.
    > - مشخصات (spec) browser را مجبور نمی‌کند که از مقدار این attribute پیروی کند؛ این فقط یک hint است.

- `src`
  - : آدرس URL ویدیویی است که قرار است جاسازی شود. این attribute اختیاری است؛ می‌توانید به جای آن از element `<source>` در داخل بلوک ویدیو استفاده کنید تا ویدیوی مورد نظر را مشخص کنید.

- `width`
  - : عرض ناحیه نمایش ویدیو، بر حسب [CSS pixels](https://drafts.csswg.org/css-values/#px) (فقط مقادیر مطلق؛ [no percentages](https://html.spec.whatwg.org/multipage/embedded-content.html#dimension-attributes)).

## رویدادها
```

- **audioprocess** (منسوخ):  
  - بافر ورودی یک `ScriptProcessorNode` آماده پردازش است.  
- **canplay**:  
  - مرورگر می‌تواند رسانه را پخش کند، اما تخمین می‌زند داده کافی برای پخش تا پایان بدون توقف برای بافر بیشتر بارگذاری نشده است.  
- **canplaythrough**:  
  - مرورگر تخمین می‌زند می‌تواند رسانه را تا پایان بدون توقف برای بافر محتوا پخش کند.  
- **complete**:  
  - رندر کردن یک `OfflineAudioContext` خاتمه یافته است.  
- **durationchange**:  
  - ویژگی `duration` به‌روزرسانی شده است.  
- **emptied**:  
  - رسانه خالی شده است؛ برای مثال، این رویداد زمانی ارسال می‌شود که رسانه قبلاً بارگذاری شده (یا بخشی از آن بارگذاری شده) و متد `load()` برای بارگذاری مجدد فراخوانی شود.  
- **ended**:  
  - پخش متوقف شده زیرا به انتهای رسانه رسیده است.  
- **error**:  
  - هنگام دریافت داده رسانه خطایی رخ داده، یا نوع منبع فرمت پشتیبانی‌شده‌ای نیست.  
- **loadeddata**:  
  - اولین فریم رسانه بارگذاری شده است.  
- **loadedmetadata**:  
  - فراداده (metadata) بارگذاری شده است.  
- **loadstart**:  
  - زمانی که مرورگر شروع به بارگذاری منبع کرده است فعال می‌شود.  
- **pause**:  
  - پخش متوقف شده است.  
- **play**:  
  - پخش آغاز شده است.  
- **playing**:  
  - پخش پس از توقف یا تأخیر به دلیل کمبود داده آماده شروع است.  
- **progress**:  
  - به‌طور دوره‌ای هنگام بارگذاری منبع توسط مرورگر فعال می‌شود.  
- **ratechange**:  
  - نرخ پخش تغییر کرده است.  
- **seeked**:  
  - عملیات جستجو (seek) تکمیل شد.  
- **seeking**:  
  - عملیات جستجو آغاز شد.  
- **stalled**:  
  - عامل کاربر در تلاش برای دریافت داده رسانه است، اما به‌طور غیرمنتظره‌ای داده‌ای نمی‌رسد.  
- **suspend**:  
  - بارگذاری داده رسانه معلق شده است.  
- **timeupdate**:  
  - زمان مشخص‌شده توسط ویژگی `currentTime` به‌روزرسانی شده است.  
- **volumechange**:  
  - صدا تغییر کرده است.  
- **waiting**:  
  - پخش به دلیل کمبود موقت داده متوقف شده است.  

## نکات استفاده

مرورگرها همه از یک فرمت ویدیویی پشتیبانی نمی‌کنند؛ می‌توانید چندین منبع را درون عناصر `<source>` تودرتو قرار دهید، و مرورگر از اولین منبعی که می‌فهمد استفاده خواهد کرد.

```html
<video controls>
  <source src="myVideo.webm" type="video/webm" />
  <source src="myVideo.mp4" type="video/mp4" />
  <p>
    Your browser doesn't support HTML video. Here is a
    <a href="myVideo.mp4" download="myVideo.mp4">link to the video</a> instead.
  </p>
</video>
```

هنگام استفاده از عناصر `<source>`، مرورگر سعی می‌کند هر منبع را به‌ترتیب بارگذاری کند. اگر یک منبع شکست بخورد (مثلاً به دلیل URL نامعتبر یا فرمت پشتیبانی‌نشده)، منبع بعدی امتحان می‌شود و همینطور ادامه می‌یابد. یک رویداد `error` روی عنصر `<video>` پس از شکست همه منابع فعال می‌شود؛ رویدادهای `error` روی هر عنصر `<source>` به‌صورت جداگانه فعال نمی‌شوند.

ما یک راهنمای جامع و دقیق برای [guide to media file types](/en-US/docs/Web/Media/Guides/Formats) و همچنین [guide to the codecs supported for video](/en-US/docs/Web/Media/Guides/Formats/Video_codecs) ارائه می‌دهیم. علاوه بر این، راهنمای [audio codecs that can be used with them](/en-US/docs/Web/Media/Guides/Formats/Audio_codecs) نیز در دسترس است.

سایر نکات استفاده:

- اگر attribute `controls` را مشخص نکنید، ویدیو کنترل‌های پیش‌فرض مرورگر را نخواهد داشت؛ می‌توانید با استفاده از JavaScript و API مربوط به `HTMLMediaElement` کنترل‌های سفارشی خود را بسازید. برای جزئیات بیشتر، [Creating a cross-browser video player](/en-US/docs/Web/Media/Guides/Audio_and_video_delivery/cross_browser_video_player) را ببینید.
- برای کنترل دقیق محتوای ویدیو (و صدا)، `HTMLMediaElement`ها رویدادهای متنوعی را صادر می‌کنند. این رویدادها علاوه بر فراهم کردن قابلیت کنترل، به شما امکان می‌دهند پیشرفت دانلود و پخش رسانه و همچنین وضعیت و موقعیت پخش را زیر نظر بگیرید.
- می‌توانید برای تنظیم موقعیت ویدیو در قابِ element از property `object-position` و برای کنترل نحوه تنظیم اندازه ویدیو جهت جا شدن در قاب از property `object-fit` استفاده کنید.
- برای نمایش زیرنویس یا کپشن همراه ویدیو، می‌توانید از مقداری JavaScript به همراه element `<track>` و فرمت [WebVTT](/en-US/docs/Web/API/WebVTT_API) استفاده کنید. اطلاعات بیشتر را در [Adding captions and subtitles to HTML video](/en-US/docs/Web/Media/Guides/Audio_and_video_delivery/Adding_captions_and_subtitles_to_HTML5_video) ببینید.
- می‌توانید فایل‌های صوتی را با استفاده از element `<video>` پخش کنید. این کار می‌تواند مفید باشد، مثلاً اگر نیاز به پخش صدا همراه با متن پیاده‌شده (transcript) مبتنی بر [WebVTT](/en-US/docs/Web/API/WebVTT_API) دارید، زیرا element `<audio>` اجازه استفاده از کپشن‌ها با WebVTT را نمی‌دهد.
- برای آزمایش محتوای جایگزین (fallback) در مرورگرهایی که از element پشتیبانی می‌کنند، می‌توانید `<video>` را با یک element غیرموجود مثل `<notavideo>` جایگزین کنید.

یک منبع عمومی خوب برای اطلاعات در مورد استفاده از HTML `<video>`، آموزش مقدماتی [HTML video and audio](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_video_and_audio) است.

### استایل‌دهی با CSS

element `<video>` یک عنصر جایگزین‌شده (replaced element) است — مقدار `display` آن به‌صورت پیش‌فرض `inline` است — اما عرض و ارتفاع پیش‌فرض آن در viewport بر اساس ویدیوی در حال پخش تعیین می‌شود.

هیچ ملاحظه خاصی برای استایل‌دهی به `<video>` وجود ندارد؛ یک روش رایج این است که به آن مقدار `display` برابر با `block` بدهید تا جایگذاری، اندازه‌گذاری و غیره آسان‌تر شود و سپس در صورت نیاز، استایل و چیدمان (layout) را اعمال کنید. [Video player styling basics](/en-US/docs/Web/Media/Guides/Audio_and_video_delivery/Video_player_styling_basics) تکنیک‌های مفیدی برای استایل‌دهی ارائه می‌دهد.

### افزودن زیرنویس و سایر trackهای متنی زمان‌بندی‌شده

افزودن trackهای متنی زمان‌بندی‌شده برای زیرنویس‌ها، کپشن‌ها، عنوان فصل‌ها و غیره، به‌صورت declarative با قرار دادن element `<track>` در داخل ویدیو انجام می‌شود. این trackها در قالب [Web Video Text Tracks File Format (WebVTT)](/en-US/docs/Web/API/WebVTT_API/Web_Video_Text_Tracks_Format) (فایل‌های `.vtt`) مشخص می‌شوند.

```html
<video controls src="video.webm">
  <track default kind="captions" src="captions.vtt" />
</video>
```

trackهای متنی زمان‌بندی‌شده را می‌توان به‌صورت برنامه‌نویسی (programmatically) نیز با استفاده از [WebVTT API](/en-US/docs/Web/API/WebVTT_API) اضافه کرد.

### تشخیص افزودن و حذف track

برای تشخیص زمانی که ترک‌ها به یک عنصر `<video>` اضافه یا از آن حذف می‌شوند، می‌توانید از رویدادهای `addtrack` و `removetrack` استفاده کنید. با این حال، این رویدادها مستقیماً به خود عنصر `<video>` ارسال نمی‌شوند. در عوض، به شیء فهرست ترک‌ها که درون `HTMLMediaElement` عنصر `<video>` قرار دارد و با نوع ترک اضافه‌شده مطابقت دارد، ارسال می‌شوند:

- `HTMLMediaElement.audioTracks`
  - : یک `AudioTrackList` شامل تمام ترک‌های صوتی عنصر رسانه. برای مطلع شدن از اضافه‌شدن ترک‌های صوتی جدید به عنصر، یک شنونده برای `addtrack` به این شیء اضافه کنید.
- `HTMLMediaElement.videoTracks`
  - : یک `VideoTrackList` شامل تمام ترک‌های ویدیویی عنصر رسانه. برای مطلع شدن از اضافه‌شدن ترک‌های ویدیویی به عنصر، یک شنونده `addtrack` به این شیء اضافه کنید.
- `HTMLMediaElement.textTracks`
  - : یک `TextTrackList` شامل تمام ترک‌های متنی عنصر رسانه (که برای زیرنویس، زیرنویس برای ناشنوایان و موارد مشابه استفاده می‌شوند). برای مطلع شدن از اضافه‌شدن ترک‌های متنی به عنصر، یک شنونده `addtrack` به این شیء اضافه کنید.

برای مثال، برای تشخیص اضافه یا حذف شدن ترک‌های صوتی به عنصر `<video>`، می‌توانید از کدی مانند این استفاده کنید:

```js
const elem = document.querySelector("video");

elem.audioTracks.onaddtrack = (event) => {
  trackEditor.addTrack(event.track);
};

elem.audioTracks.onremovetrack = (event) => {
  trackEditor.removeTrack(event.track);
};
```

این کد رویدادهای اضافه و حذف ترک‌های صوتی را در عنصر زیر نظر می‌گیرد و یک تابع فرضی را در ویرایشگر ترک فراخوانی می‌کند تا ترک را در فهرست ترک‌های موجود ویرایشگر ثبت و حذف کند.

همچنین می‌توانید برای گوش دادن به رویدادهای `addtrack` و `removetrack` از `addEventListener()` استفاده کنید.

### پشتیبانی سرور از ویدیو

اگر نوع MIME ویدیو روی سرور به‌درستی تنظیم نشده باشد، ویدیو ممکن است نمایش داده نشود یا یک جعبه خاکستری با علامت X نشان دهد (اگر جاوااسکریپت فعال باشد).

اگر از Apache Web Server برای ارائه ویدیوهای WebM استفاده می‌کنید، می‌توانید با افزودن پسوندهای نوع فایل ویدیو به نوع MIME با مقدار `video/webm` این مشکل را برطرف کنید (رایج‌ترین پسوند فایل WebM، `.webm` است). برای این کار، فایل `mime.types` را در مسیر `/etc/apache` ویرایش کنید یا از دستور پیکربندی `AddType` در `httpd.conf` استفاده کنید:

```plain
AddType video/webm .webm
```

ممکن است میزبان وب شما یک رابط آسان برای تغییر پیکربندی نوع MIME فراهم کند تا زمانی که یک به‌روزرسانی سراسری به‌طور طبیعی انجام شود.

## دسترس‌پذیری

ویدیوها باید هم زیرنویس (captions) و هم رونوشت (transcripts) داشته باشند که محتوای آن‌ها را به‌طور دقیق توصیف کنند (برای اطلاعات بیشتر درباره نحوه پیاده‌سازی این موارد، به [Adding captions and subtitles to HTML video](/en-US/docs/Web/Media/Guides/Audio_and_video_delivery/Adding_captions_and_subtitles_to_HTML5_video) مراجعه کنید). زیرنویس به افرادی که کم‌شنوا هستند کمک می‌کند محتوای صوتی ویدیو را در حین پخش درک کنند، در حالی که رونوشت به افرادی که به زمان بیشتری نیاز دارند امکان می‌دهد محتوای صوتی را با سرعت و قالبی که برایشان راحت است مرور کنند.

نکته قابل توجه این است که اگرچه می‌توانید برای رسانه‌های صوتی-تنها زیرنویس ایجاد کنید، این کار فقط زمانی امکان‌پذیر است که صدا را در یک عنصر `<video>` پخش کنید، زیرا ناحیه ویدیویی عنصر برای نمایش زیرنویس‌ها استفاده می‌شود. این یکی از سناریوهای خاصی است که در آن پخش صدا در یک عنصر ویدیویی مفید است.

اگر از سرویس‌های تولید خودکار زیرنویس استفاده می‌شود، مهم است که محتوای تولیدشده را بررسی کنید تا از مطابقت دقیق آن با ویدیوی اصلی مطمئن شوید.

علاوه بر گفتار، زیرنویس‌ها و رونوشت‌ها باید موسیقی و افکت‌های صوتی را که اطلاعات مهمی منتقل می‌کنند نیز مشخص کنند. این شامل احساسات و لحن صدا می‌شود:

```plain
14
00:03:14 --> 00:03:18
[Dramatic rock music]
```

زیرنویس‌ها نباید موضوع اصلی ویدیو را بپوشانند. می‌توان با استفاده از [تنظیمات `align` در VTT cue](/en-US/docs/Web/API/WebVTT_API/Web_Video_Text_Tracks_Format#cue_settings) موقعیت آن‌ها را تعیین کرد.

- [Web Video Text Tracks Format (WebVTT)](/en-US/docs/Web/API/WebVTT_API)
- [WebAIM: Captions, Transcripts, and Audio Descriptions](https://webaim.org/techniques/captions/)
- [MDN Understanding WCAG, Guideline 1.2 explanations](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable#guideline_1.2_—_providing_text_alternatives_for_time-based_media)
- [Understanding Success Criterion 1.2.1 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-av-only-alt.html)
- [Understanding Success Criterion 1.2.2 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-captions.html)

## مثال‌ها

### یک منبع واحد

این مثال یک ویدیو را پخش می‌کند و از کنترل‌های پیش‌فرض مرورگر برای کنترل پخش استفاده می‌کند.

#### HTML

```html
<!-- مثال ویدیوی ساده -->
<!-- 'Big Buck Bunny' با مجوز CC 3.0 توسط بنیاد Blender. میزبانی توسط archive.org -->
<!-- پوستر از peach.blender.org -->
<video
  controls
  src="https://archive.org/download/BigBuckBunny_124/Content/big_buck_bunny_720p_surround.mp4"
  poster="https://peach.blender.org/wp-content/uploads/title_anouncement.jpg?x11217"
  width="620">
  Sorry, your browser doesn't support embedded videos, but don't worry, you can
  <a href="https://archive.org/details/BigBuckBunny_124">download it</a>
  and watch it with your favorite video player!
</video>
```

#### نتیجه

تا زمانی که ویدیو شروع به پخش نکند، تصویر مشخص‌شده در attribute `poster` به جای آن نمایش داده می‌شود. اگر مرورگر از پخش ویدیو پشتیبانی نکند، متن جایگزین (fallback text) را نشان می‌دهد.

### چند منبع

این مثال بر اساس مثال قبلی ساخته شده و سه منبع مختلف برای رسانه ارائه می‌دهد. این کار باعث می‌شود ویدیو بدون توجه به اینکه کدام کدک ویدیویی توسط مرورگر پشتیبانی می‌شود، قابل تماشا باشد.

#### HTML

```html
<!-- استفاده از چند منبع به عنوان fallback برای تگ ویدیو -->
<!-- 'Elephants Dream' توسط Orange Open Movie Project Studio، با مجوز CC-3.0، میزبانی توسط archive.org -->
<!-- پوستر میزبانی توسط Wikimedia -->
<video
  width="620"
  controls
  poster="https://upload.wikimedia.org/wikipedia/commons/e/e8/Elephants_Dream_s5_both.jpg">
  <source
    src="https://archive.org/download/ElephantsDream/ed_hd.avi"
    type="video/avi" />
  <source
    src="https://archive.org/download/ElephantsDream/ed_1024_512kb.mp4"
    type="video/mp4" />

  Sorry, your browser doesn't support embedded videos, but don't worry, you can
  <a
    href="https://archive.org/download/ElephantsDream/ed_1024_512kb.mp4"
    download="ed_1024_512kb.mp4">
    download the MP4
  </a>
  and watch it with your favorite video player!
</video>
```

#### نتیجه

ابتدا فایل AVI امتحان می‌شود. اگر قابل پخش نباشد، [MP4](/en-US/docs/Web/Media/Guides/Formats/Containers#mpeg-4_mp4) امتحان می‌شود. اگر خود عنصر video پشتیبانی نشود، پیام جایگزین نمایش داده می‌شود، اما اگر هیچ‌کدام از منابع کار نکنند، چنین پیامی ظاهر نمی‌شود.

برخی از انواع فایل‌های رسانه‌ای به شما امکان می‌دهند با استفاده از پارامتر [`codecs`](/en-US/docs/Web/Media/Guides/Formats/codecs_parameter) به عنوان بخشی از رشته نوع فایل، اطلاعات دقیق‌تری ارائه دهید. برای مثال، `video/webm; codecs="vp8, vorbis"` یعنی فایل یک [WebM](/en-US/docs/Web/Media/Guides/Formats/Containers#webm) است که از [VP8](/en-US/docs/Web/Media/Guides/Formats/Video_codecs#vp8) برای ویدیو و [Vorbis](/en-US/docs/Web/Media/Guides/Formats/Audio_codecs#vorbis) برای صدا استفاده می‌کند.

## خلاصه فنی

<شروع خروجی>

| ویژگی | مقدار |
|-------|-------|
| [دسته‌بندی محتوا](/en-US/docs/Web/HTML/Guides/Content_categories) | [محتوای جریانی (Flow content)](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، محتوای عبارتی (phrasing content)، محتوای جاسازی‌شده (embedded content). اگر دارای ویژگی [`controls`](#controls) باشد: محتوای تعاملی (interactive content) و محتوای ملموس (palpable content). |
| محتوای مجاز | اگر عنصر دارای ویژگی [`src`](#src) باشد: صفر یا چند عنصر `<track>`، سپس محتوای شفاف (transparent content) که هیچ عنصر رسانه‌ای (media element) ندارد – یعنی بدون `<audio>` یا `<video>`. <br> در غیر این صورت: صفر یا چند عنصر `<source>`، سپس صفر یا چند عنصر `<track>`، سپس محتوای شفاف که هیچ عنصر رسانه‌ای ندارد – یعنی بدون `<audio>` یا `<video>`. |
| حذف تگ | هیچکدام، هم تگ شروع و هم تگ پایان اجباری هستند. |
| والدین مجاز | هر عنصری که محتوای جاسازی‌شده (embedded content) را بپذیرد. |
| نقش ARIA ضمنی | [نقش متناظری ندارد](https://w3c.github.io/html-aria/#dfn-no-corresponding-role) |
| نقش‌های ARIA مجاز | [`application`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role) |
| رابط DOM | `HTMLVideoElement` |

## مشخصات

<!-- {{Specifications}} removed -->

## سازگاری با مرورگرها

<!-- {{Compat}} removed -->

## همچنین ببینید

- [راهنمای انواع و فرمت‌های رسانه در وب](/en-US/docs/Web/Media/Guides/Formats)
  - [فرمت‌های ظرف رسانه (انواع فایل)](/en-US/docs/Web/Media/Guides/Formats/Containers)
  - [راهنمای کدک ویدیوی وب](/en-US/docs/Web/Media/Guides/Formats/Video_codecs)
  - [راهنمای کدک صوتی وب](/en-US/docs/Web/Media/Guides/Formats/Audio_codecs)

- قرار دادن و اندازه‌گیری تصویر درون قاب آن: `object-position` و `object-fit`
- `<audio>`
- [ویدیو و صدا در HTML](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_video_and_audio)
- [دستکاری ویدیو با canvas](/en-US/docs/Web/API/Canvas_API/Manipulating_video_using_canvas)
- [پیکربندی سرورها برای رسانه Ogg](/en-US/docs/Web/Media/Guides/Formats/Configuring_servers_for_Ogg_media)

<پایان خروجی>