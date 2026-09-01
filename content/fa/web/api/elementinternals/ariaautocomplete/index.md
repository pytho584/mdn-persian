---
title: "ElementInternals: ariaAutoComplete property"
short-title: ariaAutoComplete
slug: Web/API/ElementInternals/ariaAutoComplete
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaAutoComplete
---

{{APIRef("Web Components")}}

ویژگی **`ariaAutoComplete`** از رابط {{domxref("ElementInternals")}} منعکس‌کنندهٔ مقدار صفت [`aria-autocomplete`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-autocomplete) است که نشان می‌دهد آیا وارد کردن متن می‌تواند باعث نمایش یک یا چند پیش‌بینی از مقدار مورد نظر کاربر برای یک جعبه‌ترکیب (combobox)، جعبه‌جستجو (searchbox) یا جعبه‌متن (textbox) شود و مشخص می‌کند که اگر پیش‌بینی‌ها انجام شوند، چگونه ارائه خواهند شد.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را برای یک عنصر سفارشی فراهم می‌کند. این ویژگی‌ها ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که اگر نویسنده آن ویژگی‌ها را حذف کند یا اصلاً اضافه نکند، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر به [توضیح‌دهندهٔ مدل شیء دسترسی‌پذیری](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) مراجعه کنید.

## Value

یک رشته با یکی از مقادیر زیر:

- `"inline"`
  - : هنگامی که کاربر متنی را وارد می‌کند، متنی که یک راه تکمیل ورودی ارائه‌شده را پیشنهاد می‌کند ممکن است به صورت پویا بعد از مکان‌نما درج شود.
- `"list"`
  - : هنگامی که کاربر متنی را وارد می‌کند، ممکن است عنصری حاوی مجموعه‌ای از مقادیر که می‌توانند ورودی ارائه‌شده را تکمیل کنند نمایش داده شود.
- `"both"`
  - : هنگامی که کاربر متنی را وارد می‌کند، ممکن است عنصری حاوی مجموعه‌ای از مقادیر که می‌توانند ورودی ارائه‌شده را تکمیل کنند نمایش داده شود. اگر نمایش داده شود، یک مقدار در مجموعه به طور خودکار انتخاب می‌شود و متن لازم برای تکمیل مقدار انتخاب‌شدهٔ خودکار بعد از مکان‌نما در ورودی ظاهر می‌شود.
- `"none"`
  - : هنگامی که کاربر متنی را وارد می‌کند، هیچ پیشنهاد خودکاری که سعی در پیش‌بینی نحوهٔ تکمیل ورودی توسط کاربر داشته باشد نمایش داده نمی‌شود.

## Examples

در این مثال، مقدار `ariaAutoComplete` به `"inline"` تنظیم شده است.

```js
class CustomControl extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();
    this.internals_.ariaAutoComplete = "inline";
  }
  // …
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}