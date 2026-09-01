---
title: "DynamicsCompressorNode: DynamicsCompressorNode() constructor"
---

---
title: "DynamicsCompressorNode: DynamicsCompressorNode() constructor"
short-title: DynamicsCompressorNode()
slug: Web/API/DynamicsCompressorNode/DynamicsCompressorNode
page-type: web-api-constructor
browser-compat: api.DynamicsCompressorNode.DynamicsCompressorNode
---

{{APIRef("Web Audio API")}}

سازندهٔ **`DynamicsCompressorNode()`** یک نمونهٔ جدید از شیء {{domxref("DynamicsCompressorNode")}} می‌سازد که می‌توان از آن برای اعمال افکت فشرده‌سازی استفاده کرد و صدای بلندترین بخش‌های یک سیگنال را کاهش می‌دهد.

فشرده‌سازی می‌تواند به جلوگیری از کلیپینگ (بریدگی سیگنال) و اعوجاج هنگام ترکیب چند صدا کمک کند. همچنین در تولید موسیقی و صدای بازی‌ها برای کنترل دینامیک، شکل‌دهی تُن (رنگ صدا) و افکت‌های خلاقانه استفاده می‌شود.

## Syntax

```js-nolint
new DynamicsCompressorNode(context, options)
```

### Parameters

- `context`
  - : ارجاعی به یک {{domxref("AudioContext")}}.
- `options` {{optional_inline}}
  - : گزینه‌ها به صورت زیر هستند:
    - `attack`
      - : مدت زمان (بر حسب ثانیه) برای کاهش بهره (gain) به میزان ۱۰ دسیبل. مقدار پیش‌فرض آن ۰٫۰۰۳ است. این پارامتر از نوع k-rate است. محدودهٔ نامی آن \[0, 1] است.
    - `knee`
      - : مقدار دسیبلی که محدودهٔ بالای آستانه را نشان می‌دهد و در آن منحنی به نرمی به بخش «نسبت» (ratio) منتقل می‌شود. مقدار پیش‌فرض آن ۳۰ است. این پارامتر از نوع k-rate است. محدودهٔ نامی آن \[0, 40] است.
    - `ratio`
      - : میزان تغییر دسیبل در ورودی به ازای ۱ دسیبل تغییر در خروجی. مقدار پیش‌فرض آن ۱۲ است. این پارامتر از نوع k-rate است. محدودهٔ نامی آن \[1, 20] است.
    - `release`
      - : مدت زمان (بر حسب ثانیه) برای افزایش بهره به میزان ۱۰ دسیبل. مقدار پیش‌فرض آن ۰٫۲۵۰ است. این پارامتر از نوع k-rate است. محدودهٔ نامی آن \[0, 1] است.
    - `threshold`
      - : مقدار دسیبلی که بالاتر از آن فشرده‌سازی شروع به اثرگذاری می‌کند. مقدار پیش‌فرض آن ۲۴- است. این پارامتر از نوع k-rate است. محدودهٔ نامی آن \[-100, 0] است.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}