---
title: "NamedNodeMap: item() method"
short-title: item()
slug: Web/API/NamedNodeMap/item
page-type: web-api-instance-method
browser-compat: api.NamedNodeMap.item
---

{{APIRef("DOM")}}

متد **`item()`** در رابط {{domxref("NamedNodeMap")}}، آیتم موجود در نقشه را بر اساس اندیس (شاخص) بازمی‌گرداند.

> [!NOTE]
> این متد همچنین زمانی که از عملگر `[]` استفاده می‌کنید فراخوانی می‌شود.
> بنابراین، `myMap[i]` معادل `myMap.item(i)` است که در آن `i` یک عدد است.

## Syntax

```js-nolint
item(index)
[index]
```

### Parameters

- `index`
  - : عددی که اندیس آیتم مورد نظر برای بازگرداندن را نشان می‌دهد.

### Return value

یک {{domxref("Attr")}} یا اگر عدد بزرگ‌تر یا مساوی `length` نقشه باشد، `null` برگردانده می‌شود.

## Example

```html
<pre class="foo" id="bar" contenteditable></pre>
```

```js
const pre = document.querySelector("pre");
const attrMap = pre.attributes;

pre.textContent = `The attribute map contains:
0: ${attrMap.item(0).name}
1: ${attrMap[1].name}
2: ${attrMap.item(2).name}`;
```

{{EmbedLiveSample("Example", "100%", 120)}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
```