---
title: "MutationEvent: prevValue property"
short-title: prevValue
slug: Web/API/MutationEvent/prevValue
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.MutationEvent.prevValue
---

{{APIRef("UI Events")}}{{Deprecated_Header}}{{non-standard_header}}

ویژگی فقط‌خواندنی **`prevValue`** از رابط {{domxref("MutationEvent")}} یک رشته برمی‌گرداند. در رویدادهای `DOMAttrModified`، این ویژگی مقدار پیشین گرهٔ {{domxref("Attr")}} را نشان می‌دهد. در رویدادهای `DOMCharacterDataModified`، شامل مقدار پیشین گرهٔ {{domxref("CharacterData")}} است. در همهٔ موارد دیگر، رشتهٔ خالی (`""`) را برمی‌گرداند.

## مقدار

یک رشته.

## مثال‌ها

```js
element.addEventListener("DOMAttrModified", (event) => {
  console.log(event.previousValue);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}