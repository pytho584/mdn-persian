---
title: "NamedNodeMap: getNamedItemNS() method"
---

---
title: "NamedNodeMap: getNamedItemNS() method"
short-title: getNamedItemNS()
slug: Web/API/NamedNodeMap/getNamedItemNS
page-type: web-api-instance-method
browser-compat: api.NamedNodeMap.getNamedItemNS
---

{{APIRef("DOM")}}

متد **`getNamedItemNS()`** در رابط {{domxref("NamedNodeMap")}}، {{domxref("Attr")}} متناظر با نام محلی (local name) داده‌شده در فضای نام (namespace) داده‌شده را بازمی‌گرداند؛ یا اگر ویژگی متناظری وجود نداشته باشد، `null` را برمی‌گرداند.

## نحو

```js-nolint
getNamedItemNS(namespace, localName)
```

### پارامترها

- `namespace`
  - : رشته‌ای حاوی URI فضای نامِ ویژگی موردنظر.
    > [!WARNING]
    > `namespace` همان URI فضای نام است، نه پیشوند (prefix) آن.
- `localName`
  - : رشته‌ای حاوی localName ویژگی موردنظر.

### مقدار بازگشتی

یک {{domxref("Attr")}} متناظر با فضای نام و نام محلی داده‌شده در پارامترها؛ یا اگر هیچ موردی یافت نشود، `null`.

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

const value = warning.attributes.getNamedItemNS(
  "http://www.example.com/ob",
  "one",
).value;

pre.textContent = `The 'ob:one' attribute contains: ${value}.`;
```

{{EmbedLiveSample("Example", "100%", 80)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}