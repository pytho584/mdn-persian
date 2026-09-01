---
title: "EditContext: updateSelectionBounds() method"
---

---
title: "EditContext: updateSelectionBounds() method"
short-title: updateSelectionBounds()
slug: Web/API/EditContext/updateSelectionBounds
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.EditContext.updateSelectionBounds
---

{{APIRef("EditContext API")}}{{SeeCompatTable}}

متد **`EditContext.updateSelectionBounds()`** از رابط {{domxref("EditContext")}} برای اطلاع‌رسانی به سیستم‌عامل درباره مرزهای انتخاب متن در ناحیهٔ قابل ویرایشی که با شیء `EditContext` مرتبط است، استفاده می‌شود.

این متد را فراخوانی کنید تا مرزهای انتخاب فعلی کاربر را به سیستم‌عامل اطلاع دهید. هر زمان که انتخاب کاربر در ناحیهٔ قابل ویرایش تغییر کند، باید این متد را فراخوانی کنید. سیستم‌عامل از مرزهای انتخاب برای کمک به تعیین موقعیت پنجرهٔ IME یا هر سطح رابط کاربری مرتبط با ویرایش که مختص پلتفرم است، استفاده می‌کند.

## نحو

```js-nolint
updateSelectionBounds(selectionBounds)
```

### پارامترها

- `selectionBounds`
  - : یک شیء {{domxref("DOMRect")}} که مرزهای جدید انتخاب را نشان می‌دهد.

### مقدار بازگشتی

هیچ (`undefined`).

### استثناها

- {{jsxref("TypeError")}}
  - : اگر متد بدون آرگومان فراخوانی شود یا آرگومان ارائه‌شده یک شیء {{domxref("DOMRect")}} نباشد، این خطا پرتاب می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{DOMxRef("EditContext")}} که این متد به آن تعلق دارد.