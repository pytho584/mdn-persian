---
title: "NodeList: length property"
---

---
title: "NodeList: length property"
short-title: length
slug: Web/API/NodeList/length
page-type: web-api-instance-property
browser-compat: api.NodeList.length
---

{{APIRef("DOM")}}

ویژگی **`NodeList.length`**، تعداد آیتم‌های یک {{domxref("NodeList")}} را برمی‌گرداند.

## مقدار

یک مقدار صحیح (integer) که تعداد آیتم‌های یک `NodeList` را نشان می‌دهد.

## مثال‌ها

ویژگی `length` اغلب در برنامه‌نویسی DOM مفید است و معمولاً برای بررسی طول یک فهرست و این‌که آیا اصلاً وجود دارد یا نه استفاده می‌شود. همچنین معمولاً به‌عنوان شمارنده در یک حلقه `for` به کار می‌رود، همان‌طور که در این مثال دیده می‌شود.

```js
// All the paragraphs in the document
const items = document.getElementsByTagName("p");

// For each item in the list,
// append the entire element as a string of HTML
let gross = "";
for (let i = 0; i < items.length; i++) {
  gross += items[i].innerHTML;
}

// gross is now all the HTML for the paragraphs
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}