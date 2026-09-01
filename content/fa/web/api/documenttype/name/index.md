---
title: "DocumentType: name property"
short-title: name
slug: Web/API/DocumentType/name
page-type: web-api-instance-property
browser-compat: api.DocumentType.name
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`name`** در {{domxref("DocumentType")}} نوع سند را برمی‌گرداند.

برای `DocumentType` مصنوعی، این ویژگی مقدار داده‌شده به‌عنوان پارامتر در {{domxref("DOMImplementation.createDocumentType()")}} را منعکس می‌کند.

برای اسناد HTML، مرورگرها همیشه آن را روی `html` قرار می‌دهند، صرف‌نظر از اینکه `doctype` واقعی در کد منبع چیست.

## مقدار

یک رشته.

## نمونه‌ها

```js
const docType = document.implementation.createDocumentType("html", "", "");

console.log(docType.name); // Display می‌شود `html`
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
