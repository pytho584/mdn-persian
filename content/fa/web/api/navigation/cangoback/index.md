---
title: "Navigation: canGoBack property"
short-title: canGoBack
slug: Web/API/Navigation/canGoBack
page-type: web-api-instance-property
browser-compat: api.Navigation.canGoBack
---

{{APIRef("Navigation API")}}

خاصیت فقط‌خواندنی **`canGoBack`** در رابط {{domxref("Navigation")}} مقدار `true` را برمی‌گرداند اگر امکان پیمایش به عقب در تاریخچه ناوبری وجود داشته باشد (یعنی {{domxref("Navigation.currentEntry", "currentEntry")}} اولین ورودی در فهرست ورودی‌های تاریخچه نباشد)، و در غیر این صورت `false` برمی‌گرداند.

## مقدار

یک مقدار بولی: اگر امکان پیمایش به عقب در تاریخچه ناوبری وجود داشته باشد `true` است، در غیر این صورت `false`.

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

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [مسیریابی مدرن سمت کلاینت: Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح Navigation API](https://github.com/WICG/navigation-api/blob/main/README.md)