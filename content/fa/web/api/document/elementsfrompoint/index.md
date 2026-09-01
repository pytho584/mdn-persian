---
title: "Document: elementsFromPoint() method"
short-title: elementsFromPoint()
slug: Web/API/Document/elementsFromPoint
page-type: web-api-instance-method
browser-compat: api.Document.elementsFromPoint
---

{{APIRef("DOM")}}

متد **`elementsFromPoint()`** از رابط {{domxref("Document")}} آرایه‌ای از همهٔ عناصر موجود در مختصات مشخص‌شده (نسبت به viewport) را بازمی‌گرداند. عناصر به ترتیب از بالاترین جعبه تا پایین‌ترین جعبهٔ viewport مرتب می‌شوند.

این متد رفتاری مشابه با متد {{domxref("Document.elementFromPoint", "elementFromPoint()")}} دارد.

## Syntax

```js-nolint
elementsFromPoint(x, y)
```

### Parameters

- `x`
  - : مختصات افقی یک نقطه.
- `y`
  - : مختصات عمودی یک نقطه.

### Return value

یک آرایه از اشیاء {{domxref('Element')}}، مرتب‌شده از بالاترین تا پایین‌ترین جعبهٔ viewport.

## Examples

### HTML

```html
<div>
  <p>Some text</p>
</div>
<p>Elements at point 30, 20:</p>
<div id="output"></div>
```

### JavaScript

```js
let output = document.getElementById("output");
if (document.elementsFromPoint) {
  let elements = document.elementsFromPoint(30, 20);
  elements.forEach((elt, i) => {
    output.textContent += elt.localName;
    if (i < elements.length - 1) {
      output.textContent += " < ";
    }
  });
} else {
  output.innerHTML = `<span style="color: red">
  Browser does not support
  <code>document.elementsFromPoint()</code>
</span>
`;
}
```

{{EmbedLiveSample('Examples', '420', '160')}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{DOMxRef("Document.elementFromPoint()")}}
