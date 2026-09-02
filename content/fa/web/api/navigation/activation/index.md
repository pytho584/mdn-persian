---
title: "Navigation: activation property"
short-title: activation
slug: Web/API/Navigation/activation
page-type: web-api-instance-property
browser-compat: api.Navigation.activation
---

{{APIRef("Navigation API")}}

ویژگی فقط‌خواندنی **`activation`** از رابط {{domxref("Navigation")}} یک شیء {{domxref("NavigationActivation")}} را برمی‌گرداند که شامل اطلاعاتی درباره آخرین پیمایش بین‌سندی (cross-document navigation) است که این سند (Document) را «فعال» کرده است. این ویژگی در طول پیمایش‌های درون‌سندی (same-document navigations) ثابت باقی می‌ماند.

## مقدار

یک شیء {{domxref("NavigationActivation")}}، یا اگر سند جاری سند ابتدایی `about:blank` باشد، `null`.

## مثال‌ها

```js
if (navigation.activation) {
  console.log(navigation.activation.entry.url);
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [مسیریابی مدرن سمت کاربر: Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح Navigation API](https://github.com/WICG/navigation-api/blob/main/README.md)