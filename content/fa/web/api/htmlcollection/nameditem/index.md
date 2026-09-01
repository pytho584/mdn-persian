---
title: "HTMLCollection: namedItem() method"
short-title: namedItem()
slug: Web/API/HTMLCollection/namedItem
page-type: web-api-instance-method
browser-compat: api.HTMLCollection.namedItem
---

{{APIRef("DOM")}}

متد **`namedItem()`** در رابط {{domxref("HTMLCollection")}}، اولین {{domxref("Element")}} در مجموعه را برمی‌گرداند که ویژگی `id` یا `name` آن با نام مشخص‌شده مطابقت داشته باشد؛ اگر هیچ عنصری مطابقت نداشته باشد، `null` برگردانده می‌شود.

در جاوااسکریپت، به جای فراخوانی `collection.namedItem("value")` می‌توانید مستقیماً به نام موردنظر روی مجموعه دسترسی داشته باشید، مانند `collection["value"]`، مگر اینکه آن نام با یکی از ویژگی‌های موجود `HTMLCollection` تداخل داشته باشد.

## Syntax

```js-nolint
namedItem(key)
```

### Parameters

- `key`
  - : رشته‌ای که مقدار ویژگی `id` یا `name` عنصر موردنظر را نشان می‌دهد.

### Return value

اولین {{domxref("Element")}} در {{domxref("HTMLCollection")}} که با `key` مطابقت دارد، یا [`null`](/en-US/docs/Web/JavaScript/Reference/Operators/null) اگر چنین عنصری وجود نداشته باشد. اگر `key` رشته‌ی خالی باشد، همیشه `null` برمی‌گردد.

## Example

### HTML

```html
<div id="personal">
  <span name="title">Dr.</span>
  <span name="first-name">Carina</span>
  <span name="last-name">Anand</span>
  <span id="degree">(MD)</span>
</div>
```

### JavaScript

```js
const container = document.getElementById("personal");

// عنصر HTMLSpanElement با name برابر "title" را برمی‌گرداند؛ اگر چنین عنصری وجود نداشته باشد null برمی‌گردد
const titleSpan = container.children.namedItem("title");

// دو خط زیر در صورت نبود عنصر با نام یا id مطابق، به جای null مقدار undefined برمی‌گردانند
const firstNameSpan = container.children["first-name"];
const lastNameSpan = container.children["last-name"];

// عنصر span با id برابر "degree" را برمی‌گرداند
const degreeSpan = container.children.namedItem("degree");

const output = document.createElement("div");
output.textContent = `Result: ${titleSpan.textContent} ${firstNameSpan.textContent} ${lastNameSpan.textContent} ${degreeSpan.textContent}`;

container.insertAdjacentElement("afterend", output);
```

{{EmbedLiveSample("Example")}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}