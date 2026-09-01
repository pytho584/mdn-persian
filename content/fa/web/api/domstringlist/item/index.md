---
title: "DOMStringList: item() method"
short-title: item()
slug: Web/API/DOMStringList/item
page-type: web-api-instance-method
browser-compat: api.DOMStringList.item
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

متد **`item()`** یک رشته را از یک [`DOMStringList`](/en-US/docs/Web/API/DOMStringList) بر اساس ایندکس (شاخص) برمی‌گرداند.

## Syntax

```js-nolint
item(index)
```

جاوااسکریپت همچنین یک نحو براکت‌دار شبیه به آرایه برای دریافت یک مورد از
`DOMStringList` با ایندکس ارائه می‌دهد:

```js
list[index];
```

### Parameters

- `index`
  - : ایندکس رشته‌ای که باید دریافت شود. ایندکس از صفر شروع می‌شود.

### Return value

رشته‌ای که در موقعیت ایندکس در `DOMStringList` قرار دارد؛ در غیر این صورت اگر ایندکس ارائه‌شده خارج از محدوده باشد، `null` برمی‌گردد.

### Exceptions

- {{jsxref("TypeError")}}
  - : اگر آرگومانی ارائه نشود، این خطا پرتاب می‌شود.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
```