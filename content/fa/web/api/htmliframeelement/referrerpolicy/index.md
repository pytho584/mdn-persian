---
title: "HTMLIFrameElement: referrerPolicy property"
short-title: referrerPolicy
slug: Web/API/HTMLIFrameElement/referrerPolicy
page-type: web-api-instance-property
browser-compat: api.HTMLIFrameElement.referrerPolicy
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLIFrameElement.referrerPolicy`** منعکس‌کنندهٔ ویژگی HTML [`referrerpolicy`](/en-US/docs/Web/HTML/Reference/Elements/iframe#referrerpolicy) عنصر {{HTMLElement("iframe")}} است که مشخص می‌کند هنگام واکشی منبع، کدام ارجاع‌دهنده (referrer) ارسال شود.

## مقدار

- `no-referrer`
  - : هدر {{HTTPHeader("Referer")}} به‌طور کامل حذف خواهد شد. هیچ اطلاعات ارجاع‌دهنده‌ای همراه با درخواست‌ها ارسال نمی‌شود.
- `no-referrer-when-downgrade`
  - : URL به‌عنوان ارجاع‌دهنده زمانی ارسال می‌شود که سطح امنیت پروتکل یکسان بماند (HTTP→HTTP، HTTPS→HTTPS)، اما به مقصدی با امنیت کمتر (HTTPS→HTTP) ارسال نمی‌شود.
- `origin`
  - : در همه موارد فقط مبدأ (origin) سند را به‌عنوان ارجاع‌دهنده ارسال کن. سند `https://example.com/page.html` ارجاع‌دهنده `https://example.com/` را ارسال خواهد کرد.
- `origin-when-cross-origin`
  - : هنگام انجام درخواست هم‌مبدأ (same-origin) یک URL کامل ارسال شود، اما در موارد دیگر فقط مبدأ سند ارسال شود.
- `same-origin`
  - : برای مبدأهای هم‌سایت (same-site) یک ارجاع‌دهنده ارسال خواهد شد، اما درخواست‌های بین‌مبدأ (cross-origin) هیچ اطلاعات ارجاع‌دهنده‌ای نخواهند داشت.
- `strict-origin`
  - : فقط مبدأ سند را به‌عنوان ارجاع‌دهنده زمانی ارسال کن که سطح امنیت پروتکل یکسان بماند (HTTPS→HTTPS)، اما به مقصدی با امنیت کمتر (HTTPS→HTTP) ارسال نکن.
- `strict-origin-when-cross-origin` (پیش‌فرض)
  - : این رفتار پیش‌فرض عامل کاربر (user agent) است اگر هیچ خط‌مشی‌ای مشخص نشده باشد. هنگام انجام درخواست هم‌مبدأ یک URL کامل ارسال شود، فقط زمانی مبدأ ارسال شود که سطح امنیت پروتکل یکسان بماند (HTTPS→HTTPS)، و هیچ هدری به مقصد با امنیت کمتر (HTTPS→HTTP) ارسال نشود.
- `unsafe-url`
  - : هنگام انجام درخواست هم‌مبدأ یا بین‌مبدأ یک URL کامل ارسال شود.

    > [!NOTE]
    > این خط‌مشی باعث نشت مبدأها و مسیرها از منابع محافظت‌شده با TLS به مبدأهای ناامن می‌شود. تأثیر این تنظیم را با دقت در نظر بگیرید.

## مثال‌ها

```js
const iframe = document.createElement("iframe");
iframe.src = "/";
iframe.referrerPolicy = "unsafe-url";
const body = document.querySelector("body");
body.appendChild(iframe); // Fetch the image using the complete URL as the referrer
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLAnchorElement.referrerPolicy")}}،
  {{domxref("HTMLAreaElement.referrerPolicy")}}، و
  {{domxref("HTMLAreaElement.referrerPolicy")}}.