---
title: "CookieStore: get() method"
short-title: get()
slug: Web/API/CookieStore/get
page-type: web-api-instance-method
browser-compat: api.CookieStore.get
---

{{securecontext_header}}{{APIRef("Cookie Store API")}}{{AvailableInWorkers("window_and_service")}}

متد **`get()`** از رابط {{domxref("CookieStore")}} یک {{jsxref("Promise")}} برمی‌گرداند که به یک کوکی واحد که با `name` یا شیء `options` داده شده مطابقت دارد، حل می‌شود. این متد اولین کوکی‌ای که مطابقت داشته باشد را برمی‌گرداند.

## Syntax

```js-nolint
get(name)
get(options)
```

### پارامترها

این متد به یکی از موارد زیر نیاز دارد:

- `name` {{optional_inline}}
  - : یک رشته با نام کوکی.

یا

- `options` {{optional_inline}}
  - : یک شیء شامل:
    - `name`
      - : یک رشته با نام کوکی.
    - `url`
      - : یک رشته با URL کوکی.

> [!NOTE]
> گزینه `url` امکان تغییر یک کوکی را که در یک URL خاص محدود شده است، فراهم می‌کند. Service workerها می‌توانند کوکی‌هایی را که به هر URL در محدوده خود ارسال می‌شوند، دریافت کنند. از یک سند (document) شما فقط می‌توانید کوکی‌های موجود در URL فعلی را دریافت کنید، بنابراین تنها URL معتبر در یک سند، URL خود سند است.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک شیء نشان‌دهنده اولین کوکی مطابق با `name` یا `options` ارسال شده حل می‌شود، یا اگر کوکی مطابقی وجود نداشته باشد، `null` برمی‌گرداند.

شیء بازگشتی برای یک تطابق شامل ویژگی‌های زیر است:

- `domain` {{experimental_inline}} {{non-standard_inline}}
  - : یک رشته شامل دامنه کوکی.

- `expires` {{experimental_inline}} {{non-standard_inline}}
  - : یک timestamp، بر حسب {{glossary("Unix time")}} به میلی‌ثانیه، شامل تاریخ انقضای کوکی.

- `name` {{experimental_inline}} {{non-standard_inline}}
  - : یک رشته شامل نام کوکی.

- `partitioned` {{experimental_inline}} {{non-standard_inline}}
  - : یک مقدار بولی که نشان می‌دهد آیا کوکی یک کوکی پارتیشن‌بندی شده است (`true`) یا خیر (`false`). برای اطلاعات بیشتر به [Cookies Having Independent Partitioned State (CHIPS)](/en-US/docs/Web/Privacy/Guides/Third-party_cookies/Partitioned_cookies) مراجعه کنید.

- `path` {{experimental_inline}} {{non-standard_inline}}
  - : یک رشته شامل مسیر کوکی.

- `sameSite` {{experimental_inline}} {{non-standard_inline}}
  - : یکی از مقادیر [`SameSite`](/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie#samesitesamesite-value) زیر: [`"strict"`](/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie#strict)، [`"lax"`](/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie#lax) یا [`"none"`](/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie#none).

- `secure` {{experimental_inline}} {{non-standard_inline}}
  - : یک مقدار بولی که نشان می‌دهد آیا کوکی فقط در زمینه‌های امن استفاده شود (`true`) یا خیر (`false`).

- `value` {{experimental_inline}} {{non-standard_inline}}
  - : یک رشته شامل مقدار کوکی.

### استثناها

- `SecurityError` {{domxref("DOMException")}}
  - : اگر مبدأ (origin) به URL {{glossary("Serialization", "serialize")}} نشود، پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : اگر موارد زیر رخ دهد، پرتاب می‌شود:
    - پارامتر `options` یک شیء خالی باشد.
    - متد در نخ اصلی (main thread) فراخوانی شود و گزینه `url` مشخص شده باشد اما با URL پنجره فعلی مطابقت نداشته باشد.
    - متد در یک worker فراخوانی شود و گزینه `url` مشخص شده باشد اما با مبدأ worker مطابقت نداشته باشد.
    - پرس‌وجوی کوکی‌های نشان‌داده‌شده توسط `name` یا `options` داده شده ناموفق باشد.

## مثال‌ها

<!-- مثال‌ها در محیط MDN به دلیل خطاهای ناشناخته به صورت live کار نمی‌کنند -->

### دریافت یک کوکی با نام

این مثال نحوه دریافت یک کوکی خاص با نام را نشان می‌دهد.

کد ابتدا یک کوکی به نام "cookie1" با استفاده از {{domxref("CookieStore.set()")}} ایجاد می‌کند و هر خطایی را در کنسول ثبت می‌کند.
سپس منتظر می‌ماند تا `get()` اطلاعات مربوط به همان کوکی را بازیابی کند.
اگر promise بازگشتی با یک شیء حل شود، آن کوکی را ثبت می‌کند: در غیر این صورت ثبت می‌کند که کوکی مطابقی یافت نشد.

```js
async function cookieTest() {
  // Set test cookie
  try {
    await cookieStore.set("cookie1", "cookie1-value");
  } catch (error) {
    console.log(`Error setting cookie1: ${error}`);
  }

  // Get cookie, specifying name
  const cookie = await cookieStore.get("cookie1");

  if (cookie) {
    console.log(cookie);
  } else {
    console.log("cookie1: Cookie not found");
  }
}

cookieTest();
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}