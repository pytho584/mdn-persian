---
title: "HTMLTextAreaElement: setRangeText() method"
short-title: setRangeText()
slug: Web/API/HTMLTextAreaElement/setRangeText
page-type: web-api-instance-method
browser-compat: api.HTMLTextAreaElement.setRangeText
---

{{APIRef("HTML DOM")}}

متد **`setRangeText()`** در رابط {{domxref("HTMLTextAreaElement")}}، یک بازه از متن را در عنصر {{HTMLElement("textarea")}} با متن جدیدی که به‌عنوان آرگومان به آن داده می‌شود جایگزین می‌کند.

پارامترهای اختیاری دیگری نیز وجود دارند: شروع بخش متنی که باید تغییر کند، پایان آن بخش، و یک کلمه کلیدی که مشخص می‌کند پس از به‌روزرسانی متن، چه بخشی از `<textarea>` باید انتخاب شود. اگر آرگومان‌های `startSelection` و `endSelection` داده نشوند، فرض بر این است که بازه، همان انتخاب فعلی است.

آرگومان آخر تعیین می‌کند که پس از جایگزینی متن، انتخاب چگونه تنظیم شود. مقادیر ممکن عبارت‌اند از: `"select"` که متن تازه درج‌شده را انتخاب می‌کند، `"start"` که انتخاب را به درست قبل از متن درج‌شده می‌برد، `"end"` که انتخاب را به درست بعد از متن درج‌شده می‌برد، یا مقدار پیش‌فرض `"preserve"` که تلاش می‌کند انتخاب را حفظ کند.

علاوه بر این، رویدادهای {{domxref("HTMLTextAreaElement.select_event", "select")}} و {{domxref("HTMLTextAreaElement.selectionchange_event", "selectionchange")}} نیز فعال می‌شوند.

## نحو (Syntax)

```js-nolint
setRangeText(replacement)
setRangeText(replacement, startSelection)
setRangeText(replacement, startSelection, endSelection)
setRangeText(replacement, startSelection, endSelection, selectMode)
```

### پارامترها

- `replacement`
  - : رشته‌ای که باید درج شود.
- {{domxref("HTMLTextAreaElement.selectionStart", "selectionStart")}} {{optional_inline}}
  - : اندیس اولین نویسه انتخاب‌شده. اندیسی بزرگ‌تر از طول مقدار عنصر، به‌عنوان اشاره‌گر به انتهای مقدار در نظر گرفته می‌شود.
- {{domxref("HTMLTextAreaElement.selectionEnd", "selectionEnd")}} {{optional_inline}}
  - : اندیس نویسه‌ای که _بعد از_ آخرین نویسه انتخاب‌شده قرار دارد. اندیسی بزرگ‌تر از طول مقدار عنصر، به‌عنوان اشاره‌گر به انتهای مقدار در نظر گرفته می‌شود. اگر `selectionEnd` کوچک‌تر از `selectionStart` باشد، هر دو به‌عنوان مقدار `selectionEnd` در نظر گرفته می‌شوند.
- `selectMode` {{optional_inline}}
  - : یک کلمه کلیدی، شامل `select`، `start`، `end` یا مقدار پیش‌فرض `preserve`، که تعیین می‌کند پس از جایگزینی متن، انتخاب چگونه تنظیم شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

در این مثال، با کلیک روی دکمه، بخشی از متن داخل جعبه متن جایگزین می‌شود. متن تازه درج‌شده پس از آن برجسته (انتخاب) خواهد شد.

### HTML

```html
<label for="ta">Example text input:</label>
<textarea id="ta">
  This text has NOT been updated.
</textarea>
<button id="btn">Update text</button>
```

### JavaScript

```js
const btn = document.getElementById("btn");

btn.addEventListener("click", () => {
  changeText();
});

function changeText() {
  const textarea = document.getElementById("ta");
  textarea.focus();
  textarea.setRangeText("ALREADY", 14, 17, "select");
}
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("textarea")}}
- {{domxref("HTMLTextAreaElement")}}
- {{domxref("HTMLTextAreaElement.select()")}}
- {{domxref("HTMLTextAreaElement.setSelectionRange()")}}
- {{domxref("HTMLTextAreaElement.textLength")}}
- {{domxref("Selection")}}
- شبه‌عنصر {{cssxref("::selection")}}