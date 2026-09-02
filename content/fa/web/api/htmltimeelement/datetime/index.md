---
title: "HTMLTimeElement: dateTime property"
short-title: dateTime
slug: Web/API/HTMLTimeElement/dateTime
page-type: web-api-instance-property
browser-compat: api.HTMLTimeElement.dateTime
---

{{ APIRef("HTML DOM") }}

ویژگی **`dateTime`** در رابط {{domxref("HTMLTimeElement")}} یک رشته است که ویژگی HTML [`datetime`](/en-US/docs/Web/HTML/Reference/Elements/time#datetime) را منعکس می‌کند و حاوی شکلی قابل‌خواندن توسط ماشین از مقدار تاریخ و زمان عنصر است.

## مقدار

یک رشته. برای قالب‌های معتبر رشته، به [مقادیر معتبر `datetime`](/en-US/docs/Web/HTML/Reference/Elements/time#valid_datetime_values) مراجعه کنید.

## مثال‌ها

```js
// Assumes there is <time id="t"> element in the HTML

const t = document.getElementById("t");
t.dateTime = "6w 5h 34m 5s";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLTimeElement")}}
- {{domxref("HTMLModElement.dateTime")}}
- [رشته‌های تاریخ](/en-US/docs/Web/HTML/Guides/Date_and_time_formats#date_strings)
- [رشته‌های تاریخ و زمان محلی](/en-US/docs/Web/HTML/Guides/Date_and_time_formats#local_date_and_time_strings)