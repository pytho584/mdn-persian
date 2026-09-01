---
title: "GeolocationPositionError"
---

{{securecontext_header}}{{APIRef("Geolocation API")}}

**`GeolocationPositionError`** یک واسط (interface) است که دلیل بروز خطا هنگام استفاده از دستگاه موقعیت‌یابی را نشان می‌دهد.

## ویژگی‌های نمونه (Instance properties)

واسط `GeolocationPositionError` هیچ ویژگی را به ارث نمی‌برد.

- {{domxref("GeolocationPositionError.code")}} {{ReadOnlyInline}}
  - : یک عدد صحیح بدون علامت (`unsigned short`) برمی‌گرداند که کد خطا را نشان می‌دهد. مقادیر ممکن به صورت زیر هستند:

    | مقدار | ثابت مرتبط              | توضیحات                                                                                                                                                                                                                            |
    | ----- | ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | `1`   | `PERMISSION_DENIED`     | دریافت اطلاعات موقعیت جغرافیایی به دلیل نداشتن مجوزهای لازم ناموفق بود، مثلاً به دلیل مسدود شدن توسط [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy).                                                              |
    | `2`   | `POSITION_UNAVAILABLE`  | دریافت موقعیت جغرافیایی به دلیل بازگشت خطای داخلی از حداقل یک منبع داخلی موقعیت، ناموفق بود.                                                                                                                                        |
    | `3`   | `TIMEOUT`               | زمان مجاز برای دریافت موقعیت جغرافیایی پیش از به‌دست آمدن اطلاعات به پایان رسید.                                                                                                                                                    |

- {{domxref("GeolocationPositionError.message")}} {{ReadOnlyInline}}
  - : یک رشته (string) قابل خواندن برای انسان برمی‌گرداند که جزئیات خطا را توضیح می‌دهد. مشخصات (specifications) ذکر می‌کنند که این ویژگی عمدتاً برای اهداف اشکال‌زدایی (debugging) در نظر گرفته شده است و نباید مستقیماً در رابط کاربری نمایش داده شود.

## روش‌های نمونه (Instance methods)

واسط `GeolocationPositionError` هیچ روشی را پیاده‌سازی یا به ارث نمی‌برد.

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید

- [استفاده از API موقعیت جغرافیایی](/en-US/docs/Web/API/Geolocation_API/Using_the_Geolocation_API)
- {{domxref("Geolocation")}}