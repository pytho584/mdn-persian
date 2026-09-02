---
title: "NavigateEvent: hasUAVisualTransition property"
short-title: hasUAVisualTransition
slug: Web/API/NavigateEvent/hasUAVisualTransition
page-type: web-api-instance-property
browser-compat: api.NavigateEvent.hasUAVisualTransition
---

{{APIRef("Navigation API")}}

ویژگی فقط‌خواندنی **`hasUAVisualTransition`** در رابط {{domxref("NavigateEvent")}} مقدار `true` را برمی‌گرداند اگر عامل کاربر پیش از ارسال این رویداد، یک انتقال بصری برای این ناوبری انجام داده باشد؛ در غیر این صورت `false` برمی‌گردد.

عامل‌های کاربر ممکن است هنگام انجام ناوبری‌های سایت یک انتقال بصری داخلی فراهم کنند. اگر توسعه‌دهندهٔ سایت نیز یک انتقال بصری اضافه کند، انتقال‌های عامل کاربر و توسعه‌دهنده ممکن است با هم تداخل کنند و بازدیدکننده را سردرگم کنند. این ویژگی به شما امکان می‌دهد تشخیص دهید که آیا انتقالی از طرف عامل کاربر ارائه شده است یا نه، تا بتوانید برای تجربهٔ کاربری بهتر، انتقال‌های توسعه‌دهنده را کنار بگذارید.

## مقدار

یک مقدار بولی.

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
      // Fetch the new content
      const newContent = await fetchNewContent(event.destination.url, {
        signal: event.signal,
      });

      // The UA does not support View Transitions, or the UA
      // already provided a Visual Transition by itself (e.g. swipe back).
      // In either case, update the DOM directly
      if (!document.startViewTransition || event.hasUAVisualTransition) {
        doSinglePageAppNav(newContent);
        return;
      }

      // Update the content using a View Transition
      document.startViewTransition(() => {
        doSinglePageAppNav(newContent);
      });
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
- [Same-document view transitions for single-page applications](https://developer.chrome.com/docs/web-platform/view-transitions/same-document)