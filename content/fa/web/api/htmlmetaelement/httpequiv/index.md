---
title: "HTMLMetaElement: httpEquiv property"
short-title: httpEquiv
slug: Web/API/HTMLMetaElement/httpEquiv
page-type: web-api-instance-property
browser-compat: api.HTMLMetaElement.httpEquiv
---

{{APIRef("HTML DOM")}}

خاصیت **`HTMLMetaElement.httpEquiv`** مقدار دستور pragma یا نام هدر پاسخ HTTP را برای ویژگی {{domxref("HTMLMetaElement.content")}} دریافت یا تنظیم می‌کند. برای اطلاعات بیشتر در مورد مقادیر ممکن، به ویژگی [http-equiv](/en-US/docs/Web/HTML/Reference/Elements/meta/http-equiv) مراجعه کنید.

## مقدار

یک رشته (string).

## مثال‌ها

### خواندن مقدار `http-equiv` یک عنصر meta

مثال زیر یک عنصر `<meta>` با ویژگی `http-equiv` را جستجو می‌کند. مقدار `http-equiv` در کنسول ثبت می‌شود که یک [دستور pragma](/en-US/docs/Web/HTML/Reference/Elements/meta/http-equiv) از نوع `refresh` را نشان می‌دهد که به مرورگر دستور می‌دهد پس از تعداد ثانیه‌های مشخص‌شده در ویژگی `content` صفحه را تازه‌سازی کند:

```js
// با فرض <meta http-equiv="refresh" content="10" />
const meta = document.querySelector("meta[http-equiv]");
console.log(meta.httpEquiv);
// refresh
console.log(meta.content);
// 10
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{HTMLElement("meta")}}