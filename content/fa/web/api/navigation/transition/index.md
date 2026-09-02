---
title: "Navigation: transition property"
short-title: transition
slug: Web/API/Navigation/transition
page-type: web-api-instance-property
browser-compat: api.Navigation.transition
---

{{APIRef("Navigation API")}}

خاصیت فقط‌خواندنی **`transition`** در رابط {{domxref("Navigation")}} یک شیء {{domxref("NavigationTransition")}} برمی‌گرداند که وضعیت یک ناوبری در حال انجام را نشان می‌دهد و می‌توان از آن برای پیگیری آن استفاده کرد.

`Navigation.transition` فقط زمانی مقداردهی می‌شود که کنترل‌کننده [`intercept()`](/en-US/docs/Web/API/NavigateEvent/intercept) هنوز برطرف نشده باشد (یعنی در طول [رهگیری ناوبری](/en-US/docs/Web/API/Navigation/navigate_event#handling_a_navigation_using_intercept))، و در غیر این صورت `null` است.

## مقدار

یک شیء {{domxref("NavigationTransition")}}، یا `null` اگر در حال حاضر ناوبری در جریان نباشد.

## مثال‌ها

```js
async function handleTransition() {
  if (navigation.transition) {
    showLoadingSpinner();
    await navigation.transition.finished;
    hideLoadingSpinner();
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [روتینگ مدرن سمت کلاینت: Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح Navigation API](https://github.com/WICG/navigation-api/blob/main/README.md)