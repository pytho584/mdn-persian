---
title: "CustomEvent: CustomEvent() constructor"
short-title: CustomEvent()
slug: Web/API/CustomEvent/CustomEvent
page-type: web-api-constructor
browser-compat: api.CustomEvent.CustomEvent
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

سازنده **`CustomEvent()`** یک شیء جدید از نوع {{domxref("CustomEvent")}} ایجاد می‌کند.

## نحو (Syntax)

```js-nolint
new CustomEvent(type)
new CustomEvent(type, options)
```

### پارامترها

- `type`
  - : یک رشته (string) که نام رویداد را مشخص می‌کند. نام رویدادها به حروف بزرگ و کوچک حساس هستند (case-sensitive).
- `options` {{optional_inline}}
  - : یک شیء که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند دارای ویژگی‌های زیر باشد:
    - `detail` {{optional_inline}}
      - : یک مقدار وابسته به رویداد که با رویداد مرتبط است. این مقدار سپس در دسترس handler (مدیریت‌کننده) از طریق ویژگی {{domxref("CustomEvent.detail")}} قرار می‌گیرد.
        مقدار پیش‌فرض آن `null` است.

### مقدار بازگشتی

یک شیء جدید از نوع {{domxref("CustomEvent")}}.

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

// افزودن یک شنونده رویداد مناسب
element.addEventListener("animalfound", (e) => console.log(e.detail.name));

// ارسال رویدادها
element.dispatchEvent(catFound);
element.dispatchEvent(dogFound);

// "cat" و "dog" در کنسول ثبت می‌شوند
```

مثال‌های بیشتر را می‌توانید در [ایجاد و ارسال رویدادها](/en-US/docs/Web/API/Document_Object_Model/Events#creating_and_dispatching_events) پیدا کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CustomEvent")}}
- [ایجاد و ارسال رویدادها](/en-US/docs/Web/API/Document_Object_Model/Events#creating_and_dispatching_events)