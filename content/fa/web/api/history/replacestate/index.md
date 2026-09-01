---
title: "History: replaceState() method"
short-title: replaceState()
slug: Web/API/History/replaceState
page-type: web-api-instance-method
browser-compat: api.History.replaceState
---

{{APIRef("History API")}}

متد **`replaceState()`** از رابط {{domxref("History")}} ورودی فعلی تاریخچه را تغییر می‌دهد و آن را با شیء حالت (state object) و URL ارائه‌شده در پارامترهای متد جایگزین می‌کند. این متد به‌ویژه زمانی مفید است که بخواهید شیء حالت یا URL ورودی فعلی تاریخچه را در واکنش به برخی اقدامات کاربر به‌روزرسانی کنید.

## Syntax

```js-nolint
replaceState(state, unused)
replaceState(state, unused, url)
```

### Parameters

- `state`
  - : یک شیء که با ورودی تاریخچه مرتبط است و به متد `replaceState()` ارسال می‌شود. شیء حالت می‌تواند `null` باشد.
- `unused`
  - : این پارامتر به دلایل تاریخی وجود دارد و نمی‌توان آن را حذف کرد؛ ارسال رشته خالی سنتی است و در برابر تغییرات آینده متد بی‌خطر است.
- `url` {{optional_inline}}
  - : URL ورودی تاریخچه. URL جدید باید همان مبدأ (origin) URL فعلی باشد؛ در غیر این صورت متد `replaceState()` یک استثنا پرتاب می‌کند.

### Return value

هیچ ({{jsxref("undefined")}}).

### Exceptions

- `SecurityError` {{domxref("DOMException")}}
  - : اگر سند مرتبط کاملاً فعال (fully active) نباشد، یا پارامتر `url` ارائه‌شده یک URL معتبر نباشد، یا متد بیش از حد مکرر فراخوانی شود، پرتاب می‌شود.
- `DataCloneError` {{domxref("DOMException")}}
  - : اگر پارامتر `state` ارائه‌شده قابل سریال‌سازی نباشد، پرتاب می‌شود.

## Examples

فرض کنید `https://www.mozilla.org/foo.html` جاوااسکریپت زیر را اجرا می‌کند:

```js
const stateObj = { foo: "bar" };
history.pushState(stateObj, "", "bar.html");
```

در صفحه بعدی می‌توانید از `history.state` برای دسترسی به `stateObj` که به‌تازگی اضافه شده استفاده کنید.

توضیح این دو خط بالا را می‌توانید در مقاله [کار با History API](/en-US/docs/Web/API/History_API/Working_with_the_History_API#using_pushstate) بیابید. سپس فرض کنید `https://www.mozilla.org/bar.html` جاوااسکریپت زیر را اجرا می‌کند:

```js
history.replaceState(stateObj, "", "bar2.html");
```

این کار باعث می‌شود نوار آدرس `https://www.mozilla.org/bar2.html` را نمایش دهد، اما مرورگر `bar2.html` را بارگذاری نمی‌کند و حتی وجود آن را بررسی نمی‌کند.

حال فرض کنید کاربر به `https://www.microsoft.com` می‌رود و سپس دکمه «بازگشت» را کلیک می‌کند. در این مرحله، نوار آدرس `https://www.mozilla.org/bar2.html` را نمایش می‌دهد. اگر کاربر اکنون دوباره «بازگشت» را کلیک کند، نوار آدرس `https://www.mozilla.org/foo.html` را نمایش می‌دهد و کاملاً از bar.html عبور می‌کند.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}