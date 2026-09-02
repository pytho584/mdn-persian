---
title: "MediaSession: setPositionState() method"
short-title: setPositionState()
slug: Web/API/MediaSession/setPositionState
page-type: web-api-instance-method
browser-compat: api.MediaSession.setPositionState
---

{{APIRef("Media Session API")}}

متد **`setPositionState()`** از رابط {{domxref("MediaSession")}} برای به‌روزرسانی موقعیت و سرعت پخش رسانه‌ی در حال پخشِ سند جاری استفاده می‌شود، تا دستگاه کاربر بتواند آن را در هر نوع رابطی که جزئیات مربوط به رسانه‌ی در حال پخش را نمایش می‌دهد، ارائه کند. این قابلیت به‌ویژه زمانی مفید است که کد شما پخش‌کننده‌ای را برای نوعی رسانه پیاده‌سازی می‌کند که مستقیماً توسط مرورگر پشتیبانی نمی‌شود.

این متد را روی شیء `mediaSession` از شیء `navigator` صدا بزنید: {{domxref("navigator.mediaSession", "mediaSession")}}.

## نحو (Syntax)

```js-nolint
setPositionState()
setPositionState(stateDict)
```

### پارامترها

- `stateDict` {{optional_inline}}
  - : یک شیء که اطلاعات به‌روزشده درباره‌ی موقعیت و سرعت پخش رسانه‌ی در حال پخش سند را فراهم می‌کند. اگر این شیء خالی باشد، اطلاعات وضعیت پخش موجود پاک می‌شود. این شیء می‌تواند پارامترهای زیر را داشته باشد:
    - `duration` {{optional_inline}}
      - : یک مقدار اعشاری که کل مدت زمان رسانه‌ی فعلی را بر حسب ثانیه نشان می‌دهد. این مقدار باید همیشه عددی مثبت باشد؛ بی‌نهایت مثبت ({{jsxref("Infinity")}}) نشان‌دهنده‌ی رسانه‌ای است که پایان مشخصی ندارد، مانند یک پخش زنده.
    - `playbackRate` {{optional_inline}}
      - : یک مقدار اعشاری که نرخ پخش رسانه را به صورت نسبت به سرعت عادی پخش نشان می‌دهد. بنابراین مقدار ۱ یعنی پخش با سرعت عادی، ۲ یعنی پخش با سرعت دو برابر، و به همین ترتیب. مقادیر منفی نشان‌دهنده‌ی پخش معکوس هستند؛ ۱- یعنی پخش معکوس با سرعت عادی، ۲- یعنی پخش معکوس با سرعت دو برابر، و الی آخر.
    - `position` {{optional_inline}}
      - : یک مقدار اعشاری که آخرین موقعیت پخش گزارش‌شده‌ی رسانه را بر حسب ثانیه نشان می‌دهد. این مقدار باید همیشه مثبت باشد.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها (Exceptions)

- {{jsxref("TypeError")}}
  - : این خطا می‌تواند در شرایط زیر رخ دهد:
    - `duration` شیء مشخص‌شده وجود نداشته باشد، منفی باشد یا `null` باشد.
    - `position` آن منفی باشد یا از `duration` بزرگ‌تر باشد.
    - `playbackRate` آن صفر باشد.

## مثال‌ها

در زیر تابعی داریم که وضعیت موقعیتِ track جاریِ {{domxref('MediaSession')}} را به‌روزرسانی می‌کند.

```js
function updatePositionState() {
  navigator.mediaSession.setPositionState({
    duration: audioEl.duration,
    playbackRate: audioEl.playbackRate,
    position: audioEl.currentTime,
  });
}
```

می‌توانیم از این تابع هنگام به‌روزرسانی {{domxref('MediaMetadata')}} و در فراخوانی‌های (callback) اکشن‌ها استفاده کنیم، مانند مثال زیر.

```js
navigator.mediaSession.setActionHandler("seekbackward", (details) => {
  // مدت زمانی که باید بپریم
  const skipTime = details.seekOffset || 10;

  // تنظیم موقعیت جدید
  audioEl.currentTime = Math.max(audioEl.currentTime - skipTime, 0);
  updatePositionState();
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
