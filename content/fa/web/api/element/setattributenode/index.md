---
title: "Element: setAttributeNode() method"
short-title: setAttributeNode()
slug: Web/API/Element/setAttributeNode
page-type: web-api-instance-method
browser-compat: api.Element.setAttributeNode
---

{{ APIRef("DOM") }}

متد **`setAttributeNode()`** از رابط {{domxref("Element")}} یک گره {{domxref("Attr")}} جدید به عنصر مشخص‌شده اضافه می‌کند.

اگر نیازی به کار با گره ویژگی (مثلاً شبیه‌سازی آن از یک عنصر دیگر) قبل از افزودن ندارید، می‌توانید به‌جای آن از متد {{domxref("Element.setAttribute()", "setAttribute()")}} استفاده کنید.

## نحو

```js-nolint
setAttributeNode(attribute)
```

### پارامترها

- `attribute`
  - : گره {{domxref("Attr")}} که باید به عنصر اضافه شود.

### مقدار بازگشتی

گره ویژگی جایگزین‌شده، در صورت وجود، توسط این تابع بازگردانده می‌شود.

## مثال‌ها

این مثال ویژگی `lang` را از یک عنصر به عنصر دیگر کپی می‌کند.

### HTML

```html
<div id="one" lang="en-US">one</div>
<div id="two">two</div>
```

### JavaScript

```js
const d1 = document.getElementById("one");
const d2 = document.getElementById("two");
const a = d1.getAttributeNode("lang");

d2.setAttributeNode(a.cloneNode(true));

// Returns: 'en-US'
console.log(d2.attributes[1].value);
```

## یادداشت‌ها

اگر ویژگی‌ای با همان نام قبلاً روی عنصر وجود داشته باشد، آن ویژگی با ویژگی جدید جایگزین می‌شود و ویژگی جایگزین‌شده بازگردانده می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document.createAttribute()")}}
- {{domxref("Element.getAttributeNode()")}}
- {{domxref("Element.removeAttributeNode()")}}