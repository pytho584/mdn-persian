---
title: "Navigation: back() method"
short-title: back()
slug: Web/API/Navigation/back
page-type: web-api-instance-method
browser-compat: api.Navigation.back
---

{{APIRef("Navigation API")}}

متد **`back()`** از رابط {{domxref("Navigation")}} یک ورودی به عقب در تاریخچهٔ ناوبری حرکت می‌کند.

## نحو (Syntax)

```js-nolint
back(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شیء گزینه‌ها که شامل ویژگی‌های زیر است:
    - `info` {{optional_inline}}
      - : اطلاعاتی تعریف‌شده توسط توسعه‌دهنده که به رویداد {{domxref("Navigation/navigate_event", "navigate")}} منتقل می‌شود و در {{domxref("NavigateEvent.info")}} در دسترس قرار می‌گیرد. این می‌تواند هر نوع داده‌ای باشد. برای مثال، ممکن است بخواهید محتوای تازه‌ناوبری‌شده را با انیمیشنی متفاوت بسته به نحوهٔ ناوبری به آن (کشیدن به چپ، کشیدن به راست، یا رفتن به صفحهٔ اصلی) نمایش دهید. یک رشته که نشان‌دهندهٔ انیمیشن مورد استفاده است می‌تواند به عنوان `info` ارسال شود.

### مقدار بازگشتی

یک شیء با ویژگی‌های زیر:

- `committed`
  - : یک {{jsxref("Promise")}} که زمانی که URL قابل مشاهده تغییر کرده و یک {{domxref("NavigationHistoryEntry")}} جدید ایجاد شده است، برآورده می‌شود.
- `finished`
  - : یک {{jsxref("Promise")}} که زمانی که تمام قول‌های بازگردانده شده توسط کنترل‌کنندهٔ `intercept()` برآورده شوند، برآورده می‌شود. این معادل با برآورده شدن قول {{domxref("NavigationTransition.finished")}} زمانی است که رویداد {{domxref("Navigation/navigatesuccess_event", "navigatesuccess")}} رخ می‌دهد.

اگر ناوبری به هر دلیلی ناموفق باشد، هر یک از این قول‌ها رد می‌شوند.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر مقدار {{domxref("Navigation.currentEntry")}}'s {{domxref("NavigationHistoryEntry.index")}} برابر -1 یا 0 باشد، یعنی یا {{domxref("Document")}} فعلی هنوز فعال نیست، یا ورودی تاریخچهٔ فعلی اولین ورودی در تاریخچه است، به این معنا که ناوبری به عقب ممکن نیست، یا اگر {{domxref("Document")}} فعلی در حال بارگیری‌زدایی (unloading) است، پرتاب می‌شود.

## مثال‌ها

```js
async function backHandler() {
  if (navigation.canGoBack) {
    await navigation.back().finished;
    // Handle any required clean-up after
    // navigation has finished
  } else {
    displayBanner("You are on the first page");
  }
}

async function forwardHandler() {
  if (navigation.canGoForward) {
    await navigation.forward().finished;
    // Handle any required clean-up after
    // navigation has finished
  } else {
    displayBanner("You are on the last page");
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [مسیریابی مدرن سمت کلاینت: API Navigation](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح API Navigation](https://github.com/WICG/navigation-api/blob/main/README.md)