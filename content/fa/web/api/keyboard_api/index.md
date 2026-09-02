---
title: "Keyboard API"
---

---
title: Keyboard API
slug: Web/API/Keyboard_API
page-type: web-api-overview
status:
  - experimental
browser-compat:
  - api.Keyboard
  - api.KeyboardLayoutMap
spec-urls:
  - https://wicg.github.io/keyboard-lock/
  - https://wicg.github.io/keyboard-map/
---

{{SeeCompatTable}}{{DefaultAPISidebar("Keyboard API")}}

رابط برنامه‌نویسی Keyboard API متدهایی را برای کار با یک صفحه‌کلید فیزیکی که به دستگاهی در حال اجرای مرورگر متصل است، فراهم می‌کند.

این API چندین قابلیت را فراهم می‌کند. _نگاشت صفحه‌کلید_ (Keyboard mapping) یک رابط برای بازیابی رشته‌ای که توسط یک کلید فیزیکی خاص روی صفحه‌کلید تولید می‌شود، فراهم می‌کند تا آن کلید به‌درستی برای کاربر شناسایی شود. _قفل کردن صفحه‌کلید_ (Keyboard locking) به یک صفحهٔ وب امکان می‌دهد کلیدهایی را که معمولاً توسط عامل کاربر یا سیستم‌عامل زیرین رزرو شده‌اند، ضبط کند. کاربرد مورد نظر Keyboard API برای برنامه‌های وب مانند بازی‌ها یا برنامه‌های دسترسی از راه دور است که یک تجربهٔ تمام‌صفحه و همه‌جانبه ارائه می‌دهند.

## مفاهیم و کاربرد

### نگاشت صفحه‌کلید

در صفحه‌کلیدهای فیزیکی، ویژگی `code` حاوی موقعیت فیزیکی کلیدی است که فشرده شده و ویژگی `key` حاوی رشته‌ای است که با فشردن کلید در آن موقعیت فیزیکی روی صفحه‌کلید تولید می‌شود. مقدار `key` زبان محلی صفحه‌کلید (مثلاً 'en-US')، چیدمان (مثلاً 'QWERTY') و وضعیت کلیدهای اصلاح‌کننده (<kbd>Shift</kbd>، <kbd>Control</kbd> و غیره) را در نظر می‌گیرد. از نظر تاریخی، هیچ راهی برای بازیابی این اطلاعات وجود نداشته است.

رابط برنامه‌نویسی نگاشت صفحه‌کلید (Keyboard Map API) راهی برای بازیابی رشتهٔ تولیدشده توسط فشردن یک کلید خاص از طریق رابط {{domxref('Keyboard')}} و رابط {{domxref('KeyboardLayoutMap')}} فراهم می‌کند. به رابط {{domxref('Keyboard')}} از طریق {{domxref('navigator.keyboard')}} دسترسی پیدا می‌شود. رابط {{domxref('Keyboard')}} متد {{domxref('Keyboard.getLayoutMap')}} را فراهم می‌کند که یک promise برمی‌گرداند و با یک شیء {{domxref('KeyboardLayoutMap')}} حل می‌شود؛ این شیء شامل اعضایی برای تبدیل کدها به کلیدها است. فهرست مقادیر کد معتبر در بخش [Writing System Keys](https://w3c.github.io/uievents-code/#key-alphanumeric-writing-system) از مشخصات [UI Events KeyboardEvent code Values](https://w3c.github.io/uievents-code/) یافت می‌شود.

مثال زیر نشان می‌دهد که چگونه رشتهٔ مخصوص موقعیت یا مخصوص چیدمان مرتبط با کلید برچسب‌خورده با <kbd>W</kbd> را در یک صفحه‌کلید انگلیسی QWERTY دریافت کنید.

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

صفحات وب بسیار تعاملی، بازی‌ها و تجربه‌های پخش از راه دور اغلب در حالت تمام‌صفحه به دسترسی به کلیدهای ویژه و میانبرهای صفحه‌کلید نیاز دارند. نمونه‌هایی از این کلیدها/ترکیب کلیدها عبارت‌اند از <kbd>Escape</kbd>، <kbd>Alt+Tab</kbd> و <kbd>Ctrl+N</kbd>. این کلیدها و ترکیب کلیدها معمولاً توسط عامل کاربر یا سیستم‌عامل زیرین گرفته می‌شوند، همانطور که در مثال زیر نشان داده شده است.

برای گرفتن کلیدهای <kbd>W</kbd>، <kbd>A</kbd>، <kbd>S</kbd> و <kbd>D</kbd>، متد `lock()` را با فهرستی که مقدار ویژگی کد کلید را برای هر یک از این کلیدها دارد فراخوانی کنید:

```js
navigator.keyboard.lock(["KeyW", "KeyA", "KeyS", "KeyD"]);
```

این کار این کلیدها را بدون توجه به اینکه کدام اصلاح‌کننده‌ها با فشردن کلید استفاده شوند، می‌گیرد. با فرض چیدمان استاندارد QWERTY ایالات متحده، ثبت `KeyW` تضمین می‌کند که <kbd>W</kbd>، <kbd>Shift+W</kbd>، <kbd>Control+W</kbd>، <kbd>Control+Shift+W</kbd> و تمام ترکیب‌های دیگر کلید با اصلاح‌کننده به همراه <kbd>W</kbd> به برنامه ارسال شوند. همین امر در مورد `KeyA`، `KeyS` و `KeyD` نیز صدق می‌کند.

### کلیدهای سیستم نوشتاری

کدهایی که به {{domxref('Keyboard.lock')}} و به روش‌های مختلف رابط {{domxref('KeyboardLayoutMap')}} ارسال می‌شوند، «کلیدهای سیستم نوشتاری» نامیده می‌شوند.

«کلیدهای سیستم نوشتاری» در بخش [Writing System Keys](https://w3c.github.io/uievents-code/#key-alphanumeric-writing-system) از مشخصات [UI Events KeyboardEvent code Values](https://w3c.github.io/uievents-code/) تعریف شده‌اند، زیرا کلیدهای فیزیکی بر اساس زبان محلی و چیدمان صفحه‌کلید فعلی معنا را تغییر می‌دهند. این کلیدها در زیر نشان داده شده‌اند. کلیدهای آبی روی همهٔ صفحه‌کلیدهای استاندارد وجود دارند، در حالی که کلیدهای سبز فقط روی برخی صفحه‌کلیدها در دسترس هستند.

![Writing system keys as defined by the UI Events KeyboardEvent code Values spec.](writing-system-keys.png)

## رابط‌ها

- {{domxref('Keyboard')}} {{experimental_inline}}
  - : توابعی را فراهم می‌کند که نقشه‌های چیدمان صفحه‌کلید را بازیابی کرده و وضعیت ضبط فشردن کلیدها از صفحه‌کلید فیزیکی را تغییر می‌دهند.
- {{domxref('KeyboardLayoutMap')}} {{experimental_inline}}
  - : یک شیء شبیه به نقشه با توابعی برای بازیابی رشتهٔ مرتبط با کلیدهای فیزیکی خاص.

### توسعه‌های اعمال‌شده بر رابط‌های دیگر

- {{domxref('navigator.keyboard')}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک شیء {{domxref('Keyboard')}} برمی‌گرداند که دسترسی به توابعی را فراهم می‌کند که نقشه‌های چیدمان صفحه‌کلید را بازیابی کرده و وضعیت ضبط فشردن کلیدها از صفحه‌کلید فیزیکی را تغییر می‌دهند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}