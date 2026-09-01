---
title: "HTMLLinkElement: disabled property"
short-title: disabled
slug: Web/API/HTMLLinkElement/disabled
page-type: web-api-instance-property
browser-compat: api.HTMLLinkElement.disabled
---

{{APIRef("HTML DOM")}}

ویژگی **`disabled`** در رابط {{domxref("HTMLLinkElement")}} یک مقدار بولی است که نشان می‌دهد آیا پیوند غیرفعال است یا نه. این ویژگی تنها روی پیوندهای استایل‌شیت تأثیر می‌گذارد (زمانی که ویژگی `rel` برابر با `stylesheet` باشد).

اگر هنگام بارگذاری HTML، ویژگی `disabled` در آن مشخص شده باشد، استایل‌شیت در طول بارگذاری صفحه بارگذاری نمی‌شود. در عوض، استایل‌شیت تنها زمانی بارگذاری می‌شود که ویژگی `disabled` روی `false` تنظیم شود یا حذف گردد. تنظیم ویژگی `disabled` با استفاده از جاوااسکریپت باعث می‌شود استایل‌شیت از فهرست {{domxref("Document.styleSheets")}} سند حذف شود.

این ویژگی منعکس‌کنندهٔ ویژگی `disabled` عنصر {{HTMLElement("link")}} است.

## مقدار

یک مقدار بولی.

## مثال‌ها

```html
<link
  id="el"
  href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
  rel="stylesheet"
  disabled
  crossorigin="anonymous" />
```

```js
const el = document.getElementById("el");
console.log(el.disabled); // Output: true

// Set the disabled property to false to enable the stylesheet
el.disabled = false;
console.log(el.disabled); // Output: false
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLScriptElement.integrity")}}
- [Subresource Integrity](/en-US/docs/Web/Security/Defenses/Subresource_Integrity)