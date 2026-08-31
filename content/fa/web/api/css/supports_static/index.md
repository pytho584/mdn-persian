---
title: "CSS: supports() static method"
short-title: supports()
slug: Web/API/CSS/supports_static
page-type: web-api-static-method
browser-compat: api.CSS.supports_static
---

{{APIRef("CSSOM")}}

متد ایستای **`CSS.supports()`** یک مقدار بولین برمی‌گرداند که نشان می‌دهد آیا مرورگر از یک ویژگی CSS مشخص پشتیبانی می‌کند یا نه.

## نحو

```js-nolint
CSS.supports(propertyName, value)
CSS.supports(supportCondition)
```

### پارامترها

دو مجموعه پارامتر مجزا وجود دارد. مجموعه اول امکان آزمایش پشتیبانی از یک جفت _ویژگی-مقدار_ را فراهم می‌کند:

- `propertyName`
  - : رشته‌ای شامل نام ویژگی CSS که باید بررسی شود.
- `value`
  - : رشته‌ای شامل مقدار ویژگی CSS که باید بررسی شود.

سینتکس دوم یک پارامتر می‌گیرد که با شرط {{cssxref("@supports")}} مطابقت دارد:

- `supportCondition`
  - : رشته‌ای شامل شرطی که باید بررسی شود.

### مقدار بازگشتی

اگر مرورگر از قانون پشتیبانی کند، `true`؛ در غیر این صورت `false`.

## مثال‌ها

در مثال‌های زیر، `result` یک مقدار بولین است که نشان می‌دهد آیا مرورگر از ویژگی CSS داده‌شده پشتیبانی می‌کند یا نه.

```js
result = CSS.supports("text-decoration-style", "blink");
result = CSS.supports("display: flex");
result = CSS.supports("(--foo: red)");
result = CSS.supports("selector(:has(a))");
result = CSS.supports(
  "(transform-style: preserve) or (-moz-transform-style: preserve) or (-webkit-transform-style: preserve)",
);
```

برای نمونه‌های بیشتر و امکانات نحوی، به at-rule {{cssxref("@supports")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- at-rule {{cssxref("@supports")}} که همان قابلیت را به شکلی اعلانی (declarative) فراهم می‌کند.
- کلاس CSSOM {{domxref("CSSSupportsRule")}} که امکان دستکاری at-rule های {{cssxref("@supports")}} را می‌دهد.