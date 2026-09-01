---
title: "HTMLInputElement: setSelectionRange() method"
short-title: setSelectionRange()
slug: Web/API/HTMLInputElement/setSelectionRange
page-type: web-api-instance-method
browser-compat: api.HTMLInputElement.setSelectionRange
---

{{APIRef("HTML DOM")}}

متد **`HTMLInputElement.setSelectionRange()`** موقعیت شروع و پایان انتخاب متن کنونی را در یک عنصر {{HTMLElement("input")}} یا {{HTMLElement("textarea")}} تعیین می‌کند. این کار وضعیت انتخاب را بلافاصله به‌روزرسانی می‌کند، هرچند برجسته‌سازی بصری تنها زمانی ظاهر می‌شود که عنصر فوکوس داشته باشد.

به‌صورت اختیاری، می‌توانید جهتی را که انتخاب باید در نظر گرفته شود که رخ داده است مشخص کنید. این امکان به شما می‌دهد مثلاً نشان دهید که انتخاب توسط کاربر با کلیک کردن و کشیدن از انتهای متن انتخاب‌شده به سمت ابتدا انجام شده است.

این متد ویژگی‌های {{domxref("HTMLInputElement.selectionStart")}}، {{domxref("HTMLInputElement.selectionEnd")}} و {{domxref("HTMLInputElement.selectionDirection")}} را در یک فراخوانی به‌روزرسانی می‌کند، صرف‌نظر از اینکه عنصر فوکوس داشته باشد یا نه. هایلایت بصری انتخاب فقط وقتی عنصر فوکوس دارد ظاهر می‌شود.

عنصر باید یکی از انواع ورودی زیر باشد: [`password`](/en-US/docs/Web/HTML/Reference/Elements/input/password)، [`search`](/en-US/docs/Web/HTML/Reference/Elements/input/search)، [`tel`](/en-US/docs/Web/HTML/Reference/Elements/input/tel)، [`text`](/en-US/docs/Web/HTML/Reference/Elements/input/text) یا [`url`](/en-US/docs/Web/HTML/Reference/Elements/input/url). در غیر این صورت مرورگر یک استثناء `InvalidStateError` پرتاب می‌کند.

اگر می‌خواهید **همه** متن یک عنصر ورودی را انتخاب کنید، می‌توانید به‌جای آن از متد [HTMLInputElement.select()](/en-US/docs/Web/API/HTMLInputElement/select) استفاده کنید.

## نحو

```js-nolint
setSelectionRange(selectionStart, selectionEnd)
setSelectionRange(selectionStart, selectionEnd, selectionDirection)
```

### پارامترها

- `selectionStart`
  - : شاخص (index) مبتنی بر ۰ اولین نویسه انتخاب‌شده. شاخص بزرگ‌تر از طول مقدار عنصر، به‌عنوان اشاره به انتهای مقدار در نظر گرفته می‌شود.
- `selectionEnd`
  - : شاخص مبتنی بر ۰ نویسه‌ی _بعد از_ آخرین نویسه انتخاب‌شده. شاخص بزرگ‌تر از طول مقدار عنصر، به‌عنوان اشاره به انتهای مقدار در نظر گرفته می‌شود. اگر `selectionEnd` کمتر از `selectionStart` باشد، هر دو به مقدار `selectionEnd` در نظر گرفته می‌شوند.

- `selectionDirection` {{optional_inline}}
  - : رشته‌ای که جهتی را نشان می‌دهد که انتخاب در نظر گرفته می‌شود انجام شده است. مقادیر ممکن:
    - `"forward"`
    - `"backward"`
    - `"none"` اگر جهت ناشناخته یا بی‌ربط باشد. مقدار پیش‌فرض.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر عنصر یکی از انواع ورودی زیر نباشد پرتاب می‌شود: [`password`](/en-US/docs/Web/HTML/Reference/Elements/input/password)، [`search`](/en-US/docs/Web/HTML/Reference/Elements/input/search)، [`tel`](/en-US/docs/Web/HTML/Reference/Elements/input/tel)، [`text`](/en-US/docs/Web/HTML/Reference/Elements/input/text) یا [`url`](/en-US/docs/Web/HTML/Reference/Elements/input/url).

## مثال‌ها

در این مثال، روی دکمه کلیک کنید تا نویسه‌های سوم، چهارم و پنجم در کادر متن انتخاب شوند ("zil" در کلمه "Mozilla").

### HTML

```html
<input type="text" id="text-box" size="20" value="Mozilla" />
<button>Select text</button>
```

### JavaScript

```js
function selectText() {
  const input = document.getElementById("text-box");
  input.focus();
  input.setSelectionRange(2, 5);
}

document.querySelector("button").addEventListener("click", selectText);
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("input")}}
- {{HTMLElement("textarea")}}
- {{domxref("HTMLInputElement")}}
- {{domxref("Selection")}}