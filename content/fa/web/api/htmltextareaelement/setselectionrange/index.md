---
title: "HTMLTextAreaElement: setSelectionRange() method"
short-title: setSelectionRange()
slug: Web/API/HTMLTextAreaElement/setSelectionRange
page-type: web-api-instance-method
browser-compat: api.HTMLTextAreaElement.setSelectionRange
---

{{APIRef("HTML DOM")}}

متد **`setSelectionRange()`** در interface مربوط به {{domxref("HTMLTextAreaElement")}}، موقعیت شروع و پایان انتخابِ متن فعلی و بهصورت اختیاری جهت انتخاب را در یک عنصر {{HTMLElement("textarea")}} تنظیم میکند. این کار وضعیت انتخاب را بلافاصله بهروزرسانی میکند، هرچند هایلایتِ بصری فقط زمانی نمایش داده میشود که عنصر دارای focus باشد. جهت نشان میدهد که انتخاب به چه صورت انجام شده است؛ برای مثال، اینکه کاربر با کلیک و کشیدن از انتهای متنِ انتخابشده به سمت ابتدای آن، انتخاب را انجام داده است. علاوه بر این، رویدادهای {{domxref("HTMLTextAreaElement.select_event", "select")}} و {{domxref("HTMLTextAreaElement.selectionchange_event", "selectionchange")}} نیز فعال میشوند.

این متد ویژگی‌های {{domxref("HTMLTextAreaElement.selectionStart")}}، {{domxref("HTMLTextAreaElement.selectionEnd")}} و {{domxref("HTMLTextAreaElement.selectionDirection")}} را بلافاصله و بدون توجه به وضعیت focus به‌روزرسانی میکند. برای نمایش هایلایت بصری انتخاب، عنصر باید دارای focus باشد.

> [!NOTE]
> هرچند `setSelectionRange()` ویژگی‌های انتخاب را بلافاصله به‌روزرسانی میکند، هایلایت بصری انتخاب تنها زمانی ظاهر می‌شود که `<textarea>` دارای focus باشد. همچنین focus کردن عنصر باعث فعال شدن رویداد `selectionchange` نیز می‌شود.

برای انتخاب **تمام** متن یک عنصر `<textarea>`، از متد {{domxref("HTMLTextAreaElement.select()")}} استفاده کنید.

## Syntax

```js-nolint
setSelectionRange(selectionStart, selectionEnd)
setSelectionRange(selectionStart, selectionEnd, selectionDirection)
```

### پارامترها

- `selectionStart`
  - : ایندکس اولین کاراکتر انتخاب‌شده. ایندکسی بزرگ‌تر از طول مقدار عنصر، به‌عنوان اشاره‌گر به انتهای مقدار در نظر گرفته می‌شود. برای اطلاعات بیشتر به ویژگی {{domxref("HTMLTextAreaElement.selectionStart", "selectionStart")}} مراجعه کنید.
- `selectionEnd`
  - : ایندکس کاراکتری که _بعد از_ آخرین کاراکتر انتخاب‌شده قرار دارد. ایندکسی بزرگ‌تر از طول مقدار عنصر، به‌عنوان اشاره‌گر به انتهای مقدار در نظر گرفته می‌شود. اگر `selectionEnd` کوچک‌تر از `selectionStart` باشد، هر دو به‌عنوان مقدار `selectionEnd` در نظر گرفته می‌شوند. برای اطلاعات بیشتر به ویژگی {{domxref("HTMLTextAreaElement.selectionEnd", "selectionEnd")}} مراجعه کنید.
- `selectionDirection` {{optional_inline}}
  - : کلیدواژه `"forward"`، `"backward"` یا مقدار پیش‌فرض `"none"` — که جهتی را نشان می‌دهد که انتخاب بر اساس آن انجام شده است. برای اطلاعات بیشتر به ویژگی {{domxref("HTMLTextAreaElement.selectionDirection", "selectionDirection")}} مراجعه کنید.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
const textarea = document.getElementById("text-box");
const chars = textarea.textLength;
// اگر مقدار طولانی‌تر از ۱۰ کاراکتر باشد
if (chars > 10) {
  // عنصر باید focus شود تا بتوان محدوده‌ای از متن را در آن انتخاب کرد
  textarea.focus();
  // متنی را انتخاب کن که از پنج‌مین کاراکتر ابتدا شروع می‌شود
  // و تا پنج‌مین کاراکتر انتها ادامه دارد
  textarea.setSelectionRange(5, chars - 5);
} else {
  // در غیر این صورت همه متن را انتخاب کن
  textarea.select();
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{HTMLElement("textarea")}}
- {{domxref("HTMLTextAreaElement")}}
- {{domxref("HTMLTextAreaElement.select()")}}
- {{domxref("HTMLTextAreaElement.textLength")}}
- {{domxref("Selection")}}
- {{cssxref("::selection")}} pseudo-element
