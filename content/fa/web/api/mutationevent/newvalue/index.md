---
title: "MutationEvent: newValue property"
short-title: newValue
slug: Web/API/MutationEvent/newValue
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.MutationEvent.newValue
---

{{APIRef("UI Events")}}{{Deprecated_Header}}{{non-standard_header}}

ویژگی فقط‌خواندنی **`newValue`** در رابط {{domxref("MutationEvent")}} یک رشته برمی‌گرداند. در رویدادهای `DOMAttrModified`، این ویژگی مقدار جدید گرهٔ {{domxref("Attr")}} را نشان می‌دهد. در رویدادهای `DOMCharacterDataModified`، شامل مقدار جدید گرهٔ {{domxref("CharacterData")}} است. در همهٔ موارد دیگر، رشتهٔ خالی (`""`) را برمی‌گرداند.

## مقدار

یک رشته.

## مثال‌ها

```js
element.addEventListener("DOMAttrModified", (event) => {
  console.log(event.newValue);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}