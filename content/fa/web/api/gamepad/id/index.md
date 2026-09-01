---
title: "Gamepad: id property"
---

---
title: "Gamepad: id property"
short-title: id
slug: Web/API/Gamepad/id
page-type: web-api-instance-property
browser-compat: api.Gamepad.id
---

{{APIRef("Gamepad API")}}

ویژگی **`Gamepad.id`** در رابط {{domxref("Gamepad") }} یک رشته شامل اطلاعاتی دربارهٔ کنترلر برمی‌گرداند.

قالب دقیق آن به‌طور قطعی مشخص نشده است، اما در فایرفاکس، این رشته شامل سه بخش اطلاعات است که با خط تیره (`-`) از هم جدا شده‌اند:

- دو رشتهٔ هگزادسیمال چهاررقمی که شناسهٔ فروشنده و شناسهٔ محصول USB کنترلر را دربر دارند
- نام کنترلر مطابق آنچه توسط درایور ارائه شده است.

برای مثال، یک کنترلر PS2 مقدار **810-3-USB Gamepad** را برمی‌گرداند.

این اطلاعات به شما امکان می‌دهد تا نگاشت مناسبی برای کنترل‌های دستگاه پیدا کنید و همچنین بازخورد مفیدی به کاربر نمایش دهید.

## مقدار

یک رشته (string).

## مثال‌ها

```js
window.addEventListener("gamepadconnected", () => {
  const gp = navigator.getGamepads()[0];
  gamepadInfo.textContent = `Gamepad connected at index ${gp.index}: ${gp.id}.`;
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از Gamepad API](/en-US/docs/Web/API/Gamepad_API/Using_the_Gamepad_API)