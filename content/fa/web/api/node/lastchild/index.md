---
title: "Node: lastChild property"
short-title: lastChild
slug: Web/API/Node/lastChild
page-type: web-api-instance-property
browser-compat: api.Node.lastChild
---

{{APIRef("DOM")}}

ویژگی فقط-خواندنی **`lastChild`** از رابط {{domxref("Node")}}، آخرین فرزند گره را برمی‌گرداند، یا اگر هیچ گره فرزندی وجود نداشته باشد، `null` را برمی‌گرداند.

> [!NOTE]
> این ویژگی هر نوع گره‌ای که آخرین فرزند این گره باشد را برمی‌گرداند. ممکن است یک گره {{domxref("Text")}} یا {{domxref("Comment")}} باشد. اگر می‌خواهید آخرین {{domxref("Element")}} که فرزند یک عنصر دیگر است را دریافت کنید، از {{domxref("Element.lastElementChild")}} استفاده کنید.

## مقدار

یک {{domxref("Node")}} که آخرین فرزند گره است، یا `null` در صورت عدم وجود گره فرزند.

## مثال

```js
const tr = document.getElementById("row1");
const cornerTd = tr.lastChild;
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Node.firstChild")}}
- {{domxref("Element.lastElementChild")}}