---
title: "HTMLCollection: length property"
short-title: length
slug: Web/API/HTMLCollection/length
page-type: web-api-instance-property
browser-compat: api.HTMLCollection.length
---

{{APIRef("DOM")}}

ویژگی **`HTMLCollection.length`** تعداد آیتم‌های موجود در یک {{domxref("HTMLCollection")}} را برمی‌گرداند.

## مقدار

یک عدد صحیح که تعداد آیتم‌های یک `HTMLCollection` را نشان می‌دهد.

## مثال‌ها

ویژگی `length` اغلب در برنامه‌نویسی DOM مفید است. معمولاً برای بررسی طول یک فهرست و اطمینان از اینکه اصلاً وجود دارد استفاده می‌شود. همچنین معمولاً به‌عنوان شمارنده در یک حلقه `for` به کار می‌رود، همان‌طور که در این مثال می‌بینید.

```js
// All the elements with the class ".test" in the document
const items = document.getElementsByClassName("test");

// For each test item in the list,
// append the entire element as a string of HTML
let gross = "";
for (let i = 0; i < items.length; i++) {
  gross += items[i].innerHTML;
}

// gross is now all the HTML for the test elements
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}