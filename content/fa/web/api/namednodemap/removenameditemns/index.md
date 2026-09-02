---
title: "NamedNodeMap: removeNamedItemNS() method"
short-title: removeNamedItemNS()
slug: Web/API/NamedNodeMap/removeNamedItemNS
page-type: web-api-instance-method
browser-compat: api.NamedNodeMap.removeNamedItemNS
---

{{APIRef("DOM")}}

متد **`removeNamedItemNS()`** از رابط {{domxref("NamedNodeMap")}}، ویژگی {{domxref("Attr")}} متناظر با فضای نام و نام محلی داده شده را از نقشه حذف می‌کند.

## Syntax

```js-nolint
removeNamedItemNS(namespace, localName)
```

### پارامترها

- `namespace`
  - : فضای نام ویژگی‌ای که باید از نقشه حذف شود.
    > [!WARNING]
    > `namespace` URI فضای نام است، نه پیشوند.

- `localName`
  - : نام محلی ویژگی‌ای که باید از نقشه حذف شود.

### مقدار بازگشتی

ویژگی {{domxref("Attr")}} حذف شده.

### استثناها

- `NotFoundError` {{domxref("DOMException")}}
  - : در صورت عدم وجود ویژگی با فضای نام و نام محلی داده شده پرتاب می‌شود.

## مثال

```html hidden
<pre></pre>
```

```js
const parser = new DOMParser();
const xmlString =
  '<warning ob:one="test" xmlns:ob="http://www.example.com/ob">Beware!</warning>';
const doc = parser.parseFromString(xmlString, "application/xml");

const pre = document.querySelector("pre");
const warning = doc.querySelector("warning");
const attrMap = warning.attributes;

let result = `The 'ob:one' attribute initially contains '${attrMap["ob:one"].value}'.\n`;

result += "We remove it.\n\n";
attrMap.removeNamedItemNS("http://www.example.com/ob", "one");

result += attrMap["ob:one"]
  ? "And 'ob:one' still exists."
  : "And 'ob:one' is no more to be found.";

pre.textContent = result;
```

{{EmbedLiveSample("Example", "100%", 120)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}