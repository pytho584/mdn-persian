---
title: "HTMLFormElement: submit() method"
short-title: submit()
slug: Web/API/HTMLFormElement/submit
page-type: web-api-instance-method
browser-compat: api.HTMLFormElement.submit
---

{{APIRef("HTML DOM")}}

متد **`HTMLFormElement.submit()`** یک {{HtmlElement("form")}} مشخص را ارسال می‌کند.

این متد مشابه فعال‌سازی دکمه ارسال ({{HtmlElement("button")}}) فرم است، اما یکسان با آن نیست. با این حال، هنگام فراخوانی مستقیم این متد:

- رویدادی به نام {{domxref("HTMLFormElement/submit_event", "submit")}} برانگیخته نمی‌شود. به‌طور خاص، کنترل‌کننده رویداد `onsubmit` فرم اجرا نمی‌شود.
- [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) فعال نمی‌شود.

متد {{domxref("HTMLFormElement.requestSubmit()")}} با فعال‌سازی دکمه ارسال {{HtmlElement("button")}} فرم یکسان است و این تفاوت‌ها را ندارد.

یک کنترل فرم (مانند دکمه ارسال) با `name` یا `id` برابر با `submit`، متد `submit` فرم را می‌پوشاند. تلاش برای فراخوانی `myForm.submit();` خطای «submit is not a function» ایجاد می‌کند، زیرا در این حالت `submit` به کنترل فرمی اشاره دارد که `name` یا `id` آن `submit` است.

یک {{HtmlElement("input")}} با ویژگی type="submit" هنگام استفاده از **`HTMLFormElement.submit()`** همراه با فرم ارسال نمی‌شود، اما اگر با ارسال اصلی HTML فرم انجام دهید، ارسال می‌شود.

## Syntax

```js-nolint
submit()
```

### Parameters

هیچ.

### Return value

هیچ ({{jsxref("undefined")}}).

## Examples

```js
document.forms["my-form"].submit();
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}