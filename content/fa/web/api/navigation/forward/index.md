---
title: "Navigation: forward() method"
short-title: forward()
slug: Web/API/Navigation/forward
page-type: web-api-instance-method
browser-compat: api.Navigation.forward
---

{{APIRef("Navigation API")}}

متد **`forward()`** از رابط {{domxref("Navigation")}} یک ورودی به جلو در تاریخچهٔ مرور (navigation history) حرکت می‌کند.

## Syntax

```js-nolint
forward(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شیء حاوی ویژگی‌های زیر:
    - `info` {{optional_inline}}
      - : اطلاعاتی که توسعه‌دهنده تعریف می‌کند و به رویداد {{domxref("Navigation/navigate_event", "navigate")}} ارسال می‌شود و در {{domxref("NavigateEvent.info")}} در دسترس قرار می‌گیرد. این می‌تواند هر نوع داده‌ای باشد. به‌عنوان مثال، ممکن است بخواهید محتوای تازه‌بارگذاری‌شده را با انیمیشنی متفاوت نمایش دهید، بسته به اینکه چگونه به آن ناوبری شده است (حرکت به چپ، حرکت به راست، یا بازگشت به خانه). یک رشته که نوع انیمیشن را مشخص می‌کند می‌تواند به عنوان `info` ارسال شود.

### مقدار بازگشتی

یک شیء با ویژگی‌های زیر:

- `committed`
  - : یک {{jsxref("Promise")}} که زمانی که URL قابل مشاهده تغییر کرده و یک {{domxref("NavigationHistoryEntry")}} جدید ایجاد شده است، انجام می‌شود.
- `finished`
  - : یک {{jsxref("Promise")}} که زمانی که تمام promise‌های بازگردانده‌شده توسط handler رویداد {{domxref("NavigateEvent.intercept()")}} انجام شوند، انجام می‌شود. این معادل با fulfillment promise {{domxref("NavigationTransition.finished")}} است، زمانی که رویداد {{domxref("Navigation/navigatesuccess_event", "navigatesuccess")}} رخ می‌دهد.

هر یک از این promise‌ها در صورت شکست ناوبری به دلایلی رد می‌شوند.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که مقدار {{domxref("Navigation.currentEntry")}} از {{domxref("NavigationHistoryEntry.index")}} برابر ۱- یا {{domxref("Navigation.entries", "navigation.entries().length - 1")}} باشد، یعنی {{domxref("Document")}} فعلی هنوز فعال نیست، یا ورودی فعلی تاریخچه آخرین ورودی در تاریخچه است، بنابراین ناوبری به جلو امکان‌پذیر نیست، یا {{domxref("Document")}} فعلی در حال تخلیه (unloading) است.

## مثال‌ها

```js
async function backHandler() {
  if (navigation.canGoBack) {
    await navigation.back().finished;
    // پس از پایان ناوبری، هرگونه پاک‌سازی لازم را انجام دهید
  } else {
    displayBanner("شما در صفحهٔ اول هستید");
  }
}

async function forwardHandler() {
  if (navigation.canGoForward) {
    await navigation.forward().finished;
    // پس از پایان ناوبری، هرگونه پاک‌سازی لازم را انجام دهید
  } else {
    displayBanner("شما در آخرین صفحه هستید");
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [مسیریابی مدرن سمت کاربر: API Navigation](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح API Navigation](https://github.com/WICG/navigation-api/blob/main/README.md)