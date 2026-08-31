---
title: "CharacterData: substringData() method"
short-title: substringData()
slug: Web/API/CharacterData/substringData
page-type: web-api-instance-method
browser-compat: api.CharacterData.substringData
---

{{APIRef("DOM")}}

متد **`substringData()`** از رابط {{domxref("CharacterData")}} بخشی از داده‌های موجود را برمی‌گرداند که از شاخص مشخص‌شده شروع شده و به تعداد کاراکتر مشخصی ادامه می‌یابد.

## نحو (Syntax)

```js-nolint
substringData(offset, count)
```

### پارامترها

- `offset`
  - : شاخص اولین کاراکتری که در زیررشته بازگشتی قرار می‌گیرد. `0` اولین کاراکتر رشته است.
- `count`
  - : تعداد کاراکترهایی که باید برگردانده شوند.

### مقدار بازگشتی

یک رشته حاوی زیررشته.

### استثناها (Exceptions)

- `IndexSizeError` {{domxref("DOMException")}}
  - : اگر `offset + count` از طول داده‌های موجود بزرگ‌تر باشد، پرتاب می‌شود.

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}