---
title: "CookieStore: delete() method"
---

{{securecontext_header}}{{APIRef("Cookie Store API")}}{{AvailableInWorkers("window_and_service")}}

متد **`delete()`** از رابط {{domxref("CookieStore")}} کوکی‌ای را که با `name` یا شیء `options` داده‌شده مطابقت دارد حذف می‌کند. این متد با تغییر تاریخ کوکی به تاریخی در گذشته، آن را منقضی می‌کند.

توجه داشته باشید که اگر کوکی‌ای مطابقت داده نشود خطایی رخ نمی‌دهد: پرامیس بازگردانده‌شده زمانی fulfilled می‌شود که کوکی مطابق حذف شود یا اگر هیچ کوکی‌ای مطابقت نداشته باشد.

## Syntax

```js-nolint
delete(name)
delete(options)
```

### Parameters

این متد به یکی از موارد زیر نیاز دارد:

- `name` {{optional_inline}}
  - : رشته‌ای شامل نام یک کوکی.

یا

- `options` {{optional_inline}}
  - : شیئی شامل:
    - `name`
      - : رشته‌ای شامل نام یک کوکی.
    - `domain` {{Optional_Inline}}
      - : رشته‌ای شامل دامنهٔ کوکی. پیش‌فرض `null`.
    - `path` {{Optional_Inline}}
      - : رشته‌ای شامل یک مسیر. پیش‌فرض `/`.
    - `partitioned` {{Optional_Inline}}
      - : یک مقدار بولی که پیش‌فرض آن `false` است. تنظیم آن به `true` مشخص می‌کند که کوکی مورد حذف، یک کوکی پارتیشن‌بندی‌شده (partitioned) خواهد بود. برای اطلاعات بیشتر به [Cookies Having Independent Partitioned State (CHIPS)](/en-US/docs/Web/Privacy/Guides/Third-party_cookies/Partitioned_cookies) مراجعه کنید.

### Return value

یک {{jsxref("Promise")}} که وقتی عملیات حذف کامل می‌شود یا هیچ کوکی‌ای مطابقت داده نمی‌شود، با {{jsxref("undefined")}} resolve می‌شود.

### Exceptions

- `SecurityError` {{domxref("DOMException")}}
  - : در صورتی که origin نتواند به یک URL {{glossary("Serialization", "serialized")}} شود.
- {{jsxref("TypeError")}}
  - : در صورتی که کوکی مطابق با `name` یا `options` داده‌شده قابل حذف نباشد.

## Examples

<!-- The examples don't work as live examples in MDN environment (due to unknown errors) -->

### حذف یک کوکی با نام

این مثال نشان می‌دهد که چگونه می‌توان یک کوکی را با ارسال نام آن به متد `delete()` حذف کرد.

این کار زمانی کار می‌کند که کوکی مورد حذف با نام کوکی و مقادیر پیش‌فرض [`options`](#options) بالا مطابقت داشته باشد. این حالت زمانی رخ می‌دهد که کوکی با استفاده از فقط یک نام و مقدار {{domxref("CookieStore/set","set()")}} شده باشد، اما ممکن است اگر کوکی با گزینه‌ها یا با استفاده از {{domxref("Document.cookie")}} ایجاد شده باشد، چنین نباشد.

کد ابتدا تابع `setTestCookies()` را تعریف می‌کند که چند کوکی آزمایشی ایجاد می‌کند و نام آن‌ها را ثبت می‌کند.

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

  // Log cookie names
  const cookieNames = (await cookieStore.getAll())
    .map((cookie) => cookie.name)
    .join(" ");
  console.log(`Initial cookies: ${cookieNames}`);
}
```

متد `cookieTest()` تابع `setTestCookies()` را فراخوانی می‌کند. سپس "cookie1" را که به‌تازگی ایجاد کرده‌ایم حذف می‌کند و دوباره نام همه کوکی‌ها را فهرست می‌کند.

```js
async function cookieTest() {
  // Create our test cookies
  await setTestCookies();

  // Delete cookie1
  try {
    await cookieStore.delete("cookie1");
  } catch (error) {
    console.log(`Error deleting cookie1: ${error}`);
  }

  // Log cookie names again (to show cookie1 deleted)
  const cookieNames = (await cookieStore.getAll())
    .map((cookie) => cookie.name)
    .join(" ");
  console.log(
    `Cookies remaining after attempting to delete cookie1: ${cookieNames}`,
  );
}

cookieTest();
```

هنگام اجرا، لاگ کنسول باید ابتدا نشان دهد که هر دو cookie1 و cookie2 وجود دارند، اما پس از حذف cookie1، دیگر فهرست نشود.

### حذف یک کوکی با گزینه‌ها

این مثال تقریباً مشابه مثال قبلی است، با این تفاوت که نشان می‌دهد گزینه‌ها باید با گزینه‌های کوکی مورد حذف مطابقت داشته باشند.

کد ابتدا تابع `setTestCookies()` را تعریف می‌کند. این تابع دو کوکی با ویژگی `partitioned` تنظیم‌شده روی `true` ایجاد می‌کند و نام آن‌ها را ثبت می‌کند.

```js
async function setTestCookies() {
  // Set two cookies
  try {
    await cookieStore.set({
      name: "cookie1",
      value: `cookie1-value`,
      partitioned: true,
    });
  } catch (error) {
    console.log(`Error setting cookie1: ${error}`);
  }

  try {
    await cookieStore.set({
      name: "cookie2",
      value: `cookie2-value`,
      partitioned: true,
    });
  } catch (error) {
    console.log(`Error setting cookie2: ${error}`);
  }

  // Log cookie names
  const cookieNames = (await cookieStore.getAll())
    .map((cookie) => cookie.name)
    .join(" ");
  console.log(`Initial cookies: ${cookieNames}`);
}
```

متد `cookieTest()` تابع `setTestCookies()` را فراخوانی می‌کند. سپس تلاش می‌کند کوکی‌های "cookie1" (با مشخص کردن نام آن) و "cookie2" (با مشخص کردن نام و `partitioned: true`) را حذف کند. سپس دوباره نام کوکی‌ها را فهرست می‌کند.

```js
async function cookieTest() {
  // Create our test cookies
  await setTestCookies();

  // Delete cookie1 specifying just the name
  try {
    await cookieStore.delete("cookie1");
  } catch (error) {
    console.log(`Error deleting cookie1: ${error}`);
  }

  // Delete cookie2, setting partitioned to true
  try {
    await cookieStore.delete({
      name: "cookie2",
      partitioned: true,
    });
  } catch (error) {
    console.log(`Error deleting cookie2: ${error}`);
  }

  // Log cookie names again (to show cookie1 deleted)
  cookieNames = (await cookieStore.getAll())
    .map((cookie) => cookie.name)
    .join(" ");
  console.log(
    `Cookies remaining after attempted deletions (cookie2 should be deleted): ${cookieNames}`,
  );
}

cookieTest();
```

هنگام اجرا، لاگ کنسول باید نشان دهد که هر دو "cookie1" و "cookie2" در ابتدا وجود دارند، اما "cookie2" پس از آن فهرست نمی‌شود. کوکی به نام "cookie1" همچنان وجود دارد زیرا با کوکی‌های مشخص‌شده در فراخوانی `delete()` مطابقت ندارد.

> [!NOTE]
> اگر هیچ کوکی‌ای مطابقت داده نشود، حذف بی‌صدا شکست می‌خورد.

### حذف کوکی‌های ایجادشده با استفاده از document.cookies

حذف کوکی‌ای که با استفاده از {{domxref("document.cookie")}} ایجاد شده است، الزامات مشابهی با حذف کوکی‌ای دارد که با استفاده از {{domxref("CookieStore.set()")}} ایجاد شده است: کوکی یا باید با `options` ارسال‌شده مطابقت داشته باشد، یا با `name` و گزینه‌های پیش‌فرض.

> [!NOTE]
> کوکی‌های ایجادشده با `set()` همیشه یک [مسیر پیش‌فرض](/en-US/docs/Web/HTTP/Guides/Cookies#define_where_cookies_are_sent) `/` دارند، در حالی که کوکی‌های ایجادشده با `document.cookie` مسیر پیش‌فرضی برابر با مسیر سندی که در آن ایجاد شده‌اند دارند. بنابراین هنگام حذف کوکی‌های ایجادشده با `document.cookie`، نمی‌توانید فرض کنید که مسیر `/` را دارند (مگر اینکه صریحاً چنین تنظیم شده باشد)، و در نتیجه نمی‌توانید فرض کنید که با گزینه‌های پیش‌فرض `delete()` مطابقت خواهد داشت.

کد زیر از `document.cookie` برای ایجاد کوکی‌های "doc_cookie1" و "doc_cookie2" با مسیرهای `/some_path` و `/` به ترتیب استفاده می‌کند و سپس هر دو کوکی را ثبت می‌کند. سپس کد هر دو کوکی را بدون مشخص کردن گزینه تطبیق `path` حذف می‌کند و دوباره کوکی‌ها را فهرست می‌کند.

```js
async function cookieTest() {
  // Create doc_cookie1 with path /some_path
  document.cookie =
    "doc_cookie1=doc_cookie1_name; SameSite=None; Secure; max-age=10; path='/some_path'";

  // Create doc_cookie2 with path / (the CookieStore.set() default)
  document.cookie =
    "doc_cookie2=doc_cookie2_name; SameSite=None; Secure; max-age=10; path=/";

  // Log cookie names
  let cookieNames = (await cookieStore.getAll())
    .map((cookie) => cookie.name)
    .join(" ");
  console.log(`Initial cookies: ${cookieNames}`);

  // Delete doc_cookie1 (should fail)
  try {
    await cookieStore.delete("doc_cookie1");
  } catch (error) {
    console.log(`Error deleting doc_cookie1: ${error}`);
  }

  // Delete doc_cookie2 (should succeed)
  try {
    await cookieStore.delete("doc_cookie2");
  } catch (error) {
    console.log(`Error deleting cookie2: ${error}`);
  }

  // Log cookie names again (to show cookie1 deleted)
  cookieNames = (await cookieStore.getAll())
    .map((cookie) => cookie.name)
    .join(" ");
  console.log(
    `Cookies remaining after attempted deletions (doc_cookie2 should be deleted): ${cookieNames}`,
  );
}

cookieTest();
```

هنگام اجرا، لاگ اول باید نشان دهد که هر دو کوکی وجود دارند. لاگ دوم نباید شامل "doc_cookie2" باشد، زیرا باید مطابقت داده شده و حذف شده باشد. همچنین باید شامل "doc_cookie1" باشد، زیرا `/some_path` با مسیر حذف پیش‌فرض (`/`) مطابقت نخواهد داشت.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}