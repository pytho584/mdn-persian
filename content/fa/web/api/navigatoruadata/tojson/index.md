---
title: "NavigatorUAData: toJSON() method"
short-title: toJSON()
slug: Web/API/NavigatorUAData/toJSON
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.NavigatorUAData.toJSON
---

{{APIRef("User-Agent Client Hints API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

متود **`toJSON()`** از رابط {{domxref("NavigatorUAData")}} یک _سریال‌ساز_ است که نمایش JSON از ویژگی‌های _آنتروپی پایین_ شیء `NavigatorUAData` را برمی‌گرداند.

> [!NOTE]
> اصطلاحات _آنتروپی بالا_ و _آنتروپی پایین_ به میزان اطلاعاتی اشاره دارند که این مقادیر درباره مرورگر فاش می‌کنند. مقادیر آنتروپی پایین که توسط این متود برگردانده می‌شوند، آنهایی هستند که اطلاعاتی را که بتواند یک کاربر را شناسایی کند، فاش نمی‌کنند. مقادیر آنتروپی بالا فقط توسط متود {{domxref("NavigatorUAData.getHighEntropyValues()")}} قابل بازگشت هستند.

## Syntax

```js-nolint
toJSON()
```

### Parameters

هیچ.

### Return value

یک شیء JSON.

## Examples

مثال زیر شیء JSON را در کنسول چاپ می‌کند.

```js
console.log(navigator.userAgentData.toJSON());
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}