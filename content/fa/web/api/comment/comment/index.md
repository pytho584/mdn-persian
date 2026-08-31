---
title: "Comment: Comment() constructor"
short-title: Comment()
slug: Web/API/Comment/Comment
page-type: web-api-constructor
browser-compat: api.Comment.Comment
---

{{ApiRef("DOM")}}

سازنده **`Comment()`** یک شیء {{domxref("Comment")}} تازه ایجاد شده را با رشته اختیاری که به عنوان پارامتر به آن داده می‌شود، به عنوان محتوای متنی آن برمی‌گرداند.

## Syntax

```js-nolint
new Comment()
new Comment(content)
```

### پارامترها

- `content` {{optional_inline}}
  - : رشته‌ای که محتوای متنی دیدگاه را نشان می‌دهد.

### مقدار بازگشتی

یک {{domxref("Comment")}} جدید حاوی `content`، یا رشته خالی اگر پارامتری داده نشده باشد.

## مثال

```js
const comment = new Comment("Test");
```

## Specifications

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [شاخص رابط‌های DOM](/en-US/docs/Web/API/Document_Object_Model)
- {{domxref("Document.createComment()")}} یک جایگزین قدیمی برای این سازنده است.