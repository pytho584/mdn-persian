---
title: "ExtendableCookieChangeEvent: changed property"
short-title: changed
slug: Web/API/ExtendableCookieChangeEvent/changed
page-type: web-api-instance-property
browser-compat: api.ExtendableCookieChangeEvent.changed
---

{{securecontext_header}}{{APIRef("Cookie Store API")}}{{AvailableInWorkers("service")}}

خاصیتِ فقط‌خواندنی **`changed`** در رابط {{domxref("ExtendableCookieChangeEvent")}}، کوکی‌هایی را برمی‌گرداند که توسط این نمونهٔ `ExtendableCookieChangeEvent` تغییر کرده‌اند.

## مقدار

آرایه‌ای از آبجکت‌ها که کوکی(های) تغییر کرده را شامل می‌شود. هر آبجکت شامل ویژگی‌های زیر است:

- `name`
  - : رشته‌ای که نام کوکی را شامل می‌شود.
- `value`
  - : رشته‌ای که مقدار کوکی را شامل می‌شود.
- `domain`
  - : رشته‌ای که دامنهٔ کوکی را شامل می‌شود.
- `path`
  - : رشته‌ای که مسیر کوکی را شامل می‌شود.
- `expires`
  - : یک برچسب زمانی، که به صورت [زمان یونیکس](/en-US/docs/Glossary/Unix_time) بر حسب میلی‌ثانیه داده شده و تاریخ انقضای کوکی را شامل می‌شود.
- `secure`
  - : یک {{jsxref("Boolean")}} که نشان می‌دهد آیا کوکی فقط در بافت امن (HTTPS به جای HTTP) استفاده می‌شود یا خیر.
- `sameSite`
  - : یکی از مقادیر [`SameSite`](/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie#samesitesamesite-value):
    - `"strict"`
      - : کوکی‌ها فقط در بافت first-party ارسال می‌شوند و همراه با درخواست‌هایی که توسط وب‌سایت‌های شخص ثالث آغاز می‌شوند ارسال نمی‌شوند.
    - `"lax"`
      - : کوکی‌ها در درخواست‌های فرعی عادی بین‌سایتی (مثلاً برای بارگذاری تصاویر یا فریم‌ها در سایت شخص ثالث) ارسال نمی‌شوند، اما وقتی کاربر در حال پیمایش در سایت مبدأ است (مثلاً با دنبال کردن یک پیوند) ارسال می‌شوند.
    - `"none"`
      - : کوکی‌ها در همهٔ بافت‌ها ارسال می‌شوند.

- `partitioned`
  - : یک مقدار بولین که نشان می‌دهد آیا کوکی یک کوکی پارتیشن‌بندی‌شده است (`true`) یا خیر (`false`). برای اطلاعات بیشتر به [کوکی‌های دارای حالت پارتیشن‌بندی‌شده مستقل (CHIPS)](/en-US/docs/Web/Privacy/Guides/Third-party_cookies/Partitioned_cookies) مراجعه کنید.

## مثال‌ها

در این مثال، وقتی کوکی تنظیم می‌شود، شنوندهٔ رویداد، خاصیت `changed` را در کنسول ثبت می‌کند. اولین مورد در آن آرایه حاوی آبجکتی است که کوکی تازه تنظیم‌شده را نشان می‌دهد.

```js
self.addEventListener("cookiechange", (event) => {
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

## سازگاری مرورگر

{{Compat}}