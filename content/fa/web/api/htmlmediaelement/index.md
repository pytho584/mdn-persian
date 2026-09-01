---
title: "HTMLMediaElement"
---

---
title: HTMLMediaElement
slug: Web/API/HTMLMediaElement
page-type: web-api-interface
browser-compat: api.HTMLMediaElement
---

{{APIRef("HTML DOM")}}

رابطِ **`HTMLMediaElement`** ویژگی‌ها و متدهایی را به {{domxref("HTMLElement")}} می‌افزاید که برای پشتیبانی از قابلیت‌های پایه مرتبط با رسانه، که در صدا و ویدیو مشترک هستند، لازم است.

عنصرهای {{domxref("HTMLVideoElement")}} و {{domxref("HTMLAudioElement")}} هر دو از این رابط به ارث می‌برند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌هایی را از اجداد خود، {{domxref("HTMLElement")}}، {{domxref("Element")}}، {{domxref("Node")}} و {{domxref("EventTarget")}} به ارث می‌برد._

- {{domxref("HTMLMediaElement.audioTracks")}} {{ReadOnlyInline}}
  - : یک {{domxref("AudioTrackList")}} که فهرست شیءهای {{domxref("AudioTrack")}} موجود در عنصر را فهرست می‌کند.
- {{domxref("HTMLMediaElement.autoplay")}}
  - : یک مقدار بولی که ویژگی HTML [`autoplay`](/en-US/docs/Web/HTML/Reference/Elements/video#autoplay) را منعکس می‌کند و نشان می‌دهد که آیا پخش باید به محض فراهم شدن رسانه کافی، بدون وقفه به‌طور خودکار آغاز شود یا نه.

    > [!NOTE]
    > پخش خودکار صدا وقتی کاربر انتظارش را ندارد یا نمی‌خواهد، تجربه کاربری بدی است و در بیشتر موارد باید از آن اجتناب شود، هرچند استثناهایی نیز وجود دارد. برای اطلاعات بیشتر به [راهنمای پخش خودکار برای رسانه و Web Audio APIs](/en-US/docs/Web/Media/Guides/Autoplay) مراجعه کنید. به خاطر داشته باشید که مرورگرها ممکن است درخواست‌های پخش خودکار را نادیده بگیرند، بنابراین باید مطمئن شوید کد شما به کارکرد پخش خودکار وابسته نیست.

- {{domxref("HTMLMediaElement.buffered")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("TimeRanges")}} را برمی‌گرداند که محدوده‌هایی از منبع رسانه را نشان می‌دهد که مرورگر در لحظه دسترسی به ویژگی `buffered` بافر کرده است (در صورت وجود).
- {{domxref("HTMLMediaElement.controls")}}
  - : یک مقدار بولی که ویژگی HTML [`controls`](/en-US/docs/Web/HTML/Reference/Elements/video#controls) را منعکس می‌کند و نشان می‌دهد که آیا آیتم‌های رابط کاربری برای کنترل منبع باید نمایش داده شوند یا نه.
- {{domxref("HTMLMediaElement.controlsList")}}
  - : یک {{domxref("DOMTokenList")}} را برمی‌گرداند که به عامل کاربر کمک می‌کند تا هنگامی که مجموعه کنترل‌های خودش را نمایش می‌دهد، انتخاب کند کدام کنترل در عنصر رسانه نمایش داده شود. `DOMTokenList` یک یا چند مقدار از سه مقدار ممکن را می‌گیرد: `nodownload`، `nofullscreen` و `noremoteplayback`.
- {{domxref("HTMLMediaElement.crossOrigin")}}
  - : یک رشته که [تنظیم CORS](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin) را برای این عنصر رسانه نشان می‌دهد.
- {{domxref("HTMLMediaElement.currentSrc")}} {{ReadOnlyInline}}
  - : یک رشته با URL مطلق منبع رسانه انتخاب‌شده را برمی‌گرداند.
- {{domxref("HTMLMediaElement.currentTime")}}
  - : یک مقدار ممیز شناور با دقت دوگانه که زمان فعلی پخش را بر حسب ثانیه نشان می‌دهد؛ اگر رسانه شروع به پخش نکرده باشد و جابه‌جایی (seek) انجام نشده باشد، این مقدار زمان پخش اولیه رسانه است. مقداردهی این ویژگی، رسانه را به زمان جدید می‌برد. زمان نسبت به خط زمانی رسانه مشخص می‌شود.
- {{domxref("HTMLMediaElement.defaultMuted")}}
  - : یک مقدار بولی که ویژگی HTML [`muted`](/en-US/docs/Web/HTML/Reference/Elements/video#muted) را منعکس می‌کند و نشان می‌دهد که آیا خروجی صوتی عنصر رسانه باید به‌طور پیش‌فرض بی‌صدا باشد یا نه.
- {{domxref("HTMLMediaElement.defaultPlaybackRate")}}
  - : یک `double` که نرخ پخش پیش‌فرض رسانه را نشان می‌دهد.
- {{domxref("HTMLMediaElement.disableRemotePlayback")}}
  - : یک مقدار بولی که وضعیت پخش از راه دور را تنظیم یا برمی‌گرداند و نشان می‌دهد که آیا عنصر رسانه مجاز به داشتن رابط کاربری پخش از راه دور هست یا نه.
- {{domxref("HTMLMediaElement.duration")}} {{ReadOnlyInline}}
  - : یک مقدار ممیز شناور با دقت دوگانه فقط‌خواندنی که مدت کل رسانه را بر حسب ثانیه نشان می‌دهد. اگر داده رسانه‌ای در دسترس نباشد، مقدار بازگشتی `NaN` است. اگر رسانه دارای طول نامحدود باشد (مانند رسانه پخش زنده، رسانه تماس WebRTC یا موارد مشابه)، مقدار `Infinity` خواهد بود.
- {{domxref("HTMLMediaElement.ended")}} {{ReadOnlyInline}}
  - : یک مقدار بولی برمی‌گرداند که نشان می‌دهد آیا عنصر رسانه پخش را به پایان رسانده است یا نه.
- {{domxref("HTMLMediaElement.error")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("MediaError")}} برای آخرین خطا برمی‌گرداند، یا اگر خطایی رخ نداده باشد `null` را برمی‌گرداند.
- {{domxref("HTMLMediaElement.loading")}} {{experimental_inline}}
  - : یک رشته که نشان می‌دهد مرورگر باید رسانه را بلافاصله (`eager`) بارگیری کند یا زمانی که لازم شود (`lazy`). برای اطلاعات بیشتر، ویژگی‌های HTML [`<video loading>`](/en-US/docs/Web/HTML/Reference/Elements/video#loading) و [`<audio loading>`](/en-US/docs/Web/HTML/Reference/Elements/audio#loading) را ببینید.
- {{domxref("HTMLMediaElement.loop")}}
  - : یک مقدار بولی که ویژگی HTML [`loop`](/en-US/docs/Web/HTML/Reference/Elements/video#loop) را منعکس می‌کند و نشان می‌دهد که آیا عنصر رسانه باید هنگام رسیدن به پایان، دوباره شروع شود یا نه.
- {{domxref("HTMLMediaElement.mediaKeys")}} {{ReadOnlyInline}} {{SecureContext_Inline}}
  - : یک شیء {{domxref("MediaKeys")}} برمی‌گرداند که مجموعه کلیدهایی است که عنصر می‌تواند برای رمزگشایی داده‌های رسانه در طول پخش از آن‌ها استفاده کند. اگر کلیدی در دسترس نباشد، می‌تواند `null` باشد.
- {{domxref("HTMLMediaElement.muted")}}
  - : یک مقدار بولی که تعیین می‌کند صدا بی‌صدا است یا نه. اگر صدا بی‌صدا باشد `true` و در غیر این صورت `false` است.
- {{domxref("HTMLMediaElement.networkState")}} {{ReadOnlyInline}}
  - : یک `unsigned short` (شمارشی) برمی‌گرداند که وضعیت فعلی دریافت رسانه از طریق شبکه را نشان می‌دهد.
- {{domxref("HTMLMediaElement.paused")}} {{ReadOnlyInline}}
  - : یک مقدار بولی برمی‌گرداند که نشان می‌دهد عنصر رسانه متوقف شده است یا نه.
- {{domxref("HTMLMediaElement.playbackRate")}}
  - : یک `double` که نرخی را نشان می‌دهد که رسانه با آن در حال پخش است.
- {{domxref("HTMLMediaElement.played")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref('TimeRanges')}} برمی‌گرداند که محدوده‌هایی از منبع رسانه را که مرورگر پخش کرده است، در صورت وجود، شامل می‌شود.
- {{domxref("HTMLMediaElement.preload")}}
  - : یک رشته که ویژگی HTML [`preload`](/en-US/docs/Web/HTML/Reference/Elements/video#preload) را منعکس می‌کند و نشان می‌دهد چه داده‌ای باید از پیش بارگیری شود (در صورت وجود). مقادیر ممکن عبارت‌اند از: `none`، `metadata`، `auto`.
- {{domxref("HTMLMediaElement.preservesPitch")}}
  - : یک مقدار بولی که تعیین می‌کند زیروبمی صدا حفظ شود یا نه. اگر روی `false` تنظیم شود، زیروبمی با سرعت صدا تنظیم می‌شود.
- {{domxref("HTMLMediaElement.readyState")}} {{ReadOnlyInline}}
  - : یک `unsigned short` (شمارشی) برمی‌گرداند که وضعیت آمادگی رسانه را نشان می‌دهد.
- {{domxref("HTMLMediaElement.remote")}} {{ReadOnlyInline}}
  - : یک نمونه از شیء {{domxref("RemotePlayback")}} مرتبط با عنصر رسانه را برمی‌گرداند.
- {{domxref("HTMLMediaElement.seekable")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref('TimeRanges')}} برمی‌گرداند که شامل بازه‌های زمانی است که کاربر می‌تواند به آن‌ها پرش کند (در صورت وجود).
- {{domxref("HTMLMediaElement.seeking")}} {{ReadOnlyInline}}
  - : یک مقدار بولی برمی‌گرداند که نشان می‌دهد آیا رسانه در حال جابه‌جایی به موقعیت جدید است یا نه.
- {{domxref("HTMLMediaElement.sinkId")}} {{ReadOnlyInline}} {{SecureContext_Inline}}
  - : یک رشته برمی‌گرداند که شناسه یکتای دستگاه صوتی تحویل‌دهنده خروجی است، یا اگر دستگاه صوتی پیش‌فرض عامل کاربر استفاده می‌شود، یک رشته خالی برمی‌گرداند.
- {{domxref("HTMLMediaElement.src")}}
  - : یک رشته که ویژگی HTML [`src`](/en-US/docs/Web/HTML/Reference/Elements/video#src) را منعکس می‌کند و شامل URL منبع رسانه‌ای است که باید استفاده شود.
- {{domxref("HTMLMediaElement.srcObject")}}
  - : یک شیء که به‌عنوان منبع رسانه مرتبط با `HTMLMediaElement` عمل می‌کند، یا اگر اختصاص نیافته باشد `null` است.
- {{domxref("HTMLMediaElement.textTracks")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref('TextTrackList')}} برمی‌گرداند که شامل فهرستی از شیءهای {{domxref("TextTrack")}} موجود در عنصر است.
- {{domxref("HTMLMediaElement.videoTracks")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref('VideoTrackList')}} برمی‌گرداند که شامل فهرستی از شیءهای {{domxref("VideoTrack")}} موجود در عنصر است.
- {{domxref("HTMLMediaElement.volume")}}
  - : یک `double` که بلندی صدا را از 0.0 (سکوت) تا 1.0 (بلندترین) نشان می‌دهد.

## ویژگی‌های منسوخ‌شده

این ویژگی‌ها منسوخ‌شده هستند و نباید استفاده شوند، حتی اگر مرورگری همچنان از آن‌ها پشتیبانی کند.

- {{domxref("HTMLMediaElement.controller")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : یک شیء {{domxref("MediaController")}} که کنترلگر رسانه اختصاص‌داده‌شده به عنصر را نشان می‌دهد، یا اگر هیچ کنترلگری اختصاص نیافته باشد `null` است.
- {{domxref("HTMLMediaElement.mediaGroup")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : یک رشته که ویژگی HTML `mediagroup` را منعکس می‌کند و نام گروه عناصری را که به آن تعلق دارد نشان می‌دهد. یک گروه از عناصر رسانه، یک {{domxref('MediaController')}} مشترک دارند.
- `HTMLMediaElement.mozAudioCaptured` {{ReadOnlyInline}} {{Non-standard_Inline}} {{Deprecated_Inline}}
  - : یک مقدار بولی برمی‌گرداند. مرتبط با ضبط جریان صوتی است.
- `HTMLMediaElement.mozFragmentEnd` {{Non-standard_Inline}} {{Deprecated_Inline}}
  - : یک `double` که دسترسی به زمان پایان قطعه را فراهم می‌کند اگر عنصر رسانه یک URI قطعه برای `currentSrc` داشته باشد؛ در غیر این صورت برابر با مدت رسانه است.

## متدهای نمونه

_این رابط همچنین متدهایی را از اجداد خود، {{domxref("HTMLElement")}}، {{domxref("Element")}}، {{domxref("Node")}} و {{domxref("EventTarget")}} به ارث می‌برد._

- {{domxref("HTMLMediaElement.addTextTrack()")}}
  - : یک شیء {{domxref("TextTrack")}} جدید (مانند یک مسیر برای زیرنویس) به عنصر رسانه اضافه می‌کند. این فقط یک رابط برنامه‌ای است و بر DOM تأثیری ندارد.
- {{domxref("HTMLMediaElement.captureStream()")}}
  - : یک {{domxref("MediaStream")}} برمی‌گرداند؛ جریانی از محتوای رسانه را ضبط می‌کند.
- {{domxref("HTMLMediaElement.canPlayType()")}}
  - : با دریافت رشته‌ای که نوع MIME رسانه را مشخص می‌کند (احتمالاً با [پارامتر `codecs`](/en-US/docs/Web/Media/Guides/Formats/codecs_parameter) شامل شده)، `canPlayType()` رشته `probably` را برمی‌گرداند اگر رسانه باید قابل پخش باشد، `maybe` را اگر اطلاعات کافی برای تعیین پخش‌شدن یا نشدن رسانه وجود نداشته باشد، یا یک رشته خالی را اگر رسانه قابل پخش نباشد.
- {{domxref("HTMLMediaElement.fastSeek()")}}
  - : به سرعت با دقت کم به زمان داده‌شده می‌پرد.
- {{domxref("HTMLMediaElement.getStartDate()")}}
  - : یک شیء {{jsxref("Date")}} برمی‌گرداند که تاریخ و زمان واقعی جهان را متناظر با آغاز رسانه نشان می‌دهد. برای پخش زنده، این زمان شروع پخش در سرور است که ممکن است پیش از تماشای کاربر باشد.
- {{domxref("HTMLMediaElement.load()")}}
  - : رسانه را به ابتدا بازنشانی می‌کند و بهترین منبع موجود را از میان منابع ارائه‌شده با استفاده از ویژگی [`src`](/en-US/docs/Web/HTML/Reference/Elements/video#src) یا عنصر {{HTMLElement("source")}} انتخاب می‌کند.
- {{domxref("HTMLMediaElement.pause()")}}
  - : پخش رسانه را متوقف می‌کند.
- {{domxref("HTMLMediaElement.play()")}}
  - : پخش رسانه را آغاز می‌کند.
- {{domxref("HTMLMediaElement.seekToNextFrame()")}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : به فریم بعدی در رسانه می‌پرد. این متد غیراستاندارد و آزمایشی، امکان هدایت دستی خواندن و رندر رسانه با سرعت سفارشی را فراهم می‌کند، یا امکان حرکت فریم‌به‌فریم در رسانه برای انجام فیلتر یا سایر عملیات را می‌دهد.
- {{domxref("HTMLMediaElement.setMediaKeys()")}} {{SecureContext_Inline}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند. کلیدهای {{domxref("MediaKeys")}} مورد استفاده برای رمزگشایی رسانه در طول پخش را تنظیم می‌کند.
- {{domxref("HTMLMediaElement.setSinkId()")}} {{SecureContext_Inline}}
  - : شناسه دستگاه صوتی مورد استفاده برای خروجی را تنظیم می‌کند و یک {{jsxref("Promise")}} برمی‌گرداند. این فقط زمانی کار می‌کند که برنامه مجاز به استفاده از دستگاه مشخص‌شده باشد.

## متدهای منسوخ‌شده

_این متدها منسوخ‌شده هستند و نباید استفاده شوند، حتی اگر مرورگری همچنان از آن‌ها پشتیبانی کند._

- {{domxref("HTMLMediaElement.captureStream", "HTMLMediaElement.mozCaptureStream()")}} {{Non-standard_Inline}}
  - : معادل با پیشوند Firefox از {{domxref("HTMLMediaElement.captureStream()")}}. برای جزئیات به [سازگاری مرورگر](/en-US/docs/Web/API/HTMLMediaElement/captureStream#browser_compatibility) آن مراجعه کنید.
- `HTMLMediaElement.mozCaptureStreamUntilEnded()` {{Non-standard_Inline}} {{Deprecated_Inline}}
  - : یک متد غیراستاندارد و منسوخ برای ضبط جریان تا پایان آن.
- `HTMLMediaElement.mozGetMetadata()` {{Non-standard_Inline}} {{Deprecated_Inline}}
  - : یک {{jsxref('Object')}} برمی‌گرداند که حاوی ویژگی‌هایی است که فراداده منبع رسانه در حال پخش را به‌صورت جفت‌های `{key: value}` نشان می‌دهد. هر بار که متد فراخوانی می‌شود، یک نسخه جداگانه از داده‌ها برگردانده می‌شود. این متد باید پس از رویداد [`loadedmetadata`](/en-US/docs/Web/API/HTMLMediaElement/loadedmetadata_event) فراخوانی شود.

## رویدادها

_رویدادها را از والد خود، {{domxref("HTMLElement")}} به ارث می‌برد._

برای گوش‌دادن به این رویدادها از {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید یا یک شنونده رویداد به ویژگی `oneventname` این رابط نسبت دهید.

- {{domxref("HTMLMediaElement.abort_event", 'abort')}}
  - : هنگامی رخ می‌دهد که منبع به‌طور کامل بارگیری نشده است، اما نه در نتیجه یک خطا.
- {{domxref("HTMLMediaElement.canplay_event", 'canplay')}}
  - : هنگامی رخ می‌دهد که عامل کاربر می‌تواند رسانه را پخش کند، اما تخمین می‌زند که **داده کافی** برای پخش رسانه تا پایان، بدون نیاز به توقف برای بافر بیشتر محتوا، بارگیری نشده است.
- {{domxref("HTMLMediaElement.canplaythrough_event", 'canplaythrough')}}
  - : هنگامی رخ می‌دهد که عامل کاربر می‌تواند رسانه را پخش کند و تخمین می‌زند که داده کافی برای پخش رسانه تا پایان، بدون نیاز به توقف برای بافر بیشتر محتوا، بارگیری شده است.
- {{domxref("HTMLMediaElement.durationchange_event", 'durationchange')}}
  - : هنگامی رخ می‌دهد که ویژگی مدت (duration) به‌روزرسانی شده است.
- {{domxref("HTMLMediaElement.emptied_event", 'emptied')}}
  - : هنگامی رخ می‌دهد که رسانه خالی شده است؛ برای مثال، وقتی رسانه قبلاً بارگیری شده (یا به‌طور جزئی بارگیری شده) و متد {{domxref("HTMLMediaElement.load()")}} برای بارگیری دوباره آن فراخوانی می‌شود.
- {{domxref("HTMLMediaElement.encrypted_event", 'encrypted')}}
  - : هنگامی رخ می‌دهد که داده‌های اولیه‌سازی (initialization data) در رسانه یافت می‌شود که نشان می‌دهد رسانه رمزگذاری شده است.
- {{domxref("HTMLMediaElement.ended_event", 'ended')}}
  - : هنگامی رخ می‌دهد که پخش با رسیدن به پایان رسانه (\<audio> یا \<video>) یا به دلیل در دسترس نبودن داده بیشتر متوقف می‌شود.
- {{domxref("HTMLMediaElement.error_event", 'error')}}
  - : هنگامی رخ می‌دهد که منبع به دلیل یک خطا قابل بارگیری نبود.
- {{domxref("HTMLMediaElement.loadeddata_event", 'loadeddata')}}
  - : هنگامی رخ می‌دهد که اولین فریم رسانه به پایان بارگیری شده است.
- {{domxref("HTMLMediaElement.loadedmetadata_event", 'loadedmetadata')}}
  - : هنگامی رخ می‌دهد که فراداده بارگیری شده است.
- {{domxref("HTMLMediaElement.loadstart_event", 'loadstart')}}
  - : هنگامی رخ می‌دهد که مرورگر شروع به بارگیری یک منبع کرده است.
- {{domxref("HTMLMediaElement.pause_event", 'pause')}}
  - : هنگامی رخ می‌دهد که درخواست توقف پخش پردازش می‌شود و فعالیت وارد حالت توقف شده است؛ این حالت معمولاً زمانی رخ می‌دهد که متد {{domxref("HTMLMediaElement.pause()")}} رسانه فراخوانی می‌شود.
- {{domxref("HTMLMediaElement.play_event", 'play')}}
  - : هنگامی رخ می‌دهد که ویژگی `paused` در نتیجه متد {{domxref("HTMLMediaElement.play()")}} یا ویژگی `autoplay` از `true` به `false` تغییر می‌کند.
- {{domxref("HTMLMediaElement.playing_event", "playing")}}
  - : هنگامی رخ می‌دهد که پخش پس از توقف یا تأخیر به دلیل کمبود داده، آماده شروع است.
- {{domxref("HTMLMediaElement.progress_event", "progress")}}
  - : به‌طور متناوب در حالی که مرورگر منبع را بارگیری می‌کند رخ می‌دهد.
- {{domxref("HTMLMediaElement.ratechange_event", 'ratechange')}}
  - : هنگامی رخ می‌دهد که نرخ پخش تغییر کرده است.
- {{domxref("HTMLMediaElement.seeked_event", 'seeked')}}
  - : هنگامی رخ می‌دهد که یک عملیات جابه‌جایی (seek) تکمیل می‌شود.
- {{domxref("HTMLMediaElement.seeking_event", 'seeking')}}
  - : هنگامی رخ می‌دهد که یک عملیات جابه‌جایی آغاز می‌شود.
- {{domxref("HTMLMediaElement.stalled_event", 'stalled')}}
  - : هنگامی رخ می‌دهد که عامل کاربر در حال تلاش برای دریافت داده رسانه است، اما به‌طور غیرمنتظره‌ای داده دریافت نمی‌شود.
- {{domxref("HTMLMediaElement.suspend_event", 'suspend')}}
  - : هنگامی رخ می‌دهد که بارگیری داده رسانه معلق شده است.
- {{domxref("HTMLMediaElement.timeupdate_event", 'timeupdate')}}
  - : هنگامی رخ می‌دهد که زمان نشان‌داده‌شده توسط ویژگی {{domxref("HTMLMediaElement.currentTime", "currentTime")}} به‌روزرسانی شده است.
- {{domxref("HTMLMediaElement.volumechange_event", 'volumechange')}}
  - : هنگامی رخ می‌دهد که بلندی صدا تغییر کرده است.
- {{domxref("HTMLMediaElement.waiting_event", 'waiting')}}
  - : هنگامی رخ می‌دهد که پخش به دلیل کمبود موقت داده متوقف شده است.
- {{domxref("HTMLMediaElement.waitingforkey_event", 'waitingforkey')}}
  - : هنگامی رخ می‌دهد که پخش ابتدا در حالی که منتظر کلید است مسدود می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

### مراجع

- عنصرهای HTML {{HTMLElement("video")}} و {{HTMLElement("audio")}}
- رابط‌های {{domxref("HTMLVideoElement")}} و {{domxref("HTMLAudioElement")}} که از `HTMLMediaElement` مشتق شده‌اند

### راهنماها

- [فناوری‌های رسانه وب](/en-US/docs/Web/Media)
- حوزه یادگیری: [ویدیو و صوت HTML](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_video_and_audio)
- [راهنمای نوع رسانه و قالب](/en-US/docs/Web/Media/Guides/Formats)
- [مدیریت مشکلات پشتیبانی از رسانه در محتوای وب](/en-US/docs/Web/Media/Guides/Formats/Support_issues)