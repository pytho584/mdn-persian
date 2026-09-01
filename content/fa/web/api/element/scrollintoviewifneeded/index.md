---
title: "Element: scrollIntoViewIfNeeded() method"
short-title: scrollIntoViewIfNeeded()
slug: Web/API/Element/scrollIntoViewIfNeeded
page-type: web-api-instance-method
status:
  - non-standard
browser-compat: api.Element.scrollIntoViewIfNeeded
---

{{APIRef("DOM")}}{{Non-standard_header}}

روش **`Element.scrollIntoViewIfNeeded()`** عنصر جاری را به ناحیهٔ قابل مشاهدهٔ پنجرهٔ مرورگر اسکرول می‌کند اگر قبلاً در آن ناحیه نباشد. اگر عنصر از قبل در ناحیهٔ قابل مشاهده باشد، هیچ اسکرولی انجام نمی‌شود. این روش یک نوع اختصاصی از روش استاندارد [`Element.scrollIntoView()`](/en-US/docs/Web/API/Element/scrollIntoView) است.

## نحو

```js-nolint
scrollIntoViewIfNeeded()
scrollIntoViewIfNeeded(centerIfNeeded)
```

### پارامترها

- `centerIfNeeded` {{optional_inline}}
  - : یک مقدار بولی اختیاری با پیش‌فرض `true`:
    - اگر `true` باشد، عنصر به گونه‌ای تراز می‌شود که در مرکز ناحیهٔ قابل مشاهدهٔ جد اسکرول‌پذیر قرار گیرد.
    - اگر `false` باشد، عنصر به نزدیک‌ترین لبهٔ ناحیهٔ قابل مشاهدهٔ جد اسکرول‌پذیر تراز می‌شود. بسته به اینکه کدام لبهٔ ناحیهٔ قابل مشاهده به عنصر نزدیک‌تر است، یا بالای عنصر با لبهٔ بالایی ناحیهٔ قابل مشاهده تراز می‌شود، یا لبهٔ پایینی عنصر با لبهٔ پایینی ناحیهٔ قابل مشاهده تراز می‌شود.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

```js
const element = document.getElementById("my-el");

element.scrollIntoViewIfNeeded(); // Centers the element in the visible area
element.scrollIntoViewIfNeeded(false); // Aligns the element to the nearest edge in the visible area
```

## مشخصات

بخشی از هیچ مشخصه‌ای نیست. این یک روش اختصاصی و مخصوص WebKit است.

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [اشکال W3C CSSOM شماره 17152: پشتیبانی از مرکز کردن یک عنصر هنگام اسکرول به درون نما](https://www.w3.org/Bugs/Public/show_bug.cgi?id=17152) (درخواست ویژگی برای یک معادل استاندارد شده برای `scrollIntoViewIfNeeded`)