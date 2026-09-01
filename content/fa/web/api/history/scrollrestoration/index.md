---
title: "History: scrollRestoration property"
short-title: scrollRestoration
slug: Web/API/History/scrollRestoration
page-type: web-api-instance-property
browser-compat: api.History.scrollRestoration
---

{{APIRef("History API")}}

ویژگی **`scrollRestoration`** در رابط {{DOMxRef("History")}} به برنامه‌های وب اجازه می‌دهد تا رفتار پیش‌فرض بازگردانیِ موقعیت اسکرول را هنگام ناوبری در تاریخچه، به‌صورت صریح تنظیم کنند.

## مقدار

یکی از مقادیر زیر:

- `auto`
  - : موقعیتی از صفحه که کاربر به آن اسکرول کرده بود، بازگردانی می‌شود.
- `manual`
  - : موقعیت صفحه بازگردانی نمی‌شود و کاربر باید به‌صورت دستی به آن موقعیت اسکرول کند.

## مثال‌ها

### دریافت رفتار فعلی بازگردانی اسکرول

```js
const scrollRestoration = history.scrollRestoration;
if (scrollRestoration === "manual") {
  console.log(
    "The location on the page is not restored, user will need to scroll manually.",
  );
}
```

### جلوگیری از بازگردانی خودکار موقعیت صفحه

```js
history.scrollRestoration = "manual";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}