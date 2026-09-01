---
title: "HTMLImageElement: longDesc property"
short-title: longDesc
slug: Web/API/HTMLImageElement/longDesc
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.HTMLImageElement.longDesc
---

{{APIRef("HTML DOM")}}{{deprecated_header}}

ویژگی **منسوخ‌شده** `longDesc` در رابط {{domxref("HTMLImageElement")}}، نشانی (URL) یک فایل متنی یا HTML را مشخص می‌کند که حاوی توضیح بلند و مفصلی از تصویر است. این ویژگی می‌تواند برای ارائه جزئیات اضافی اختیاری فراتر از توضیح کوتاه ارائه‌شده در ویژگی [`title`](/en-US/docs/Web/HTML/Reference/Global_attributes/title) استفاده شود. این ویژگی منعکس‌کننده ویژگی محتوایی [`longdesc`](/en-US/docs/Web/HTML/Reference/Elements/img#longdesc) عنصر `<img>` است.

این ویژگی در [مشخصات HTML](https://html.spec.whatwg.org/multipage/obsolete.html#element-attrdef-img-longdesc) منسوخ تلقی می‌شود و آینده نامشخصی دارد. نویسندگان باید از یک جایگزین {{glossary("WAI")}}-{{glossary("ARIA")}} مانند [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) یا [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details) استفاده کنند. همچنین می‌توانید تصویر را درون یک پیوند با استفاده از عنصر {{HTMLElement("a")}} قرار دهید.

## مقدار

یک رشته که می‌تواند یک رشته خالی باشد (نشان‌دهنده عدم وجود توضیح بلند) یا نشانی یک فایل حاوی توضیح بلند از محتوای تصویر.

## مثال‌ها

HTML قدیمی زیر را در نظر بگیرید:

```html
<img
  src="taco-tuesday.jpg"
  alt="Taco Tuesday"
  longdesc="image-descriptions/taco-tuesday.html" />
```

در اینجا، `longDesc` برای نشان دادن این استفاده می‌شود که کاربر باید بتواند به توضیح دقیق تصویر `taco-tuesday.jpg` در فایل HTML `image-descriptions/taco-tuesday.html` دسترسی داشته باشد.

این کد باید به HTML زیر تبدیل شود:

```html
<a href="image-descriptions/taco-tuesday.html">
  <img src="taco-tuesday.jpg" alt="Taco Tuesday" />
</a>
```

با این کار، تصویر به یک پیوند به فایل HTML که تصویر را با جزئیات بیشتر توضیح می‌دهد، تبدیل می‌شود.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details)