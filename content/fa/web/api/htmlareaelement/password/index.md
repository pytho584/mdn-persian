---
title: "HTMLAreaElement: password property"
short-title: password
slug: Web/API/HTMLAreaElement/password
page-type: web-api-instance-property
browser-compat: api.HTMLAreaElement.password
---

{{ApiRef("HTML DOM")}}

خاصیت **`password`** از رابط {{domxref("HTMLAreaElement")}} یک رشته است که مؤلفه‌ی رمز عبور (password) از `href` عنصر `<area>` را شامل می‌شود. اگر URL رمز عبور نداشته باشد، این خاصیت یک رشته‌ی خالی `""` را برمی‌گرداند.

این خاصیت قابل تنظیم است تا رمز عبور URL تغییر کند. اگر URL فاقد {{domxref("HTMLAreaElement.host", "host")}} باشد یا طرح آن `file:` باشد، تنظیم این خاصیت تأثیری ندارد.

رمز عبور هنگام تنظیم {{Glossary("Percent-encoding", "درصد-کدگذاری")}} می‌شود، اما هنگام خواندن درصد-کدگشایی نمی‌شود.

برای اطلاعات بیشتر به {{domxref("URL.password")}} مراجعه کنید.

## مقدار

یک رشته.

## مثال‌ها

```js
// یک <area id="myArea" href="https://anonymous:flabada@developer.mozilla.org/en-US/docs/HTMLAreaElement"> در سند وجود دارد
const area = document.getElementByID("myArea");
area.password; // 'flabada' را برمی‌گرداند
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("HTMLAreaElement")}} که این خاصیت به آن تعلق دارد.