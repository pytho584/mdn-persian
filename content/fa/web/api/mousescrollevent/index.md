---
title: "MouseScrollEvent"
---

---
title: MouseScrollEvent
slug: Web/API/MouseScrollEvent
page-type: web-api-interface
status:
  - deprecated
  - non-standard
browser-compat: api.MouseScrollEvent
---

{{APIRef("UI Events")}}{{ Non-standard_Header }}{{Deprecated_Header}}

اینترفیس **`MouseScrollEvent`** رویدادهایی را نشان می‌دهد که در اثر حرکت چرخ ماوس یا وسیله ورودی مشابه توسط کاربر رخ می‌دهند.

> [!WARNING]
> از این اینترفیس برای رویدادهای چرخ (wheel) استفاده نکنید.
>
> مانند `MouseWheelEvent`، این اینترفیس غیراستاندارد و منسوخ است. فقط در مرورگرهای مبتنی بر Gecko استفاده می‌شد. در عوض از استاندارد _{{domxref("WheelEvent")}}_ استفاده کنید.

## نمای کلی متدها

```webidl
void initMouseScrollEvent(
  in DOMString typeArg,
  in boolean canBubbleArg,
  in boolean cancelableArg,
  in nsIDOMAbstractView viewArg,
  in long detailArg,
  in long screenXArg,
  in long screenYArg,
  in long clientXArg,
  in long clientYArg,
  in boolean ctrlKeyArg,
  in boolean altKeyArg,
  in boolean shiftKeyArg,
  in boolean metaKeyArg,
  in unsigned short buttonArg,
  in nsIDOMEventTarget relatedTargetArg,
  in long axis);
```

## ویژگی‌ها

| ویژگی                       | نوع    | توضیحات                          |
| --------------------------- | ------ | --------------------------------- |
| `axis` {{ReadOnlyInline}}   | `long` | جهت اسکرول را نشان می‌دهد.        |

## ثابت‌ها

### حالت‌های دلتا

| ثابت               | مقدار   | توضیحات                                    |
| ------------------ | ------- | ------------------------------------------- |
| `HORIZONTAL_AXIS`  | `0x01`  | رویداد در اثر چرخش افقی چرخ ایجاد شده است.  |
| `VERTICAL_AXIS`    | `0x02`  | رویداد در اثر چرخش عمودی چرخ ایجاد شده است. |

## روش‌های نمونه

- `initMouseScrollEvent()`
  - : به `nsIDOMMouseScrollEvent::initMouseScrollEvent()` مراجعه کنید.

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- `DOMMouseScroll`
- `MozMousePixelScroll`
- شیء استاندارد رویداد چرخ ماوس: {{ domxref("WheelEvent") }}