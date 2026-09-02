---
title: "Keyboard: lock() method"
short-title: lock()
slug: Web/API/Keyboard/lock
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.Keyboard.lock
---

{{APIRef("Keyboard API")}}{{SeeCompatTable}}{{securecontext_header}}

متد **`lock()`** در رابط {{domxref("Keyboard")}} یک {{jsxref('Promise')}} برمی‌گرداند که پس از فعال‌سازی ضبط (capture) فشار کلیدها برای همه یا برخی از کلیدهای صفحه‌کلید فیزیکی حل می‌شود. این متد فقط می‌تواند کلیدهایی را ضبط کند که توسط سیستم‌عامل زیرین دسترسی آن‌ها مجاز شده باشد.

اگر `lock()` چند بار فراخوانی شود، فقط کدهای کلیدی که در آخرین فراخوانی مشخص شده‌اند قفل خواهند شد. هر کلیدی که توسط فراخوانی قبلی `lock()` قفل شده باشد، از قفل خارج می‌شود.

## سینتکس

```js-nolint
lock()
lock(keyCodes)
```

### پارامترها

- `keyCodes` {{optional_inline}}
  - : یک {{jsxref('Array')}} شامل یک یا چند کد کلید برای قفل کردن. اگر هیچ کد کلیدی ارائه نشود، همه کلیدها قفل خواهند شد. فهرستی از مقادیر کد معتبر در مشخصات [UI Events KeyboardEvent code Values](https://w3c.github.io/uievents-code/#key-alphanumeric-writing-system) موجود است.

### مقدار بازگشتی

یک {{jsxref('Promise')}} که هنگام موفقیت قفل کردن، با {{jsxref('undefined')}} حل می‌شود.

### استثناها

- `AbortError` {{domxref("DOMException")}}
  - : اگر فراخوانی جدیدی از `lock()` قبل از اتمام فراخوانی فعلی انجام شود، پرتاب می‌شود.
- `InvalidAccessError` {{domxref("DOMException")}}
  - : اگر هر کلیدی در `keyCodes` یک [مقدار ویژگی کد کلید](https://w3c.github.io/uievents-code/#key-code-attribute-value) معتبر نباشد، پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر `lock()` در یک زمینه مرور سطح‌بالای فعال (active top-level browsing context) فراخوانی نشود، پرتاب می‌شود.

## امنیت

[فعال‌سازی کاربر موقت (Transient user activation)](/en-US/docs/Web/Security/Defenses/User_activation) الزامی است. کاربر باید با صفحه یا یک عنصر رابط کاربری تعامل کند تا این ویژگی کار کند.

## مثال‌ها

### ضبط همه کلیدها

مثال زیر همه فشارهای کلید را ضبط می‌کند.

```js
navigator.keyboard.lock();
```

### ضبط کلیدهای خاص

مثال زیر کلیدهای <kbd>W</kbd>، <kbd>A</kbd>، <kbd>S</kbd> و <kbd>D</kbd> را ضبط می‌کند. این کلیدها صرف‌نظر از اینکه از کدام اصلاح‌کننده‌ها (modifiers) همراه با فشار کلید استفاده شود، ضبط می‌شوند. با فرض چیدمان استاندارد آمریکایی QWERTY، ثبت `"KeyW"` تضمین می‌کند که <kbd>W</kbd>، <kbd>Shift</kbd>+<kbd>W</kbd>، <kbd>Control</kbd>+<kbd>W</kbd>، <kbd>Control</kbd>+<kbd>Shift</kbd>+<kbd>W</kbd> و همه ترکیب‌های دیگر اصلاح‌کننده‌ها با <kbd>W</kbd> به برنامه ارسال شوند. همین امر برای `"KeyA"`، `"KeyS"` و `"KeyD"` نیز صدق می‌کند.

```js
navigator.keyboard.lock(["KeyW", "KeyA", "KeyS", "KeyD"]);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}