---
title: "HTMLAnchorElement: password property"
short-title: password
slug: Web/API/HTMLAnchorElement/password
page-type: web-api-instance-property
browser-compat: api.HTMLAnchorElement.password
---

{{ApiRef("HTML DOM")}}

ویژگی **`password`** در رابط {{domxref("HTMLAnchorElement")}} یک رشته است که بخش «رمز عبور» از `href` عنصر `<a>` را شامل می‌شود. اگر URL رمز عبور نداشته باشد، این ویژگی شامل یک رشته خالی، `""` خواهد بود.

این ویژگی قابل تنظیم است تا رمز عبور URL تغییر کند. اگر URL دارای {{domxref("HTMLAnchorElement.host", "host")}} نباشد یا پروتکل آن `file:` باشد، تنظیم این ویژگی هیچ تأثیری ندارد.

رمز عبور هنگام تنظیم، {{Glossary("Percent-encoding", "درصد-نشانه‌گذاری")}} می‌شود، اما هنگام خواندن، درصد-رمزگشایی نمی‌شود.

برای اطلاعات بیشتر به {{domxref("URL.password")}} مراجعه کنید.

## مقدار

یک رشته.

## مثال‌ها

```js
// An <a id="myAnchor" href="https://anonymous:flabada@developer.mozilla.org/en-US/docs/HTMLAnchorElement"> is in the document
const anchor = document.getElementByID("myAnchor");
anchor.password; // returns 'flabada'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("HTMLAnchorElement")}} که این ویژگی به آن تعلق دارد.
```