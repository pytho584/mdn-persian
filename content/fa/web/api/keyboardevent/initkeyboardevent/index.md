---
title: "KeyboardEvent: initKeyboardEvent() method"
short-title: initKeyboardEvent()
slug: Web/API/KeyboardEvent/initKeyboardEvent
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.KeyboardEvent.initKeyboardEvent
---

{{APIRef("UI Events")}}{{Deprecated_Header}}

متد **`KeyboardEvent.initKeyboardEvent()`** ویژگی‌های یک شیء رویداد صفحه‌کلید را مقداردهی اولیه می‌کند. این متد در پیش‌نویس DOM Level 3 Events معرفی شد، اما در پیش‌نویس جدیدتر منسوخ (deprecated) اعلام گردید. Gecko از این ویژگی پشتیبانی نخواهد کرد، زیرا پیاده‌سازی این متد به صورت آزمایشی باعث خراب شدن برنامه‌های وب موجود شد (به [اشکال ۹۹۹۶۴۵ فایرفاکس](https://bugzil.la/999645) مراجعه کنید). برنامه‌های وب باید در صورت در دسترس بودن، به جای این متد از سازنده (constructor) استفاده کنند.

## نحو (Syntax)

```js-nolint
initKeyboardEvent(type, canBubble, cancelable,
                  view, key, location, ctrlKey,
                  altKey, shiftKey, metaKey)
```

### پارامترها

- `type`
  - : نوع رویداد صفحه‌کلید؛ مرورگرها همیشه آن را روی یکی از مقادیر `keydown`، `keypress` یا `keyup` تنظیم می‌کنند.
- `canBubble` {{optional_inline}}
  - : مشخص می‌کند که آیا رویداد می‌تواند بالا برود (bubble) یا خیر. پیش‌فرض `false` است.
- `cancelable` {{optional_inline}}
  - : مشخص می‌کند که آیا رویداد قابل لغو شدن است یا خیر. پیش‌فرض `false` است.
- `view` {{optional_inline}}
  - : {{glossary("WindowProxy")}} ای که با آن مرتبط است. پیش‌فرض `null` است.
- `key` {{optional_inline}}
  - : مقدار ویژگی key. پیش‌فرض `""` است.
- `location` {{optional_inline}}
  - : مقدار ویژگی location. پیش‌فرض `0` است.
- `ctrlKey` {{optional_inline}}
  - : مشخص می‌کند که کلید اصلاح‌گر control فعال است یا خیر. پیش‌فرض `false` است.
- `altKey` {{optional_inline}}
  - : مشخص می‌کند که کلید اصلاح‌گر alt فعال است یا خیر. پیش‌فرض `false` است.
- `shiftKey` {{optional_inline}}
  - : مشخص می‌کند که کلید اصلاح‌گر shift فعال است یا خیر. پیش‌فرض `false` است.
- `metaKey` {{optional_inline}}
  - : مشخص می‌کند که کلید اصلاح‌گر meta فعال است یا خیر. پیش‌فرض `false` است.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مشخصات

{{Specifications}}

مشخصات رابط `KeyboardEvent` نسخه‌های پیش‌نویس متعددی را پشت سر گذاشت؛ ابتدا در DOM Events Level 2 که به دلیل عدم توافق کنار گذاشته شد و سپس در DOM Events Level 3. این امر منجر به پیاده‌سازی متدهای مقداردهی اولیه غیراستاندارد شد: نسخه اولیه DOM Events Level 2 با نام `KeyboardEvent.initKeyEvent()` توسط مرورگرهای Gecko و نسخه اولیه DOM Events Level 3 با نام `KeyboardEvent.initKeyboardEvent()` توسط سایر مرورگرها. هر دوی اینها با استفاده مدرن از یک سازنده به نام {{domxref("KeyboardEvent.KeyboardEvent", "KeyboardEvent()")}} جایگزین شده‌اند.

## سازگاری با مرورگر

{{Compat}}
```