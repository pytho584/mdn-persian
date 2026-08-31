---
title: "CookieStore"
---

---
title: CookieStore
slug: Web/API/CookieStore
page-type: web-api-interface
browser-compat: api.CookieStore
---

{{securecontext_header}}{{APIRef("Cookie Store API")}}{{AvailableInWorkers("window_and_service")}}

رابطهٔ **`CookieStore`** در {{domxref("Cookie Store API", "", "", "nocode")}} روش‌هایی برای دریافت و تنظیم کوکی‌ها به‌صورت ناهمگام از یک صفحه یا یک service worker فراهم می‌کند.

`CookieStore` از طریق ویژگی‌های موجود در حوزهٔ سراسری (global scope) در بافت {{domxref("Window")}} یا {{domxref("ServiceWorkerGlobalScope")}} قابل دسترسی است. بنابراین سازنده‌ای برای آن وجود ندارد.

{{InheritanceDiagram}}

## روش‌های نمونه

- {{domxref("CookieStore.delete()")}}
  - : روش `delete()` کوکی‌ای با `name` یا شیء `options` داده‌شده را حذف می‌کند.
    یک {{jsxref("Promise")}} برمی‌گرداند که وقتی حذف کامل شود یا اگر هیچ کوکی‌ای مطابقت نداشته باشد، resolve می‌شود.
- {{domxref("CookieStore.get()")}}
  - : روش `get()` یک کوکی واحد با `name` یا شیء `options` داده‌شده را دریافت می‌کند.
    یک {{jsxref("Promise")}} برمی‌گرداند که با جزئیات یک کوکی واحد resolve می‌شود.
- {{domxref("CookieStore.getAll()")}}
  - : روش `getAll()` همهٔ کوکی‌های مطابقت‌دار را دریافت می‌کند.
    یک {{jsxref("Promise")}} برمی‌گرداند که با فهرستی از کوکی‌ها resolve می‌شود.
- {{domxref("CookieStore.set()")}}
  - : روش `set()` کوکی‌ای با `name` و `value` یا شیء `options` داده‌شده تنظیم می‌کند.
    یک {{jsxref("Promise")}} برمی‌گرداند که وقتی کوکی تنظیم شود، resolve می‌شود.

## رویدادها

- {{domxref("CookieStore.change_event", "change")}}
  - : رویداد `change` زمانی رخ می‌دهد که در هر کوکی تغییری ایجاد شود.

## مثال‌ها

مثال‌های زیر را می‌توان با کپی کردن کد در یک محیط آزمایشی و اجرای آن با یک [سرور محلی](/en-US/docs/Learn_web_development/Howto/Tools_and_setup/set_up_a_local_testing_server) یا استقرار آن در وب‌سایتی مانند GitHub Pages آزمایش کرد.

<!-- مثال‌ها در محیط MDN به‌صورت نمونهٔ زنده کار نمی‌کنند (به دلیل خطاهای ناشناخته) -->

### تنظیم کوکی‌ها

این مثال نشان می‌دهد که چگونه می‌توان کوکی‌ها را با عبور دادن `name` و `value` و همچنین با تنظیم یک مقدار `options` تنظیم کرد.

روش `cookieTest()` یک کوکی با ویژگی‌های `name` و `value` و کوکی دیگری با ویژگی‌های `name`، `value` و `expires` تنظیم می‌کند.
سپس از روش {{domxref("CookieStore.get()")}} برای دریافت هر یک از کوکی‌ها استفاده می‌کنیم که پس از آن ثبت (log) می‌شوند.

```js
async function cookieTest() {
  // تنظیم کوکی: عبور دادن name و value
  try {
    await cookieStore.set("cookie1", "cookie1-value");
  } catch (error) {
    console.log(`Error setting cookie1: ${error}`);
  }

  // تنظیم کوکی: عبور دادن options
  const day = 24 * 60 * 60 * 1000;

  try {
    await cookieStore.set({
      name: "cookie2",
      value: "cookie2-value",
      expires: Date.now() + day,
      partitioned: true,
    });
  } catch (error) {
    log(`Error setting cookie2: ${error}`);
  }

  // دریافت کوکی‌های نام‌دار و ثبت ویژگی‌های آن‌ها
  const cookie1 = await cookieStore.get("cookie1");
  console.log(cookie1);

  const cookie2 = await cookieStore.get("cookie2");
  console.log(cookie2);
}

cookieTest();
```

> [!NOTE]
> در [مرورگرهای پشتیبانی‌کننده](/en-US/docs/Web/API/CookieStore/set#browser_compatibility)، می‌توانید زمان انقضای کوکی را به‌جای `expires` با استفاده از `maxAge` تنظیم کنید.

### دریافت کوکی‌ها

این مثال نشان می‌دهد که چگونه می‌توانید یک کوکی خاص را با {{domxref("CookieStore.get()")}} یا همهٔ کوکی‌ها را با {{domxref("CookieStore.getAll()")}} دریافت کنید.

کد مثال ابتدا سه کوکی تنظیم می‌کند که برای نمایش روش‌های دریافت از آن‌ها استفاده خواهیم کرد.
ابتدا `cookie1` و `cookie2` را با روش {{domxref("CookieStore.set()")}} ایجاد می‌کند.
سپس کوکی سومی را با استفاده از ویژگی قدیمی همزمان {{domxref("Document.cookie")}} ایجاد می‌کند (فقط برای نشان دادن اینکه این کوکی‌ها نیز با روش‌های `get()` و `getAll()` دریافت می‌شوند).

سپس کد از {{domxref("CookieStore.get()")}} برای دریافت «cookie1» و ثبت ویژگی‌های آن استفاده می‌کند، و از {{domxref("CookieStore.getAll()")}} (بدون آرگومان) برای دریافت همهٔ کوکی‌ها در بافت فعلی استفاده می‌کند.

```js
async function cookieTest() {
  // تنظیم یک کوکی با عبور دادن name و value
  try {
    await cookieStore.set("cookie1", "cookie1-value");
  } catch (error) {
    console.log(`Error setting cookie1: ${error}`);
  }

  // تنظیم یک کوکی با عبور دادن یک شیء options
  const day = 24 * 60 * 60 * 1000;
  try {
    await cookieStore.set({
      name: "cookie2",
      value: `cookie2-value`,
      expires: Date.now() + day,
      partitioned: true,
    });
  } catch (error) {
    console.log(`Error setting cookie2: ${error}`);
  }

  // تنظیم کوکی با استفاده از document.cookie
  // (برای نشان دادن اینکه این‌ها نیز دریافت می‌شوند)
  document.cookie = "favorite_food=tripe; SameSite=None; Secure";

  // دریافت کوکی نام‌دار و ثبت ویژگی‌های آن
  const cookie1 = await cookieStore.get("cookie1");
  console.log(cookie1);

  // دریافت همهٔ کوکی‌ها و ثبت هر یک
  const cookies = await cookieStore.getAll();
  if (cookies.length > 0) {
    console.log(`getAll(): ${cookies.length}:`);
    cookies.forEach((cookie) => console.log(cookie));
  } else {
    console.log("Cookies not found");
  }
}

cookieTest();
```

مثال باید «cookie1» و هر سه کوکی را جداگانه ثبت کند.
نکته‌ای که باید به آن توجه کنید این است که کوکی ایجاد شده با {{domxref("Document.cookie")}} ممکن است مسیر (path) متفاوتی نسبت به کوکی‌هایی داشته باشد که با {{domxref("CookieStore.set()","set()")}} ایجاد شده‌اند (که به‌طور پیش‌فرض `/` است).

### حذف یک کوکی نام‌دار

این مثال نشان می‌دهد که چگونه می‌توان یک کوکی نام‌دار را با استفاده از روش {{domxref("CookieStore.delete()","delete()")}} حذف کرد.

کد ابتدا دو کوکی تنظیم می‌کند و آن‌ها را در کنسول ثبت می‌کند.
سپس یکی از کوکی‌ها را حذف می‌کنیم و دوباره همهٔ کوکی‌ها را فهرست می‌کنیم.
کوکی حذف‌شده («cookie1») در آرایهٔ اولین ثبت (log) وجود دارد و در دومین وجود ندارد.

```js
async function cookieTest() {
  // تنظیم دو کوکی
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

  // ثبت نام کوکی‌ها
  let cookieNames = (await cookieStore.getAll())
    .map((cookie) => cookie.name)
    .join(" ");
  console.log(`Initial cookies: ${cookieNames}`);

  // حذف cookie1
  await cookieStore.delete("cookie1");

  // ثبت دوبارهٔ کوکی‌ها (برای نشان دادن حذف cookie1)
  cookieNames = (await cookieStore.getAll())
    .map((cookie) => cookie.name)
    .join(" ");
  console.log(
    `Cookies remaining after attempted deletions (cookie1 should be deleted): ${cookieNames}`,
  );
}

cookieTest();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}