---
title: "HTMLModElement: dateTime property"
short-title: dateTime
slug: Web/API/HTMLModElement/dateTime
page-type: web-api-instance-property
browser-compat: api.HTMLModElement.dateTime
---

{{ APIRef("HTML DOM") }}

خاصیت **`dateTime`** از رابط {{domxref("HTMLModElement")}} یک رشته است که شامل یک تاریخ قابل خواندن توسط ماشین به همراه یک مقدار زمانی اختیاری می‌باشد. این خاصیت منعکس‌کنندهٔ ویژگی HTML [`datetime`](/en-US/docs/Web/HTML/Reference/Elements/time#datetime) عناصر {{HTMLElement("del")}} و {{HTMLElement("ins")}} است.

## مقدار

یک رشته. برای مشاهدهٔ قالب‌های معتبر رشته، به [مقادیر معتبر `datetime`](/en-US/docs/Web/HTML/Reference/Elements/time#valid_datetime_values) مراجعه کنید.

## مثال‌ها

با توجه به HTML زیر:

```html
<p>The paragraph <del datetime="2021-11-01">has been</del> changed</p>
```

می‌توانیم مقدار ویژگی `dateTime` عنصر `<del>` را دریافت کنیم:

```js
const deletedText = document.querySelector("del");
console.log(deletedText.dateTime); // "2021-11-01"
```

همچنین می‌توانیم خاصیت `dateTime` را تنظیم کنیم. در اینجا، یک عنصر `<ins>` ایجاد می‌کنیم، سپس خاصیت `dateTime` عنصر `<ins>` را به تاریخ جاری در قالب `YYYY-MM-DD` تنظیم کرده و آن را بعد از متن حذف‌شده درج می‌کنیم:

```js
const insertedText = document.createElement("ins");
const now = new Date();
insertedText.dateTime = `${now.getFullYear()}-${now.getMonth() + 1}-${now.getDate()}`;
insertedText.appendChild(document.createTextNode("was"));
deletedText.insertAdjacentElement("afterend", insertedText);
```

اگر اسکریپت ما در ۹ ژانویهٔ ۲۰۲۵ اجرا شود، HTML ما به صورت زیر خواهد بود:

```html
<p>
  The paragraph <del datetime="2021-11-01">has been</del
  ><ins datetime="2025-1-9">was</ins> changed
</p>
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("del")}}
- {{HTMLElement("ins")}}
- {{domxref("HTMLModElement")}}
- {{domxref("HTMLModElement.cite")}}
- {{domxref("HTMLTimeElement.dateTime")}}
- [رشته‌های تاریخ](/en-US/docs/Web/HTML/Guides/Date_and_time_formats#date_strings)
- [رشته‌های تاریخ و زمان محلی](/en-US/docs/Web/HTML/Guides/Date_and_time_formats#local_date_and_time_strings)
- {{jsxref("Date")}}
- {{domxref("Element.insertAdjacentElement()")}}