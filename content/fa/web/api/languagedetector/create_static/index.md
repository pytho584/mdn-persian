---
title: "LanguageDetector: create() static method"
short-title: create()
slug: Web/API/LanguageDetector/create_static
page-type: web-api-static-method
status:
  - experimental
browser-compat: api.LanguageDetector.create_static
---

{{APIRef("Translator and Language Detector APIs")}}{{SeeCompatTable}}{{securecontext_header}}

متد ایستای **`create()`** از رابط {{domxref("LanguageDetector")}}، یک نمونه جدید `LanguageDetector` برای تشخیص زبان ایجاد می‌کند.

> [!NOTE]
> متد `create()` به [اعتبارگذاری گذرا](/en-US/docs/Glossary/Transient_activation) نیاز دارد؛ یعنی باید در پاسخ به کنش کاربر مانند کلیک ماوس یا فشردن دکمه فراخوانی شود.

## سینتکس

```js-nolint
LanguageDetector.create(options)
```

### پارامترها

- `options`
  - : یک شیء که گزینه‌های پیکربندی برای `LanguageDetector` را مشخص می‌کند. مقادیر ممکن عبارت‌اند از:
    - `expectedInputLanguages`
      - : آرایه‌ای از رشته‌ها که زبان‌های مورد انتظار متن ورودی را مشخص می‌کند و به بهبود دقت تشخیص زبان کمک می‌کند. این‌ها باید {{glossary("BCP 47 language tag", "BCP 47 language tags")}} معتبر باشند. مقدار پیش‌فرض `["en"]` است.
    - `monitor` {{optional_inline}}
      - : یک تابع بازخوان (callback) با آرگومان {{domxref("CreateMonitor")}} که نظارت بر پیشرفت دانلود مدل هوش مصنوعی را امکان‌پذیر می‌کند.
    - `signal` {{optional_inline}}
      - : یک نمونه از شیء {{domxref("AbortSignal")}} که امکان لغو عملیات `create()` را از طریق {{domxref("AbortController")}} مرتبط فراهم می‌کند. اثر دقیق آن به زمان فراخوانی {{domxref("AbortController.abort()")}} بستگی دارد:
        - اگر `abort()` پیش از resolve شدن پرامیس `create()` فراخوانی شود، عملیات `create()` لغو می‌شود.
        - اگر `abort()` پس از fulfilled شدن پرامیس `create()` فراخوانی شود، همان اثر فراخوانی {{domxref("LanguageDetector.destroy()")}} را دارد: منابع اختصاص‌یافته به نمونه `LanguageDetector` حاصل آزاد می‌شوند و تمام فراخوانی‌های متدهای `LanguageDetector`، چه در حال انجام و چه بعدی، با `AbortError` رد می‌شوند.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک نمونه شیء `LanguageDetector` برآورده می‌شود.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("Document")}} صفحه هنوز فعال نباشد، پرتاب می‌شود.
- `NetworkError` {{domxref("DOMException")}}
  - : اگر:
    - شبکه برای دانلود مدل هوش مصنوعی در دسترس نبود.
    - کاربر دانلود مدل هوش مصنوعی را لغو کرده باشد.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر:
    - استفاده از متد توسط {{httpheader('Permissions-Policy/language-detector','language-detector')}} در {{httpheader("Permissions-Policy")}} مسدود شده باشد.
    - کاربر به نحوی دانلود مدل هوش مصنوعی را مسدود کرده باشد.
    - متد `create()` از طریق {{glossary("transient activation")}} فراخوانی نشده باشد.
- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر:
    - برچسب‌های زبانی که در `expectedInputLanguages` مشخص شده‌اند نامعتبر یا پشتیبانی‌نشده باشند.
    - مدل هوش مصنوعی برای پشتیبانی از `expectedInputLanguages` مشخص‌شده در دسترس نباشد.
- `OperationError` {{domxref("DOMException")}}
  - : استثنای عمومی که اگر ایجاد `LanguageDetector` به هر دلیل دیگری با شکست مواجه شود، پرتاب می‌شود.

## مثال‌ها

### ایجاد پایه `LanguageDetector`

```js
const detector = await LanguageDetector.create({
  expectedInputLanguages: ["en-US", "zh"],
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از APIهای Translator و Language Detector](/en-US/docs/Web/API/Translator_and_Language_Detector_APIs/Using)