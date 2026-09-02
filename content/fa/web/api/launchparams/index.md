---
title: LaunchParams
slug: Web/API/LaunchParams
page-type: web-api-interface
status:
  - experimental
browser-compat: api.LaunchParams
---

{{APIRef("Launch Handler API")}}{{SeeCompatTable}}

اینترفیس **`LaunchParams`** از {{domxref("Launch Handler API", "Launch Handler API", "", "nocode")}} هنگام پیاده‌سازی مدیریت ناوبری سفارشیِ راه‌اندازی در یک PWA استفاده می‌شود. وقتی متد {{domxref("LaunchQueue.setConsumer", "window.launchQueue.setConsumer()")}} برای تنظیم عملکرد مدیریت ناوبری راه‌اندازی فراخوانی می‌شود، یک نمونهٔ `LaunchParams` به تابع بازخوانی (callback) درون `setConsumer()` ارسال می‌شود.

چنین مدیریت ناوبری سفارشی از طریق {{domxref("Window.launchQueue")}} آغاز می‌شود، زمانی که یک PWA با [`launch_handler`](/en-US/docs/Web/Progressive_web_apps/Manifest/Reference/launch_handler) دارای مقدار `client_mode` برابر با `focus-existing`، `navigate-new` یا `navigate-existing` راه‌اندازی شده باشد.

{{InheritanceDiagram}}

## خصوصیات نمونه

- {{domxref("LaunchParams.files")}} {{ReadOnlyInline}}{{Experimental_Inline}}
  - : یک آرایهٔ فقط‌خواندنی از شیءهای {{domxref("FileSystemHandle")}} برمی‌گرداند که نمایانگر هر فایلی است که همراه با ناوبری راه‌اندازی و از طریق متد [`POST`](/en-US/docs/Web/HTTP/Reference/Methods/POST) ارسال شده است.
- {{domxref("LaunchParams.targetURL")}} {{ReadOnlyInline}}{{Experimental_Inline}}
  - : URL مقصدِ راه‌اندازی را برمی‌گرداند.

## مثال‌ها

```js
if ("launchQueue" in window) {
  window.launchQueue.setConsumer((launchParams) => {
    if (launchParams.targetURL) {
      const params = new URL(launchParams.targetURL).searchParams;

      // Assuming a music player app that gets a track passed to it to be played
      const track = params.get("track");
      if (track) {
        audio.src = track;
        title.textContent = new URL(track).pathname.slice(1);
        audio.play();
      }
    }
  });
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Launch Handler API: Control how your app is launched](https://developer.chrome.com/docs/web-platform/launch-handler/)
- {{domxref("Window.launchQueue")}}
- [Musicr 2.0](https://mdn.github.io/dom-examples/launch-handler/) برنامهٔ نمایشی