---
title: "CookieChangeEvent: changed property"
short-title: changed
slug: Web/API/CookieChangeEvent/changed
page-type: web-api-instance-property
browser-compat: api.CookieChangeEvent.changed
---

{{securecontext_header}}{{APIRef("Cookie Store API")}}

خاصیت فقط-خواندنی **`changed`** از رابط {{domxref("CookieChangeEvent")}}، آرایه‌ای از کوکی‌هایی که تغییر کرده‌اند را برمی‌گرداند. توجه داشته باشید که این شامل کوکی‌هایی که با تاریخ انقضای در گذشته ایجاد شده‌اند نمی‌شود، زیرا این کوکی‌ها بلافاصله حذف می‌شوند.

## مقدار

آرایه‌ای از اشیاء حاوی کوکی(های) تغییر یافته. هر شیء شامل ویژگی‌های زیر است:

- `name`
  - : یک رشته حاوی نام کوکی.
- `value`
  - : یک رشته حاوی مقدار کوکی.
- `domain`
  - : یک رشته حاوی دامنه کوکی.
- `path`
  - : یک رشته حاوی مسیر کوکی.
- `expires`
  - : یک timestamp (مهر زمانی) بر حسب میلی‌ثانیه از {{glossary("Unix time")}}، که تاریخ انقضای کوکی را نشان می‌دهد.
- `secure`
  - : یک {{jsxref("Boolean")}} که نشان می‌دهد آیا کوکی فقط در یک بافت امن (HTTPS به جای HTTP) استفاده می‌شود.
- `sameSite`
  - : یکی از مقادیر [`SameSite`](/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie#samesitesamesite-value) زیر:
    - `"strict"`
      - : کوکی‌ها فقط در بافت first-party (متعلق به سایت اصلی) ارسال می‌شوند و با درخواست‌های آغاز شده توسط وب‌سایت‌های شخص ثالث ارسال نمی‌شوند.
    - `"lax"`
      - : کوکی‌ها در درخواست‌های فرعی عادی بین سایتی (مثلاً برای بارگذاری تصاویر یا فریم‌ها در یک سایت شخص ثالث) ارسال نمی‌شوند، اما زمانی که کاربر درون سایت مبدأ حرکت می‌کند (یعنی با دنبال کردن یک پیوند) ارسال می‌شوند.
    - `"none"`
      - : کوکی‌ها در همه بافت‌ها ارسال می‌شوند.
- `partitioned`
  - : یک مقدار بولی (boolean) که نشان می‌دهد آیا کوکی یک کوکی پارتیشن‌بندی شده است (`true`) یا خیر (`false`). برای اطلاعات بیشتر به [Cookies Having Independent Partitioned State (CHIPS)](/en-US/docs/Web/Privacy/Guides/Third-party_cookies/Partitioned_cookies) مراجعه کنید.

## مثال‌ها

در این مثال، هنگامی که کوکی تنظیم می‌شود، شنونده رویداد (event listener) خاصیت `changed` را در کنسول ثبت می‌کند. اولین آیتم در آن آرایه شامل یک شیء است که کوکی تازه تنظیم شده را نشان می‌دهد.

```js
cookieStore.addEventListener("change", (event) => {
  console.log(event.changed[0]);
});

const oneDay = 24 * 60 * 60 * 1000;
cookieStore.set({
  name: "cookie1",
  value: "cookie1-value",
  expires: Date.now() + oneDay,
  domain: "example.com",
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}