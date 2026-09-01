```markdown
---
title: "HTMLAudioElement: Audio() constructor"
short-title: Audio()
slug: Web/API/HTMLAudioElement/Audio
page-type: web-api-constructor
browser-compat: api.HTMLAudioElement.Audio
---

{{APIRef("HTML DOM")}}

سازنده‌ی **`Audio()`** یک شیء جدید از نوع {{domxref("HTMLAudioElement")}} ایجاد کرده و بازمی‌گرداند. این شیء می‌تواند به یک سند (document) متصل شود تا کاربر با آن تعامل داشته باشد و/یا به آن گوش دهد، یا می‌توان از آن به‌صورت خارج از صفحه (offscreen) برای مدیریت و پخش صدا استفاده کرد.

## Syntax

```js-nolint
new Audio()
new Audio(url)
```

### پارامترها

- `url` {{optional_inline}}
  - : یک رشته (string) اختیاری حاوی نشانی اینترنتی (URL) یک فایل صوتی که باید به عنصر صوتی جدید مرتبط شود.

### مقدار بازگشتی

یک شیء جدید از نوع {{domxref("HTMLAudioElement")}} که برای پخش صدا از فایل مشخص‌شده توسط `url` پیکربندی شده است. ویژگی {{domxref("HTMLMediaElement.preload", "preload")}} این شیء جدید روی `auto` تنظیم می‌شود و ویژگی `src` آن به نشانی اینترنتی مشخص‌شده یا در صورت نبودن نشانی، به `null` تنظیم می‌گردد. اگر نشانی اینترنتی مشخص شده باشد، مرورگر قبل از بازگرداندن شیء جدید، بارگذاری منبع رسانه‌ای را به‌صورت _ناهمزمان_ (asynchronously) آغاز می‌کند.

## نکات استفاده

همچنین می‌توانید از روش‌های دیگری برای ایجاد عنصر استفاده کنید، مانند متد {{domxref("Document.createElement", "createElement()")}} متعلق به شیء {{domxref("document")}}، برای ساخت یک {{domxref("HTMLAudioElement")}} جدید.

### تشخیص زمان شروع پخش

سه راه برای تشخیص اینکه چه زمانی به اندازه‌ی کافی از فایل صوتی بارگذاری شده است تا پخش آغاز شود وجود دارد:

- مقدار ویژگی {{domxref("HTMLMediaElement.readyState", "readyState")}} را بررسی کنید. اگر برابر با `HTMLMediaElement.HAVE_FUTURE_DATA` باشد، به اندازه‌ی کافی داده برای شروع پخش و ادامه‌ی آن برای حداقل مدت کوتاهی در دسترس است. اگر برابر با `HTMLMediaElement.HAVE_ENOUGH_DATA` باشد، داده‌ی کافی در دسترس است که با توجه به سرعت دانلود فعلی، بتوانید صدا را بدون وقفه تا انتها پخش کنید.
- به رویداد {{domxref("HTMLMediaElement.canplay_event", "canplay")}} گوش دهید. این رویداد به عنصر `<audio>` ارسال می‌شود زمانی که به اندازه‌ی کافی صدا برای شروع پخش موجود باشد، هرچند ممکن است وقفه‌هایی رخ دهد.
- به رویداد {{domxref("HTMLMediaElement.canplaythrough_event", "canplaythrough")}} گوش دهید. این رویداد زمانی ارسال می‌شود که تخمین زده شود صدا باید بتواند بدون وقفه تا انتها پخش شود.

رویکرد مبتنی بر رویداد بهترین روش است:

```js
myAudioElement.addEventListener("canplaythrough", (event) => {
  /* the audio is now playable; play it if permissions allow */
  myAudioElement.play();
});
```

### استفاده و مدیریت حافظه

اگر همه‌ی ارجاع‌ها به یک عنصر صوتی که با استفاده از سازنده‌ی `Audio()` ایجاد شده است حذف شوند، خود عنصر توسط مکانیزم جمع‌آوری زباله (garbage collection) زمان اجرای جاوااسکریپت از حافظه حذف نخواهد شد، در صورتی که پخش در حال انجام باشد. در عوض، صدا به پخش ادامه می‌دهد و شیء تا پایان پخش در حافظه باقی می‌ماند. در آن زمان، شیء مشمول جمع‌آوری زباله می‌شود.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [فناوری‌های رسانه‌ای وب](/en-US/docs/Web/Media)
- عنصر HTML پیاده‌سازی‌کننده‌ی این رابط: {{HTMLElement("audio")}}.
```