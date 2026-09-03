---
title: "NavigationPrecommitController: redirect() method"
short-title: redirect()
slug: Web/API/NavigationPrecommitController/redirect
page-type: web-api-instance-method
browser-compat: api.NavigationPrecommitController.redirect
---

{{APIRef("Navigation API")}}

متد **`redirect()`** از رابط {{domxref("NavigationPrecommitController")}}، مرورگر را به یک URL مشخص تغییر مسیر می‌دهد و رفتار تاریخچه و هرگونه اطلاعات وضعیت موردنظر را تعیین می‌کند.

## سینتکس

```js-nolint
redirect(url, options)
```

### پارامترها

- `url`
  - : URL‌ای که باید به آن تغییر مسیر داده شود.
- `options` {{optional_inline}}
  - : یک شیء گزینه‌ها که ویژگی‌های آن می‌تواند شامل موارد زیر باشد:
    - `state` {{optional_inline}}
      - : حاوی هرگونه اطلاعات وضعیتی است که می‌خواهید همراه با پیمایش ارسال کنید؛ مثلاً برای اهداف ثبت وقایع یا ردیابی. مقدار آن می‌تواند از هر نوعی باشد. وضعیت این پیمایش را می‌توانید بعداً با متد {{domxref("NavigationHistoryEntry.getState()")}} روی مدخل تاریخچهٔ حاصل بازیابی کنید.
    - `history` {{optional_inline}}
      - : یک مقدار شمارشی است که مشخص می‌کند این تغییر مسیر چگونه باید به تاریخچه پیمایش اضافه شود و می‌تواند یکی از مقادیر زیر را داشته باشد:
        - `auto`
          - : مقدار پیش‌فرض، که به مرورگر اجازه می‌دهد تصمیم بگیرد چگونه با آن رفتار کند:
            - اگر پیمایش اصلی در نتیجهٔ فراخوانی {{domxref("Navigation.navigate()")}} رخ داده باشد، مقدار استفاده‌شده همانی خواهد بود که در گزینهٔ [`history`](/en-US/docs/Web/API/Navigation/navigate#history) فراخوانیِ `navigate()` تعیین شده است.
            - در غیر این صورت، مقدار استفاده‌شده معمولاً `push` خواهد بود؛ اما اگر تغییر مسیر به همان URL پیش از پیمایش اشاره کند، به `replace` تبدیل می‌شود.
        - `push`
          - : یک {{domxref("NavigationHistoryEntry")}} جدید به تاریخچه پیمایش اضافه می‌کند و هر پیمایشِ رو به جلوی موجود را پاک می‌کند (یعنی اگر کاربر قبلاً به مکان‌های دیگری رفته و سپس با دکمهٔ «بازگشت» در تاریخچه به عقب برگشته باشد، قبل از شروع پیمایشی که باعث تغییر مسیر شده، آن پیمایش‌های رو به جلو حذف می‌شوند).
        - `replace`
          - : {{domxref("Navigation.currentEntry")}} را با `NavigationHistoryEntry` جدیدِ حاصل جایگزین می‌کند.

> [!NOTE]
> متد `redirect()` می‌تواند رفتار تاریخچه را بین `auto`، `push` و `replace` تغییر دهد، اما نمی‌تواند یک پیمایش `traverse` را به پیمایش `push`/`replace` تبدیل کند و بالعکس.

### مقدار بازگشتی

هیچ مقداری بازگردانده نمی‌شود (`undefined`).

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : در موارد زیر پرتاب می‌شود:
    - {{domxref("NavigateEvent")}} آغازگر رهگیری نشده باشد.
    - {{domxref("NavigateEvent.navigationType")}} برابر با `push` یا `replace` نباشد.
- `SyntaxError` {{domxref("DOMException")}}
  - : اگر `url` مشخص‌شده نامعتبر باشد پرتاب می‌شود.
- `SecurityError` {{domxref("DOMException")}}
  - : اگر سند جاری نتواند URL خود را به `url` تغییر مسیر داده‌شده بازنویسی کند، پرتاب می‌شود.

## مثال‌ها

برای مشاهدهٔ مثال، به صفحهٔ اصلی {{domxref("NavigationPrecommitController")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [مسیریابی مدرن سمت کلاینت: Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)