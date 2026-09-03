---
title: "Node: hasChildNodes() method"
short-title: hasChildNodes()
slug: Web/API/Node/hasChildNodes
page-type: web-api-instance-method
browser-compat: api.Node.hasChildNodes
---

{{APIRef("DOM")}}

متد **`hasChildNodes()`** در رابط {{domxref("Node")}}
یک مقدار بولی برمی‌گرداند که نشان می‌دهد
آیا {{domxref("Node")}} داده‌شده دارای [گره‌های فرزند](/en-US/docs/Web/API/Node/childNodes) است یا خیر.

## نحو (Syntax)

```js-nolint
hasChildNodes()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک مقدار بولی که اگر گره دارای گره‌های فرزند باشد `true` است و در غیر این صورت
`false` است.

## مثال

```js
let foo = document.getElementById("foo");

if (foo.hasChildNodes()) {
  // Do something with 'foo.childNodes'
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Node.childNodes")}}