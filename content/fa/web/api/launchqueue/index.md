---
title: LaunchQueue
slug: Web/API/LaunchQueue
page-type: web-api-interface
status:
  - experimental
browser-compat: api.LaunchQueue
---

{{APIRef("Launch Handler API")}}{{SeeCompatTable}}

رابط **`LaunchQueue`** از {{domxref("Launch Handler API", "Launch Handler API", "", "nocode")}} از طریق ویژگی {{domxref("Window.launchQueue")}} در دسترس است. هنگامی که یک [برنامه وب پیش‌رونده](/en-US/docs/Web/Progressive_web_apps) (PWA) با مقدار `client_mode` برابر با `focus-existing`، `navigate-new` یا `navigate-existing` در [`launch_handler`](/en-US/docs/Web/Progressive_web_apps/Manifest/Reference/launch_handler) راه‌اندازی می‌شود، `LaunchQueue` دسترسی به قابلیتی را فراهم می‌کند که امکان پیاده‌سازی مدیریت راه‌اندازی سفارشی برای ناوبری در PWA را می‌دهد. این قابلیت توسط ویژگی‌های شی {{domxref("LaunchParams")}} که به تابع callback {{domxref("LaunchQueue.setConsumer", "setConsumer()")}} ارسال می‌شود، کنترل می‌گردد.

{{InheritanceDiagram}}

## روش‌های نمونه

- {{domxref("LaunchQueue.setConsumer", "setConsumer()")}} {{Experimental_Inline}}
  - شامل یک تابع callback است که ناوبری راه‌اندازی سفارشی را برای یک PWA مدیریت می‌کند.

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

- [Launch Handler API: نحوه راه‌اندازی برنامه خود را کنترل کنید](https://developer.chrome.com/docs/web-platform/launch-handler/)
- {{domxref("Window.launchQueue")}}
- برنامه نمایشی [Musicr 2.0](https://mdn.github.io/dom-examples/launch-handler/)