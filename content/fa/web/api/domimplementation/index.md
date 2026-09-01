---
title: DOMImplementation
slug: Web/API/DOMImplementation
page-type: web-api-interface
browser-compat: api.DOMImplementation
---

{{ ApiRef("DOM") }}

اینترفیس **`DOMImplementation`** شیئی را نشان می‌دهد که متدهایی را ارائه می‌کند که به هیچ سند خاصی وابسته نیستند. چنین شیئی توسط ویژگی {{domxref("Document.implementation")}} بازگردانده می‌شود.

## Property

این اینترفیس هیچ ویژگی خاصی ندارد و هیچ ویژگی‌ای را به ارث نمی‌برد.

## Instance methods

هیچ متد ارث‌برده‌شده‌ای وجود ندارد.

- {{domxref("DOMImplementation.createDocument()")}}
  - : یک {{domxref("XMLDocument")}} ایجاد و بازمی‌گرداند.
- {{domxref("DOMImplementation.createDocumentType()")}}
  - : یک {{domxref("DocumentType")}} ایجاد و بازمی‌گرداند.
- {{domxref("DOMImplementation.createHTMLDocument()")}}
  - : یک {{domxref("Document")}} اچ‌تی‌ام‌ال ایجاد و بازمی‌گرداند.
- {{domxref("DOMImplementation.hasFeature()")}} {{Deprecated_Inline}}
  - : یک مقدار بولین بازمی‌گرداند که نشان می‌دهد آیا یک قابلیت مشخص پشتیبانی می‌شود یا خیر. این تابع قابلیت اطمینان ندارد و صرفاً برای سازگاری نگهداری می‌شود: به‌جز پرس‌وجوهای مرتبط با SVG، همیشه `true` بازمی‌گرداند. مرورگرهای قدیمی در رفتار خود بسیار ناسازگارند.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [فهرست رابط‌های DOM](/en-US/docs/Web/API/Document_Object_Model)