---
title: "LaunchParams: targetURL property"
short-title: targetURL
slug: Web/API/LaunchParams/targetURL
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.LaunchParams.targetURL
---

{{APIRef("Launch Handler API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`targetURL`** از رابط {{domxref("LaunchParams")}}، نشانی اینترنتی (URL) هدف راه‌اندازیِ برنامهٔ وب مرتبط را برمی‌گرداند.

## مقدار

یک رشته.

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