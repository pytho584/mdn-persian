---
title: "HTMLTableElement: rows property"
---

---
title: "HTMLTableElement: rows property"
short-title: rows
slug: Web/API/HTMLTableElement/rows
page-type: web-api-instance-property
browser-compat: api.HTMLTableElement.rows
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`rows`** در {{domxref("HTMLTableElement")}} یک {{domxref("HTMLCollection")}} زنده از تمام ردیف‌های جدول برمی‌گرداند، از جمله ردیف‌هایی که درون عناصر {{HTMLElement("thead")}}، {{HTMLElement("tfoot")}} و {{HTMLElement("tbody")}} قرار دارند.

اگرچه خود ویژگی فقط‌خواندنی است، شیء بازگردانده‌شده زنده است و امکان تغییر محتوای آن را فراهم می‌کند.

## مقدار

یک {{domxref("HTMLCollection")}} که فهرستی به‌روزشونده به صورت زنده از اشیای {{domxref("HTMLTableRowElement")}} ارائه می‌دهد؛ این اشیا نمایانگر تمام عناصر {{HTMLElement("tr")}} موجود در جدول هستند. این فهرست دسترسی سریع به تمام ردیف‌های جدول را بدون نیاز به جستجوی دستی آن‌ها فراهم می‌کند.

## مثال‌ها

```js
myRows = myTable.rows;
firstRow = myTable.rows[0];
lastRow = myTable.rows.item(myTable.rows.length - 1);
```

این مثال نشان می‌دهد که چگونه می‌توانید هم از دسترسی ایندکس‌دار و هم از متد {{domxref("HTMLCollection.item()")}} برای دریافت ردیف‌های جداگانه جدول استفاده کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}