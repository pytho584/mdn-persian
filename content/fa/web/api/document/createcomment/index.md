---
title: "Document: createComment() method"
short-title: createComment()
slug: Web/API/Document/createComment
page-type: web-api-instance-method
browser-compat: api.Document.createComment
---

{{APIRef("DOM")}}

**`createComment()`** یک گره دیدگاه (Comment) جدید می‌سازد و آن را برمی‌گرداند.

## سینتکس

```js-nolint
createComment(data)
```

### پارامترها

- `data`
  - : رشته‌ای حاوی داده‌ای که باید به Comment اضافه شود.

### مقدار بازگشتی

یک شیء جدید {{domxref("Comment")}}.

## مثال‌ها

```js
const doc = new DOMParser().parseFromString("<xml></xml>", "application/xml");
const comment = doc.createComment(
  "This is a not-so-secret comment in your document",
);

doc.querySelector("xml").appendChild(comment);

console.log(new XMLSerializer().serializeToString(doc));
// Displays: <xml><!--This is a not-so-secret comment in your document--></xml>
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}