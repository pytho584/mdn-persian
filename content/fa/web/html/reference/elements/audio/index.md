---
title: "<audio> HTML embed audio element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/audio"
translated_by: "n8n + AI"
---

المنت `<audio>` در [HTML](/en-US/docs/Web/HTML) برای جاسازی محتوای صوتی در اسناد استفاده می‌شود. این المنت می‌تواند شامل یک یا چند منبع صوتی باشد که با attribute `src` یا المنت [`<source>`](/en-US/docs/Web/HTML/Reference/Elements/source) مشخص می‌شوند؛ مرورگر مناسب‌ترین منبع را انتخاب می‌کند. همچنین می‌تواند با استفاده از [`MediaStream`](/en-US/docs/Web/API/MediaStream) مقصد رسانهٔ استریم‌شده باشد.

```html interactive-example
<figure>
  <figcaption>Listen to the T-Rex:</figcaption>
  <audio controls src="/shared-assets/audio/t-rex-roar.mp3"></audio>
  <a href="/shared-assets/audio/t-rex-roar.mp3"> Download audio </a>
</figure>
```

```css interactive-example
figure {
  margin: 0;
}
```

مثال بالا کاربرد پایهٔ `<audio>` را نشان می‌دهد. مشابه المنت [`<img>`](/en-US/docs/Web/HTML/Reference/Elements/img)، مسیر رسانه‌ای که می‌خواهیم جاسازی کنیم را در attribute `src` قرار می‌دهیم؛ می‌توانیم ویژگی‌های دیگری مثل `autoplay` و `loop` را برای تعیین رفتار پخش تنظیم کنیم یا مشخص کنیم که کنترل‌های پیش‌فرض صدا در مرورگر نمایش داده شوند و غیره.

محتوای داخل تگ‌های آغازین و پایانی `<audio></audio>` در مرورگرهایی که این المنت را پشتیبانی نمی‌کنند، به‌عنوان جایگزین (fallback) نمایش داده می‌شود.

## Attributes

ویژگی‌های این المنت شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) می‌شود.

- `autoplay`
  - : یک Boolean attribute است؛ اگر مشخص شود، صدا به محض آماده‌شدن پخش به‌صورت خودکار شروع می‌شود، بدون اینکه منتظر دانلود کامل فایل صوتی بماند.

    > [!NOTE]
    > سایت‌هایی که صدا (یا ویدیوهای دارای ورودی صوتی) را به‌صورت خودکار پخش می‌کنند، می‌توانند تجربهٔ ناخوشایندی برای کاربران ایجاد کنند؛ بنابراین در صورت امکان باید از این کار پرهیز کرد. اگر نیاز به ارائهٔ قابلیت پخش خودکار دارید، آن را به‌صورت انتخابی (opt-in) تعریف کنید؛ یعنی کاربر باید به‌طور صریح آن را فعال کند. با این حال، این قابلیت می‌تواند هنگام ساخت المنت‌های رسانه‌ای که منبع آن‌ها بعداً و تحت کنترل کاربر تنظیم می‌شود مفید باشد. برای اطلاعات بیشتر دربارهٔ استفادهٔ صحیح از autoplay، [راهنمای autoplay](/en-US/docs/Web/Media/Guides/Autoplay) را ببینید.

    > [!NOTE]
    > صدایی که attribute [`loading="lazy"`](#loading) روی آن تنظیم شده باشد، تا وقتی کنترل‌های رسانه به viewport نزدیک یا داخل آن نباشند، دانلود و پخش خودکار آغاز نمی‌شود. همچنین، صدایی که با loading از نوع lazy بارگذاری شده و attribute `controls` نداشته باشد، به‌طور خودکار پخش نخواهد شد.

- `controls`
  - : اگر این attribute وجود داشته باشد، مرورگر کنترل‌هایی را برای مدیریت پخش صدا نمایش می‌دهد؛ از جمله حجم صدا، پرش زمان پخش (seeking) و توقف/ادامهٔ پخش.

- `controlslist`
  - : ویژگی [`controlslist`](https://wicg.github.io/controls-list/explainer.html) وقتی مشخص شود، به مرورگر کمک می‌کند تعیین کند چه کنترل‌هایی را برای المنت `audio` نمایش دهد؛ به شرطی که مرورگر مجموعه‌ای از کنترل‌های خودش را نشان دهد (یعنی وقتی attribute `controls` تنظیم شده باشد).

    مقادیر مجاز عبارتند از `nodownload`، `nofullscreen` و `noremoteplayback`.

- [`crossorigin`](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin)
  - : این ویژگی از نوع **شمارشی (enumerated)** است و مشخص می‌کند که آیا برای دریافت فایل صوتی مرتبط از CORS استفاده شود یا نه. منابعی که با CORS بارگیری شده‌اند (CORS-enabled resources) می‌توانند درون عنصر `<canvas>` بدون **آلوده شدن (tainted)** مجدداً استفاده شوند. مقادیر مجاز عبارتند از:
    - `anonymous`
      - : یک درخواست cross-origin بدون اعتبارنامه (credential) ارسال می‌کند. به عبارت دیگر، هدر `Origin:` را بدون کوکی، گواهی X.509 یا احراز هویت پایه HTTP می‌فرستد. اگر سرور به سایت مبدأ اعتبارنامه ندهد (با تنظیم نکردن هدر `Access-Control-Allow-Origin:`)، منبع **آلوده** می‌شود و استفاده از آن محدود می‌گردد.
    - `use-credentials`
      - : یک درخواست cross-origin همراه با اعتبارنامه ارسال می‌کند. یعنی هدر `Origin:` را همراه با کوکی، گواهی یا احراز هویت پایه HTTP می‌فرستد. اگر سرور از طریق هدر `Access-Control-Allow-Credentials:` به سایت مبدأ اعتبارنامه ندهد، منبع **آلوده** شده و استفاده از آن محدود می‌شود.

    در صورت отсутствие این ویژگی، منبع بدون درخواست CORS (یعنی بدون ارسال هدر `Origin:`) بارگیری می‌شود و در نتیجه نمی‌توان از آن به صورت غیر آلوده در عناصر `<canvas>` استفاده کرد. اگر مقدار نامعتبر باشد، طوری رفتار می‌شود که گویی کلیدواژه‌ی شمارشی **anonymous** وارد شده است. برای اطلاعات بیشتر به [ویژگی‌های تنظیمات CORS](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin) مراجعه کنید.

- `disableremoteplayback`
  - : یک ویژگی Boolean که برای غیرفعال کردن قابلیت پخش از راه دور (remote playback) در دستگاه‌هایی که از طریق فناوری‌های باسیم (HDMI, DVI و غیره) و بی‌سیم (Miracast, Chromecast, DLNA, AirPlay و غیره) متصل شده‌اند استفاده می‌شود. برای اطلاعات بیشتر به [مشخصات پیشنهادی Remote Playback API](https://w3c.github.io/remote-playback/#the-disableremoteplayback-attribute) مراجعه کنید.

    در Safari می‌توانید از [`x-webkit-airplay="deny"`](https://developer.apple.com/library/archive/documentation/AudioVideo/Conceptual/AirPlayGuide/OptingInorOutofAirPlay/OptingInorOutofAirPlay.html) به عنوان راهکار جایگزین استفاده کنید.

- `loading`  
  - : نحوه بارگیری صدا توسط مرورگر را مشخص می‌کند:
    - `eager`
      - : بلافاصله صدا را بارگیری می‌کند، بدون توجه به اینکه آیا صدا در حال حاضر در viewport قابل مشاهده است یا خیر (این مقدار پیش‌فرض است).
    - `lazy`
      - : بارگیری صدا را تا زمانی که کنترل‌ها به فاصله‌ای محاسبه‌شده از viewport برسند (مطابق تعریف مرورگر) به تأخیر می‌اندازد.

        > [!NOTE]
        > برای اینکه عناصر صوتی به صورت بصری با viewport برخورد کنند، باید قابل مشاهده باشند. مرورگرها از ویژگی `controls` برای قابل مشاهده کردن عناصر صوتی استفاده می‌کنند، بنابراین این ویژگی برای lazy loading ضروری است. صداهای lazy-loaded بدون ویژگی `controls` بارگیری نخواهند شد.

        Lazy loading از پهنای باند شبکه و فضای ذخیره‌سازی مورد نیاز برای مدیریت صدا جلوگیری می‌کند تا زمانی که اطمینان نسبتاً بالایی وجود داشته باشد که به آن نیاز خواهد بود. این کار عملکرد را در بیشتر موارد معمول بهبود می‌بخشد.

        صداهای lazy-loaded که در viewport بصری قرار دارند ممکن است هنگام رویداد `load` در `Window` (رویداد `Window.load`) هنوز دانلود نشده باشند. دلیل این است که این رویداد تنها بر اساس بارگیری‌های eager-fired صادر می‌شود؛ صداهای lazy-loaded حتی اگر در viewport بصری در بارگیری اولیه صفحه باشند، در نظر گرفته نمی‌شوند.

        بارگیری فقط زمانی به تأخیر می‌افتد که JavaScript فعال باشد. این یک اقدام ضد ردیابی (anti-tracking) است؛ زیرا اگر user agent از lazy loading در حالی که اسکریپت غیرفعال است پشتیبانی کند، همچنان امکان ردیابی موقعیت تقریبی اسکرول کاربر در طول یک جلسه توسط سایت وجود خواهد داشت؛ با قرار دادن استراتژیک صدا در نشانه‌گذاری صفحه به گونه‌ای که سرور بتواند تعداد درخواست‌های صوتی و زمان آن‌ها را ردیابی کند.

        > [!NOTE]
        > ویژگی `loading="lazy"` همچنین روی ویژگی [`autoplay`](#autoplay) تأثیر می‌گذارد؛ همان طور که در آن بخش از این صفحه توضیح داده شده است.

- `loop`
  - : یک ویژگی بولین (Boolean) است. اگر تنظیم شود، پخش‌کنندهٔ صدا پس از پایان فایل، به‌طور خودکار به ابتدا برمی‌گردد و دوباره پخش را شروع می‌کند.

- `muted`
  - : یک ویژگی بولین که وضعیت پیش‌فرض بی‌صدا بودن صدا را مشخص می‌کند. اگر این ویژگی وجود داشته باشد، صدا در ابتدا قطع است. مقدار پیش‌فرض آن `false` است، یعنی صدا هنگام پخش شنیده می‌شود.

    > **نکته:**
    > برای برگرداندن صدا، تنظیم `muted="false"` کار نمی‌کند؛ اگر این attribute وجود داشته باشد، صدا قطع باقی می‌ماند. برای برگرداندن صدا باید attribute را به‌کلی حذف کنید.

- `preload`
  - : این یک ویژگی شمارشی (enumerated) است و به مرورگر hint می‌دهد که نویسنده فکر می‌کند کدام رفتار تجربهٔ کاربری بهتری دارد. مقادیر ممکن:
    - `none`: یعنی صدا نباید از قبل بارگیری شود.
    - `metadata`: فقط متادیتای صدا (مثلاً طول فایل) دریافت می‌شود.
    - `auto`: یعنی کل فایل صوتی می‌تواند دانلود شود، حتی اگر کاربر قرار نباشد از آن استفاده کند.
    - _رشتهٔ خالی_: معادل مقدار `auto` است.

    مقدار پیش‌فرض در مرورگرهای مختلف متفاوت است. مشخصات (spec) توصیه می‌کند که `metadata` باشد.

    > **نکته:**
    >
    > - اگر صدا دارای ویژگی `loading="lazy"` باشد، رفتار `preload` فقط زمانی اعمال می‌شود که کنترل‌های صدا نزدیک viewport یا درون آن باشند.
    > - ویژگی `autoplay` اولویت بالاتری نسبت به `preload` دارد. اگر `autoplay` مشخص شده باشد، مشخص است که مرورگر باید برای پخش، دانلود صدا را شروع کند.
    > - مرورگر طبق مشخصات مجبور نیست از مقدار این attribute پیروی کند؛ این فقط یک hint است.

- `src`
  - : آدرس URL صدایی که قرار است嵌入 شود. این آدرس تحت [محدودیت‌های دسترسی HTTP (CORS)](/en-US/docs/Web/HTTP/Guides/CORS) است. این ویژگی اختیاری است؛ می‌توانید به‌جای آن از عنصر {{htmlelement("source")}} درون بلوک صدا برای مشخص کردن فایل صوتی استفاده کنید.

- `audioprocess`
  - : بافر ورودی یک `ScriptProcessorNode` آمادهٔ پردازش است.
- `canplay`
  - : مرورگر می‌تواند رسانه را پخش کند، اما تخمین می‌زند که دادهٔ کافی برای پخش تا انتها بدون توقف برای بافر کردن مجدد محتوا بارگذاری نشده است.
- `canplaythrough`
  - : مرورگر تخمین می‌زند که بتواند رسانه را تا انتها بدون توقف برای بافر کردن محتوا پخش کند.
- `complete`
  - : رندر یک `OfflineAudioContext` تمام شده است.
- `durationchange`
  - : ویژگی `duration` به‌روزرسانی شده است.
- `emptied`
  - : رسانه خالی شده است؛ برای مثال، این رویداد وقتی ارسال می‌شود که رسانه قبلاً بارگذاری شده (یا به‌طور جزئی بارگذاری شده) و متد `load()` برای بارگذاری مجدد آن فراخوانی شده باشد.
- `ended`
  - : پخش به دلیل رسیدن به انتهای رسانه متوقف شده است.
- `loadeddata`
  - : اولین فریم رسانه بارگذاری شده است.
- `loadedmetadata`
  - : فراداده بارگذاری شده است.
- `loadstart`
  - : هنگامی که مرورگر شروع به بارگذاری منبع می‌کند، این رویداد رخ می‌دهد.
- `pause`
  - : پخش متوقف شده است.
- `play`
  - : پخش شروع شده است.
- `playing`
  - : پخش پس از توقف یا تأخیر به دلیل کمبود داده، برای شروع آماده است.
- `ratechange`
  - : نرخ پخش تغییر کرده است.
- `seeked`
  - : یک عملیات seek کامل شد.
- `seeking`
  - : یک عملیات seek آغاز شد.
- `stalled`
  - : عامل کاربر در حال تلاش برای دریافت داده‌های رسانه است، اما داده به‌طور غیرمنتظره‌ای نمی‌رسد.
- `suspend`
  - : بارگذاری داده‌های رسانه معلق شده است.
- `timeupdate`
  - : زمان مشخص‌شده توسط ویژگی `currentTime` به‌روزرسانی شده است.
- `volumechange`
  - : صدا تغییر کرده است.
- `waiting`
  - : پخش به دلیل کمبود موقت داده متوقف شده است.

## نکات استفاده

همه مرورگرها از [فرمت‌های فایل](/en-US/docs/Web/Media/Guides/Formats/Containers) و [کدک‌های صوتی](/en-US/docs/Web/Media/Guides/Formats/Audio_codecs) یکسانی پشتیبانی نمی‌کنند؛ می‌توانید چندین منبع را درون عناصر `<source>` تو در تو قرار دهید و مرورگر از اولین موردی که پشتیبانی می‌کند استفاده خواهد کرد:

```html
<audio controls>
  <source src="myAudio.mp3" type="audio/mpeg" />
  <source src="myAudio.ogg" type="audio/ogg" />
  <p>
    Download <a href="myAudio.mp3" download="myAudio.mp3">MP3</a> or
    <a href="myAudio.ogg" download="myAudio.ogg">OGG</a> audio.
  </p>
</audio>
```

منبع صوتی را می‌توان روی هر URL معتبری تنظیم کرد، از جمله URLهای HTTP(S) و URLهای Data. هنگام استفاده از URLهای HTTP(S)، توجه داشته باشید که رفتار کش مرورگر روی تعداد دفعات درخواست فایل از سرور تأثیر می‌گذارد. URLهای Data داده صوتی را مستقیماً در HTML جاسازی می‌کنند؛ این کار برای فایل‌های صوتی کوچک مفید است، اما برای فایل‌های بزرگ‌تر توصیه نمی‌شود، چون حجم فایل HTML را افزایش می‌دهد.

وقتی از عناصر `<source>` استفاده می‌کنید، مرورگر هر منبع را به‌ترتیب و پشت‌سرهم بارگذاری می‌کند. اگر یک منبع شکست بخورد (مثلاً به دلیل آدرس نامعتبر یا فرمت پشتیبانی‌نشده)، منبع بعدی امتحان می‌شود و همین‌طور ادامه می‌یابد. بعد از شکست همه منابع، یک رویداد `error` روی عنصر `<audio>` رخ می‌دهد؛ رویدادهای `error` روی هر عنصر `<source>` به‌طور جداگانه فعال نمی‌شوند.

همچنین می‌توانید از [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) استفاده کنید تا مستقیماً جریان‌های صوتی را از کد JavaScript تولید و دستکاری کنید، به‌جای پخش فایل‌های صوتی از پیش موجود. می‌توانید در JavaScript خاصیت [`srcObject`](/en-US/docs/Web/API/HTMLMediaElement/srcObject) را روی یک شیء {{domxref("MediaStream")}} تنظیم کنید. این روش معمولاً برای جریان‌های صوتی زنده یا پردازش بلادرنگ صدا به کار می‌رود.

```js
const audioElement = document.querySelector("audio");
navigator.mediaDevices
  .getUserMedia({ audio: true })
  .then((stream) => {
    audioElement.srcObject = stream;
  })
  .catch((error) => {
    console.error("خطا در دسترسی به میکروفون", error);
  });
```

توجه داشته باشید که منابع `MediaStream` محدودیت‌هایی دارند: قابلیت جستجو (seek) ندارند و فقط از مجموعه محدودی از codecها پشتیبانی می‌کنند.

ما یک [راهنمای کامل و جامع درباره انواع فایل‌های رسانه‌ای](/en-US/docs/Web/Media/Guides/Formats) و [codecهای صوتی که می‌توان در آن‌ها استفاده کرد](/en-US/docs/Web/Media/Guides/Formats/Audio_codecs) ارائه داده‌ایم. همچنین [راهنمایی برای codecهای پشتیبانی‌شده در ویدئو](/en-US/docs/Web/Media/Guides/Formats/Video_codecs) در دسترس است.

سایر نکات استفاده:

- اگر ویژگی `controls` را مشخص نکنید، پخش‌کننده صوتی کنترل‌های پیش‌فرض مرورگر را نمایش نمی‌دهد. اما می‌توانید با استفاده از JavaScript و API {{domxref("HTMLMediaElement")}} کنترل‌های سفارشی خود را بسازید.
- برای کنترل دقیق روی محتوای صوتی، عناصر `HTMLMediaElement` رویدادهای مختلفی [ایجاد می‌کنند](/en-US/docs/Web/API/HTMLMediaElement#events). این رویدادها همچنین راهی برای نظارت بر فرایند دریافت صدا فراهم می‌کنند تا بتوانید خطاها را رصد کنید یا تشخیص دهید که چه زمانی داده کافی برای شروع پخش یا دستکاری وجود دارد.
- عناصر `<audio>` نمی‌توانند زیرنویس یا caption داشته باشند، برخلاف عناصر `<video>`. برای اطلاعات مفید و راه‌حل‌های جایگزین به مقاله [WebVTT and Audio](https://www.iandevlin.com/blog/2015/12/html5/webvtt-and-audio/) نوشته Ian Devlin مراجعه کنید.
- برای آزمایش محتوای fallback در مرورگرهایی که از عنصر پشتیبانی می‌کنند، می‌توانید `<audio>` را با یک عنصر ناموجود مثل `<notanaudio>` جایگزین کنید.

یک منبع خوب و عمومی برای استفاده از HTML `<audio>`، آموزش مقدماتی [ویدئو و صدا در HTML](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_video_and_audio) است.

### استایل‌دهی با CSS

عنصر `<audio>` ذاتاً خروجی بصری ندارد، مگر اینکه ویژگی `controls` مشخص شده باشد که در این صورت کنترل‌های پیش‌فرض مرورگر نمایش داده می‌شوند.

کنترل‌های پیش‌فرض به طور پیش‌فرض مقدار {{cssxref("display")}} برابر `inline` دارند و معمولاً بهتر است مقدار آن را به `block` تغییر دهید تا کنترل بیشتری روی موقعیت‌یابی و چیدمان داشته باشید، مگر اینکه بخواهید داخل یک بلوک متنی یا مشابه آن قرار گیرد.

می‌توانید کنترل‌های پیش‌فرض را با ویژگی‌هایی که روی کل بلوک تأثیر می‌گذارند، استایل دهید؛ مثلاً می‌توانید {{cssxref("border")}} و {{cssxref("border-radius")}}، {{cssxref("padding")}}، {{cssxref("margin")}} و ... تنظیم کنید. اما نمی‌توانید اجزای داخلی پخش‌کننده صوتی را جداگانه استایل دهید (مثلاً اندازه دکمه‌ها یا آیکون‌ها را تغییر دهید، فونت را عوض کنید و ...) و کنترل‌ها در مرورگرهای مختلف متفاوت هستند.

برای داشتن ظاهر و احساس یکسان در مرورگرهای مختلف، باید کنترل‌های سفارشی ایجاد کنید؛ این کنترل‌ها را می‌توان به هر شکلی که می‌خواهید نشانه‌گذاری و استایل داد و سپس با استفاده از JavaScript و API {{domxref("HTMLMediaElement")}} عملکرد آن‌ها را پیاده‌سازی کرد.

در مقالهٔ [مبانی استایل‌دهی پخش‌کنندهٔ ویدیو](/en-US/docs/Web/Media/Guides/Audio_and_video_delivery/Video_player_styling_basics) تکنیک‌های مفیدی برای استایل‌دهی ارائه شده است — این مقاله در بافت `<video>` نوشته شده، اما بسیاری از موارد آن برای `<audio>` نیز کاربرد دارد.

### تشخیص افزوده‌شدن و حذف ترک‌ها (tracks)

شما می‌توانید با استفاده از رویدادهای `addtrack` و `removetrack` متوجه شوید که چه زمانی ترک‌هایی به عنصر `<audio>` اضافه یا حذف می‌شوند. با این حال، این رویدادها مستقیماً به خود عنصر `<audio>` ارسال نمی‌شوند. در عوض، آن‌ها به شیء فهرست ترک که درون `HTMLMediaElement` عنصر `<audio>` قرار دارد و متناظر با نوع ترک اضافه‌شده است ارسال می‌شوند:

- `HTMLMediaElement.audioTracks`
  - : یک `AudioTrackList` که شامل همهٔ ترک‌های صوتی عنصر رسانه است. می‌توانید یک شنونده (listener) برای رویداد `addtrack` به این شیء اضافه کنید تا وقتی ترک صوتی جدیدی به عنصر اضافه می‌شود مطلع شوید.
- `HTMLMediaElement.videoTracks`
  - : برای اطلاع از اضافه‌شدن ترک‌های ویدیویی به عنصر، یک شنونده `addtrack` به این شیء `VideoTrackList` اضافه کنید.
- `HTMLMediaElement.textTracks`
  - : یک شنوندهٔ رویداد `addtrack` به این `TextTrackList` اضافه کنید تا از اضافه‌شدن ترک‌های متنی جدید به عنصر مطلع شوید.

> [!NOTE]
> اگرچه این یک عنصر `<audio>` است، همچنان فهرست ترک‌های ویدیویی و متنی دارد و در واقع می‌تواند برای نمایش ویدیو نیز استفاده شود، هرچند پیامدهای رابط کاربری ممکن است عجیب باشند.

برای مثال، برای تشخیص اینکه چه زمانی ترک‌های صوتی به یک عنصر `<audio>` اضافه یا حذف می‌شوند، می‌توانید از کدی مانند این استفاده کنید:

```js
const elem = document.querySelector("audio");

elem.audioTrackList.onaddtrack = (event) => {
  trackEditor.addTrack(event.track);
};

elem.audioTrackList.onremovetrack = (event) => {
  trackEditor.removeTrack(event.track);
};
```

این کد منتظر افزوده‌شدن و حذف‌شدن ترک‌های صوتی به/از عنصر می‌ماند و یک تابع فرضی را روی یک ویرایشگر ترک صدا می‌زند تا ترک را در فهرست ترک‌های موجود ویرایشگر ثبت یا از آن حذف کند.

همچنین می‌توانید از `addEventListener()` برای گوش دادن به رویدادهای `addtrack` و `removetrack` استفاده کنید.

## دسترس‌پذیری

صوتی که گفتار (دیالوگ) دارد باید شامل زیرنویس (caption) و رونوشت (transcript) باشد که محتوا را به‌دقت توصیف می‌کنند. زیرنویس‌ها که با استفاده از [WebVTT](/en-US/docs/Web/API/WebVTT_API) مشخص می‌شوند، به افراد کم‌شنوا امکان می‌دهند محتوای ضبط‌شده را هنگام پخش درک کنند، در حالی که رونوشت‌ها به افرادی که زمان بیشتری نیاز دارند اجازه می‌دهند محتوای ضبط‌شده را با سرعت و قالبی که برایشان راحت است مرور کنند.

اگر از خدمات زیرنویس خودکار استفاده می‌شود، مهم است که محتوای تولیدشده را بررسی کنید تا مطمئن شوید به‌طور دقیق منبع صوتی را بازنمایی می‌کند.

عنصر `<audio>` به‌طور مستقیم از WebVTT پشتیبانی نمی‌کند. باید کتابخانه یا فریم‌ورکی پیدا کنید که این قابلیت را فراهم کند، یا خودتان کد نمایش زیرنویس را بنویسید. یک گزینه این است که صدا را با استفاده از عنصر `<video>` پخش کنید که از WebVTT پشتیبانی می‌کند.

علاوه بر گفتار، زیرنویس‌ها و رونوشت‌ها باید موسیقی و افکت‌های صوتی‌ای را که اطلاعات مهمی منتقل می‌کنند نیز شناسایی کنند. این شامل احساسات و لحن صدا می‌شود. برای مثال، در WebVTT زیر، به استفاده از کروشه برای ارائهٔ بینش دربارهٔ لحن و احساس به بیننده توجه کنید؛ این کار می‌تواند به ایجاد حال‌وهوایی کمک کند که در غیر این صورت با موسیقی، صداهای غیرکلامی و افکت‌های صوتی مهم ایجاد می‌شود.

<!-- cSpell:ignore switchwatch Swisswatch -->

```plain
1
00:00:00 --> 00:00:45
[Energetic techno music]

2
00:00:46 --> 00:00:51
Welcome to the Time Keeper's podcast! In this episode we're discussing which Swisswatch is a wrist switchwatch?
```

همچنین کار خوبی است که برای کاربرانی که مرورگرشان از `<audio>` پشتیبانی نمی‌کند، محتوای جایگزین (مثلاً لینک مستقیم دانلود) قرار دهید:

```html
<audio controls>
  <source src="myAudio.mp3" type="audio/mpeg" />
  <source src="myAudio.ogg" type="audio/ogg" />
  <p>
    دانلود <a href="myAudio.mp3">MP3</a> یا
    <a href="myAudio.ogg" download="myAudio.ogg">OGG</a> صوتی.
  </p>
</audio>
```

- [Web Video Text Tracks Format (WebVTT)](/en-US/docs/Web/API/WebVTT_API)
- [WebAIM: Captions, Transcripts, and Audio Descriptions](https://webaim.org/techniques/captions/)
- [MDN Understanding WCAG, Guideline 1.2 explanations](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable#guideline_1.2_—_providing_text_alternatives_for_time-based_media)
- [Understanding Success Criterion 1.2.1 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-av-only-alt.html)
- [Understanding Success Criterion 1.2.2 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-captions.html)

## مثال‌ها

### استفاده‌ی پایه

مثال زیر استفاده‌ی پایه از عنصر `<audio>` برای پخش یک فایل OGG را نشان می‌دهد. به دلیل وجود attribute `autoplay`، اگر صفحه اجازه داشته باشد، فایل به‌طور خودکار پخش می‌شود. همچنین محتوای جایگزین هم در آن گنجانده شده است.

```html
<!-- پخش پایه‌ی صدا -->
<audio src="AudioTest.ogg" autoplay>
  <a href="AudioTest.ogg" download="AudioTest.ogg">دانلود صدای OGG</a>.
</audio>
```

برای جزئیات بیشتر دربارهٔ زمان کارکرد autoplay، نحوهٔ دریافت مجوز برای استفاده از آن، و زمان مناسب استفاده از آن، به [راهنمای autoplay](/en-US/docs/Web/Media/Guides/Autoplay) مراجعه کنید.

### عنصر `<audio>` با عنصر `<source>`

این مثال مشخص می‌کند که کدام track صوتی با استفاده از attribute `src` روی یک عنصر `<source>` تو در تو (نه مستقیماً روی `<audio>`) درج شود. همیشه مفید است که نوع MIME فایل را در attribute `type` قرار دهید، چون مرورگر می‌تواند فوراً تشخیص دهد که آیا می‌تواند آن فایل را پخش کند یا نه و در غیر این صورت وقت تلف نمی‌کند.

```html
<audio controls>
  <source src="foo.wav" type="audio/wav" />
  <a href="foo.wav" download="foo.wav">دانلود صدای WAV</a>.
</audio>
```

### `<audio>` با چندین عنصر `<source>`

این مثال شامل چندین عنصر `<source>` است. مرورگر ابتدا سعی می‌کند اولین عنصر (Opus) را بارگیری کند، اگر بتواند آن را پخش کند؛ در غیر این صورت به سراغ دومین (Vorbis) و در نهایت MP3 می‌رود:

```html
<audio controls>
  <source src="foo.opus" type="audio/ogg; codecs=opus" />
  <source src="foo.ogg" type="audio/ogg; codecs=vorbis" />
  <source src="foo.mp3" type="audio/mpeg" />
</audio>
```

## خلاصه‌ی فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">دسته‌بندی محتوا (Content categories)</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a>، phrasing content، embedded content. اگر دارای ویژگی <a href="#controls"><code>controls</code></a> باشد: interactive content و palpable content.
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز (Permitted content)</th>
      <td>
        اگر عنصر دارای ویژگی <a href="#src"><code>src</code></a> باشد: صفر یا چند عنصر {{HTMLElement("track")}} به دنبال محتوای شفافی که شامل هیچ عنصر رسانه‌ای <code>&lt;audio&gt;</code> یا {{HTMLElement("video")}} نباشد.<br />در غیر این صورت: صفر یا چند عنصر {{HTMLElement("source")}} به دنبال صفر یا چند عنصر {{HTMLElement("track")}} و سپس محتوای شفافی که شامل هیچ عنصر <code>&lt;audio&gt;</code> یا {{HTMLElement("video")}} نباشد.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ (Tag omission)</th>
      <td>هیچ‌کدام؛ هر دو تگ شروع و پایان اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز (Permitted parents)</th>
      <td>هر عنصری که محتوای جاسازی‌شده (embedded content) را بپذیرد.</td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی (Implicit ARIA role)</th>
      <td>
        <a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role">نقش متناظری ندارد</a>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز (Permitted ARIA roles)</th>
      <td><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role"><code>application</code></a></td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td>{{domxref("HTMLAudioElement")}}</td>
    </tr>
  </tbody>
</table>

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## جستارهای وابسته

- [فناوری‌های رسانه‌ای وب](/en-US/docs/Web/Media)
  - [فرمت‌های کانتینر (انواع فایل)](/en-US/docs/Web/Media/Guides/Formats/Containers)
  - [راهنمای کدک‌های صوتی مورد استفاده در وب](/en-US/docs/Web/Media/Guides/Formats/Audio_codecs)

- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)
- {{domxref("HTMLAudioElement")}}
- {{htmlelement("source")}}
- {{htmlelement("video")}}
- [بخش یادگیری: ویدئو و صدا در HTML](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_video_and_audio)
- [مبانی صوتی بین‌مرورگری](/en-US/docs/Web/Media/Guides/Audio_and_video_delivery/Cross-browser_audio_basics)