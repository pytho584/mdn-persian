---
title: "Document: createRange() method"
short-title: createRange()
slug: Web/API/Document/createRange
page-type: web-api-instance-method
browser-compat: api.Document.createRange
---

{{APIRef("DOM")}}

متد **`Document.createRange()`** یک شیء {{domxref("Range")}} جدید بازمی‌گرداند که نقطهٔ آغاز و پایان آن در آفست ۰ از شیء {{domxref("Document")}}ای قرار دارد که این متد روی آن فراخوانی شده است.

## نحو (Syntax)

```js-nolint
createRange()
```

### پارامترها

هیچ.

### مقدار بازگشتی

شیء {{domxref("Range")}} ساخته‌شده.

## مثال‌ها

```js
const range = document.createRange();

range.setStart(startNode, startOffset);
range.setEnd(endNode, endOffset);
```

## نکات

پس از ایجاد یک `Range`، باید نقاط مرزی آن را تنظیم کنید تا بتوانید از بیشتر متدهای آن استفاده کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}