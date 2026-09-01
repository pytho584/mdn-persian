---
title: "HTMLTableElement: createTHead() method"
---

---
title: "HTMLTableElement: createTHead() method"
short-title: createTHead()
slug: Web/API/HTMLTableElement/createTHead
page-type: web-api-instance-method
browser-compat: api.HTMLTableElement.createTHead
---

{{APIRef("HTML DOM")}}

متد **`createTHead()`** از اشیاء {{domxref("HTMLTableElement")}}، عنصر {{HTMLElement("thead")}} مرتبط با یک {{HtmlElement("table")}} مشخص را بازمی‌گرداند. اگر هیچ سربرگی در جدول وجود نداشته باشد، این متد آن را ایجاد کرده و سپس بازمی‌گرداند.

> [!NOTE]
> اگر هیچ سربرگی وجود نداشته باشد، `createTHead()` یک سربرگ جدید را مستقیماً داخل جدول درج می‌کند. برخلاف حالتی که از {{domxref("Document.createElement()")}} برای ایجاد عنصر `<thead>` جدید استفاده می‌شود، در اینجا نیازی به افزودن جداگانهٔ سربرگ نیست.

## سینتکس

```js-nolint
createTHead()
```

### پارامترها

هیچ.

### مقدار بازگشتی

{{domxref("HTMLTableSectionElement")}}

## مثال‌ها

```js
let myHead = myTable.createTHead();
// Now this should be true: myHead === myTable.tHead
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}