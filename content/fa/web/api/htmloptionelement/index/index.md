---
title: "HTMLOptionElement: index property"
short-title: index
slug: Web/API/HTMLOptionElement/index
page-type: web-api-instance-property
browser-compat: api.HTMLOptionElement.index
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`index`** از رابط {{DOMxRef("HTMLOptionElement")}}، ایندکس (شاخص) مبتنی بر صفر عنصر را مشخص می‌کند؛ یعنی موقعیت {{HTMLElement("option")}} درون فهرست گزینه‌هایی که به آن تعلق دارد، به ترتیب درخت، به صورت یک عدد صحیح. اگر `<option>` بخشی از یک فهرست گزینه نباشد، مقدار `0` است.

## مقدار

یک عدد.

## مثال‌ها

```js
const optionElement = document.getElementById("myOption");
console.log(optionElement.index);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("option")}}
- {{HTMLElement("select")}}
- {{HTMLElement("datalist")}}
- {{DOMxRef("HTMLOptionElement.defaultSelected")}}
- {{DOMxRef("HTMLOptionElement.selected")}}
- {{DOMxRef("HTMLSelectElement.selectedIndex")}}
- {{DOMxRef("HTMLOptionsCollection")}}