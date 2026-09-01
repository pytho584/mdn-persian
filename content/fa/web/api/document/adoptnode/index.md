---
title: "Document: adoptNode() method"
short-title: adoptNode()
slug: Web/API/Document/adoptNode
page-type: web-api-instance-method
browser-compat: api.Document.adoptNode
---

{{ ApiRef("DOM") }}

متد **`Document.adoptNode()`** یک {{Glossary("node/dom", "گره (node)")}} را از یک {{domxref("Document", "سند (document)", "", "1")}} دیگر به سند جاری منتقل می‌کند.
گره‌ی پذیرفته‌شده و زیردرخت آن از سند اصلی خود (در صورت وجود) حذف می‌شوند و {{domxref("Node.ownerDocument", "ownerDocument")}} آن‌ها به سند جاری تغییر می‌کند.
سپس می‌توان گره را در سند جاری درج کرد.

## نحو (Syntax)

```js-nolint
adoptNode(externalNode)
```

### پارامترها

- `externalNode`
  - : گره‌ای از سندی دیگر که قرار است پذیرفته شود.

### مقدار بازگشتی

گره‌ی کپی‌شده‌ی `importedNode` در محدوده‌ی سند واردکننده.

پس از فراخوانی این متد، `importedNode` و `externalNode` همان شیء واحد هستند.

> [!NOTE]
> {{domxref("Node.parentNode")}} مربوط به `importedNode` برابر با `null` است، زیرا هنوز در درخت سند درج نشده است!

## مثال‌ها

```js
const iframe = document.querySelector("iframe");
const iframeImages = iframe.contentDocument.querySelectorAll("img");
const newParent = document.getElementById("images");

iframeImages.forEach((imgEl) => {
  newParent.appendChild(document.adoptNode(imgEl));
});
```

## نکات

پیش از آنکه گره‌های متعلق به اسناد خارجی بتوانند در سند جاری درج شوند، باید یکی از این دو کار انجام شود:

- با استفاده از {{domXref("document.importNode()")}}克隆 (clone) شوند؛ یا
- با استفاده از `document.adoptNode()` پذیرفته شوند.

برای اطلاعات بیشتر دربارهٔ مسائل مربوط به {{domXref("Node.ownerDocument")}}، به [پرسش‌های متداول DOM در W3C](https://www.w3.org/DOM/faq.html#ownerdoc) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("document.importNode()")}}