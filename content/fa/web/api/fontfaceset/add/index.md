---
title: "FontFaceSet: add() method"
short-title: add()
slug: Web/API/FontFaceSet/add
page-type: web-api-instance-method
browser-compat: api.FontFaceSet.add
---

{{APIRef("CSS Font Loading API")}}{{AvailableInWorkers}}

متد **`add()`** از رابط {{domxref("FontFaceSet")}} یک فونت جدید به مجموعه اضافه می‌کند.

## Syntax

```js-nolint
add(font)
```

### پارامترها

- `font`
  - : یک {{domxref("FontFace")}} که باید به مجموعه اضافه شود.

### مقدار بازگشتی

یک {{domxref("FontFaceSet")}} جدید.

### استثناها

- `InvalidModificationError` {{domxref("DOMException")}}
  - : اگر این فونت از قبل از طریق قانون CSS {{cssxref("@font-face")}} اضافه شده باشد، پرتاب می‌شود.

## مثال‌ها

در مثال زیر یک شیء {{domxref("FontFace")}} جدید ساخته می‌شود و سپس به {{domxref("FontFaceSet")}} اضافه می‌گردد.

```js
const font = new FontFace("MyFont", 'url("myFont.woff2")');
document.fonts.add(font);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}