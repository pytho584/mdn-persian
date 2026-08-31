```
---
title: "CookieChangeEvent: deleted property"
short-title: deleted
slug: Web/API/CookieChangeEvent/deleted
page-type: web-api-instance-property
browser-compat: api.CookieChangeEvent.deleted
---

{{securecontext_header}}{{APIRef("Cookie Store API")}}

ویژگی فقط‌خواندنی **`deleted`** در رابط {{domxref("CookieChangeEvent")}} آرایه‌ای از کوکی‌هایی را برمی‌گرداند که توسط نمونه‌ی `CookieChangeEvent` داده‌شده حذف شده‌اند.

توجه داشته باشید که این شامل کوکی‌هایی نیز می‌شود که با تاریخ انقضای در گذشته ایجاد شده‌اند، زیرا این کوکی‌ها بلافاصله حذف می‌شوند.

## مقدار

آرایه‌ای از اشیاء حاوی کوکی(های) حذف‌شده. هر شیء دارای ویژگی‌های زیر است:

- `name`
  - : رشته‌ای حاوی نام کوکی.
- `value`
  - : رشته‌ای حاوی مقدار کوکی.
- `domain`
  - : رشته‌ای حاوی دامنه‌ی کوکی.
- `path`
  - : رشته‌ای حاوی مسیر کوکی.
- `expires`
  - : یک برچسب زمانی، که به صورت {{glossary("Unix time")}} در میلی‌ثانیه ارائه می‌شود و تاریخ انقضای کوکی را نشان می‌دهد.
- `secure`
  - : یک {{jsxref("Boolean")}} که نشان می‌دهد آیا کوکی فقط در بافت امن (HTTPS به جای HTTP) استفاده می‌شود یا خیر.
- `sameSite`
  - : یکی از مقادیر [`SameSite`](/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie#samesitesamesite-value) به صورت زیر:
    - `"strict"`
      - : کوکی‌ها فقط در بافت طرف اول ارسال می‌شوند و همراه با درخواست‌های آغازشده توسط وب‌سایت‌های شخص ثالث ارسال نمی‌شوند.
    - `"lax"`
      - : کوکی‌ها در درخواست‌های فرعی متقاطع عادی (مثلاً برای بارگذاری تصاویر یا فریم‌ها در یک سایت شخص ثالث) ارسال نمی‌شوند، اما زمانی که کاربر در حال پیمایش در سایت مبدأ است (یعنی هنگام دنبال کردن یک پیوند) ارسال می‌شوند.
    - `"none"`
      - : کوکی‌ها در همه‌ی بافت‌ها ارسال می‌شوند.

- `partitioned`
  - : یک مقدار بولین که نشان می‌دهد آیا کوکی یک کوکی پارتیشن‌بندی‌شده است (`true`) یا خیر (`false`). برای اطلاعات بیشتر به [Cookies Having Independent Partitioned State (CHIPS)](/en-US/docs/Web/Privacy/Guides/Third-party_cookies/Partitioned_cookies) مراجعه کنید.

## مثال‌ها

در این مثال، وقتی کوکی حذف می‌شود، شنونده‌ی رویداد اولین مورد از ویژگی `CookieChangeEvent.deleted` را در کنسول ثبت می‌کند. این مورد شامل شیءای است که کوکی تازه‌حذف‌شده را نشان می‌دهد.

```js
cookieStore.addEventListener("change", (event) => {
  console.log(event.deleted[0]);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
```