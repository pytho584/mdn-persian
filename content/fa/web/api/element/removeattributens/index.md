---
title: "Element: removeAttributeNS() method"
short-title: removeAttributeNS()
slug: Web/API/Element/removeAttributeNS
page-type: web-api-instance-method
browser-compat: api.Element.removeAttributeNS
---

{{ APIRef("DOM") }}

متد **`removeAttributeNS()`** در رابط {{domxref("Element")}}، ویژگی مشخص‌شده با فضای نام مشخص را از یک عنصر حذف می‌کند.

اگر با HTML کار می‌کنید و نیازی به مشخص کردن ویژگی درخواستی به عنوان بخشی از یک فضای نام خاص ندارید، به جای آن از متد {{domxref("Element.removeAttribute()", "removeAttribute()")}} استفاده کنید.

## نحو

```js-nolint
removeAttributeNS(namespace, attrName)
```

### پارامترها

- `namespace`
  - : یک رشته که شامل فضای نام ویژگی است.
- `attrName`
  - : یک رشته که نام ویژگی‌ای را مشخص می‌کند که باید از گره فعلی حذف شود.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

```js
// با توجه به:
//   <div id="div1" xmlns:special="http://www.mozilla.org/ns/specialspace"
//     special:specialAlign="utterleft" width="200px" />
d = document.getElementById("div1");
d.removeAttributeNS("http://www.mozilla.org/ns/specialspace", "specialAlign");
// اکنون: <div id="div1" width="200px" />
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("Element.hasAttributeNS()")}}
- {{domxref("Element.getAttributeNS()")}}
- {{domxref("Element.setAttributeNS()")}}