---
title: "Element: hasAttributeNS() method"
short-title: hasAttributeNS()
slug: Web/API/Element/hasAttributeNS
page-type: web-api-instance-method
browser-compat: api.Element.hasAttributeNS
---

{{ APIRef("DOM") }}

متد **`hasAttributeNS()`** از رابط {{domxref("Element")}} یک مقدار بولی برمی‌گرداند که نشان می‌دهد آیا عنصر جاری دارای ویژگی مشخص‌شده با فضای نام مشخص است یا خیر.

اگر با اسناد HTML کار می‌کنید و نیازی به تعیین این ندارید که ویژگی درخواستی بخشی از یک فضای نام خاص باشد، به‌جای آن از متد {{domxref("Element.hasAttribute()", "hasAttribute()")}} استفاده کنید.

## نحو

```js-nolint
hasAttributeNS(namespace,localName)
```

### پارامترها

- `namespace`
  - : رشته‌ای که فضای نام ویژگی را مشخص می‌کند.
- `localName`
  - : نام ویژگی.

### مقدار بازگشتی

یک مقدار بولی.

## مثال‌ها

```js
// Check that the attribute exists before you set a value
const d = document.getElementById("div1");
if (
  d.hasAttributeNS("http://www.mozilla.org/ns/specialspace/", "special-align")
) {
  d.setAttribute("align", "center");
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("Element.getAttributeNS()")}}
- {{domxref("Element.setAttributeNS()")}}
- {{domxref("Element.removeAttributeNS()")}}