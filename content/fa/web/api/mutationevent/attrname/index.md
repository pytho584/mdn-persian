---
title: "MutationEvent: attrName property"
---

---
title: "MutationEvent: attrName property"
short-title: attrName
slug: Web/API/MutationEvent/attrName
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.MutationEvent.attrName
---

{{APIRef("UI Events")}}{{Deprecated_Header}}{{non-standard_header}}

ویژگی فقط‌خواندنی **`attrName`** در رابط {{domxref("MutationEvent")}} رشته‌ای را برمی‌گرداند که نام گرهٔ متأثر از رویداد `DOMAttrModified` را در بر دارد. این ویژگی برای سایر رویدادها معنایی ندارد و در آن صورت، مقدار آن به رشتهٔ خالی (`""`) تنظیم می‌شود.

## مقدار

یک رشته.

## مثال‌ها

```js
element.addEventListener("DOMAttrModified", (event) => {
  console.log(event.attrName);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}