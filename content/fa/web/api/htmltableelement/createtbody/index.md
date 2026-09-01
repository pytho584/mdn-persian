---
title: "HTMLTableElement: createTBody() method"
short-title: createTBody()
slug: Web/API/HTMLTableElement/createTBody
page-type: web-api-instance-method
browser-compat: api.HTMLTableElement.createTBody
---

{{APIRef("HTML DOM")}}

متد **`createTBody()`** از اشیاء {{domxref("HTMLTableElement")}} یک عنصر جدید {{HTMLElement("tbody")}} مرتبط با یک {{HtmlElement("table")}} مشخص ایجاد کرده و برمی‌گرداند.

> [!NOTE]
> برخلاف {{domxref("HTMLTableElement.createTHead()")}} و {{domxref("HTMLTableElement.createTFoot()")}}، `createTBody()` به طور سیستماتیک یک عنصر `<tbody>` جدید ایجاد می‌کند، حتی اگر جدول از قبل یک یا چند بدنه داشته باشد. در این صورت، عنصر جدید بعد از بدنه‌های موجود درج می‌شود.

## نحو

```js-nolint
createTBody()
```

### پارامترها

هیچ.

### مقدار بازگشتی

{{domxref("HTMLTableSectionElement")}}

## مثال‌ها

```js
let myBody = myTable.createTBody();
// Now this should be true: myBody === myTable.tBodies.item(myTable.tBodies.length - 1)
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}