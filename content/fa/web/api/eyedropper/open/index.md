---
title: "EyeDropper: open() method"
---

---
title: "EyeDropper: open() method"
short-title: open()
slug: Web/API/EyeDropper/open
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.EyeDropper.open
---

{{securecontext_header}}{{APIRef("EyeDropper API")}}{{SeeCompatTable}}

متد **`EyeDropper.open()`** حالت قطره‌چکان را آغاز می‌کند و یک {{jsxref("Promise")}} برمی‌گرداند که پس از انتخاب رنگ توسط کاربر و خروج از حالت قطره‌چکان، برآورده (fulfilled) می‌شود.

## نحو

```js-nolint
open()
open(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شیء گزینه‌ها برای ارسال سیگنال {{domxref("AbortSignal")}}:
    - `signal` {{optional_inline}}
      - : یک {{domxref("AbortSignal")}}. هرگاه متد {{domxref("AbortController/abort()", "abort()")}} متعلق به این `AbortSignal` فراخوانی شود، حالت قطره‌چکان لغو خواهد شد.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که وقتی کاربر رنگی را از صفحه انتخاب کند، در نهایت resolve می‌شود.

این Promise به شیئی با ویژگی زیر resolve می‌شود:

- `sRGBHex`
  - : رشته‌ای که رنگ انتخاب‌شده را در قالب sRGB هگزادسیمال (`#aabbcc`) نمایش می‌دهد.

### استثناها

استثناها پرتاب نمی‌شوند، بلکه هنگام رد شدن (reject) {{jsxref("Promise")}} بازگردانده می‌شوند.

- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر `open()` از طریق یک [فعال‌سازی گذرای کاربر](/en-US/docs/Glossary/Transient_activation) فراخوانی نشود، رخ می‌دهد.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر یک قطره‌چکان دیگر از قبل باز شده باشد، رخ می‌دهد.
- `AbortError` {{domxref("DOMException")}}
  - : اگر کاربر با فشردن کلید <kbd>Esc</kbd> انتخاب را لغو کند، یا اگر انتخاب توسط یک {{domxref("AbortController")}} که به عنوان آرگومان به `open()` ارسال شده، لغو شود، رخ می‌دهد.
- `OperationError` {{domxref("DOMException")}}
  - : اگر انتخاب به دلایل دیگری با شکست مواجه شود، رخ می‌دهد.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- رابط {{DOMxRef("EyeDropper")}} که این متد به آن تعلق دارد.