---
title: "NavigateEvent: info property"
short-title: info
slug: Web/API/NavigateEvent/info
page-type: web-api-instance-property
browser-compat: api.NavigateEvent.info
---

{{APIRef("Navigation API")}}

ویژگی فقط‌خواندنی **`info`** در رابط {{domxref("NavigateEvent")}} مقدار `info` را برمی‌گرداند که توسط عملیات ناوبری آغازکننده (مانند {{domxref("Navigation.back()")}} یا {{domxref("Navigation.navigate()")}}) ارسال شده است؛ یا اگر دادهٔ `info` ارسال نشده باشد، مقدار `undefined` برمی‌گردد.

## مقدار

مقدار `info` ارسال‌شده توسط عملیات ناوبری آغازکننده، یا اگر هیچ مقداری ارسال نشده باشد، `undefined`.

## مثال‌ها

یکی از کاربردهای `info` می‌تواند ایجاد رندرهای متفاوت برای ناوبری تک‌صفحه‌ای بر اساس نحوهٔ رسیدن به یک مسیر خاص باشد. برای مثال، برنامه‌ای برای گالری عکس در نظر بگیرید که می‌توانید از مسیرهای گوناگون به همان URL و state عکس برسید. ممکن است بخواهید برای نمایش عکس، به‌ازای هر مسیر از انیمیشنی متفاوت استفاده کنید.

```js
navigation.addEventListener("navigate", (event) => {
  if (isPhotoNavigation(event)) {
    event.intercept({
      async handler() {
        switch (event.info?.via) {
          case "go-left": {
            await animateLeft();
            break;
          }
          case "go-right": {
            await animateRight();
            break;
          }
          case "gallery": {
            await animateZoomFromThumbnail(event.info.thumbnail);
            break;
          }
        }

        // TODO: actually load the photo.
      },
    });
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [مسیریابی مدرن سمت کلاینت: Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح Navigation API](https://github.com/WICG/navigation-api/blob/main/README.md)
- متدهایی که امکان ارسال `info` را می‌دهند — {{domxref("Navigation.back()")}}, {{domxref("Navigation.forward()")}}, {{domxref("Navigation.navigate()")}}, {{domxref("Navigation.reload()")}} و {{domxref("Navigation.traverseTo()")}}