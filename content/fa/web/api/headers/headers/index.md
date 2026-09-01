---
title: "Headers: Headers() constructor"
short-title: Headers()
slug: Web/API/Headers/Headers
page-type: web-api-constructor
browser-compat: api.Headers.Headers
---

{{APIRef("Fetch API")}} {{AvailableInWorkers}}

سازندهٔ **`Headers()`** یک شیء جدید {{domxref("Headers")}} ایجاد می‌کند.

## Syntax

```js-nolint
new Headers()
new Headers(init)
```

### Parameters

- `init` {{optional_inline}}
  - : یک شیء شامل هر [سرآیند HTTP](/en-US/docs/Web/HTTP/Reference/Headers) که می‌خواهید شیء `Headers` خود را با آن از پیش پر کنید. این می‌تواند یک شیء ساده با مقادیر {{jsxref("String")}}، یک آرایه از جفت‌های نام-مقدار که هر جفت یک آرایهٔ دو عضوی از رشته‌ها است، یا یک شیء `Headers` موجود باشد. در حالت آخر، شیء جدید `Headers` داده‌های خود را از شیء `Headers` موجود کپی می‌کند.

## Examples

ایجاد یک شیء خالی `Headers` ساده است:

```js
const myHeaders = new Headers(); // Currently empty
```

می‌توانید با استفاده از {{domxref("Headers.append")}} یک سرآیند به آن اضافه کنید:

```js
myHeaders.append("Content-Type", "image/jpeg");
myHeaders.get("Content-Type"); // Returns 'image/jpeg'
```

یا می‌توانید سرآیندهای مورد نظر خود را در هنگام ایجاد شیء `Headers` اضافه کنید. در قطعه کد زیر، یک شیء جدید {{domxref("Headers")}} ایجاد می‌کنیم و با ارسال یک شیء init به سازنده، چند سرآیند اضافه می‌کنیم:

```js
const httpHeaders = {
  "Content-Type": "image/jpeg",
  "X-My-Custom-Header": "Zeke are cool",
};
const myHeaders = new Headers(httpHeaders);
```

اکنون می‌توانید یک شیء `Headers` دیگر ایجاد کنید و اولین شیء `Headers` را به عنوان شیء init آن ارسال کنید:

```js
const secondHeadersObj = new Headers(myHeaders);
secondHeadersObj.get("Content-Type"); // Would return 'image/jpeg' — it inherits it from the first headers object
```

همچنین می‌توانید سرآیندهای مورد نظر خود را در هنگام ایجاد شیء `Headers` با استفاده از یک آرایه دو بعدی برای اضافه کردن چندین سرآیند با مقادیر یکسان اضافه کنید. در قطعه کد زیر، یک شیء جدید {{domxref("Headers")}} با چندین سرآیند `Set-Cookie` با ارسال یک آرایه init به سازنده ایجاد می‌کنیم:

```js
const headers = [
  ["Set-Cookie", "greeting=hello"],
  ["Set-Cookie", "name=world"],
];
const myHeaders = new Headers(headers);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [ServiceWorker API](/en-US/docs/Web/API/Service_Worker_API)
- [HTTP access control (CORS)](/en-US/docs/Web/HTTP/Guides/CORS)
- [HTTP](/en-US/docs/Web/HTTP)