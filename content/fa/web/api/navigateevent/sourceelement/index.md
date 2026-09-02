---
title: "NavigateEvent: sourceElement property"
---

{{APIRef("Navigation API")}}

ویژگی فقطخواندنی **`sourceElement`** در رابط {{domxref("NavigateEvent")}} یک شیء {{domxref("Element")}} برمی‌گرداند که عنصر آغازگر را نشان می‌دهد؛ در مواردی که ناوبری توسط یک عنصر شروع شده باشد.

عنصر آغازگر می‌تواند یکی از موارد زیر باشد:

- یک عنصر HTML {{htmlelement("a")}} (یا عنصر SVG [`<a>`](/en-US/docs/Web/SVG/Reference/Element/a)).
- یک عنصر {{htmlelement("area")}}.
- یک دکمه ارسال ([`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) یا [`<button type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/button)).
- یک عنصر {{htmlelement("form")}} که ارسال شده باشد.

## مقدار

یک شیء {{domxref("Element")}} که نشان‌دهنده عنصر شروع‌کننده ناوبری است، یا اگر ناوبری توسط عنصری آغاز نشده باشد، `null` برمی‌گرداند.

## نمونه‌ها

### دریافت `sourceElement` برای یک رویداد

```js
navigation.addEventListener("navigate", (event) => {
  console.log(event.sourceElement);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [مسیریابی سمت کلاینت مدرن: Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح‌نامه Navigation API](https://github.com/WICG/navigation-api/blob/main/README.md)