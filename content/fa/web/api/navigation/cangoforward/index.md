---
title: "Navigation: canGoForward property"
short-title: canGoForward
slug: Web/API/Navigation/canGoForward
page-type: web-api-instance-property
browser-compat: api.Navigation.canGoForward
---

{{APIRef("Navigation API")}}

ویژگی فقط‌خواندنی **`canGoForward`** در رابط {{domxref("Navigation")}} مقدار `true` را بازمی‌گرداند اگر امکان پیمایش به جلو در تاریخچهٔ پیمایش وجود داشته باشد (یعنی {{domxref("Navigation.currentEntry", "currentEntry")}} آخرین ورودی در فهرست ورودی‌های تاریخچه نباشد)، و در غیر این صورت `false` بازمی‌گرداند.

## مقدار

یک مقدار بولین: اگر امکان پیمایش به جلو در تاریخچهٔ پیمایش وجود داشته باشد، `true` است؛ در غیر این صورت `false`.

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

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)