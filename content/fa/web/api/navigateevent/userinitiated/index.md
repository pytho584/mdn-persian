---
title: "NavigateEvent: userInitiated property"
short-title: userInitiated
slug: Web/API/NavigateEvent/userInitiated
page-type: web-api-instance-property
browser-compat: api.NavigateEvent.userInitiated
---

{{APIRef("Navigation API")}}

ویژگی فقط خواندنی **`userInitiated`** از رابط {{domxref("NavigateEvent")}} مقدار `true` را برمی‌گرداند اگر ناوبری توسط کاربر آغاز شده باشد (مثلاً با کلیک روی یک پیوند، ارسال یک فرم، یا فشار دادن دکمه‌های «بازگشت»/«رفتن به جلو» مرورگر)، و در غیر این صورت `false` را برمی‌گرداند.

> [!NOTE]
> جدول موجود در [ضمیمه: انواع ناوبری‌ها](https://github.com/WICG/navigation-api#appendix-types-of-navigations) نشان می‌دهد که کدام نوع ناوبری‌ها توسط کاربر آغاز می‌شوند.

## مقدار

یک مقدار بولی — `true` اگر ناوبری توسط کاربر آغاز شده باشد، `false` در غیر این صورت.

## مثال‌ها

### دریافت `userInitiated` برای یک رویداد

```js
navigation.addEventListener("navigate", (event) => {
  console.log(event.userInitiated);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [مسیریابی مدرن سمت کلاینت: API ناوبری](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح API ناوبری](https://github.com/WICG/navigation-api/blob/main/README.md)