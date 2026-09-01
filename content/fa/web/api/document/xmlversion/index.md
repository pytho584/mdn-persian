---
title: "Document: xmlVersion property"
---

---
title: "Document: xmlVersion property"
short-title: xmlVersion
slug: Web/API/Document/xmlVersion
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.Document.xmlVersion
---

{{APIRef("DOM")}}{{deprecated_header}}

شماره نسخه را طبق آنچه در اعلامیه XML مشخص شده است (مثلاً `<?xml version="1.0"?>`) برمی‌گرداند، یا اگر این اعلامیه وجود نداشته باشد، «1.0» را برمی‌گرداند.

این ویژگی هرگز واقعاً مفید نبود، زیرا همیشه مقدار 1.0 را برمی‌گرداند و در DOM Level 4 حذف شده است. به همین دلیل، فایرفاکس ۱۰ دیگر آن را پیاده‌سازی نمی‌کند. کاربرد اصلی آن در گذشته، تشخیص این بود که آیا سند به‌صورت XML رندر می‌شود یا HTML. برای تشخیص این موضوع، می‌توانید یک عنصر با نام کوچک (lowercase) بسازید و بررسی کنید که آیا به حروف بزرگ (uppercase) تبدیل می‌شود؛ در این صورت، سند در حالت غیر-XML و HTML قرار دارد:

```js
if (document.createElement("foo").tagName === "FOO") {
  /* Document is not XML */
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
