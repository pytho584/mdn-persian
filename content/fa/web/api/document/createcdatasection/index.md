---
title: "Document: createCDATASection() method"
---

---
title: "Document: createCDATASection() method"
short-title: createCDATASection()
slug: Web/API/Document/createCDATASection
page-type: web-api-instance-method
browser-compat: api.Document.createCDATASection
---

{{APIRef("DOM")}}

**`createCDATASection()`** یک گره بخش CDATA جدید ایجاد می‌کند و آن را برمی‌گرداند.

## Syntax

```js-nolint
createCDATASection(data)
```

### Parameters

- `data`
  - : یک رشته شامل داده‌هایی که باید به بخش CDATA اضافه شوند.

### Return value

یک گره [بخش CDATA](/en-US/docs/Web/API/CDATASection).

## Examples

```js
const doc = new DOMParser().parseFromString("<xml></xml>", "application/xml");
const cdata = doc.createCDATASection("Some <CDATA> data & then some");
doc.querySelector("xml").appendChild(cdata);
console.log(new XMLSerializer().serializeToString(doc));
// Displays: <xml><![CDATA[Some <CDATA> data & then some]]></xml>
```

## Notes

- این روش فقط با اسناد XML کار می‌کند، نه اسناد HTML (زیرا اسناد HTML از بخش‌های CDATA پشتیبانی نمی‌کنند). تلاش برای استفاده از آن روی یک سند HTML باعث ایجاد خطای `NOT_SUPPORTED_ERR` می‌شود.
- اگر کسی بخواهد دنباله پایانی CDATA (`]]>`) را به عنوان بخشی از داده ارسال کند، یک استثنا از نوع `NS_ERROR_DOM_INVALID_CHARACTER_ERR` پرتاب می‌شود؛ بنابراین داده‌های ارائه‌شده توسط کاربر که فرار (escape) نشده‌اند، نمی‌توانند به صورت ایمن بدون اینکه این روش این استثنا را دریافت کند استفاده شوند ({{domxref("document.createTextNode","createTextNode()")}} اغلب می‌تواند به جای آن استفاده شود).

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}