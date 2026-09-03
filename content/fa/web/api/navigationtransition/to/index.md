---
title: "NavigationTransition: to property"
short-title: to
slug: Web/API/NavigationTransition/to
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.NavigationTransition.to
---

{{APIRef("Navigation API")}}{{seecompattable}}

ویژگی فقط‌خواندنی **`to`** در رابط {{domxref("NavigationTransition")}}، شیء {{domxref("NavigationDestination")}} را برمی‌گرداند که انتقال به سمت آن در حال انجام است.

این ویژگی معادل {{domxref("NavigateEvent.destination")}} است، اما برخلاف آن، خارج از کنترل‌کننده رویداد {{domxref("Navigation.navigate_event", "navigate")}} نیز در دسترس است. این ویژگی به‌ویژه زمانی مفید است که بخواهید قبل از تغییر URL تابعی را فراخوانی کنید (مثلاً در مرحله پیش از تأیید یا هنگام بروز خطا).

## مقدار

یک شیء {{domxref("NavigationDestination")}}.

## مثال‌ها

### مدیریت خطای ناوبری

```js
navigation.onnavigateerror = (e) => {
  if (navigation.transition?.to?.url === loginPageURL) {
    /* زمانی که رفتن به صفحه ورود با شکست مواجه می‌شود، کاری انجام بده */
  }
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [مسیریابی مدرن سمت کلاینت: API ناوبری](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح API ناوبری](https://github.com/WICG/navigation-api/blob/main/README.md)