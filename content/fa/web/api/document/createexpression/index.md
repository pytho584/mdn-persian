---
title: "Document: createExpression() method"
short-title: createExpression()
slug: Web/API/Document/createExpression
page-type: web-api-instance-method
browser-compat: api.Document.createExpression
---

{{APIRef("DOM")}}

این متد یک {{DOMxRef("XPathExpression")}} را کامپایل می‌کند که می‌تواند برای ارزیابی‌های (تکراری) استفاده شود.

شما باید این متد را روی همان سندی فراخوانی کنید که عبارت را روی آن اجرا می‌کنید.

## نحو (Syntax)

```js-nolint
createExpression(xpathText, namespaceURLMapper)
```

### پارامترها

- `xpathText`
  - : یک رشته که عبارت XPath برای کامپایل شدن است.
- `namespaceURLMapper`
  - : یک تابع که پیشوند فضای نام را به یک URL فضای نام (یا اگر نیازی نباشد `null`) نگاشت می‌کند.

### مقدار بازگشتی

{{DOMxRef("XPathExpression")}}

## مثال‌ها

```js
const xpathExpr = document.createExpression("//div");
const xpathResult = xpathExpr.evaluate(document); // returns an XPathResult object
const nodeContext = document.querySelector("nav");
// Re-using the XPathExpression "xpathExpr"
const otherResult = xpathExpr.evaluate(nodeContext); // returns an XPathResult object
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("Document.evaluate()")}}
- {{DOMxRef("XPathExpression")}}