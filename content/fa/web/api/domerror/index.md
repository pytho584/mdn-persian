---
title: "DOMError"
---

---
title: DOMError
slug: Web/API/DOMError
page-type: web-api-interface
status:
  - deprecated
  - non-standard
browser-compat: api.DOMError
---

{{APIRef("DOM")}}{{Deprecated_Header}}{{non-standard_header}}

رابط **`DOMError`** یک شیء خطا را توصیف می‌کند که شامل نام خطا است.

## ویژگی‌های نمونه

- {{domxref("DOMError.name")}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : یک رشته برمی‌گرداند که یکی از نام‌های نوع خطا را نشان می‌دهد (به پایین مراجعه کنید).
- {{domxref("DOMError.message")}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : یک رشته برمی‌گرداند که پیام یا توضیح مرتبط با نام نوع خطای داده‌شده را نشان می‌دهد.

## انواع خطا

| Type                         | Description                                                                              |
| ---------------------------- | ---------------------------------------------------------------------------------------- |
| `IndexSizeError`             | ایندکس در محدوده مجاز نیست (مثلاً در یک شیء {{ domxref("range") }} پرتاب می‌شود). |
| `HierarchyRequestError`      | سلسله‌مراتب درخت گره صحیح نیست.                                                          |
| `WrongDocumentError`         | شیء در {{ domxref("document") }} اشتباهی قرار دارد.                                      |
| `InvalidCharacterError`      | رشته شامل نویسه‌های نامعتبر است.                                                         |
| `NoModificationAllowedError` | شیء قابل تغییر نیست.                                                                     |
| `NotFoundError`              | شیء در اینجا یافت نمی‌شود.                                                               |
| `NotSupportedError`          | عملیات پشتیبانی نمی‌شود.                                                                 |
| `InvalidStateError`          | شیء در وضعیت نامعتبری قرار دارد.                                                         |
| `SyntaxError`                | رشته با الگوی مورد انتظار مطابقت نداشت.                                                  |
| `InvalidModificationError`   | شیء به این شکل قابل تغییر نیست.                                                          |
| `NamespaceError`             | عملیات توسط Namespaceها در XML مجاز نیست.                                                |
| `InvalidAccessError`         | شیء از عملیات یا آرگومان پشتیبانی نمی‌کند.                                               |
| `TypeMismatchError`          | نوع شیء با نوع مورد انتظار مطابقت ندارد.                                                 |
| `SecurityError`              | عملیات امن نیست.                                                                         |
| `NetworkError`               | خطای شبکه‌ای رخ داد.                                                                     |
| `AbortError`                 | عملیات لغو شد.                                                                           |
| `URLMismatchError`           | URL داده‌شده با URL دیگری مطابقت ندارد.                                                  |
| `TimeoutError`               | مهلت زمانی عملیات به پایان رسید.                                                         |
| `InvalidNodeTypeError`       | گره نادرست است یا برای این عملیات، نیای (ancestor) نادرستی دارد.                        |
| `DataCloneError`             | شیء قابل کلون‌کردن نیست.                                                                 |

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{ domxref("DOMException") }}