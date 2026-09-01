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

هیچ‌کدام ({{jsxref("undefined")}}).

### Exceptions

هیچ‌کدام.

## Examples

در این مثال، شناسه یک عنصر ورودی را ارسال می‌کنیم و بسته به اینکه مقدار وجود نداشته باشد، خیلی کم باشد یا خیلی زیاد باشد، پیام‌های خطای متفاوتی تنظیم می‌کنیم. توجه داشته باشید که پیام بلافاصله نمایش داده نمی‌شود. تلاش برای ارسال فرم، پیام را نمایش می‌دهد، یا می‌توانید متد [`reportValidity()`](/en-US/docs/Web/API/HTMLInputElement/reportValidity) را روی عنصر فراخوانی کنید.

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

تنظیم پیام به یک رشته خالی در صورت عدم وجود خطا ضروری است. تا زمانی که پیام خطا خالی نباشد، فرم اعتبارسنجی را پاس نمی‌کند و ارسال نمی‌شود.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [یادگیری: اعتبارسنجی فرم سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- {{domxref('ValidityState')}}