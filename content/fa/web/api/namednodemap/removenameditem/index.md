---
title: "NamedNodeMap: removeNamedItem() method"
short-title: removeNamedItem()
slug: Web/API/NamedNodeMap/removeNamedItem
page-type: web-api-instance-method
browser-compat: api.NamedNodeMap.removeNamedItem
---

{{APIRef("DOM")}}

متد **`removeNamedItem()`** در رابط {{domxref("NamedNodeMap")}}، گره {{domxref("Attr")}} متناظر با نام داده‌شده را از نقشه حذف می‌کند.

## نحو

```js-nolint
removeNamedItem(attrName)
```

### پارامترها

- `attrName`
  - : نام ویژگی که باید از نقشه حذف شود.

### مقدار بازگشتی

شیء {{domxref("Attr")}} حذف‌شده.

### استثناها

- `NotFoundError` {{domxref("DOMException")}}
  - : اگر ویژگی‌ای با نام داده‌شده وجود نداشته باشد پرتاب می‌شود.

## مثال

```html
<pre test="testValue"></pre>
```

```js
const pre = document.querySelector("pre");
const attrMap = pre.attributes;

let result = `The 'test' attribute initially contains '${attrMap["test"].value}'.\n`;

result += "We remove it.\n\n";
attrMap.removeNamedItem("test");

result += attrMap.getNamedItem("test")
  ? "And 'test' still exists."
  : "And 'test' is no more to be found.";

pre.textContent = result;
```

{{EmbedLiveSample("Example", "100%", 120)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}