---
title: "HTMLElement: tabIndex property"
short-title: tabIndex
slug: Web/API/HTMLElement/tabIndex
page-type: web-api-instance-property
browser-compat: api.HTMLElement.tabIndex
---

{{APIRef("HTML DOM")}}

ویژگی **`tabIndex`** از رابط {{DOMxRef("HTMLElement")}}، ترتیب پیمایش با کلید Tab را برای عنصر فعلی مشخص می‌کند.

ترتیب پیمایش با Tab به این صورت است:

1. عناصر با `tabIndex` مثبت. عناصری که مقدار `tabIndex` یکسانی دارند باید به ترتیب ظاهر شدن در صفحه پیمایش شوند. پیمایش از کمترین `tabIndex` به بیشترین آن انجام می‌شود.
2. عناصری که از ویژگی `tabIndex` پشتیبانی نمی‌کنند، یا آن را پشتیبانی کرده و `tabIndex` را برابر `0` قرار می‌دهند، به ترتیب ظاهر شدن پیمایش می‌شوند.

عناصر غیرفعال در ترتیب پیمایش با Tab شرکت نمی‌کنند.

مقادیر نیازی به متوالی بودن ندارند و نه لزوماً باید با مقدار خاصی شروع شوند. حتی می‌توانند منفی باشند؛ البته هر مرورگری مقادیر بسیار بزرگ را محدود می‌کند.

## مقدار

یک عدد صحیح.

## مثال‌ها

```js
const b1 = document.getElementById("button1");

b1.tabIndex = 1;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [دسترس‌پذیری ویجت‌های جاوااسکریپتی قابل پیمایش با صفحه‌کلید](/en-US/docs/Web/Accessibility/Guides/Keyboard-navigable_JavaScript_widgets)
- ویژگی سراسری [`tabindex`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) در HTML