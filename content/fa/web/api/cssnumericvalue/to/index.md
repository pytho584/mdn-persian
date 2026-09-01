---
title: "CSSNumericValue: to() method"
short-title: to()
slug: Web/API/CSSNumericValue/to
page-type: web-api-instance-method
browser-compat: api.CSSNumericValue.to
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

متد **`to()`** از رابط {{domxref("CSSNumericValue")}} یک مقدار عددی را از یک واحد به واحد دیگر تبدیل می‌کند.

## نحو (Syntax)

```js-nolint
to(unit)
```

### پارامترها

- `unit`
  - : واحدی که می‌خواهید به آن تبدیل کنید.

### مقدار بازگشتی

یک {{domxref('CSSUnitValue')}}.

### استثناها

- `SyntaxError` {{domxref("DOMException")}}
  - : در صورت ارسال یک واحد نامعتبر به متد پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : در صورت بروز هر یک از موارد زیر پرتاب می‌شود:
    - مقدار `CSSNumericValue` که متد روی آن فراخوانی می‌شود نتواند به یک مقدار و نوع واحد تفکیک شود.
      این ممکن است زمانی رخ دهد که مقدار از یک متغیر محاسبه شده باشد و مقدار آن متغیر در این بافت قابل دانستن نباشد.
    - مقدار نتواند به واحد جدید تبدیل شود، زیرا در دسته‌بندی یکسانی قرار ندارد.
      برای مثال، نمی‌توانید متر را به ثانیه تبدیل کنید.

## مثال‌ها

### استفاده پایه

```js
// چاپ می‌کند "0.608542cm"
console.log(CSS.px("23").to("cm").toString());
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}