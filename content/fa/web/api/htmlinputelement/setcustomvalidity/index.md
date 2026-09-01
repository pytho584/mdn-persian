---
title: "HTMLInputElement: setCustomValidity() method"
short-title: setCustomValidity()
slug: Web/API/HTMLInputElement/setCustomValidity
page-type: web-api-instance-method
browser-compat: api.HTMLInputElement.setCustomValidity
---

{{APIRef("HTML DOM")}}

متد **`HTMLInputElement.setCustomValidity()`** یک پیام اعتبارسنجی سفارشی برای عنصر تنظیم می‌کند.

## Syntax

```js-nolint
setCustomValidity(message)
```

### Parameters

- `message`
  - : پیامی که برای خطاهای اعتبارسنجی استفاده می‌شود.

### Return value

هیچ ({{jsxref("undefined")}}).

### Exceptions

هیچ.

## Examples

در این مثال، شناسه (ID) یک عنصر ورودی را پاس می‌دهیم و بسته به اینکه مقدار وجود نداشته باشد، خیلی کم باشد یا خیلی زیاد باشد، پیام‌های خطای متفاوتی تنظیم می‌کنیم. توجه داشته باشید که پیام بلافاصله نمایش داده نمی‌شود. با تلاش برای ارسال فرم، پیام نمایش داده می‌شود، یا می‌توانید متد [`reportValidity()`](/en-US/docs/Web/API/HTMLInputElement/reportValidity) را روی عنصر فراخوانی کنید.

```js
function validate(inputID) {
  const input = document.getElementById(inputID);
  const validityState = input.validity;

  if (validityState.valueMissing) {
    input.setCustomValidity("You gotta fill this out, yo!");
  } else if (validityState.rangeUnderflow) {
    input.setCustomValidity("We need a higher number!");
  } else if (validityState.rangeOverflow) {
    input.setCustomValidity("That's too high!");
  } else {
    input.setCustomValidity("");
  }

  input.reportValidity();
}
```

بسیار مهم است که اگر خطایی وجود نداشته باشد، پیام را روی یک رشته خالی تنظیم کنید. تا زمانی که پیام خطا خالی نباشد، فرم از اعتبارسنجی عبور نمی‌کند و ارسال نخواهد شد.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Learn: Client-side form validation](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [Guide: Constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- {{domxref('ValidityState')}}