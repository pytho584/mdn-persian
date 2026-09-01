---
title: "HTMLElement: draggable property"
---

---
title: "HTMLElement: draggable property"
short-title: draggable
slug: Web/API/HTMLElement/draggable
page-type: web-api-instance-property
browser-compat: api.HTMLElement.draggable
---

{{APIRef("HTML Drag and Drop API")}}

ویژگی **`draggable`** در رابط {{domxref("HTMLElement")}} یک مقدار اولیهٔ {{jsxref("Boolean")}} را دریافت و تنظیم می‌کند که نشان می‌دهد آیا عنصر قابل کشیدن است یا نه.

این ویژگی مقدارِ [ویژگی سراسری HTML `draggable`](/en-US/docs/Web/HTML/Reference/Global_attributes/draggable) را بازتاب می‌دهد.

## مقدار

یک مقدار اولیهٔ {{jsxref("Boolean")}} که اگر عنصر قابل کشیدن باشد `true` است و در غیر این صورت `false`.

## مثال‌ها

مثال زیر نشان می‌دهد که چگونه می‌توان قابلیت کشیدن عنصر را از طریق اسکریپت فعال یا غیرفعال کرد:

```js
const draggableElement = document.querySelector(".draggable-element");
const notDraggableElement = document.querySelector(".not-draggable-element");

// enable the target element's ability to drag
draggableElement.draggable = true;

// disable the target element's ability to drag
notDraggableElement.draggable = false;
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی سراسری HTML [`draggable`](/en-US/docs/Web/HTML/Reference/Global_attributes/draggable)
- مروری بر [HTML Drag and Drop API](/en-US/docs/Web/API/HTML_Drag_and_Drop_API)