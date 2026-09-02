---
title: "LaunchParams: files property"
short-title: files
slug: Web/API/LaunchParams/files
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.LaunchParams.files
---

{{APIRef("Launch Handler API")}}{{SeeCompatTable}}

خصوصیت فقط‌خواندنی **`files`** در رابط {{domxref("LaunchParams")}} یک آرایه از اشیاء {{domxref("FileSystemHandle")}} برمی‌گرداند که هر فایلی را که همراه با ناوبری راه‌اندازی از طریق متد [`POST`](/en-US/docs/Web/HTTP/Reference/Methods/POST) ارسال شده، نشان می‌دهد.

## مقدار

یک آرایه فقط‌خواندنی از اشیاء {{domxref("FileSystemHandle")}}.

## مثال‌ها

```js
if ("launchQueue" in window) {
  window.launchQueue.setConsumer((launchParams) => {
    if (launchParams.files) {
      const files = launchParams.files;
      for (file in files) {
        // Do stuff with file handles
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

- [Launch Handler API: نحوه کنترل نحوه راه‌اندازی برنامه شما](https://developer.chrome.com/docs/web-platform/launch-handler/)
- {{domxref("Window.launchQueue")}}