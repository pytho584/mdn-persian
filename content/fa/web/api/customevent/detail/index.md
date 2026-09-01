---
title: "CustomEvent: detail property"
short-title: detail
slug: Web/API/CustomEvent/detail
page-type: web-api-instance-property
browser-compat: api.CustomEvent.detail
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

خاصیتِ **`detail`** (فقط‌خواندنی) در رابط {{domxref("CustomEvent")}} هر داده‌ای را که هنگام مقداردهی رویداد ارسال شده باشد، برمی‌گرداند.

## مقدار

هر داده‌ای که رویداد با آن مقداردهی شده است.

## مثال

```js
// ایجاد رویدادهای سفارشی
const catFound = new CustomEvent("animalfound", {
  detail: {
    name: "cat",
  },
});
const dogFound = new CustomEvent("animalfound", {
  detail: {
    name: "dog",
  },
});

const element = document.createElement("div"); // ایجاد یک عنصر <div>

// افزودن شنونده‌ی رویداد مناسب
element.addEventListener("animalfound", (e) => console.log(e.detail.name));

// ارسال رویدادها
element.dispatchEvent(catFound);
element.dispatchEvent(dogFound);

// «cat» و «dog» در کنسول ثبت می‌شوند
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("CustomEvent")}}