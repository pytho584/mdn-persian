---
title: "HTMLAreaElement: referrerPolicy property"
short-title: referrerPolicy
slug: Web/API/HTMLAreaElement/referrerPolicy
page-type: web-api-instance-property
browser-compat: api.HTMLAreaElement.referrerPolicy
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLAreaElement.referrerPolicy`**  
ویژگی HTML [`referrerpolicy`](/en-US/docs/Web/HTML/Reference/Elements/area#referrerpolicy) عنصر {{HTMLElement("area")}} را منعکس می‌کند که مشخص می‌کند هنگام درخواست منبع، کدام ارجاع‌دهنده (referrer) ارسال شود.

## مقدار

یک رشته؛ یکی از مقادیر زیر:

- `no-referrer`
  - : هدر {{HTTPHeader("Referer")}} به‌کلی حذف می‌شود. هیچ اطلاعات ارجاع‌دهنده‌ای همراه با درخواست‌ها ارسال نمی‌گردد.
- `no-referrer-when-downgrade`
  - : هنگامی که سطح امنیت پروتکل یکسان بماند (مثلاً HTTP→HTTP، HTTPS→HTTPS)، URL به‌عنوان ارجاع‌دهنده ارسال می‌شود، اما به مقصدی با امنیت کمتر (مثلاً HTTPS→HTTP) ارسال نمی‌شود.
- `origin`
  - : در همه موارد فقط خاستگاه (origin) سند را به‌عنوان ارجاع‌دهنده ارسال می‌کند. سند `https://example.com/page.html` ارجاع‌دهنده `https://example.com/` را ارسال خواهد کرد.
- `origin-when-cross-origin`
  - : هنگام انجام یک درخواست هم‌خاستگاه (same-origin) URL کامل را ارسال می‌کند، اما در سایر موارد فقط خاستگاه سند را ارسال می‌کند.
- `same-origin`
  - : یک ارجاع‌دهنده برای [خاستگاه‌های هم‌سایت](/en-US/docs/Web/Security/Defenses/Same-origin_policy) ارسال می‌شود، اما درخواست‌های بین‌خاستگاهی (cross-origin) هیچ اطلاعات ارجاع‌دهنده‌ای ندارند.
- `strict-origin`
  - : فقط هنگامی که سطح امنیت پروتکل یکسان بماند (مثلاً HTTPS→HTTPS) خاستگاه سند را به‌عنوان ارجاع‌دهنده ارسال می‌کند، اما آن را به مقصدی با امنیت کمتر (مثلاً HTTPS→HTTP) ارسال نمی‌کند.
- `strict-origin-when-cross-origin` (پیش‌فرض)
  - : این رفتار پیش‌فرض عامل کاربر (user agent) در صورت مشخص نشدن سیاست است. هنگام انجام یک درخواست هم‌خاستگاه URL کامل را ارسال می‌کند، فقط هنگامی که سطح امنیت پروتکل یکسان بماند (مثلاً HTTPS→HTTPS) خاستگاه را ارسال می‌کند، و هیچ هدری به مقصدی با امنیت کمتر (مثلاً HTTPS→HTTP) ارسال نمی‌کند.
- `unsafe-url`
  - : هنگام انجام یک درخواست هم‌خاستگاه یا بین‌خاستگاه URL کامل را ارسال می‌کند. این سیاست باعث نشت خاستگاه‌ها و مسیرها از منابع محافظت‌شده با TLS به خاستگاه‌های ناامن می‌شود. تأثیر این تنظیم را با دقت بررسی کنید.

## مثال‌ها

```html
<img usemap="#my-map" width="100" height="100" src="/img/logo@2x.png" />
<map id="my-map" name="my-map"></map>
```

```js
const elt = document.createElement("area");
elt.href = "/img2.png";
elt.shape = "rect";
elt.referrerPolicy = "no-referrer";
elt.coords = "0,0,100,100";
const map = document.getElementById("my-map");

map.appendChild(elt);
// هنگام کلیک روی ناحیه، لینک آن هدر ارجاع‌دهنده ارسال نخواهد کرد.
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLImageElement.referrerPolicy")}}،
  {{domxref("HTMLAnchorElement.referrerPolicy")}}، و
  {{domxref("HTMLIFrameElement.referrerPolicy")}}.