---
title: "LaunchQueue: setConsumer() method"
short-title: setConsumer()
slug: Web/API/LaunchQueue/setConsumer
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.LaunchQueue.setConsumer
---

{{APIRef("Launch Handler API")}}{{SeeCompatTable}}

متد **`setConsumer()`** از رابط {{domxref("LaunchQueue")}} برای تعیین تابع برگشت‌به‌صدایی (callback) استفاده می‌شود که مدیریت ناوبری راه‌اندازی سفارشی را در یک [برنامه وب پیشرو (PWA)](/en-US/docs/Web/Progressive_web_apps) بر عهده می‌گیرد. چنین ناوبری سفارشی از طریق {{domxref("Window.launchQueue")}} آغاز می‌شود، زمانی که یک PWA با مقدار `client_mode` برابر با `focus-existing`، `navigate-new` یا `navigate-existing` در [`launch_handler`](/en-US/docs/Web/Progressive_web_apps/Manifest/Reference/launch_handler) راه‌اندازی شده باشد.

## نحو (Syntax)

```js-nolint
setConsumer(callback)
```

### پارامترها

- `callback`
  - : یک تابع برگشت‌به‌صدا که ناوبری سفارشی را برای PWA مدیریت می‌کند. این تابع یک شیء از نوع {{domxref("LaunchParams")}} را به عنوان پارامتر دریافت می‌کند.

### مقدار بازگشتی

`undefined`.

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