---
title: "HTMLAnchorElement: username property"
short-title: username
slug: Web/API/HTMLAnchorElement/username
page-type: web-api-instance-property
browser-compat: api.HTMLAnchorElement.username
---

{{ApiRef("HTML DOM")}}

ویژگی **`username`** در رابط {{domxref("HTMLAnchorElement")}} یک رشته است که جزء نام کاربری (username) از `href` عنصر `<a>` را شامل می‌شود. اگر URL نام کاربری نداشته باشد، این ویژگی شامل یک رشته خالی، `""` است.

این ویژگی را می‌توان برای تغییر نام کاربری URL تنظیم کرد. اگر URL فاقد {{domxref("HTMLAnchorElement.host", "host")}} باشد یا طرح آن `file:` باشد، تنظیم این ویژگی هیچ اثری ندارد.

نام کاربری هنگام تنظیم، {{Glossary("Percent-encoding", "درصد-کدگذاری")}} می‌شود اما هنگام خواندن، درصد-کدگشایی نمی‌شود.

برای اطلاعات بیشتر به {{domxref("URL.username")}} مراجعه کنید.

## مقدار

یک رشته.

## مثال‌ها

### دریافت نام کاربری از یک پیوند anchor

```js
// یک عنصر <a id="myAnchor" href="https://anonymous:flabada@developer.mozilla.org/en-US/docs/HTMLAnchorElement"> در سند وجود دارد
const anchor = document.getElementByID("myAnchor");
anchor.username; // 'anonymous' را برمی‌گرداند
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("HTMLAnchorElement")}} که این ویژگی به آن تعلق دارد.