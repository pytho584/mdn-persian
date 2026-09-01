---
title: "HTMLAreaElement: search property"
---

{{ApiRef("HTML DOM")}}

خاصیت **`search`** از رابط {{domxref("HTMLAreaElement")}} یک رشته جست‌وجو (که به آن _رشته پرس‌وجو_ یا query string نیز گفته می‌شود) است. این رشته شامل یک `"?"` به همراه پارامترهای `href` عنصر `<area>` می‌باشد. اگر URL فاقد رشته جست‌وجو باشد، این خاصیت شامل یک رشته خالی `""` خواهد بود.

این خاصیت قابل تنظیم است تا رشته پرس‌وجوی URL تغییر کند. هنگام تنظیم، یک پیشوند `"?"` به مقدار ارائه‌شده اضافه می‌شود، مگر اینکه از قبل وجود داشته باشد. تنظیم آن به `""` باعث حذف رشته پرس‌وجو می‌شود.

رشته پرس‌وجو هنگام تنظیم {{Glossary("Percent-encoding", "درصد-کدگذاری")}} می‌شود اما هنگام خواندن درصد-کدگشایی نمی‌شود.

مرورگرهای مدرن [`URLSearchParams`](/en-US/docs/Web/API/URLSearchParams/get#examples) و [`URL.searchParams`](/en-US/docs/Web/API/URL/searchParams#examples) را ارائه می‌دهند تا تجزیه پارامترها از رشته پرس‌وجو آسان‌تر شود.

برای اطلاعات بیشتر به {{domxref("URL.search")}} مراجعه کنید.

## مقدار

یک رشته.

## مثال‌ها

### دریافت رشته جست‌وجو از یک پیوند ناحیه

```js
// An <area id="myArea" href="/en-US/docs/HTMLAreaElement?q=123"> element is in the document
const area = document.getElementById("myArea");
area.search; // returns '?q=123'
```

### تجزیه پیشرفته با استفاده از URLSearchParams

همچنین می‌توان از [`URLSearchParams`](/en-US/docs/Web/API/URLSearchParams/get#examples) استفاده کرد:

```js
let params = new URLSearchParams(queryString);
let q = parseInt(params.get("q"), 10); // returns the number 123
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("HTMLAreaElement")}} که این خاصیت به آن تعلق دارد.