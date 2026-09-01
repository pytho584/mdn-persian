---
title: "HTMLLinkElement: href property"
short-title: href
slug: Web/API/HTMLLinkElement/href
page-type: web-api-instance-property
browser-compat: api.HTMLLinkElement.href
---

{{APIRef("HTML DOM")}}

ویژگی **`href`** در رابط {{domxref("HTMLLinkElement")}} شامل یک رشته (string) است که URL مرتبط با پیوند را نشان می‌دهد.

این ویژگی بازتاب‌دهندهٔ ویژگی `href` عنصر {{HTMLElement("link")}} است. اگر عنصر فاقد ویژگی `href` باشد، مقدار این ویژگی رشتهٔ خالی (`""`) خواهد بود.

> [!NOTE]
> هر عنصر `<link>` باید شامل یکی یا هر دوی ویژگی‌های `href` یا [`imagesrcset`](/en-US/docs/Web/HTML/Reference/Elements/link#imagesrcset) باشد. این یعنی برای هر `<link>` معتبر، یا این ویژگی یا {{domxref("HTMLLinkElement.imageSrcset", "imageSrcset")}} خالی نخواهد بود.

## مقدار

یک رشته که شامل URL است، یا رشتهٔ خالی (`""`) اگر ویژگی `href` وجود نداشته باشد.

## مثال‌ها

```html
<link rel="stylesheet" href="example.css" />
```

```js
const link = document.getElementsByTag("link")[0];
console.log(link.href); // 'example.css'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- ویژگی {{domxref("HTMLLinkElement.imageSrcset")}}
- ویژگی {{domxref("HTMLAnchorElement.href")}}