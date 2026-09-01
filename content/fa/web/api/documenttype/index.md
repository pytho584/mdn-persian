---
title: "DocumentType"
---

---
title: DocumentType
slug: Web/API/DocumentType
page-type: web-api-interface
browser-compat: api.DocumentType
---

{{APIRef("DOM")}}

interface **`DocumentType`** نمایانگر یک {{domxref("Node")}} حاوی doctype است.

{{InheritanceDiagram}}

## ویژگیهای نمونه

_ویژگیهای والد خود، {{domxref("Node")}} را به ارث میبرد._

- {{domxref("DocumentType.name")}} {{ReadOnlyInline}}
  - : نوع سند. برای اسناد HTML همیشه `"html"` است، اما برای اسناد XML متغیر خواهد بود.
- {{domxref("DocumentType.publicId")}} {{ReadOnlyInline}}
  - : یک رشته شامل شناسه نوع سند. اگر doctype داده‌شده شناسه عمومی مشخص نکرده باشد، خالی است.
- {{domxref("DocumentType.systemId")}} {{ReadOnlyInline}}
  - : یک رشته شامل URL مربوط به DTD مرتبط. اگر doctype داده‌شده شناسه سیستمی مشخص نکرده باشد، خالی است.

## روش‌های نمونه

_روش‌های والد خود، {{domxref("Node")}} را به ارث می‌برد._

- {{domxref("DocumentType.after()")}}
  - : مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها را در فهرست فرزندان والدِ شیء، دقیقاً بعد از این گره درج می‌کند.
- {{domxref("DocumentType.before()")}}
  - : مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها را در فهرست فرزندان والدِ شیء، دقیقاً قبل از این گره درج می‌کند.
- {{domxref("DocumentType.remove()")}}
  - : این شیء را از فهرست فرزندان والدش حذف می‌کند.
- {{domxref("DocumentType.replaceWith()")}}
  - : نوع سند را با مجموعه‌ای از گره‌های داده‌شده جایگزین می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [فهرست interfaceهای DOM.](/en-US/docs/Web/API/Document_Object_Model)
- {{domxref("DOMImplementation.createDocumentType()")}} برای ایجاد یک گره `DocumentType` جدید.