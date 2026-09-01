---
title: "Document: createNSResolver() method"
short-title: createNSResolver()
slug: Web/API/Document/createNSResolver
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.Document.createNSResolver
---

{{ ApiRef("DOM") }}{{deprecated_header}}

متد **`createNSResolver()`** از رابط {{domxref("Document")}} قبلاً برای ایجاد یک شیء سفارشی `XPathNSResolver` استفاده می‌شد. اکنون این متد ورودی را به همان صورت بازمی‌گرداند و تنها به دلایل سازگاری نگه داشته شده است.

## Syntax

```js-nolint
createNSResolver(nodeResolver)
```

### Parameters

- `nodeResolver`
  - : یک {{domxref("Node")}}.

### Return value

خود `nodeResolver`.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Document.evaluate()")}}
- [آشنایی با استفاده از XPath در JavaScript](/en-US/docs/Web/XML/XPath/Guides/Introduction_to_using_XPath_in_JavaScript)