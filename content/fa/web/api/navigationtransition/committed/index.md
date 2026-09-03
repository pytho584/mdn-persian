---
title: "NavigationTransition: committed property"
short-title: committed
slug: Web/API/NavigationTransition/committed
page-type: web-api-instance-property
browser-compat: api.NavigationTransition.committed
---

{{APIRef("Navigation API")}}

ویژگی فقط‌خواندنی **`committed`** در رابط {{domxref("NavigationTransition")}} یک {{jsxref("Promise")}} برمی‌گرداند که زمانی وفا می‌شود که {{domxref("Navigation.currentEntry")}} به‌روزرسانی شده و URL جدید در مرورگر نمایش داده شود، یعنی ناوبری به عنوان committed (ثبت‌شده) علامت‌گذاری می‌شود. این اتفاق پس از اجرای تمام [مدیران پیش‌ازثبت (precommit handlers)](/en-US/docs/Web/API/NavigateEvent/intercept#handling_precommit_actions_with_precommithandler) برای آن ناوبری رخ می‌دهد.

اگر هر یک از مدیران پیش‌ازثبت رد شوند، پرامیس `committed` نیز رد می‌شود.

## مقدار

یک {{jsxref("Promise")}} که به `undefined` تبدیل می‌شود.

## مثال‌ها

```js
async function lockInNavigation() {
  await navigation.transition.committed;
  // ناوبری با موفقیت ثبت شد
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [مسیریابی مدرن سمت کلاینت: API Navigation](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح API Navigation](https://github.com/WICG/navigation-api/blob/main/README.md)