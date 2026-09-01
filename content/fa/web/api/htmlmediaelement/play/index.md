---
title: "HTMLMediaElement: play() method"
---

---
title: "HTMLMediaElement: play() method"
short-title: play()
slug: Web/API/HTMLMediaElement/play
page-type: web-api-instance-method
browser-compat: api.HTMLMediaElement.play
---

{{APIRef("HTML DOM")}}

متد **`play()`** در {{domxref("HTMLMediaElement")}} تلاش می‌کند پخش رسانه را آغاز کند. این متد یک {{jsxref("Promise")}} برمی‌گرداند که وقتی پخش با موفقیت شروع شود، برآورده (resolve) می‌شود. اگر شروع پخش به هر دلیلی، مانند مشکلات مجوز، صورت نگیرد، پرامیس رد (reject) می‌شود.

## نحو

```js-nolint
play()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که وقتی پخش شروع شده باشد برآورده می‌شود؛ یا اگر به هر دلیلی نتوان پخش را شروع کرد، رد می‌شود.

> [!NOTE]
> مرورگرهای منتشرشده پیش از ۲۰۱۹ ممکن است از `play()` مقداری برنگردانند.

### استثناها

هندلر **رد** پرامیس با یک شیء {{domxref("DOMException")}} فراخوانی می‌شود که به‌عنوان تنها پارامتر ورودی به آن داده می‌شود (و نه یک استثنای سنتی که پرتاب شود). خطاهای احتمالی عبارت‌اند از:

- `NotAllowedError` {{domxref("DOMException")}}
  - : در مواردی ارائه می‌شود که عامل کاربر (مرورگر) یا سیستم‌عامل اجازهٔ پخش رسانه را در بافتار یا موقعیت فعلی ندهد. ممکن است مرورگر از کاربر بخواهد پخش رسانه را با کلیک روی دکمهٔ «پخش» به‌صورت صریح شروع کند؛ برای مثال به دلیل [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy).
- `NotSupportedError` {{domxref("DOMException")}}
  - : در مواردی ارائه می‌شود که منبع رسانه (که ممکن است برای مثال به صورت {{domxref("MediaStream")}}، {{domxref("MediaSource")}}، {{domxref("Blob")}} یا {{domxref("File")}} مشخص شده باشد) قالب رسانه‌ای پشتیبانی‌شده‌ای را نشان ندهد.

سایر استثناها نیز ممکن است بسته به جزئیات پیاده‌سازی مرورگر، پیاده‌سازی پخش‌کنندهٔ رسانه و موارد دیگر گزارش شوند.

## یادداشت‌های استفاده

اگرچه اصطلاح «پخش خودکار» معمولاً به صفحه‌هایی اشاره دارد که بلافاصله پس از بارگذاری شروع به پخش رسانه می‌کنند، سیاست‌های پخش خودکار مرورگرها برای هرگونه پخش رسانه که توسط اسکریپت آغاز می‌شود نیز اعمال می‌شود، از جمله فراخوانی‌های `play()`.

اگر عامل کاربر ({{Glossary("user agent")}}) به‌گونه‌ای پیکربندی شده باشد که اجازهٔ پخش خودکار یا پخش آغازشده توسط اسکریپت را ندهد، فراخوانی `play()` باعث می‌شود پرامیس بازگشتی بلافاصله با `NotAllowedError` رد شود. وب‌سایت‌ها باید برای این وضعیت آماده باشند. برای مثال، یک وب‌سایت نباید رابط کاربری‌ای ارائه دهد که فرض را بر شروع خودکار پخش بگذارد؛ بلکه باید رابط کاربری خود را بر اساس برآورده شدن یا رد شدن پرامیس بازگشتی به‌روزرسانی کند. برای اطلاعات بیشتر به [مثال](#examples) زیر مراجعه کنید.

> [!NOTE]
> متد `play()` ممکن است باعث شود از کاربر خواسته شود برای پخش رسانه اجازه بدهد، که می‌تواند تأخیری پیش از برآورده شدن پرامیس بازگشتی ایجاد کند. مطمئن شوید که کد شما انتظار پاسخ فوری ندارد.

برای اطلاعات عمیق‌تر دربارهٔ پخش خودکار و مسدودسازی آن، مقالهٔ [راهنمای پخش خودکار برای رسانه و Web Audio APIs](/en-US/docs/Web/Media/Guides/Autoplay) را ببینید.

## مثال‌ها

### تأیید شروع پخش و مدیریت حالت‌ها

این مثال نشان می‌دهد که چگونه تأیید کنیم پخش آغاز شده است و چگونه با مسدود شدن پخش خودکار به‌شکلی مناسب برخورد کنیم.

این مثال هنگام اجرا، ابتدا ارجاع‌هایی به عنصر {{HTMLElement("video")}} و همچنین عنصر {{HTMLElement("button")}} که برای روشن و خاموش کردن پخش استفاده می‌شود جمع‌آوری می‌کند. سپس یک کنترل‌کنندهٔ رویداد برای رویداد {{domxref("Element/click_event", "click")}} روی دکمهٔ تغییر وضعیت تنظیم می‌کند و تلاش می‌کند پخش را به‌صورت خودکار با فراخوانی تابع `playVideo()` که [`async`](/en-US/docs/Web/JavaScript/Reference/Statements/async_function) است آغاز کند.

تابع کمکی `toggleButton()` به ما این امکان را می‌دهد که تعیین کنیم وقتی یک مقدار بولی نشان‌دهندهٔ وضعیت پخش به آن می‌دهیم (مثلاً `toggleButton(true)`) چه اتفاقی در کد بیفتد. اگر پخش موفق باشد، متن دکمه و [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) آن به «مکث» تغییر می‌کند. اگر پخش ناموفق باشد، دکمه و `aria-label` «پخش» را نشان می‌دهند. با این کار، با نظارت بر برآورده یا رد شدن {{jsxref("Promise")}} بازگشتی از `play()`، اطمینان حاصل می‌شود که `playButton` با وضعیت پخش هماهنگ بماند:

```html live-sample___handling-states
<div class="video-box">
  <video
    id="video"
    width="480"
    loop
    src="/shared-assets/videos/flower.mp4"></video>
  <button type="button" id="play-button" aria-label="Play"></button>
</div>
```

```js live-sample___handling-states
let videoElem = document.getElementById("video");
let playButton = document.getElementById("play-button");

playButton.addEventListener("click", handlePlayButton);
playVideo();

function toggleButton(playing) {
  if (playing) {
    playButton.textContent = "Pause";
    playButton.setAttribute("aria-label", "Pause");
  } else {
    playButton.textContent = "Play";
    playButton.setAttribute("aria-label", "Play");
  }
}

async function playVideo() {
  try {
    await videoElem.play();
    toggleButton(true);
  } catch (err) {
    toggleButton(false);
  }
}

function handlePlayButton() {
  if (videoElem.paused) {
    playVideo();
  } else {
    videoElem.pause();
    toggleButton(false);
  }
}
```

```css hidden live-sample___handling-states
.video-box {
  position: relative;
}

#video {
  border: 2px solid black;
}

#play-button {
  position: absolute;
  top: 10px;
  left: 10px;
  padding: 8px 12px;
  background-color: black;
  color: white;
  border: none;
  cursor: pointer;
}
```

{{embedlivesample("handling-states", , "300")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [فناوری‌های رسانهٔ وب](/en-US/docs/Web/Media)
- یادگیری: [ویدئو و صوتی HTML](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_video_and_audio)
- [راهنمای پخش خودکار برای رسانه و Web Audio APIs](/en-US/docs/Web/Media/Guides/Autoplay)
- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)