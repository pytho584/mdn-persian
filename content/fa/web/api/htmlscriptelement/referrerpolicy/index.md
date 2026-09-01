---
title: "HTMLScriptElement: referrerPolicy property"
short-title: referrerPolicy
slug: Web/API/HTMLScriptElement/referrerPolicy
page-type: web-api-instance-property
browser-compat: api.HTMLScriptElement.referrerPolicy
---

{{APIRef("HTML DOM")}}

ویژگی **`referrerPolicy`** در رابط {{domxref("HTMLScriptElement")}} بازتاب‌دهندهٔ [`referrerpolicy`](/en-US/docs/Web/HTML/Reference/Elements/script#referrerpolicy) عنصر {{HTMLElement("script")}} است که مشخص می‌کند هنگام واکشی اسکریپت و هر اسکریپتی که وارد می‌کند، مرجع (referrer) چگونه تنظیم شود.

## مقدار

یک رشته؛ یکی از موارد زیر:

- `no-referrer`
  - : هدر {{HTTPHeader("Referer")}} به‌طور کامل حذف می‌شود. هیچ اطلاعات مرجعی همراه با درخواست‌ها ارسال نمی‌شود.
- `no-referrer-when-downgrade`
  - : وقتی سطح امنیتی پروتکل یکسان می‌ماند (مثلاً HTTP→HTTP، HTTPS→HTTPS)، URL به‌عنوان مرجع ارسال می‌شود، اما به مقصدی با امنیت پایین‌تر (مثلاً HTTPS→HTTP) ارسال نمی‌شود.
- `origin`
  - : فقط مبدأ (origin) سند را در همه موارد به‌عنوان مرجع ارسال کن. سند `https://example.com/page.html` مرجع `https://example.com/` را ارسال خواهد کرد.
- `origin-when-cross-origin`
  - : برای درخواست‌های هم‌مبدأ، URL کامل ارسال می‌شود، اما برای سایر موارد فقط مبدأ سند ارسال می‌شود.
- `same-origin`
  - : برای [مبدأهای هم‌سایت](/en-US/docs/Web/Security/Defenses/Same-origin_policy) یک مرجع ارسال می‌شود، اما درخواست‌های متقاطع (cross-origin) هیچ اطلاعات مرجعی ندارند.
- `strict-origin`
  - : فقط وقتی سطح امنیتی پروتکل یکسان می‌ماند (مثلاً HTTPS→HTTPS)، مبدأ سند به‌عنوان مرجع ارسال می‌شود، اما به مقصد کم‌امنیت‌تر (مثلاً HTTPS→HTTP) ارسال نمی‌شود.
- `strict-origin-when-cross-origin` (پیش‌فرض)
  - : این رفتار پیش‌فرض عامل کاربر (user agent) است، اگر خط‌مشی‌ای مشخص نشده باشد. هنگام انجام درخواست هم‌مبدأ، URL کامل ارسال می‌شود؛ وقتی سطح امنیتی پروتکل یکسان است (مثلاً HTTPS→HTTPS) فقط مبدأ ارسال می‌شود؛ و به مقصد کم‌امنیت‌تر (مثلاً HTTPS→HTTP) هیچ هدری ارسال نمی‌شود.
- `unsafe-url`
  - : هنگام انجام درخواست هم‌مبدأ یا متقاطع، URL کامل ارسال می‌شود. این خط‌مشی مبدأها و مسیرهای منابع محافظت‌شده با TLS را به مبدأهای ناامن درز می‌دهد. تأثیر این تنظیم را به‌دقت در نظر بگیرید.

> [!NOTE]
> مقدار رشتهٔ خالی (`""`) هم مقدار پیش‌فرض است و هم مقدار جایگزین (fallback) در صورتی که `referrerpolicy` پشتیبانی نشود. اگر `referrerpolicy` به‌طور صریح روی عنصر `<script>` مشخص نشده باشد، یک خط‌مشی مرجع سطح‌بالاتر را به کار می‌گیرد؛ یعنی خط‌مشی‌ای که روی کل سند یا دامنه تنظیم شده است. اگر خط‌مشی سطح‌بالاتری در دسترس نباشد، رشتهٔ خالی معادل `no-referrer-when-downgrade` در نظر گرفته می‌شود.

## مثال‌ها

```js
const scriptElem = document.createElement("script");
scriptElem.src = "/";
scriptElem.referrerPolicy = "unsafe-url";
document.body.appendChild(scriptElem);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLIFrameElement.referrerPolicy")}}