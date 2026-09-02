---
title: "MouseEvent: mozInputSource property"
short-title: mozInputSource
slug: Web/API/MouseEvent/mozInputSource
page-type: web-api-instance-property
status:
  - non-standard
---

{{APIRef("Pointer Events")}} {{ Non-standard_header() }}

ویژگی فقط‌خواندنی **`MouseEvent.mozInputSource`** در {{domxref("MouseEvent")}} اطلاعاتی در مورد نوع دستگاهی که رویداد را تولید کرده است فراهم می‌کند. این به شما امکان می‌دهد، برای مثال، تشخیص دهید که یک رویداد ماوس توسط یک ماوس واقعی تولید شده است یا توسط یک رویداد لمسی (که ممکن است بر دقت تفسیر مختصات مرتبط با رویداد تأثیر بگذارد).

## مقدار

مقادیر زیر امکان‌پذیر هستند.

| نام ثابت               | مقدار | توضیحات                                            |
| ---------------------- | ----- | -------------------------------------------------- |
| `MOZ_SOURCE_UNKNOWN`   | 0     | دستگاه ورودی ناشناخته است.                         |
| `MOZ_SOURCE_MOUSE`     | 1     | رویداد توسط یک ماوس (یا دستگاه مشابه ماوس) تولید شده است. |
| `MOZ_SOURCE_PEN`       | 2     | رویداد توسط یک قلم روی تبلت تولید شده است.         |
| `MOZ_SOURCE_ERASER`    | 3     | رویداد توسط یک پاک‌کن روی تبلت تولید شده است.      |
| `MOZ_SOURCE_CURSOR`    | 4     | رویداد توسط یک نشانگر تولید شده است.               |
| `MOZ_SOURCE_TOUCH`     | 5     | رویداد روی یک رابط لمسی تولید شده است.             |
| `MOZ_SOURCE_KEYBOARD`  | 6     | رویداد توسط یک صفحه‌کلید تولید شده است.            |

## مشخصات

جزء هیچ مشخصه‌ای نیست.

## همچنین ببینید

- {{ domxref("MouseEvent") }}