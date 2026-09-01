---
title: "Document: createTouchList() method"
short-title: createTouchList()
slug: Web/API/Document/createTouchList
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.Document.createTouchList
---

{{APIRef("DOM")}}{{Deprecated_Header}}{{Non-standard_header}}

متد **`Document.createTouchList()`** یک شیء {{DOMxRef("TouchList")}} جدید ایجاد کرده و آن را بازمی‌گرداند.

## نحو (Syntax)

```js-nolint
createTouchList(touch1)
createTouchList(touch1, touch2)
createTouchList(touch1, touch2, /* …, */ touchN)
```

### پارامترها

- `touch1`، …، `touchN`
  - : صفر یا چند شیء {{DOMxRef("Touch")}}. فایرفاکس همچنین یک [آرایه](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) از اشیاء {{DOMxRef("Touch")}} را می‌پذیرد.

### مقدار بازگشتی

یک شیء {{DOMxRef("TouchList")}} شامل اشیاء {{DOMxRef("Touch")}} که توسط پارامتر `touches` مشخص شده‌اند.

## مثال‌ها

این مثال استفاده از متد `Document.createTouchList()` را برای ایجاد اشیاء {{DOMxRef("TouchList")}} نشان می‌دهد.

در قطعه کد زیر، چند شیء {{DOMxRef("Touch")}} برای عنصر `target` ایجاد شده و سپس از آن نقاط لمسی برای ایجاد چند شیء {{DOMxRef("TouchList")}} استفاده می‌شود.

```js
const target = document.getElementById("target");

// ایجاد چند نقطه لمسی
const touch1 = document.createTouch(window, target, 1, 15, 20, 35, 40);
const touch2 = document.createTouch(window, target, 2, 25, 30, 45, 50);

// ایجاد یک شیء TouchList خالی
const list0 = document.createTouchList();

// ایجاد یک TouchList با فقط یک شیء Touch
const list1 = document.createTouchList(touch1);

// ایجاد یک لیست با دو شیء Touch
const list2 = document.createTouchList(touch1, touch2);
```

## مشخصات

این ویژگی بخشی از هیچ مشخصات فعلی نیست و دیگر در مسیر تبدیل شدن به استاندارد قرار ندارد.

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [رویدادهای لمسی](/en-US/docs/Web/API/Touch_events)
- {{DOMxRef("Touch")}}
- {{DOMxRef("TouchEvent")}}
- {{DOMxRef("TouchList")}}
- {{DOMxRef("Document.createTouch()")}}