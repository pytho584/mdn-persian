---
title: "Node: contains() method"
short-title: contains()
slug: Web/API/Node/contains
page-type: web-api-instance-method
browser-compat: api.Node.contains
---

{{APIRef("DOM")}}

متد **`contains()`** از رابط {{domxref("Node")}} یک مقدار بولین (Boolean) برمی‌گرداند که نشان می‌دهد آیا یک گره (node) از نوادگان (descendant) گره مشخص‌شده است یا خیر؛ یعنی خود آن گره، یکی از فرزندان مستقیم آن ({{domxref("Node.childNodes", "childNodes")}})، یکی از فرزندان مستقیم آن فرزندان، و همین‌طور الی‌آخر.

> [!NOTE]
> یک گره درون _خودش_ قرار دارد.

## نحو (Syntax)

```js-nolint
contains(otherNode)
```

### پارامترها

- `otherNode`
  - : {{domxref("Node")}}ای که باید آزمایش شود.
    > [!NOTE]
    > `otherNode` اختیاری نیست، اما می‌توان آن را `null` تنظیم کرد.

### مقدار بازگشتی

یک مقدار بولین که اگر `otherNode` درون گره (node) باشد `true` و در غیر این صورت `false` است.

اگر پارامتر `otherNode` برابر با `null` باشد، `contains()` همیشه `false` برمی‌گرداند.

## مثال

این تابع بررسی می‌کند که آیا یک عنصر درون بدنه (body) صفحه قرار دارد یا خیر. از آنجایی که `contains` شامل خود گره نیز می‌شود و تعیین اینکه آیا بدنه خودش را شامل می‌شود هدف `isInPage` نیست، در این حالت به‌صراحت `false` برگردانده می‌شود.

```js
function isInPage(node) {
  return node === document.body ? false : document.body.contains(node);
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Node.compareDocumentPosition")}}
- {{domxref("Node.hasChildNodes")}}