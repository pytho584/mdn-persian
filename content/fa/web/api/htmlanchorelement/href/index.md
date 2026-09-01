---
title: "HTMLAnchorElement: href property"
short-title: href
slug: Web/API/HTMLAnchorElement/href
page-type: web-api-instance-property
browser-compat: api.HTMLAnchorElement.href
---

{{ApiRef("HTML DOM")}}

ویژگی **`href`** در رابط {{domxref("HTMLAnchorElement")}} یک {{Glossary("stringifier")}} است که URL مطلق متناظر با ویژگی `href` عنصر را برمیگرداند (یا اگر `href` تنظیم نشده باشد، یک رشتهٔ خالی). تنظیم این ویژگی، ویژگی `href` عنصر را به مقدار داده‌شده به‌روزرسانی می‌کند.

## مقدار

یک رشته.

- اگر ویژگی `href` وجود نداشته باشد، مقدار یک رشتهٔ خالی (`""`) است.
- اگر ویژگی `href` وجود داشته باشد اما URL نسبی یا مطلق معتبری نباشد، مقدار، همان مقدار ویژگی است.
- اگر ویژگی `href` وجود داشته باشد و یک URL نسبی یا مطلق معتبر باشد، مقدار، URL مطلق است که نسبت به URL پایهٔ سند (base URL) تفکیک می‌شود. رشتهٔ خالی (`""`) یک URL نسبی معتبر در نظر گرفته می‌شود و به URL پایهٔ سند تفکیک می‌شود.

## مثال‌ها

یک عنصر `<a>` که تازه ایجاد شده، ویژگی `href` ندارد، بنابراین ویژگی `href` آن یک رشتهٔ خالی برمی‌گرداند.

```js
const anchor = document.createElement("a");
console.log(anchor.href); // ""
```

اگر ویژگی روی یک رشتهٔ خالی تنظیم شود، ویژگی مذکور URL پایهٔ سند را برمی‌گرداند، زیرا رشتهٔ خالی یک URL نسبی معتبر است.

```js
anchor.href = "";
console.log(anchor.href); // "https://developer.mozilla.org/en-US/docs/Web/API/HTMLAnchorElement/href"
```

اگر ویژگی روی یک URL نسبی تنظیم شود، ویژگی مذکور URL مطلق تفکیک‌شده نسبت به URL پایهٔ سند را برمی‌گرداند.

```js
anchor.href = "../../..";
console.log(anchor.href); // "https://developer.mozilla.org/en-US/docs/"
```

توجه داشته باشید که مقدار ویژگی بدون تفکیک، همان‌طور که تنظیم شده باقی می‌ماند.

```js
console.log(anchor.getAttribute("href")); // "../../.."
```

اگر ویژگی روی یک URL مطلق تنظیم شود، ویژگی مذکور همان URL مطلق را بدون تغییر برمی‌گرداند.

```js
anchor.href = "https://example.com/path";
console.log(anchor.href); // "https://example.com/path"
```

اگر ویژگی روی یک URL نامعتبر تنظیم شود، ویژگی مذکور مقدار ویژگی را بدون تغییر برمی‌گرداند.

```js
anchor.href = "https://";
console.log(anchor.href); // "https://"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("HTMLAnchorElement")}} که این ویژگی به آن تعلق دارد.