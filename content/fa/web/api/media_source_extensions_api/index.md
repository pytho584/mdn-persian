---
title: Media Source API
slug: Web/API/Media_Source_Extensions_API
page-type: web-api-overview
spec-urls:
  - https://w3c.github.io/media-source/
  - https://w3c.github.io/media-playback-quality/
---

{{DefaultAPISidebar("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}

رابط برنامه‌نویسی **Media Source** که به طور رسمی با نام **Media Source Extensions** (**MSE**) شناخته می‌شود، قابلیت‌هایی را برای پخش رسانه‌های جریانی مبتنی بر وب بدون نیاز به افزونه فراهم می‌کند. با استفاده از MSE، می‌توان جریان‌های رسانه‌ای را از طریق JavaScript ایجاد کرد و با استفاده از عناصر {{htmlelement("audio")}} و {{htmlelement("video")}} پخش نمود.

## مفاهیم و کاربرد

پخش ویدئو و صدا در برنامه‌های وب بدون نیاز به افزونه چند سالی است که امکان‌پذیر شده است، اما ویژگی‌های پایه‌ای ارائه‌شده تنها برای پخش تک‌تک آهنگ‌های کامل مفید بوده‌اند. به عنوان مثال، نمی‌توانیم arraybufferها را ترکیب یا تقسیم کنیم. تا همین اواخر، رسانه‌های جریانی حوزه انحصاری Flash بودند، با فناوری‌هایی مانند Flash Media Server که جریان‌های ویدئویی را با استفاده از پروتکل RTMP ارائه می‌کردند.

### استاندارد MSE

با Media Source Extensions (MSE)، این وضعیت در حال تغییر است. MSE به ما امکان می‌دهد تا URI تدریجی منفرد معمولی که به عناصر رسانه‌ای داده می‌شود را با یک ارجاع به شیء `MediaSource` جایگزین کنیم. این شیء یک ظرف برای اطلاعاتی مانند وضعیت آمادگی رسانه برای پخش، و ارجاعات به چندین شیء `SourceBuffer` است که تکه‌های مختلف رسانه تشکیل‌دهنده کل جریان را نمایش می‌دهند. MSE کنترل دقیق‌تری بر میزان و دفعات دریافت محتوا و همچنین کنترل جزئی بر جزئیات مصرف حافظه، مانند زمان تخلیه بافرها، به ما می‌دهد. این API پایه‌ای برای ساخت مشتری‌های پخش تطبیقی با نرخ بیت (مانند آنهایی که از DASH یا HLS استفاده می‌کنند) بر روی API توسعه‌پذیر خود فراهم می‌کند.

ایجاد دارایی‌هایی که با MSE در مرورگرهای مدرن کار کنند فرآیندی دشوار است و زمان، توان محاسباتی و انرژی قابل توجهی می‌طلبد. استفاده از ابزارهای خارجی برای تبدیل محتوا به قالبی مناسب ضروری است. در حالی که پشتیبانی مرورگرها از ظروف رسانه‌ای مختلف با MSE ناقص است، استفاده از کدک ویدئویی H.264، کدک صوتی AAC و قالب ظرف MP4 یک مبنا رایج است. MSE همچنین یک API برای تشخیص زمان اجرای پشتیبانی از ظروف و کدک‌ها فراهم می‌کند.

اگر نیاز به کنترل صریح کیفیت ویدئو در طول زمان، نرخ دریافت محتوا یا نرخ تخلیه حافظه ندارید، برچسب‌های {{htmlelement("video")}} و {{htmlelement("source")}} ممکن است راه حلی ساده و کافی باشند.

### DASH

پخش تطبیقی پویا از طریق HTTP (DASH) یک پروتکل برای مشخص کردن نحوه دریافت محتوای تطبیقی است. این پروتکل در واقع لایه‌ای است که بر روی MSE برای ساخت مشتری‌های پخش تطبیقی با نرخ بیت ساخته شده است. در حالی که پروتکل‌های دیگری مانند HTTP Live Streaming (HLS) نیز وجود دارند، DASH بیشترین پشتیبانی پلتفرمی را دارد.

DASH منطق زیادی را از پروتکل شبکه به منطق برنامه سمت کلاینت منتقل می‌کند و از پروتکل ساده‌تر HTTP برای دریافت فایل‌ها استفاده می‌کند. در واقع، می‌توان DASH را با یک سرور فایل ایستا ساده پشتیبانی کرد که برای CDNها نیز عالی است. این در تضاد مستقیم با راه‌حل‌های قبلی پخش جریانی است که نیاز به مجوزهای گران‌قیمت برای پیاده‌سازی‌های اختصاصی و غیراستاندارد پروتکل سرویس‌گیرنده/سرور داشتند.

دو مورد استفاده رایج برای DASH شامل تماشای محتوای «درخواستی» (on demand) یا «زنده» (live) است. حالت درخواستی به توسعه‌دهنده اجازه می‌دهد تا دارایی‌ها را به چندین وضوح با کیفیت‌های مختلف تبدیل کند.

محتوای پروفایل زنده به دلیل تبدیل و پخش ممکن است تأخیر ایجاد کند، بنابراین DASH برای ارتباطات بلادرنگ مانند [WebRTC](/en-US/docs/Web/API/WebRTC_API) مناسب نیست. با این حال، می‌تواند تعداد قابل توجهی بیشتری از اتصالات کلاینت را نسبت به WebRTC پشتیبانی کند.

ابزارهای رایگان و متن‌باز متعددی برای تبدیل محتوا و آماده‌سازی آن برای استفاده با DASH، سرورهای فایل DASH و کتابخانه‌های کلاینت DASH نوشته‌شده با JavaScript وجود دارد. مقاله [پخش تطبیقی DASH برای ویدئوی HTML](/en-US/docs/Web/API/Media_Source_Extensions_API/DASH_Adaptive_Streaming) نمونه‌ای از نحوه استفاده از DASH با MSE را ارائه می‌دهد.

### در دسترس بودن در workerها

از Chrome 108 به بعد، ویژگی‌های MSE در workerهای اختصاصی (dedicated workers) {{domxref("Web Workers API", "web workers", "", "nocode")}} در دسترس هستند که امکان بهبود عملکرد هنگام دستکاری {{domxref("MediaSource")}} و {{domxref("SourceBuffer")}} را فراهم می‌کنند. برای پخش رسانه، از ویژگی {{domxref("MediaSource.handle")}} برای دریافت ارجاع به یک شیء {{domxref("MediaSourceHandle")}} استفاده می‌شود. این شیء یک نماینده برای `MediaSource` است که می‌تواند به رشته اصلی بازگردانده شده و از طریق ویژگی {{domxref("HTMLMediaElement.srcObject")}} به یک عنصر رسانه متصل شود.

برای یک مثال زنده، به [نمایش MSE در Workerها توسط Matt Wolenetz](https://wolenetz.github.io/mse-in-workers-demo/mse-in-workers-demo.html) مراجعه کنید.

## رابط‌ها

- {{domxref("MediaSource")}}
  - : یک منبع رسانه را نشان می‌دهد که قرار است از طریق یک شیء {{domxref("HTMLMediaElement")}} پخش شود.
- {{domxref("MediaSourceHandle")}}
  - : یک نماینده برای {{domxref("MediaSource")}} که می‌تواند از یک worker اختصاصی به رشته اصلی منتقل شده و از طریق ویژگی {{domxref("HTMLMediaElement.srcObject")}} به یک عنصر رسانه متصل شود.
- {{domxref("SourceBuffer")}}
  - : یک تکه از رسانه را نشان می‌دهد که قرار است از طریق یک شیء `MediaSource` به {{domxref("HTMLMediaElement")}} ارسال شود.
- {{domxref("SourceBufferList")}}
  - : یک لیست ظرف ساده برای چندین شیء `SourceBuffer`.
- {{domxref("ManagedMediaSource")}}
  - : یک {{domxref("MediaSource")}} که به طور فعال محتوای حافظه خود را مدیریت می‌کند. بر خلاف یک `MediaSource` معمولی، یک `ManagedMediaSource` می‌تواند در هر زمان به دلایلی مانند محدودیت‌های حافظه یا سخت‌افزار، محتوا را از بافرهای منبع خود تخلیه کند.
- {{domxref("ManagedSourceBuffer")}}
  - : یک {{domxref("SourceBuffer")}} ایجاد شده توسط یک `ManagedMediaSource`. رویدادهای {{domxref("ManagedSourceBuffer.bufferedchange_event", "bufferedchange")}} را برای اطلاع‌رسانی به برنامه در هنگام تغییر محدوده‌های بافر شده، از جمله زمانی که عامل کاربر محتوا را تخلیه می‌کند، پرتاب می‌کند.
- {{domxref("BufferedChangeEvent")}}
  - : شیء رویداد برای رویداد {{domxref("ManagedSourceBuffer.bufferedchange_event", "bufferedchange")}} که شامل {{domxref("TimeRanges")}} نشان‌دهنده محدوده‌های بافر شده اضافه و حذف شده است.
- {{domxref("VideoPlaybackQuality")}}
  - : شامل اطلاعاتی درباره کیفیت ویدئوی در حال پخش توسط یک عنصر {{htmlelement("video")}} است، مانند تعداد فریم‌های افتاده یا خراب. توسط متد {{domxref("HTMLVideoElement.getVideoPlaybackQuality()")}} بازگردانده می‌شود.

### افزونه‌هایی برای سایر رابط‌ها

- {{domxref("HTMLMediaElement.buffered")}}
  - : یک شیء {{domxref("TimeRanges")}} را بازمی‌گرداند که محدوده‌های بافر شده منبع رسانه (در صورت وجود) را در لحظه دسترسی به ویژگی `buffered` نشان می‌دهد.
- {{domxref("HTMLMediaElement.seekable")}}
  - : یک شیء {{domxref('TimeRanges')}} را بازمی‌گرداند که شامل محدوده‌های زمانی است که کاربر می‌تواند به آنها جستجو کند، در صورت وجود.
- {{domxref("HTMLMediaElement.srcObject")}}
  - : یک شیء ارائه‌دهنده رسانه که نشان‌دهنده منبع رسانه‌ای است که در `HTMLMediaElement` جاری پخش می‌شود یا پخش شده است، یا اگر تخصیص داده نشده باشد `null`.
- {{domxref("HTMLVideoElement.getVideoPlaybackQuality()")}}
  - : یک شیء {{domxref("VideoPlaybackQuality")}} را برای ویدئوی در حال پخش بازمی‌گرداند.
- {{domxref("AudioTrack.sourceBuffer")}}، {{domxref("VideoTrack.sourceBuffer")}}، {{domxref("TextTrack.sourceBuffer")}}
  - : {{domxref("SourceBuffer")}}ای که آهنگ مورد نظر را ایجاد کرده است را بازمی‌گرداند.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [تبدیل دارایی‌ها برای Media Source Extensions](/en-US/docs/Web/API/Media_Source_Extensions_API/Transcoding_assets_for_MSE)
- استفاده از MSE برای ایجاد یک سرویس پخش جریانی پایه (در دست تهیه)
- استفاده از MPEG DASH برای ایجاد یک برنامه پخش جریانی (در دست تهیه)
- عناصر {{htmlelement("audio")}} و {{htmlelement("video")}}.
- {{domxref("HTMLMediaElement")}}، {{domxref("HTMLVideoElement")}}، {{domxref("HTMLAudioElement")}}.