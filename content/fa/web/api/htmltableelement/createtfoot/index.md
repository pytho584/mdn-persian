---
title: "HTMLTableElement: createTFoot() method"
short-title: createTFoot()
slug: Web/API/HTMLTableElement/createTFoot
page-type: web-api-instance-method
browser-compat: api.HTMLTableElement.createTFoot
---

{{APIRef("HTML DOM")}}

متد **`createTFoot()`** از شیء {{domxref("HTMLTableElement")}}، عنصر {{HTMLElement("tfoot")}} مرتبط با یک {{HtmlElement("table")}} داده شده را بازمی‌گرداند. اگر هیچ پاورقی (footer) در جدول وجود نداشته باشد، این متد آن را ایجاد کرده و سپس بازمی‌گرداند.

> **نکته:** اگر پاورقی وجود نداشته باشد، `createTFoot()` یک پاورقی جدید مستقیماً درون جدول درج می‌کند. نیازی به افزودن جداگانه پاورقی نیست، برخلاف حالتی که از {{domxref("Document.createElement()")}} برای ایجاد عنصر جدید `<tfoot>` استفاده شده باشد.

## نحو (Syntax)

```js-nolint
createTFoot()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

{{domxref("HTMLTableSectionElement")}}

## مثال

```js
let myFoot = myTable.createTFoot();
// اکنون این باید true باشد: myFoot === myTable.tFoot
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}