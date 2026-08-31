---
title: "CookieStore: getAll() method"
short-title: getAll()
slug: Web/API/CookieStore/getAll
page-type: web-api-instance-method
browser-compat: api.CookieStore.getAll
---

{{securecontext_header}}{{APIRef("Cookie Store API")}}{{AvailableInWorkers("window_and_service")}}

متد **`getAll()`** در رابط {{domxref("CookieStore")}} یک {{jsxref("Promise")}} برمی‌گرداند که با آرایه‌ای از کوکی‌های منطبق با `name` یا `options` ارسال‌شده به آن resolve می‌شود. فراخوانی بدون پارامتر، تمام کوکی‌های مربوط به بافتار (context) فعلی را برمی‌گرداند.

## نحو (Syntax)

```js-nolint
getAll()
getAll(name)
getAll(options)
```

### پارامترها

- `name` {{optional_inline}}
  - : رشته‌ای شامل نام یک کوکی.

یا

- `options` {{optional_inline}}
  - : شیئی شامل:
    - `name`
      - : رشته‌ای شامل نام یک کوکی.
    - `url`
      - : رشته‌ای شامل URL یک کوکی.

> [!NOTE]
> گزینه `url` امکان تغییر کوکی‌ای را می‌دهد که در محدوده یک URL خاص تعریف شده است. کارگرهای خدماتی (service workers) می‌توانند کوکی‌هایی را دریافت کنند که به هر URL در محدوده خودشان ارسال می‌شوند. از یک سند (document) فقط می‌توانید کوکی‌های مربوط به URL فعلی را دریافت کنید، بنابراین تنها URL معتبر در بافتار یک سند، URL خود آن سند است.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با آرایه‌ای از اشیاء نمایش‌دهنده کوکی‌های منطبق با `name` یا `options` داده‌شده resolve می‌شود.

هر شیء شامل ویژگی‌های زیر است:

- `domain`
  - : رشته‌ای شامل دامنه کوکی.

- `expires`
  - : یک برچسب زمانی، بر حسب [زمان یونیکس](/en-US/docs/Glossary/Unix_time) در میلی‌ثانیه، که تاریخ انقضای کوکی را نشان می‌دهد.

- `name`
  - : رشته‌ای شامل نام کوکی.

- `partitioned`
  - : یک مقدار بولی که نشان می‌دهد آیا کوکی یک کوکی پارتیشن‌بندی‌شده است (`true`) یا نه (`false`). برای اطلاعات بیشتر به [کوکی‌های با حالت مستقل پارتیشن‌بندی‌شده (CHIPS)](/en-US/docs/Web/Privacy/Guides/Third-party_cookies/Partitioned_cookies) مراجعه کنید.

- `path`
  - : رشته‌ای شامل مسیر کوکی.

- `sameSite`
  - : یکی از مقادیر [`SameSite`](/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie#samesitesamesite-value) زیر: [`"strict"`](/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie#strict)، [`"lax"`](/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie#lax) یا [`"none"`](/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie#none).

- `secure`
  - : یک مقدار بولی که نشان می‌دهد آیا کوکی فقط باید در بافتارهای امن استفاده شود (`true`) یا نه (`false`).

- `value`
  - : رشته‌ای شامل مقدار کوکی.

### استثناها (Exceptions)

- `SecurityError` {{domxref("DOMException")}}
  - : اگر مبدأ (origin) به یک URL {{glossary("Serialization", "سریال‌سازی")}} نشود، پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : در موارد زیر پرتاب می‌شود:
    - متد در ترد اصلی فراخوانی شود و گزینه `url` مشخص شده باشد اما با URL پنجره فعلی مطابقت نداشته باشد.
    - متد در یک کارگر (worker) فراخوانی شود و گزینه `url` مشخص شده باشد اما با مبدأ کارگر مطابقت نداشته باشد.
    - پرس‌وجوی کوکی‌های نمایش‌داده‌شده توسط `name` یا `options` داده‌شده ناموفق باشد.

## مثال‌ها

<!-- مثال‌ها در محیط MDN به‌عنوان مثال زنده کار نمی‌کنند (به دلیل خطاهای ناشناخته) -->

### دریافت همه کوکی‌های این بافتار

این مثال نحوه دریافت همه کوکی‌ها در بافتار فعلی را نشان می‌دهد.

ابتدا تابع `setTestCookies()` را تعریف می‌کنیم که کوکی‌های آزمایشی «cookie1» و «cookie2» را می‌سازد و هر خطایی را ثبت می‌کند.

```js
async function setTestCookies() {
  // Set two cookies
  try {
    await cookieStore.set("cookie1", "cookie1-value");
  } catch (error) {
    console.log(`Error setting cookie1: ${error}`);
  }

  try {
    await cookieStore.set("cookie2", "cookie2-value");
  } catch (error) {
    console.log(`Error setting cookie2: ${error}`);
  }
}
```

متد `cookieTest()` ابتدا `setTestCookies()` را فراخوانی کرده و سپس منتظر `getAll()` می‌ماند. این متد یک {{jsxref("Promise")}} برمی‌گرداند که با آرایه‌ای از اشیاء شامل تمام کوکی‌های این بافتار resolve می‌شود، یا اگر کوکی‌ای وجود نداشته باشد، با آرایه‌ای خالی. اگر پرامیسی که برگردانده شده با آرایه‌ای حاوی اطلاعات کوکی resolve شود، آرایه را پیمایش کرده و هر کوکی («cookie1» و «cookie2») را ثبت می‌کنیم.

```js
async function cookieTest() {
  // Set our test cookies
  await setTestCookies();

  // Get all cookies
  const cookies = await cookieStore.getAll();

  // Iterate the cookies, or log that none were found
  if (cookies.length > 0) {
    console.log(`Found cookies: ${cookies.length}:`);
    cookies.forEach((cookie) => console.log(cookie));
  } else {
    console.log("Cookies not found");
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}