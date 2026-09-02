---
title: "Location: search property"
short-title: search
slug: Web/API/Location/search
page-type: web-api-instance-property
browser-compat: api.Location.search
---

{{ApiRef("Location")}}

ویژگی **`search`** در رابط {{domxref("Location")}} یک رشتهٔ جست‌وجو است که «رشتهٔ کوئری» (query string) نیز نامیده می‌شود. این ویژگی رشته‌ای است شامل `"?"` و به‌دنبال آن پارامترهای URLِ همان مکان. اگر URL دارای کوئری جست‌وجو نباشد، مقدار این ویژگی یک رشتهٔ خالی (`""`) خواهد بود.

این ویژگی قابل تنظیم است تا رشتهٔ کوئریِ URL تغییر کند. هنگام تنظیم، یک پیشوند `"?"` به مقدار داده‌شده اضافه می‌شود، مگر اینکه از قبل وجود داشته باشد. تنظیم آن روی `""` رشتهٔ کوئری را حذف می‌کند.

زمانی که این ویژگی تنظیم می‌شود، کوئری به‌صورت {{Glossary("Percent-encoding", "percent-encoded")}} درمی‌آید؛ اما هنگام خواندن، درصد-کدگشایی نمی‌شود.

مرورگرهای مدرن، [`URLSearchParams`](/en-US/docs/Web/API/URLSearchParams/get#examples) و [`URL.searchParams`](/en-US/docs/Web/API/URL/searchParams#examples) را فراهم می‌کنند تا تجزیه‌کردن پارامترها از رشتهٔ کوئری آسان شود.

برای اطلاعات بیشتر، {{domxref("URL.search")}} را ببینید.

## Value

یک رشته.

## Examples

```js
// Let an <a id="myAnchor" href="/en-US/docs/Location.search?q=123"> element be in the document
const anchor = document.getElementById("myAnchor");
const queryString = anchor.search; // Returns:'?q=123'

// Further parsing:
const params = new URLSearchParams(queryString);
const q = parseInt(params.get("q"), 10); // is the number 123
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}