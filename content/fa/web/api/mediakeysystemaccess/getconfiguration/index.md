---
title: "MediaKeySystemAccess: getConfiguration() method"
short-title: getConfiguration()
slug: Web/API/MediaKeySystemAccess/getConfiguration
page-type: web-api-instance-method
browser-compat: api.MediaKeySystemAccess.getConfiguration
---

{{APIRef("Encrypted Media Extensions")}}{{SecureContext_Header}}

متد **`getConfiguration()`** از رابط {{domxref("MediaKeySystemAccess")}} یک شیء شامل ترکیب پشتیبانی‌شده از گزینه‌های پیکربندی زیر را برمی‌گرداند:

- `label` {{ReadOnlyInline}}
  - : رشته‌ای که پیکربندی را شناسایی می‌کند و دقیقاً همانطور که در پیکربندی ارسال‌شده به {{domxref("Navigator.requestMediaKeySystemAccess()")}} بوده، حفظ می‌شود.
    مقدار پیش‌فرض آن رشتهٔ خالی (`""`) است.
- `initDataTypes` {{ReadOnlyInline}}
  - : فهرستی از نام انواع دادهٔ مقداردهی اولیهٔ پشتیبانی‌شده را برمی‌گرداند. نوع دادهٔ مقداردهی اولیه رشته‌ای است که قالب دادهٔ مقداردهی اولیه را مشخص می‌کند.
- `audioCapabilities` {{ReadOnlyInline}}
  - : فهرستی از جفت‌های نوع صوتی و قابلیت پشتیبانی‌شده را برمی‌گرداند.
- `videoCapabilities` {{ReadOnlyInline}}
  - : فهرستی از جفت‌های نوع ویدیویی و قابلیت پشتیبانی‌شده را برمی‌گرداند.
- `distinctiveIdentifier` {{ReadOnlyInline}}
  - : مشخص می‌کند که آیا شناسهٔ متمایز پایدار مورد نیاز است یا خیر.
- `persistentState` {{ReadOnlyInline}}
  - : مشخص می‌کند که آیا قابلیت ماندگاری حالت مورد نیاز است یا خیر.
- `sessionTypes` {{ReadOnlyInline}}
  - : آرایه‌ای از رشته‌ها که نوع جلسه‌های پشتیبانی‌شده توسط پیکربندی را نشان می‌دهد.

    مقادیر مجاز عبارت‌اند از:
    - `temporary`
      - : جلسه‌ای که در آن مجوز، کلید(ها) و رکورد یا داده‌های مرتبط با جلسه ذخیره نمی‌شوند.
        برنامه نیازی به مدیریت چنین فضای ذخیره‌سازی‌ای ندارد.
        پیاده‌سازی‌ها باید از این گزینه پشتیبانی کنند و این گزینه پیش‌فرض است.
    - `persistent-license`
      - : جلسه‌ای که در آن مجوز (و احتمالاً داده‌های دیگر مرتبط با جلسه) ذخیره خواهد شد.
        رکوردی از مجوز و کلیدهای مرتبط حتی اگر مجوز از بین برود نیز باقی می‌ماند و گواهی می‌دهد که مجوز و کلید(های) موجود در آن دیگر توسط کلاینت قابل استفاده نیستند.

## نحو

```js-nolint
getConfiguration()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک شیء.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}