---
title: "NamedNodeMap: getNamedItem() method"
short-title: getNamedItem()
slug: Web/API/NamedNodeMap/getNamedItem
page-type: web-api-instance-method
browser-compat: api.NamedNodeMap.getNamedItem
---

{{APIRef("DOM")}}

متد **`getNamedItem()`** از رابط {{domxref("NamedNodeMap")}}، شیء {{domxref("Attr")}} متناظر با نام داده شده را برمی‌گرداند، یا اگر ویژگی متناظری وجود نداشته باشد، `null` را برمی‌گرداند.

> [!NOTE]
> این متد همچنین زمانی که از عملگر `[]` استفاده می‌کنید فراخوانی می‌شود.
> بنابراین، `myMap[str]` معادل `myMap.getNamedItem(str)` است که در آن `str` یک رشته است.

## نحو

```js-nolint
getNamedItem(name)
[name]
```

### پارامترها

- `name`
  - : یک رشته شامل نام ویژگی مورد نظر.

### مقدار بازگشتی

یک {{domxref("Attr")}} متناظر با `name` داده شده در پارامتر، یا `null` اگر هیچ‌کدام پیدا نشود.

## مثال

```html
<pre test="test"></pre>
```

```js
const pre = document.querySelector("pre");
const attrMap = pre.attributes;
const value = attrMap.getNamedItem("test").value;
pre.textContent = `The 'test' attribute contains ${value}.
And 'foo' has ${attrMap["foo"] ? "been" : "not been"} found.`;
```

{{EmbedLiveSample("Example", "100%", 80)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}