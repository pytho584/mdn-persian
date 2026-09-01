---
title: "HTMLAreaElement: username property"
short-title: username
slug: Web/API/HTMLAreaElement/username
page-type: web-api-instance-property
browser-compat: api.HTMLAreaElement.username
---

{{ApiRef("HTML DOM")}}

خاصیت **`username`** در رابط {{domxref("HTMLAreaElement")}} یک رشته است که جزء نام کاربری (username) از `href` عنصر `<area>` را شامل می‌شود. اگر URL فاقد نام کاربری باشد، این خاصیت حاوی یک رشته خالی (`""`) خواهد بود.

این خاصیت قابل تنظیم است تا نام کاربری URL تغییر کند. اگر URL دارای {{domxref("HTMLAreaElement.host", "host")}} نباشد یا طرح آن `file:` باشد، تنظیم این خاصیت هیچ تأثیری ندارد.

نام کاربری هنگام تنظیم، {{Glossary("Percent-encoding", "درصد-کدگذاری")}} می‌شود، اما هنگام خواندن، درصد-کدگشایی نمی‌شود.

برای اطلاعات بیشتر به {{domxref("URL.username")}} مراجعه کنید.

## مقدار

یک رشته.

## مثال‌ها

### دریافت نام کاربری از یک پیوند area

```js
// An <area id="myArea" href="https://anonymous:flabada@developer.mozilla.org/en-US/docs/HTMLAreaElement"> element is in the document
const area = document.getElementByID("myArea");
area.username; // returns 'anonymous'
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("HTMLAreaElement")}} که این خاصیت به آن تعلق دارد.