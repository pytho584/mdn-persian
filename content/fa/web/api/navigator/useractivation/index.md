---
title: "Navigator: userActivation property"
short-title: userActivation
slug: Web/API/Navigator/userActivation
page-type: web-api-instance-property
browser-compat: api.Navigator.userActivation
---

{{APIRef("HTML DOM")}}

ویژگی فقطخواندنی **`userActivation`** در رابط {{domxref("Navigator")}} یک شیء {{domxref("UserActivation")}} برمی‌گرداند که شامل اطلاعاتی دربارهٔ وضعیت فعال‌سازی کاربر برای پنجرهٔ فعلی است.

## مقدار

یک شیء {{domxref("UserActivation")}}.

## مثال‌ها

### بررسی اینکه آیا یک کنش کاربر اخیراً انجام شده است

برای بررسی اینکه آیا کاربر در حال حاضر با صفحه در تعامل است ({{Glossary("Transient activation")}}) از {{domxref("UserActivation.isActive")}} استفاده کنید.

```js
if (navigator.userActivation.isActive) {
  // proceed to request playing media, for example
}
```

### بررسی اینکه آیا کاربر تاکنون کنشی انجام داده است

برای بررسی اینکه آیا کاربر تاکنون با صفحه تعامل داشته است ({{Glossary("Sticky activation")}}) از {{domxref("UserActivation.hasBeenActive")}} استفاده کنید.

```js
if (navigator.userActivation.hasBeenActive) {
  // proceed with auto-playing an animation, for example
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("UserActivation")}}
- {{domxref("UserActivation.hasBeenActive")}}
- {{domxref("UserActivation.isActive")}}
- [Features gated by user activation](/en-US/docs/Web/Security/Defenses/User_activation)