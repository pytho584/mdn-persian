---
title: "Animation: updatePlaybackRate() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Animation/updatePlaybackRate"
translated_by: "n8n + AI"
---

---
title: "Animation: updatePlaybackRate() method"
short-title: updatePlaybackRate()
slug: Web/API/Animation/updatePlaybackRate
page-type: web-api-instance-method
browser-compat: api.Animation.updatePlaybackRate
---

{{APIRef("Web Animations")}}

متد **`updatePlaybackRate()`** از [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
در رابط {{domxref("Animation")}}، سرعت یک انیمیشن را پس از همگام‌سازی‌ اولیه موقعیت پخش آن تنظیم می‌کند.

در برخی موارد، یک انیمیشن ممکن است در یک رشته (thread) یا فرآیند جداگانه اجرا شود و حتی زمانی که جاوااسکریپت طولانی‌مدت، رشته اصلی را به تأخیر می‌اندازد، به‌روزرسانی ادامه یابد. در چنین حالتی، تنظیم مستقیم {{domxref("Animation.playbackRate", "playbackRate")}} روی انیمیشن ممکن است باعث پرش موقعیت پخش انیمیشن شود، زیرا موقعیت پخش آن در رشته اصلی ممکن است از موقعیت پخش جاری آن جا مانده باشد.

`updatePlaybackRate()` یک متد ناهمگام (asynchronous) است که سرعت یک انیمیشن را پس از همگام‌سازی با موقعیت پخش فعلی آن تنظیم می‌کند و اطمینان می‌دهد که تغییر سرعت حاصل، باعث پرش ناگهانی نمی‌شود. پس از فراخوانی `updatePlaybackRate()`، ویژگی {{domxref("Animation.playbackRate", "playbackRate")}} انیمیشن _بلافاصله_ به‌روزرسانی نمی‌شود. این مقدار زمانی به‌روزرسانی می‌شود که پرامیسه {{domxref("Animation.ready", "ready")}} انیمیشن حل شود.

## Syntax

```js-nolint
updatePlaybackRate(playbackRate)
```

### Parameters

- `playbackRate`
  - : سرعت جدیدی که باید تنظیم شود. این می‌تواند یک عدد مثبت (برای افزایش یا کاهش سرعت انیمیشن)، یک عدد منفی (برای پخش معکوس)، یا صفر (برای توقف مؤثر انیمیشن) باشد.

### Return value

هیچ مقداری ({{jsxref("undefined")}}).

## Examples

یک کامپوننت انتخاب‌گر سرعت می‌تواند از به‌روزرسانی نرم `updatePlaybackRate()` بهره‌مند شود، همانطور که در زیر نشان داده شده است:

```js
speedSelector.addEventListener("input", (evt) => {
  cartoon.updatePlaybackRate(parseFloat(evt.target.value));
  cartoon.ready.then(() => {
    console.log(`Playback rate set to ${cartoon.playbackRate}`);
  });
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("Animation.playbackRate")}} — خواندن نرخ پخش فعلی یا تنظیم آن به صورت همگام.
- {{domxref("Animation.reverse()")}} — معکوس کردن نرخ پخش و راه‌اندازی مجدد پخش در صورت نیاز.
- {{domxref("Animation")}} — شامل سایر متدها و ویژگی‌هایی است که می‌توانید برای کنترل انیمیشن صفحه وب استفاده کنید.