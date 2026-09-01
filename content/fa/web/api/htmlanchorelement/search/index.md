---
title: "HTMLAnchorElement: search property"
---

---
title: "HTMLAnchorElement: search property"
short-title: search
slug: Web/API/HTMLAnchorElement/search
page-type: web-api-instance-property
browser-compat: api.HTMLAnchorElement.search
---

{{ApiRef("HTML DOM")}}

ویژگی **`search`** در رابط {{domxref("HTMLAnchorElement")}} یک رشتهٔ جستجو است که به آن _رشتهٔ پرس‌وجو (query string)_ نیز گفته می‌شود؛ این رشته شامل یک `"?"` و به دنبال آن پارامترهای `href` عنصر `<a>` است. اگر URL پرس‌وجوی جستجو نداشته باشد، این ویژگی شامل یک رشتهٔ خالی، `""`، است.

این ویژگی را می‌توان برای تغییر رشتهٔ پرس‌وجوی URL مقداردهی کرد. هنگام مقداردهی، اگر مقدار داده‌شده از قبل پیشوند `"?"` نداشته باشد، یک `"?"` به ابتدای آن اضافه می‌شود. تنظیم آن به `""` رشتهٔ پرس‌وجو را حذف می‌کند.

پرس‌وجو هنگام مقداردهی {{Glossary("Percent-encoding", "percent-encoded")}} می‌شود، اما هنگام خواندن percent-decoded نمی‌شود.

مرورگرهای مدرن امکانات [`URLSearchParams`](/en-US/docs/Web/API/URLSearchParams/get#examples) و [`URL.searchParams`](/en-US/docs/Web/API/URL/searchParams#examples) را فراهم می‌کنند تا تجزیهٔ پارامترهای رشتهٔ پرس‌وجو آسان شود.

برای اطلاعات بیشتر به {{domxref("URL.search")}} مراجعه کنید.

## مقدار

یک رشته.

## مثال‌ها

### دریافت رشتهٔ جستجو از یک پیوند anchor

```js
// An <a id="myAnchor" href="/en-US/docs/HTMLAnchorElement?q=123"> element is in the document
const anchor = document.getElementById("myAnchor");
anchor.search; // returns '?q=123'
```

### تجزیهٔ پیشرفته با استفاده از URLSearchParams

به‌عنوان جایگزین، می‌توان از [`URLSearchParams`](/en-US/docs/Web/API/URLSearchParams/get#examples) استفاده کرد:

```js
let params = new URLSearchParams(queryString);
let q = parseInt(params.get("q"), 10); // returns the number 123
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("HTMLAnchorElement")}} که این ویژگی به آن تعلق دارد.