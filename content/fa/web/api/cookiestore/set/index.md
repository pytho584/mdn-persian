---
title: "CookieStore: set() method"
short-title: set()
slug: Web/API/CookieStore/set
page-type: web-api-instance-method
browser-compat: api.CookieStore.set
---

{{securecontext_header}}{{APIRef("Cookie Store API")}}{{AvailableInWorkers("window_and_service")}}

متد **`set()`** از رابط {{domxref("CookieStore")}} یک کوکی را با `name` و `value` یا شیء `options` داده شده تنظیم می‌کند.

## Syntax

```js-nolint
set(name, value)
set(options)
```

### پارامترها

این متد به یکی از موارد زیر نیاز دارد:

- `name` {{optional_inline}}
  - : یک رشته که نام کوکی است.
- `value` {{optional_inline}}
  - : یک رشته که مقدار کوکی است.

یا

- `options` {{optional_inline}}
  - : یک شیء شامل:
    - `domain` {{Optional_Inline}}
      - : یک رشته شامل دامنه کوکی. پیش‌فرض `null` است.
    - `expires` {{Optional_Inline}}
      - : یک برچسب زمانی بر حسب {{glossary("Unix time")}} (زمان یونیکس) به میلی‌ثانیه که تاریخ انقضای کوکی را مشخص می‌کند. پیش‌فرض `null` است.
    - `maxAge` {{Optional_Inline}}
      - : یک عدد که تعداد ثانیه‌های باقی‌مانده تا انقضای کوکی را نشان می‌دهد. عدد صفر یا منفی بلافاصله کوکی را منقضی می‌کند. اگر هر دو `expires` و `maxAge` تنظیم شده باشند، فراخوانی `set()` با یک `TypeError` شکست می‌خورد. پیش‌فرض `null` است.
    - `name`
      - : یک رشته با نام یک کوکی.
    - `partitioned` {{Optional_Inline}}
      - : یک مقدار بولین که پیش‌فرض `false` است. اگر `true` تنظیم شود، کوکی تنظیم‌شده یک کوکی پارتیشن‌بندی‌شده خواهد بود. برای اطلاعات بیشتر به [کوکی‌های دارای حالت مستقل پارتیشن‌بندی‌شده (CHIPS)](/en-US/docs/Web/Privacy/Guides/Third-party_cookies/Partitioned_cookies) مراجعه کنید.
    - `path` {{Optional_Inline}}
      - : یک رشته شامل مسیر کوکی. پیش‌فرض `/` است.
    - `sameSite` {{Optional_Inline}}
      - : یکی از مقادیر [`SameSite`](/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie#samesitesamesite-value) زیر: [`"strict"`](/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie#strict)، [`"lax"`](/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie#lax)، یا [`"none"`](/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie#none).
    - `value`
      - : یک رشته با مقدار کوکی.

> [!NOTE]
> اگرچه مقادیر را می‌توان در اینجا تنظیم کرد و داخلیاً استفاده خواهد شد، برخی مرورگرها فقط گزینه‌های `name` و `value` را از {{domxref("CookieStore.get()")}} و {{domxref("CookieStore.getAll()")}} بازمی‌گردانند.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که پس از تکمیل تنظیم کوکی با {{jsxref("undefined")}} حل می‌شود.

### استثناها

- `SecurityError` {{domxref("DOMException")}}
  - : اگر مبدأ (origin) قابل {{glossary("Serialization", "سریال‌سازی")}} به یک URL نباشد، پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : در موارد زیر پرتاب می‌شود:
    - هر دو ویژگی `expires` و `maxAge` تنظیم شده باشند.
    - تنظیم کوکی با `name` و `value` یا `options` داده شده به هر شکل دیگری شکست بخورد.

## مثال‌ها

<!-- مثال‌ها در محیط MDN به دلیل خطاهای ناشناخته به صورت زنده کار نمی‌کنند -->

### تنظیم کوکی با نام و مقدار

این مثال یک کوکی را با ارسال `name` و `value` به ترتیب "cookie1" و "cookie1-value" تنظیم می‌کند.
سایر ویژگی‌های کوکی با مقادیر پیش‌فرض، همان‌طور که در پارامتر [`options`](#options) تعریف شده است، تنظیم می‌شوند.

کد ابتدا منتظر می‌ماند تا کوکی تنظیم شود: از آنجا که این عملیات ممکن است با شکست مواجه شود، عملیات در یک بلوک `try...catch` انجام می‌شود و هر خطایی در کنسول ثبت می‌شود. سپس کوکی را که به تازگی تنظیم شده است دریافت و ثبت می‌کند.

```js
async function cookieTest() {
  // Set cookie: passing name and value
  try {
    await cookieStore.set("cookie1", "cookie1-value");
  } catch (error) {
    console.log(`Error setting cookie1: ${error}`);
  }

  // Get the cookie and log its values
  const cookie = await cookieStore.get("cookie1");
  console.log(cookie);
}
```

### تنظیم کوکی با گزینه‌ها

این مثال یک کوکی را با ارسال یک شیء `options` شامل `name`، `value`، `expires` و `partitioned` تنظیم می‌کند.

کد ابتدا منتظر می‌ماند تا کوکی تنظیم شود: از آنجا که این عملیات ممکن است با شکست مواجه شود، عملیات در یک بلوک `try...catch` انجام می‌شود و هر خطایی در کنسول ثبت می‌شود. سپس کوکی را که به تازگی تنظیم شده است دریافت و ثبت می‌کند.

```js
async function cookieTest() {
  const day = 24 * 60 * 60 * 1000;
  const cookieName = "cookie2";
  try {
    // Set cookie: passing options
    await cookieStore.set({
      name: cookieName,
      value: `${cookieName}-value`,
      expires: Date.now() + day,
      partitioned: true,
    });
  } catch (error) {
    log(`Error setting ${cookieName}: ${error}`);
    console.log(error);
  }

  // Log the new cookie
  const cookie = await cookieStore.get(cookieName);
  console.log(cookie);
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}