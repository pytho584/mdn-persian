---
title: "CSSTransformComponent: toMatrix() method"
short-title: toMatrix()
slug: Web/API/CSSTransformComponent/toMatrix
page-type: web-api-instance-method
browser-compat: api.CSSTransformComponent.toMatrix
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

متد **`toMatrix()`** از رابط {{domxref("CSSTransformComponent")}} یک شیء {{domxref('DOMMatrix')}} را برمی‌گرداند.

همه توابع تبدیل را می‌توان از نظر ریاضیاتی به صورت یک ماتریس تبدیل ۴×۴ نمایش داد.

> [!NOTE]
> ویژگی `is2D` بر این تأثیر می‌گذارد که کدام تبدیل و در نتیجه چه نوع ماتریسی بازگردانده می‌شود.
> تبدیل‌های دوبعدی و سه‌بعدی CSS به دلایل سازگاری با گذشته با یکدیگر تفاوت دارند.
> توضیح کوتاهی دربارهٔ تفاوت تبدیل‌های دوبعدی و سه‌بعدی را می‌توانید در [استفاده از تبدیل‌های CSS](/en-US/docs/Web/CSS/Guides/Transforms/Using) ببینید.

## نحو

```js-nolint
toMatrix()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک شیء {{domxref('DOMMatrix')}}

### استثناها

- {{jsxref("TypeError")}}
  - : اگر هر یک از طول‌های مورد استفاده در تولید ماتریس با واحد px سازگار نباشند (مانند طول‌های نسبی یا درصدها)، این خطا پرتاب می‌شود.

## مثال‌ها

برای انجام

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
