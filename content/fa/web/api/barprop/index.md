---
title: "BarProp"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BarProp"
translated_by: "n8n + AI"
---

---
title: BarProp
slug: Web/API/BarProp
page-type: web-api-interface
browser-compat: api.BarProp
---

{{APIRef("DOM")}}

رابط **`BarProp`** از [Document Object Model](/en-US/docs/Web/API/Document_Object_Model) عناصر رابط کاربری مرورگر وب را که در معرض اسکریپت‌ها در صفحات وب قرار دارند، نمایش می‌دهد. هر یک از عناصر رابط زیر توسط یک شیء `BarProp` نمایش داده می‌شوند.

- {{domxref("Window.locationbar")}}
  - : نوار آدرس مرورگر.
- {{domxref("Window.menubar")}}
  - : نوار منوی مرورگر.
- {{domxref("Window.personalbar")}}
  - : نوار شخصی مرورگر.
- {{domxref("Window.scrollbars")}}
  - : نوارهای پیمایش مرورگر.
- {{domxref("Window.statusbar")}}
  - : نوار وضعیت مرورگر.
- {{domxref("Window.toolbar")}}
  - : نوار ابزار مرورگر.

رابط `BarProp` به‌طور مستقیم در دسترس نیست، بلکه از طریق یکی از این عناصر در دسترس قرار می‌گیرد.

## ویژگی‌های نمونه

- {{domxref("BarProp.visible")}} {{ReadOnlyInline}}
  - : یک {{jsxref("Boolean")}} که اگر نوار نمایش‌داده‌شده توسط عنصر رابط مورد استفاده قابل مشاهده باشد، مقدار آن `true` است.

## مثال‌ها

مثال زیر یک شیء `BarProp` را که نشان‌دهنده نوار آدرس است، در کنسول چاپ می‌کند.

```js
console.log(window.locationbar);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}