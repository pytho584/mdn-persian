---
title: "AudioSession: type property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioSession/type"
translated_by: "n8n + AI"
---

---
title: "AudioSession: type property"
short-title: type
slug: Web/API/AudioSession/type
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.AudioSession.type
---

{{APIRef("Audio Session API")}}{{SeeCompatTable}}

**`type`** ویژگی از رابط {{domxref("AudioSession")}} نوع جلسه صوتی را برمی‌گرداند یا تنظیم می‌کند.

نوع جلسه صوتی ماهیت کلی خروجی صوتی یک صفحه وب را توصیف می‌کند و به پلتفرم اجازه می‌دهد تعیین کند که صدای مبتنی بر وب چگونه باید با سایر صداهای در حال پخش روی دستگاه تعامل داشته باشد.

## مقدار

یک رشته که نوع جلسه صوتی را نشان می‌دهد. مقادیر ممکن عبارتند از:

- `"auto"`
  - : مقدار پیش‌فرض. عامل کاربر به طور خودکار بهترین نوع جلسه صوتی را بر اساس APIهای صوتی استفاده‌شده توسط صفحه انتخاب می‌کند.
- `"playback"`
  - : صدا برای پخش رسانه، مانند پخش ویدیو یا موسیقی، پادکست‌ها و غیره. این یک نوع انحصاری است که سایر صداهای پخش روی دستگاه را متوقف می‌کند، اما ممکن است به صداهای غیر پخش (مانند صداهای اعلان) اجازه ادامه دهد.
- `"transient"`
  - : صدای گذرا، مانند صداهای اعلان. این نوع معمولاً روی سایر صداها پخش می‌شود و ممکن است باعث شود که آن‌ها کاهش حجم پیدا کنند (duck).
- `"transient-solo"`
  - : صدای گذرای انحصاری، مانند مسیریابی یا پیام‌های صوتی. این نوع تمام صداهای دیگر را متوقف یا ساکت می‌کند و به طور انحصاری پخش می‌شود. وقتی صدا به پایان رسید، صدای قبلی ممکن است از سر گرفته شود.
- `"ambient"`
  - : صدای محیطی که می‌تواند با سایر انواع صدا ترکیب شود. این برای زمانی مفید است که کاربران می‌خواهند صدا را از چندین صفحه یا برنامه ترکیب کنند.
- `"play-and-record"`
  - : صدا برای ضبط یا ارتباطات بلادرنگ. این زمانی مناسب است که از میکروفون استفاده می‌شود یا در برنامه‌های کنفرانس ویدیویی.

## مثال‌ها

### تنظیم نوع جلسه صوتی برای پخش رسانه

```js
// Set the audio session type for music playback
navigator.audioSession.type = "playback";

// Play music
audioElement.play();
```

### راه‌اندازی کنفرانس ویدیویی

```js
// Set up for video conferencing (both playback and recording)
navigator.audioSession.type = "play-and-record";

// Start video call
const stream = await navigator.mediaDevices.getUserMedia({
  audio: true,
  video: true,
});
localVideo.srcObject = stream;
```

### استفاده از صدای گذرا برای اعلان‌ها

```js
// Set transient type for a notification sound
navigator.audioSession.type = "transient";

// Play notification
notificationSound.play();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("AudioSession")}}
- {{domxref("Navigator.audioSession")}}
- [Audio Session API](/en-US/docs/Web/API/Audio_Session_API)