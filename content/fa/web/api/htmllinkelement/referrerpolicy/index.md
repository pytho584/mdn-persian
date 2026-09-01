---
title: "HTMLLinkElement: referrerPolicy property"
short-title: referrerPolicy
slug: Web/API/HTMLLinkElement/referrerPolicy
page-type: web-api-instance-property
browser-compat: api.HTMLLinkElement.referrerPolicy
---

{{APIRef("HTML DOM")}}

ویژگی **`referrerPolicy`** از رابط {{domxref("HTMLLinkElement")}} منعکس‌کنندهٔ ویژگی HTML [`referrerpolicy`](/en-US/docs/Web/HTML/Reference/Elements/link#referrerpolicy) در عنصر {{HTMLElement("link")}} است که تعیین می‌کند هنگام دریافت منبع، چه ارجاع‌دهنده‌ای (referrer) ارسال شود.

برای جزئیات بیشتر، هدر HTTP {{HTTPHeader("Referrer-Policy")}} را ببینید.

## مقدار

یک رشته؛ یکی از موارد زیر:

- `no-referrer`
  - : هدر {{HTTPHeader("Referer")}} به‌کلی حذف خواهد شد. هیچ اطلاعات ارجاع‌دهنده‌ای همراه با درخواست‌ها ارسال نمی‌شود.
- `no-referrer-when-downgrade`
  - : نشانی وب به‌عنوان ارجاع‌دهنده زمانی ارسال می‌شود که سطح امنیت پروتکل ثابت بماند (مثلاً HTTP→HTTP، HTTPS→HTTPS)، اما به یک مقصد با امنیت پایین‌تر (مثلاً HTTPS→HTTP) ارسال نمی‌شود.
- `origin`
  - : در همه موارد فقط مبدأ (origin) سند را به‌عنوان ارجاع‌دهنده ارسال کنید. سند `https://example.com/page.html` ارجاع‌دهندهٔ `https://example.com/` را ارسال خواهد کرد.
- `origin-when-cross-origin`
  - : هنگام انجام یک درخواست هم‌مبدأ (same-origin)، نشانی کامل را ارسال کنید، اما برای سایر موارد فقط مبدأ سند را ارسال کنید.
- `same-origin`
  - : یک ارجاع‌دهنده برای [مبدأهای هم‌سایت](/en-US/docs/Web/Security/Defenses/Same-origin_policy) ارسال خواهد شد، اما درخواست‌های بین‌مبدأ (cross-origin) هیچ اطلاعات ارجاع‌دهنده‌ای نخواهند داشت.
- `strict-origin`
  - : فقط مبدأ سند را به‌عنوان ارجاع‌دهنده زمانی ارسال کنید که سطح امنیت پروتکل ثابت بماند (مثلاً HTTPS→HTTPS)، اما آن را به یک مقصد با امنیت پایین‌تر (مثلاً HTTPS→HTTP) ارسال نکنید.
- `strict-origin-when-cross-origin` (پیش‌فرض)
  - : این رفتار پیش‌فرض عامل کاربر (user agent) در صورت عدم تعیین خط‌مشی است. هنگام انجام یک درخواست هم‌مبدأ، نشانی کامل را ارسال کنید، فقط زمانی مبدأ را ارسال کنید که سطح امنیت پروتکل ثابت بماند (مثلاً HTTPS→HTTPS)، و هیچ هدری به یک مقصد با امنیت پایین‌تر (مثلاً HTTPS→HTTP) ارسال نکنید.
- `unsafe-url`
  - : هنگام انجام یک درخواست هم‌مبدأ یا بین‌مبدأ، نشانی کامل را ارسال کنید. این خط‌مشی باعث نشت مبدأها و مسیرها از منابع محافظت‌شده با TLS به مبدأهای ناامن می‌شود. تأثیر این تنظیم را به دقت در نظر بگیرید.

## مثال‌ها

```js
const links = document.getElementsByTagName("link");
links[0].referrerPolicy; // "no-referrer"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- هدر HTTP {{HTTPHeader("Referrer-Policy")}}
- {{domxref("HTMLAnchorElement.referrerPolicy")}}
- {{domxref("HTMLAreaElement.referrerPolicy")}}
- {{domxref("HTMLIFrameElement.referrerPolicy")}}
- {{domxref("HTMLImageElement.referrerPolicy")}}