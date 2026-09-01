---
title: "HTMLDetailsElement: name property"
short-title: name
slug: Web/API/HTMLDetailsElement/name
page-type: web-api-instance-property
browser-compat: api.HTMLDetailsElement.name
---

{{ APIRef("HTML DOM") }}

خاصیت **`name`** از رابط {{domxref("HTMLDetailsElement")}} منعکس‌کنندهٔ ویژگی [`name`](/en-US/docs/Web/HTML/Reference/Elements/details#name) عناصر {{htmlelement("details")}} است. این امکان را فراهم می‌کند که چندین عنصر `<details>` به هم متصل شوند، به‌طوری‌که فقط یکی از عناصر `<details>` می‌تواند در یک زمان باز باشد. این به توسعه‌دهندگان اجازه می‌دهد تا به‌راحتی ویژگی‌های رابط کاربری مانند آکاردئون‌ها را بدون نیاز به اسکریپت‌نویسی ایجاد کنند.

ویژگی `name` یک نام گروه را مشخص می‌کند — به چندین عنصر `<details>` مقدار `name` یکسان بدهید تا آن‌ها را گروه‌بندی کنید. فقط یکی از عناصر `<details>` گروه‌بندی‌شده می‌تواند در یک زمان باز باشد — باز کردن یکی باعث بسته شدن دیگری می‌شود. اگر به چندین عنصر `<details>` گروه‌بندی‌شده ویژگی `open` داده شود، تنها اولین عنصر در ترتیب منبع به‌صورت باز نمایش داده می‌شود.

## مقدار

یک رشته. اگر عنصر جزئی از هیچ گروهی نباشد، رشتهٔ خالی.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- عناصر {{htmlelement("details")}} و {{htmlelement("summary")}}