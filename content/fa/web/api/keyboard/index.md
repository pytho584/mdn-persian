---
title: Keyboard
slug: Web/API/Keyboard
page-type: web-api-interface
status:
  - experimental
browser-compat: api.Keyboard
---

{{SeeCompatTable}}{{APIRef("Keyboard API")}}{{securecontext_header}}

رابط **`Keyboard`** در {{domxref("Keyboard API", "", "", "nocode")}} توابعی را فراهم می‌کند که نقشه‌های چیدمان صفحه‌کلید را بازیابی می‌کنند و ضبط فشردن کلیدها از صفحه‌کلید فیزیکی را روشن یا خاموش می‌کنند.

فهرستی از مقادیر کد معتبر در مشخصات [UI Events KeyboardEvent code Values](https://w3c.github.io/uievents-code/) آمده است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_همچنین ویژگی‌های رابط والد خود، یعنی {{DOMxRef("EventTarget")}} را به ارث می‌برد._

## متدهای نمونه

_همچنین متدهای رابط والد خود، یعنی {{DOMxRef("EventTarget")}} را به ارث می‌برد._

- {{domxref('Keyboard.getLayoutMap()')}} {{experimental_inline}}
  - : یک {{jsxref('Promise')}} برمی‌گرداند که با یک نمونه از {{domxref('KeyboardLayoutMap')}} حل می‌شود؛ این نمونه یک شیء شبیه به نقشه است و توابعی برای بازیابی رشته‌های مرتبط با کلیدهای فیزیکی خاص دارد.
- {{domxref('Keyboard.lock()')}} {{experimental_inline}}
  - : یک {{jsxref('Promise')}} برمی‌گرداند که پس از فعال‌سازی ضبط فشردن کلیدها برای هر یک یا همه کلیدهای صفحه‌کلید فیزیکی حل می‌شود.
- {{domxref('Keyboard.unlock()')}} {{experimental_inline}}
  - : همه کلیدهایی را که توسط متد `lock()` ضبط شده‌اند آزاد می‌کند و به صورت همزمان برمی‌گردد.

## مثال

### نگاشت صفحه‌کلید

مثال زیر نشان می‌دهد که چگونه می‌توان رشته مخصوص مکان یا چیدمان مرتبط با کلیدی را که با کلید «W» در صفحه‌کلید انگلیسی QWERTY متناظر است، به دست آورد.

```js
if (navigator.keyboard) {
  const keyboard = navigator.keyboard;
  keyboard.getLayoutMap().then((keyboardLayoutMap) => {
    const upKey = keyboardLayoutMap.get("KeyW");
    window.alert(`Press ${upKey} to move up.`);
  });
} else {
  // Do something else.
}
```

### قفل کردن صفحه‌کلید

مثال زیر کلیدهای <kbd>W</kbd>، <kbd>A</kbd>، <kbd>S</kbd> و <kbd>D</kbd> را ضبط می‌کند؛ برای این کار `lock()` را با فهرستی شامل مقدار ویژگی کد کلید برای هر یک از این کلیدها فراخوانی کنید:

```js
navigator.keyboard.lock(["KeyW", "KeyA", "KeyS", "KeyD"]);
```

این کار این کلیدها را بدون توجه به اینکه کدام اصلاح‌کننده‌ها با فشردن کلید استفاده شوند، ضبط می‌کند. با فرض چیدمان استاندارد آمریکایی QWERTY، ثبت `KeyW` تضمین می‌کند که <kbd>W</kbd>، <kbd>Shift+W</kbd>، <kbd>Control+W</kbd>، <kbd>Control+Shift+W</kbd> و همه ترکیب‌های دیگر اصلاح‌کننده‌ها با <kbd>W</kbd> به برنامه ارسال شوند. همین امر در مورد `KeyA`، `KeyS` و `KeyD` نیز صدق می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}