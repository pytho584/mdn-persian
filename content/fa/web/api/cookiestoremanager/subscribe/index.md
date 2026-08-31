---
title: "CookieStoreManager: subscribe() method"
short-title: subscribe()
slug: Web/API/CookieStoreManager/subscribe
page-type: web-api-instance-method
browser-compat: api.CookieStoreManager.subscribe
---

{{securecontext_header}}{{APIRef("Cookie Store API")}}{{AvailableInWorkers("window_and_service")}}

متد **`subscribe()`** از رابط {{domxref("CookieStoreManager")}} یک {{domxref("ServiceWorkerRegistration")}} را برای دریافت رویدادهای تغییر کوکی ثبت‌نام می‌کند. اشتراک‌های تکراری نادیده گرفته می‌شوند: یعنی اگر یک سرویس‌ورکر بیش از یک بار برای همان کوکی ثبت‌نام کند، فقط یک بار اعلان تغییر را دریافت خواهد کرد.

## سینتکس

```js-nolint
subscribe(subscriptions)
```

### پارامترها

- `subscriptions`
  - : آرایه‌ای از اشیاء که هر کدام دارای ویژگی‌های زیر است:
    - `name` {{optional_inline}}
      - : یک رشته برابر با نام یک کوکی. اگر `name` حذف شود، سرویس‌ورکر برای رویدادهای تغییر تمام کوکی‌هایی که در محدوده (scope) هستند، ثبت‌نام می‌شود.
    - `url` {{optional_inline}}
      - : یک رشته برابر با URL محدوده (scope) یک کوکی. این می‌تواند محدودتر از محدوده ثبت‌نام سرویس‌ورکر باشد. اگر `url` حذف شود، به طور پیش‌فرض برابر با محدوده ثبت‌نام سرویس‌ورکر خواهد بود.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که پس از تکمیل اشتراک با {{jsxref("undefined")}} حل می‌شود.

### استثناها

- {{jsxref("TypeError")}}
  - : اگر `url` یک URL معتبر نباشد یا با {{domxref("ServiceWorkerRegistration.scope","scope")}} ثبت‌نام سرویس‌ورکر شروع نشود، پرتاب می‌شود.

## مثال‌ها

### تنظیم نام و URL

در این مثال، {{domxref("ServiceWorkerRegistration")}} که با `registration` نشان داده می‌شود، برای رویدادهای تغییر کوکی به نام `"cookie1"` با محدوده `"/path1"` ثبت‌نام می‌کند.

```js
// Subscribe to a specific cookie and URL
const subscriptions = [{ name: "cookie1", url: `/path1` }];
await registration.cookies.subscribe(subscriptions);
```

### تنظیم فقط نام

در این مثال، فقط `name` را تنظیم کرده و `url` را حذف می‌کنیم: اشتراک برای همه کوکی‌های به نام `cookie1` در محدوده سرویس‌ورکر اعمال می‌شود.

```js
// Subscribe to all cookies named "cookie1" in the registration scope
await registration.cookies.subscribe([{ name: "cookie1" }]);
```

### تنظیم فقط URL

در این مثال، فقط `url` را تنظیم کرده و `name` را حذف می‌کنیم: اشتراک برای همه کوکی‌های درون محدوده URL مشخص شده اعمال می‌شود.

```js
// Subscribe to all cookie changes within a specific path
await registration.cookies.subscribe([{ url: "/path/one/" }]);
```

### اشتراک برای همه کوکی‌ها

در این مثال، هر دو `name` و `url` حذف شده‌اند. اشتراک برای همه کوکی‌های درون محدوده سرویس‌ورکر اعمال می‌شود.

```js
// Subscribe to all cookie changes within the entire registration scope
await registration.cookies.subscribe([{}]);
```

### تنظیم URL خارج از محدوده سرویس‌ورکر

اگر URL خارج از محدوده سرویس‌ورکر باشد، `subscribe()` یک `TypeError` پرتاب می‌کند.

```js example-bad
await registration.cookies.subscribe([
  { name: "cookie1", url: "/out-of-scope/" },
]);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}