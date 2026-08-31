---
title: "Audio Session API"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Audio_Session_API"
translated_by: "n8n + AI"
---

---
title: Audio Session API
slug: Web/API/Audio_Session_API
page-type: web-api-overview
status:
  - experimental
browser-compat:
  - api.AudioSession
  - api.Navigator.audioSession
---

{{DefaultAPISidebar("Audio Session API")}}{{SeeCompatTable}}

**Audio Session API** مکانیزمی را برای برنامه‌های وب فراهم می‌کند تا نحوه تعامل صدای خود با سایر صداهای در حال پخش روی دستگاه را کنترل کنند.

## مفاهیم و کاربرد

افراد به‌طور فزاینده‌ای رسانه را از طریق وب مصرف می‌کنند: این رسانه اکنون کانال اصلی برای دسترسی به محتوای صوتی و تصویری است. با این حال، رسانه در وب اغلب فاقد یکپارچگی بی‌درز با پلتفرم‌های زیرین است. Audio Session API این شکاف را با اجازه دادن به توسعه‌دهندگان برای مشخص کردن نحوه تعامل صدای تولید‌شده توسط برنامه‌های وب‌شان با صدای سایر برنامه‌ها روی دستگاه برطرف می‌کند — به عنوان مثال، پخش هم‌زمان با سایر صداها، کاهش بلندی آن (کاهش حجم آن)، یا توقف آن به‌طوری که صدای خودشان به تنهایی پخش شود.

یک صفحه وب می‌تواند پردازش صوتی را به روش‌های مختلف با استفاده از APIهایی مانند {{domxref("HTMLMediaElement")}} و [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) انجام دهد. یک **جلسه صوتی** نمایانگر صدای تجمیع‌شده تولید‌شده توسط یک صفحه وب است و آن را قادر می‌سازد تا ماهیت کلی خروجی صوتی خود را بیان کند.

### انواع جلسه صوتی

این API از چند نوع جلسه صوتی پشتیبانی می‌کند که نوع صدای تولید‌شده توسط یک برنامه را مشخص می‌کنند:

- `"auto"` — پیش‌فرض. عامل کاربر به‌طور خودکار بهترین نوع را بر اساس APIهای صوتی مورد استفاده انتخاب می‌کند.
- `"playback"` — برای پخش رسانه مانند موسیقی یا ویدیو. این نوع نباید با پخش صوتی دیگر ترکیب شود.
- `"transient"` — برای صداهای کوتاه مانند اعلان‌ها. این نوع معمولاً روی سایر صداها پخش می‌شود.
- `"transient-solo"` — برای صدایی که باید به‌صورت انحصاری پخش شود و سایر صداها را متوقف کند (مانند پیام‌های صوتی).
- `"ambient"` — برای صدایی که می‌تواند با سایر منابع صوتی ترکیب شود.
- `"play-and-record"` — برای برنامه‌هایی که هم صدا پخش می‌کنند و هم ضبط می‌کنند، مانند کنفرانس ویدیویی.

## رابط‌ها

- {{domxref("AudioSession")}} {{Experimental_Inline}}
  - : رابط اصلی برای کنترل رفتار جلسه صوتی، از جمله تنظیم نوع جلسه صوتی.

### افزونه‌های رابط‌های دیگر

- {{domxref("Navigator.audioSession")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : شیء {{domxref("AudioSession")}} را برای سند فعلی برمی‌گرداند.

## مثال‌ها

### راه‌اندازی یک جلسه صوتی کنفرانس ویدیویی

در یک برنامه کنفرانس ویدیویی، هم پخش و هم ضبط به‌طور هم‌زمان مورد نیاز است؛ این چیزی است که Audio Session API می‌تواند در آن کمک کند.

ابتدا، نوع جلسه صوتی را به `"play-and-record"` تنظیم می‌کنیم تا به پلتفرم اطلاع دهیم که این صفحه به دسترسی میکروفون در کنار خروجی صوتی نیاز دارد. در پلتفرم‌های پشتیبان، این ممکن است مسیریابی صدای سیستم را تنظیم کند (مثلاً استفاده از گوشی به جای بلندگو در دستگاه‌های تلفن همراه) و از قطع شدن تماس توسط صدای سایر برنامه‌ها جلوگیری کند.

```js
navigator.audioSession.type = "play-and-record";
```

سپس، جریان‌های رسانه‌ای را برای تماس ویدیویی طبق معمول تنظیم می‌کنیم. پلتفرم اکنون صدای تولید‌شده توسط این جریان‌ها را مطابق نوع جلسه `"play-and-record"` مدیریت خواهد کرد.

```js
// Start playing remote media
remoteVideo.srcObject = remoteMediaStream;
remoteVideo.play();

// Start capturing local media
navigator.mediaDevices
  .getUserMedia({ audio: true, video: true })
  .then((stream) => {
    localVideo.srcObject = stream;
  });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("AudioSession")}}
- {{domxref("Navigator.audioSession")}}
- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)
- {{domxref("HTMLMediaElement")}}