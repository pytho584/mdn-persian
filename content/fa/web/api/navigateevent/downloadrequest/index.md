---
title: "NavigateEvent: downloadRequest property"
short-title: downloadRequest
slug: Web/API/NavigateEvent/downloadRequest
page-type: web-api-instance-property
browser-compat: api.NavigateEvent.downloadRequest
---

{{APIRef("Navigation API")}}

ویژگی فقط‌خواندنی **`downloadRequest`** از رابط {{domxref("NavigateEvent")}} نام فایل درخواست‌شده برای دانلود را در صورت پیمایش دانلودی (مثلاً یک عنصر {{htmlelement("a")}} یا {{htmlelement("area")}} با ویژگی `download`) برمی‌گرداند، و در غیر این صورت `null` برمی‌گرداند.

## مقدار

رشته‌ای شامل نام فایل درخواست‌شده برای دانلود، یا `null`.

## مثال‌ها

```js
navigation.addEventListener("navigate", (event) => {
  // Some navigations, e.g. cross-origin navigations, we
  // cannot intercept. Let the browser handle those normally.
  if (!event.canIntercept) {
    return;
  }

  // Don't intercept fragment navigations or downloads.
  if (event.hashChange || event.downloadRequest !== null) {
    return;
  }

  event.intercept({
    handler() {
      if (event.formData) {
        processFormDataAndUpdateUI(event.formData, event.signal);
      } else {
        doSinglePageAppNav(event.destination, event.signal);
      }
    },
  });
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)