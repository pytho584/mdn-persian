---
title: "HTMLAnchorElement: referrerPolicy property"
short-title: referrerPolicy
slug: Web/API/HTMLAnchorElement/referrerPolicy
page-type: web-api-instance-property
browser-compat: api. HTMLAnchorElement.referrerPolicy
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLAnchorElement.referrerPolicy`** منعکس‌کنندهٔ ویژگی HTML [`referrerpolicy`](/en-US/docs/Web/HTML/Reference/Elements/a#referrerpolicy) از عنصر {{HTMLElement("a")}} است که مشخص می‌کند هنگام واکشی منبع، کدام ارجاع‌دهنده (referrer) ارسال شود.

## مقدار

یک رشته (string) که یکی از مقادیر زیر را دارد:

- `no-referrer`
  - : هدر {{HTTPHeader("Referer")}} به‌طور کامل حذف می‌شود. هیچ اطلاعات ارجاع‌دهنده‌ای همراه با درخواست‌ها ارسال نمی‌گردد.
- `no-referrer-when-downgrade`
  - : زمانی که سطح امنیت پروتکل یکسان باقی بماند (مثلاً HTTP→HTTP یا HTTPS→HTTPS)، URL به‌عنوان ارجاع‌دهنده ارسال می‌شود، اما به مقصدی با امنیت پایین‌تر (مثلاً HTTPS→HTTP) ارسال نمی‌گردد.
- `origin`
  - : در همه موارد فقط خاستگاه (origin) سند به‌عنوان ارجاع‌دهنده ارسال می‌شود. برای مثال، سند `https://example.com/page.html` ارجاع‌دهنده `https://example.com/` را ارسال خواهد کرد.
- `origin-when-cross-origin`
  - : هنگام انجام درخواست‌های هم‌خاستگاه (same-origin)، URL کامل ارسال می‌شود، اما در سایر موارد فقط خاستگاه سند ارسال می‌گردد.
- `same-origin`
  - : برای خاستگاه‌های هم‌سایت (same-site) ارجاع‌دهنده ارسال می‌شود، اما درخواست‌های بین‌خاستگاهی (cross-origin) هیچ اطلاعات ارجاع‌دهنده‌ای شامل نمی‌شوند.
- `strict-origin`
  - : فقط زمانی که سطح امنیت پروتکل یکسان باقی بماند (مثلاً HTTPS→HTTPS) خاستگاه سند به‌عنوان ارجاع‌دهنده ارسال می‌گردد، اما به مقصدی با امنیت پایین‌تر (مثلاً HTTPS→HTTP) ارسال نمی‌شود.
- `strict-origin-when-cross-origin` (پیش‌فرض)
  - : این رفتار پیش‌فرض عامل کاربر (user agent) است زمانی که هیچ سیاستی مشخص نشده باشد. هنگام درخواست هم‌خاستگاه URL کامل ارسال می‌شود، فقط زمانی که سطح امنیت پروتکل یکسان است (مثلاً HTTPS→HTTPS) خاستگاه ارسال می‌گردد، و به مقصدی با امنیت پایین‌تر (مثلاً HTTPS→HTTP) هیچ هدری ارسال نمی‌شود.
- `unsafe-url`
  - : هنگام درخواست هم‌خاستگاه یا بین‌خاستگاهی URL کامل ارسال می‌شود. این سیاست باعث نشت خاستگاه‌ها و مسیرها از منابع محافظت‌شده با TLS به خاستگاه‌های ناامن می‌شود. تأثیر این تنظیم را با دقت در نظر بگیرید.

## نمونه‌ها

```js
const elt = document.createElement("a");
const linkText = document.createTextNode("My link");
elt.appendChild(linkText);
elt.href = "https://developer.mozilla.org/en-US/";
elt.referrerPolicy = "no-referrer";

const div = document.getElementById("divAround");
div.appendChild(elt); // When clicked, the link will not send a referrer header.
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLImageElement.referrerPolicy")}}،
  {{domxref("HTMLAreaElement.referrerPolicy")}} و
  {{domxref("HTMLIFrameElement.referrerPolicy")}}.