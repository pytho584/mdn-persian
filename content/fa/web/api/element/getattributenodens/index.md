---
title: "Element: getAttributeNodeNS() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Element/getAttributeNodeNS"
---

---
title: "Element: getAttributeNodeNS() method"
short-title: getAttributeNodeNS()
slug: Web/API/Element/getAttributeNodeNS
page-type: web-api-instance-method
browser-compat: api.Element.getAttributeNodeNS
---

{{ APIRef("DOM") }}

متد **`getAttributeNodeNS()`** در رابط {{domxref("Element")}}، گره {{domxref("Attr")}} دارای فضای نام (namespace) یک عنصر را برمی‌گرداند.

این متد زمانی مفید است که به [ویژگی‌های نمونه](/en-US/docs/Web/API/Attr#instance_properties) مربوط به ویژگی دارای فضای نام نیاز داشته باشید. اگر فقط مقدار ویژگی دارای فضای نام را نیاز دارید، می‌توانید به جای آن از متد {{domxref("Element.getAttributeNS()", "getAttributeNS()")}} استفاده کنید.

اگر در اسناد HTML به گره {{domxref("Attr")}} یک عنصر نیاز دارید و ویژگی دارای فضای نام نیست، به جای آن از متد {{domxref("Element.getAttributeNode()", "getAttributeNode()")}} استفاده کنید.

## Syntax

```js-nolint
getAttributeNodeNS(namespace, nodeName)
```

### Parameters

- `namespace`
  - : رشته‌ای که فضای نام ویژگی را مشخص می‌کند.
- `nodeName`
  - : رشته‌ای که نام ویژگی را مشخص می‌کند.

### Return value

گره مربوط به ویژگی مشخص‌شده.

## Notes

`getAttributeNodeNS` نسبت به [getAttributeNode](/en-US/docs/Web/API/Element/getAttributeNode) دقیق‌تر است، زیرا به شما امکان می‌دهد ویژگی‌هایی را که بخشی از یک فضای نام خاص هستند مشخص کنید. متد تنظیم‌کننده متناظر با آن، [setAttributeNodeNS](/en-US/docs/Web/API/Element/setAttributeNodeNS) است.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Document.createAttribute()")}}
- {{domxref("Document.createAttributeNS()")}}
- {{domxref("Element.setAttributeNodeNS()")}}