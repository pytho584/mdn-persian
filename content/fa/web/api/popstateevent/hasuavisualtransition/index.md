---
title: "PopStateEvent: hasUAVisualTransition property"
short-title: hasUAVisualTransition
slug: Web/API/PopStateEvent/hasUAVisualTransition
page-type: web-api-instance-property
browser-compat: api.PopStateEvent.hasUAVisualTransition
---

{{APIRef("History API")}}

ویژگی فقط‌خواندنی **`hasUAVisualTransition`** در رابط {{domxref("PopStateEvent")}} اگر عامل کاربر (user agent) پیش از صدور این رویداد، یک گذار بصری برای این ناوبری انجام داده باشد، `true` برمی‌گرداند؛ در غیر این صورت `false` برمی‌گرداند.

عامل‌های کاربر ممکن است هنگام اجرای ناوبری‌های سایت یک گذار بصری داخلی ارائه دهند. اگر نویسندهٔ سایت نیز گذار بصری خود را اضافه کند، ممکن است گذار عامل کاربر و گذار نویسنده با هم تداخل پیدا کنند و بازدیدکننده را سردرگم کنند. این ویژگی به شما امکان می‌دهد تشخیص دهید که آیا گذاری از سوی عامل کاربر ارائه شده است یا نه؛ بنابراین می‌توانید برای تجربهٔ کاربری بهتر، از اعمال گذارهای سمت خودتان صرف‌نظر کنید.

## مقدار

یک مقدار بولین (boolean).

## مثال‌ها

```js
window.addEventListener("popstate", async (event) => {
  // Fetch the new content
  const newContent = await fetchNewContent(location.href);

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