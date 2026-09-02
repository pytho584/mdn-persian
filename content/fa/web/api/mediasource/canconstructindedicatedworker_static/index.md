---
title: "MediaSource: canConstructInDedicatedWorker static property"
short-title: canConstructInDedicatedWorker
slug: Web/API/MediaSource/canConstructInDedicatedWorker_static
page-type: web-api-static-property
browser-compat: api.MediaSource.canConstructInDedicatedWorker_static
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی ایستای **`canConstructInDedicatedWorker`** در رابط {{domxref("MediaSource")}} اگر پشتیبانی از `MediaSource` در worker پیاده‌سازی شده باشد، مقدار `true` را برمی‌گرداند و بدین ترتیب مکانیزمی برای شناسایی ویژگی با تأخیر کم فراهم می‌کند.

اگر این امکان در دسترس نبود، جایگزین آن رویکردی با تأخیر بسیار بیشتر بود؛ مانند تلاش برای ایجاد یک شیء `MediaSource` از یک dedicated worker و انتقال نتیجه به نخ اصلی.

## مقدار

یک مقدار بولی. اگر پشتیبانی از `MediaSource` در worker پیاده‌سازی شده باشد، `true` و در غیر این صورت `false` برمی‌گرداند.

## مثال‌ها

```js
if (MediaSource.canConstructInDedicatedWorker) {
  // MSE is available in workers; let's do this
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [MSE-in-Workers Demo by Matt Wolenetz](https://wolenetz.github.io/mse-in-workers-demo/mse-in-workers-demo.html)
- {{domxref("Media Source Extensions API", "Media Source Extensions API", "", "nocode")}}
- {{domxref("MediaSource")}}
- {{domxref("SourceBuffer")}}