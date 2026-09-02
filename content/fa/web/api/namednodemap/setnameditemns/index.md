---
title: "NamedNodeMap: setNamedItemNS() method"
short-title: setNamedItemNS()
slug: Web/API/NamedNodeMap/setNamedItemNS
page-type: web-api-instance-method
browser-compat: api.NamedNodeMap.setNamedItemNS
---

{{APIRef("DOM")}}

متد **`setNamedItemNS()`** از رابط {{domxref("NamedNodeMap")}}، ویژگی {{domxref("Attr")}} مشخص‌شده با نام خود را در نقشه قرار می‌دهد. اگر قبلاً یک {{domxref("Attr")}} با همان نام در نقشه وجود داشته باشد، _جایگزین_ می‌شود.

> [!NOTE]
> این متد نام مستعار (alias) `setNamedItem()` است و می‌توانید از آن‌ها به جای هم استفاده کنید.

## Syntax

```js-nolint
setNamedItemNS(attr)
```

### Parameters

- `attr`
  - : ویژگی‌ای که باید در نقشه درج شود.

### Return value

در صورت جایگزینی، ویژگی قدیمی را برمی‌گرداند و اگر ویژگی جدید باشد، `null` را برمی‌گرداند.

### Exceptions

- `InUseAttributeError` {{domxref("DOMException")}}
  - : در صورتی که ویژگی همچنان بخشی از نقشه دیگری باشد، پرتاب می‌شود.

## Example

```html
<span ob:one="one"></span>
<pre></pre>
```

```js
const parser = new DOMParser();
// ob:one in <span> is not in a namespace, while ob:one in <warning>, is.
const xmlString =
  '<warning ob:one="test" xmlns:ob="http://www.example.com/ob">Beware!</warning>';
const doc = parser.parseFromString(xmlString, "application/xml");

const span = document.querySelector("span");
const pre = document.querySelector("pre");
const warning = doc.querySelector("warning");
const attrMap = span.attributes;

let result = `The '<span>' element initially contains ${attrMap.length} attribute.\n\n`;

result += "We remove `one` from '<span>' and adds it to '<pre>'.\n";
const one = warning.attributes.removeNamedItemNS(
  "http://www.example.com/ob",
  "one",
);
attrMap.setNamedItemNS(one);
result += `The '<span>' element now contains ${span.attributes.length} attributes:\n\n`;
result += "Prefix\tLocal name\tQualified name\n";
result += "=========================================\n";

for (const attr of attrMap) {
  result += `${attr.prefix}\t${attr.localName}\t\t${attr.name}\n`;
}

pre.textContent = result;
```

{{EmbedLiveSample("Example", "100%", 200)}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}