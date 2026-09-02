---
title: "NavigateEvent: hashChange property"
short-title: hashChange
slug: Web/API/NavigateEvent/hashChange
page-type: web-api-instance-property
browser-compat: api.NavigateEvent.hashChange
---

{{APIRef("Navigation API")}}

خاصیت فقط‑خواندنی **`hashChange`** از رابط {{domxref("NavigateEvent")}} مقدار `true` را برمی‌گرداند اگر ناوبری یک ناوبری قطعه‌ای (fragment navigation) باشد (یعنی به یک شناسه‌ی قطعه در همان سند)، و در غیر این صورت `false` را برمی‌گرداند.

## مقدار

یک مقدار بولی — `true` اگر ناوبری از نوع ناوبری قطعه‌ای باشد، `false` در غیر این صورت.

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

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [مسیریابی مدرن سمت کاربر: API Navigation](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح API Navigation](https://github.com/WICG/navigation-api/blob/main/README.md)