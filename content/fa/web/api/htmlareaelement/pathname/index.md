---
title: "HTMLAreaElement: pathname property"
short-title: pathname
slug: Web/API/HTMLAreaElement/pathname
page-type: web-api-instance-property
browser-compat: api.HTMLAreaElement.pathname
---

{{ApiRef("HTML DOM")}}

ویژگی **`HTMLAreaElement.pathname`** یک رشته است که شامل یک `'/'` ابتدایی و به دنبال آن مسیر URL است، بدون رشتهٔ جستجو (query string) یا قطعه (fragment). اگر مسیری وجود نداشته باشد، این رشته خالی است.

هنگام تنظیم، pathname به‌صورت {{Glossary("Percent-encoding", "percent-encoded")}} (درصد-رمزگذاری‌شده) درمی‌آید؛ اما هنگام خواندن، درصد-رمزگشایی نمی‌شود.

## مقدار

یک رشته.

## مثال‌ها

```js
// An <area id="myArea" href="/en-US/docs/HTMLAreaElement"> element is in the document
const area = document.getElementById("myArea");
area.pathname; // returns '/en-US/docs/HTMLAreaElement'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("HTMLAreaElement")}} که این ویژگی به آن تعلق دارد.