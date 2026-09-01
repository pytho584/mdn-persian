---
title: "ElementInternals: setValidity() method"
short-title: setValidity()
slug: Web/API/ElementInternals/setValidity
page-type: web-api-instance-method
browser-compat: api.ElementInternals.setValidity
---

{{APIRef("Web Components")}}

متد **`setValidity()`** از رابط {{domxref("ElementInternals")}} وضعیت اعتبار (validity) عنصر را تنظیم می‌کند.

## نحو (Syntax)

```js-nolint
setValidity(flags)
setValidity(flags, message)
setValidity(flags, message, anchor)
```

### پارامترها

- `flags` {{Optional_Inline}}
  - : یک شیء دیکشنری حاوی یک یا چند پرچم که وضعیت اعتبار عنصر را نشان می‌دهد:
    - `valueMissing`
      - : یک مقدار بولی که اگر عنصر دارای ویژگی [`required`](/en-US/docs/Web/HTML/Reference/Elements/input#required) باشد اما مقداری نداشته باشد `true` است، در غیر این صورت `false`. اگر `true` باشد، عنصر با کلاس شبه- CSS {{cssxref(":invalid")}} مطابقت دارد.
    - `typeMismatch`
      - : یک مقدار بولی که اگر مقدار در نحو (syntax) مورد نیاز نباشد (زمانی که [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#type) برابر `email` یا `url` باشد) `true` است، یا اگر نحو صحیح باشد `false`. اگر `true` باشد، عنصر با کلاس شبه- CSS {{cssxref(":invalid")}} مطابقت دارد.
    - `patternMismatch`
      - : یک مقدار بولی که اگر مقدار با [`pattern`](/en-US/docs/Web/HTML/Reference/Elements/input#pattern) مشخص شده مطابقت نداشته باشد `true` است، و اگر مطابقت داشته باشد `false`. اگر `true` باشد، عنصر با کلاس شبه- CSS {{cssxref(":invalid")}} مطابقت دارد.
    - `tooLong`
      - : یک مقدار بولی که اگر مقدار از `maxlength` مشخص شده برای اشیاء {{domxref("HTMLInputElement")}} یا {{domxref("HTMLTextAreaElement")}} تجاوز کند `true` است، یا اگر طول آن کمتر یا برابر با حداکثر طول باشد `false`. اگر `true` باشد، عنصر با کلاس‌های شبه- CSS {{cssxref(":invalid")}} و {{cssxref(":out-of-range")}} مطابقت دارد.
    - `tooShort`
      - : یک مقدار بولی که اگر مقدار به `minlength` مشخص شده برای اشیاء {{domxref("HTMLInputElement")}} یا {{domxref("HTMLTextAreaElement")}} نرسد `true` است، یا اگر طول آن بزرگتر یا برابر با حداقل طول باشد `false`. اگر `true` باشد، عنصر با کلاس‌های شبه- CSS {{cssxref(":invalid")}} و {{cssxref(":out-of-range")}} مطابقت دارد.
    - `rangeUnderflow`
      - : یک مقدار بولی که اگر مقدار کمتر از حداقل مشخص شده توسط ویژگی [`min`](/en-US/docs/Web/HTML/Reference/Elements/input#min) باشد `true` است، یا اگر بزرگتر یا برابر با حداقل باشد `false`. اگر `true` باشد، عنصر با کلاس‌های شبه- CSS {{cssxref(":invalid")}} و {{cssxref(":out-of-range")}} مطابقت دارد.
    - `rangeOverflow`
      - : یک مقدار بولی که اگر مقدار بیشتر از حداکثر مشخص شده توسط ویژگی [`max`](/en-US/docs/Web/HTML/Reference/Elements/input#max) باشد `true` است، یا اگر کمتر یا برابر با حداکثر باشد `false`. اگر `true` باشد، عنصر با کلاس‌های شبه- CSS {{cssxref(":invalid")}} و {{cssxref(":out-of-range")}} مطابقت دارد.
    - `stepMismatch`
      - : یک مقدار بولی که اگر مقدار با قوانین تعیین شده توسط ویژگی [`step`](/en-US/docs/Web/HTML/Reference/Elements/input#step) مطابقت نداشته باشد (یعنی به طور مساوی بر مقدار گام تقسیم نشود) `true` است، یا اگر با قانون گام مطابقت داشته باشد `false`. اگر `true` باشد، عنصر با کلاس‌های شبه- CSS {{cssxref(":invalid")}} و {{cssxref(":out-of-range")}} مطابقت دارد.
    - `badInput`
      - : یک مقدار بولی که اگر کاربر ورودی‌ای ارائه کرده باشد که مرورگر قادر به تبدیل آن نیست `true` است.
    - `customError`
      - : یک مقدار بولی که نشان می‌دهد آیا پیام اعتبار سفارشی عنصر با فراخوانی متد {{domxref('HTMLInputElement.setCustomValidity', 'setCustomValidity()')}} عنصر روی یک رشته غیر خالی تنظیم شده است یا خیر.

    > [!NOTE]
    > برای تنظیم همه پرچم‌ها روی `false`، که نشان می‌دهد این عنصر از تمام قوانین اعتبارسنجی عبور می‌کند، یک شیء خالی `{}` ارسال کنید. در این حالت، نیازی به ارسال `message` نیز ندارید.

- `message` {{Optional_Inline}}
  - : یک رشته حاوی یک پیام که اگر هر یک از `flags`ها `true` باشند تنظیم می‌شود. این پارامتر فقط در صورتی اختیاری است که همه `flags`ها `false` باشند.
- `anchor` {{Optional_Inline}}
  - : یک {{domxref("HTMLElement")}} که می‌تواند توسط عامل کاربر (user agent) برای گزارش مشکلات مربوط به این ارسال فرم استفاده شود.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها (Exceptions)

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر عنصر خاصیت `formAssociated` خود را روی `true` تنظیم نکرده باشد، پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : اگر یک یا چند `flags` `true` باشند، پرتاب می‌شود.
- `NotFoundError` {{domxref("DOMException")}}
  - : اگر `anchor` داده شده باشد، اما لنگر (anchor) یک فرزند سایه-شامل (shadow-including descendant) از عنصر نباشد، پرتاب می‌شود.

## مثال‌ها

در مثال زیر، `setValidity` با یک پارامتر `flags` خالی فراخوانی می‌شود تا نشان دهد عنصر با قوانین اعتبارسنجی مطابقت دارد.

```js
this.internals_.setValidity({});
```

در مثال زیر، `setValidity` با پرچم `valueMissing` تنظیم شده روی `true` فراخوانی می‌شود. سپس باید یک پارامتر `message` حاوی یک پیام نیز ارسال شود.

```js
this.internals_.setValidity({ valueMissing: true }, "my message");
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}