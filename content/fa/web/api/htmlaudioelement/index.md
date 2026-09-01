---
title: HTMLAudioElement
slug: Web/API/HTMLAudioElement
page-type: web-api-interface
browser-compat: api.HTMLAudioElement
---

{{APIRef("HTML DOM")}}

رابط **`HTMLAudioElement`** دسترسی به خصوصیات عناصر {{HTMLElement("audio")}} و همچنین روش‌هایی برای دستکاری آن‌ها فراهم می‌کند.

این عنصر بر پایه رابط {{domxref("HTMLMediaElement")}} است و خصوصیات و روش‌ها را از آن به ارث می‌برد.

{{InheritanceDiagram}}

## سازنده (Constructor)

- {{domxref("HTMLAudioElement.Audio", "Audio()")}}
  - : یک شیء `HTMLAudioElement` جدید ایجاد و بازمی‌گرداند. در صورت ارائه URL فایل، فرایند بارگذاری فایل صوتی را نیز آغاز می‌کند.

## خصوصیات نمونه (Instance properties)

_هیچ خصوصیت خاصی ندارد؛ خصوصیات را از والد خود {{domxref("HTMLMediaElement")}} و از {{domxref("HTMLElement")}} به ارث می‌برد._

## روش‌های نمونه (Instance methods)

_روش‌ها را از والد خود {{domxref("HTMLMediaElement")}} و از {{domxref("HTMLElement")}} به ارث می‌برد. هیچ روش خاص خود را ارائه نمی‌دهد._

## مثال‌ها

### استفاده پایه

می‌توانید یک `HTMLAudioElement` را کاملاً با جاوااسکریپت با استفاده از سازنده {{domxref("HTMLAudioElement.Audio", "Audio()")}} ایجاد کنید:

```js
const audioElement = new Audio("car_horn.wav");
```

سپس می‌توانید متد `play()` را روی عنصر فراخوانی کنید:

```js
audioElement.play();
```

> [!NOTE]
> یک مشکل رایج، تلاش برای پخش یک عنصر صوتی بلافاصله پس از بارگذاری صفحه است. سیاست پیش‌فرض پخش خودکار مرورگرهای مدرن از این کار جلوگیری می‌کند. برای بهترین روش‌ها و راه‌حل‌های جایگزین به [Firefox](https://hacks.mozilla.org/2019/02/firefox-66-to-block-automatically-playing-audible-video-and-audio/) و [Chrome](https://developer.chrome.com/blog/autoplay/) مراجعه کنید.

برخی از پرکاربردترین خصوصیات عنصر صوتی عبارتند از {{domxref("HTMLMediaElement.src", "src")}}، {{domxref("HTMLMediaElement.currentTime", "currentTime")}}، {{domxref("HTMLMediaElement.duration", "duration")}}، {{domxref("HTMLMediaElement.paused", "paused")}}، {{domxref("HTMLMediaElement.muted", "muted")}} و {{domxref("HTMLMediaElement.volume", "volume")}}. این قطعه کد مدت زمان فایل صوتی را در یک متغیر کپی می‌کند:

```js
const audioElement = new Audio("car_horn.wav");
audioElement.addEventListener("loadeddata", () => {
  let duration = audioElement.duration;
  // The duration variable now holds the duration (in seconds) of the audio clip
});
```

## رویدادها

_رویدادها را با استفاده از [`addEventListener()`](/en-US/docs/Web/API/EventTarget/addEventListener) یا با انتساب یک شنونده رویداد به ویژگی `oneventname` این رابط گوش دهید._

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [فناوری‌های رسانه وب](/en-US/docs/Web/Media)
- [تحویل صدا و ویدئو](/en-US/docs/Web/Media/Guides/Audio_and_video_delivery)
- عنصر HTML که این رابط را پیاده‌سازی می‌کند: {{HTMLElement("audio")}}.