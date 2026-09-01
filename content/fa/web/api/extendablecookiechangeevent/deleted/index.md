---
title: "ExtendableCookieChangeEvent: deleted property"
short-title: deleted
slug: Web/API/ExtendableCookieChangeEvent/deleted
page-type: web-api-instance-property
browser-compat: api.ExtendableCookieChangeEvent.deleted
---

{{securecontext_header}}{{APIRef("Cookie Store API")}}{{AvailableInWorkers("service")}}

ویژگی فقط‌خواندنی **`deleted`** از رابط {{domxref("ExtendableCookieChangeEvent")}}، هر کوکی‌ای را که توسط نمونه‌ی `ExtendableCookieChangeEvent` داده شده حذف شده است، بازمی‌گرداند.

## مقدار

یک آرایه از اشیاء که شامل کوکی(های) حذف شده است. هر شیء شامل ویژگی‌های زیر است:

- `name`
  - : یک رشته که نام کوکی را شامل می‌شود.
- `value`
  - : یک رشته که مقدار کوکی را شامل می‌شود.
- `domain`
  - : یک رشته که دامنه‌ی کوکی را شامل می‌شود.
- `path`
  - : یک رشته که مسیر کوکی را شامل می‌شود.
- `expires`
  - : یک برچسب زمانی، بر حسب [زمان یونیکس](/en-US/docs/Glossary/Unix_time) به میلی‌ثانیه، که تاریخ انقضای کوکی را شامل می‌شود.
- `secure`
  - : یک {{jsxref("Boolean")}} که نشان می‌دهد آیا کوکی فقط در یک بافت امن (HTTPS به جای HTTP) استفاده می‌شود یا خیر.
- `sameSite`
  - : یکی از مقادیر [`SameSite`](/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie#samesitesamesite-value) زیر:
    - `"strict"`
      - : کوکی‌ها فقط در یک بافت اول-شخص ارسال می‌شوند و با درخواست‌های آغاز شده توسط وب‌سایت‌های شخص ثالث ارسال نمی‌شوند.
    - `"lax"`
      - : کوکی‌ها در درخواست‌های فرعی متقاطع (cross-site) معمولی (مثلاً برای بارگذاری تصاویر یا فریم‌ها در یک سایت شخص ثالث) ارسال نمی‌شوند، اما زمانی که کاربر در داخل سایت مبدأ در حال مرور است (یعنی پس از کلیک روی یک پیوند) ارسال می‌شوند.
    - `"none"`
      - : کوکی‌ها در همه‌ی بافت‌ها ارسال خواهند شد.

- `partitioned`
  - : یک مقدار بولی (boolean) که نشان می‌دهد آیا کوکی یک کوکی پارتیشن‌بندی شده است (`true`) یا خیر (`false`). برای اطلاعات بیشتر به [کوکی‌های با وضعیت پارتیشن‌بندی مستقل (CHIPS)](/en-US/docs/Web/Privacy/Guides/Third-party_cookies/Partitioned_cookies) مراجعه کنید.

## مثال‌ها

در این مثال، هنگامی که کوکی حذف می‌شود، شنونده‌ی رویداد اولین آیتم را در ویژگی `deleted` در کنسول ثبت می‌کند. این آیتم شامل یک شیء است که کوکی تازه حذف شده را نمایش می‌دهد.

```js
self.addEventListener("cookiechange", (event) => {
  console.log(event.deleted[0]);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}