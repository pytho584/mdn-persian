---
title: "MouseEvent: MouseEvent() constructor"
short-title: MouseEvent()
slug: Web/API/MouseEvent/MouseEvent
page-type: web-api-constructor
browser-compat: api.MouseEvent.MouseEvent
---

{{APIRef("Pointer Events")}}

سازندهٔ **`MouseEvent()`** یک شیء جدید از نوع {{domxref("MouseEvent")}} می‌سازد.

## سینتکس

```js-nolint
new MouseEvent(type)
new MouseEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای شامل نام رویداد. این مقدار به بزرگی و کوچکی حروف حساس است و مرورگرها آن را روی `click`، `dblclick`، `mousedown`، `mouseenter`، `mouseleave`، `mousemove`، `mouseout`، `mouseover` یا `mouseup` تنظیم می‌کنند.
- `options` {{optional_inline}}
  - : شیئی که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("UIEvent/UIEvent", "UIEvent()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `screenX` {{optional_inline}}
      - : عددی با پیش‌فرض `0` که موقعیت افقی رویداد ماوس را روی صفحه‌نمایش کاربر مشخص می‌کند؛ تنظیم این مقدار، نشانگر ماوس را حرکت نمی‌دهد.
    - `screenY` {{optional_inline}}
      - : عددی با پیش‌فرض `0` که موقعیت عمودی رویداد ماوس را روی صفحه‌نمایش کاربر مشخص می‌کند؛ تنظیم این مقدار، نشانگر ماوس را حرکت نمی‌دهد.
    - `clientX` {{optional_inline}}
      - : عددی با پیش‌فرض `0` که موقعیت افقی رویداد ماوس را روی پنجرهٔ کلاینت (client window) صفحه‌نمایش کاربر مشخص می‌کند؛ تنظیم این مقدار، نشانگر ماوس را حرکت نمی‌دهد.
    - `clientY` {{optional_inline}}
      - : عددی با پیش‌فرض `0` که موقعیت عمودی رویداد ماوس را روی پنجرهٔ کلاینت (client window) صفحه‌نمایش کاربر مشخص می‌کند؛ تنظیم این مقدار، نشانگر ماوس را حرکت نمی‌دهد.
    - `ctrlKey` {{optional_inline}}
      - : مقدار بولی که مشخص می‌کند آیا کلید <kbd>ctrl</kbd> هم‌زمان فشرده شده است. پیش‌فرض آن `false` است.
    - `shiftKey` {{optional_inline}}
      - : مقدار بولی که مشخص می‌کند آیا کلید <kbd>shift</kbd> هم‌زمان فشرده شده است. پیش‌فرض آن `false` است.
    - `altKey` {{optional_inline}}
      - : مقدار بولی که مشخص می‌کند آیا کلید <kbd>alt</kbd> هم‌زمان فشرده شده است. پیش‌فرض آن `false` است.
    - `metaKey` {{optional_inline}}
      - : مقدار بولی که مشخص می‌کند آیا کلید <kbd>meta</kbd> هم‌زمان فشرده شده است. پیش‌فرض آن `false` است.
    - `button` {{optional_inline}}
      - : عددی با پیش‌فرض `0` که مشخص می‌کند هنگام رویدادهای مربوط به فشردن یا رها کردن دکمه، کدام دکمه فشرده شده است:

        | مقدار | معنی                                                          |
        | ----- | ------------------------------------------------------------- |
        | `0`   | دکمهٔ اصلی فشرده شده (معمولاً دکمهٔ چپ) یا مقداردهی‌نشده       |
        | `1`   | دکمهٔ کمکی فشرده شده (معمولاً دکمهٔ وسط)                       |
        | `2`   | دکمهٔ ثانویه فشرده شده (معمولاً دکمهٔ راست)                    |

    - `buttons` {{optional_inline}}
      - : عددی با پیش‌فرض `0` که مشخص می‌کند هنگام صدور رویداد کدام دکمه‌ها فشرده شده‌اند:

        | مقدار بیت‌فیلد | معنی                                                |
        | -------------- | --------------------------------------------------- |
        | `0`            | هیچ دکمه‌ای فشرده نشده است                          |
        | `1`            | دکمهٔ اصلی فشرده شده (معمولاً دکمهٔ چپ)              |
        | `2`            | دکمهٔ ثانویه فشرده شده (معمولاً دکمهٔ راست)          |
        | `4`            | دکمهٔ کمکی فشرده شده (معمولاً دکمهٔ وسط)             |

    - `relatedTarget` {{optional_inline}}
      - : یک {{domxref("EventTarget")}} با پیش‌فرض `null` که عنصری است که به‌تازگی از آن خارج شده‌ایم (در صورت رخداد {{domxref("Element/mouseenter_event", "mouseenter")}} یا {{domxref("Element/mouseover_event", "mouseover")}}) یا عنصری است که در حال ورود به آن هستیم (در صورت رخداد {{domxref("Element/mouseout_event", "mouseout")}} یا {{domxref("Element/mouseleave_event", "mouseleave")}}).
    - `region` {{non-standard_inline}} {{optional_inline}}
      - : رشته‌ای با پیش‌فرض `null` که شناسهٔ ناحیهٔ برخورد (hit region) متأثر از رویداد است. نبود هر ناحیهٔ برخورد متأثری با مقدار `null` نمایش داده می‌شود.

    در برخی پیاده‌سازی‌ها، پاس دادن هر چیزی به‌جز عدد برای فیلدهای screen و client باعث پرتاب شدن {{jsxref("TypeError")}} می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## جستارهای وابسته

- {{domxref("MouseEvent")}}، رابط اشیایی که این سازنده می‌سازد.