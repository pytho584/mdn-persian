---
title: "HTMLTextAreaElement"
---

---
title: HTMLTextAreaElement
slug: Web/API/HTMLTextAreaElement
page-type: web-api-interface
browser-compat: api.HTMLTextAreaElement
---

{{APIRef("HTML DOM")}}

رابطهٔ **`HTMLTextAreaElement`** ویژگی‌ها و روش‌هایی را برای دستکاری چیدمان و نمایش عناصر {{HTMLElement("textarea")}} فراهم می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_همچنین ویژگی‌ها را از رابط والد خود، {{DOMxRef("HTMLElement")}} به ارث می‌برد._

- {{domxref("HTMLTextAreaElement.autocomplete", "autocomplete")}}
  - : رشته‌ای که ویژگی [`autocomplete`](/en-US/docs/Web/HTML/Reference/Elements/textarea#autocomplete) عنصر را نشان می‌دهد.
- {{domxref("HTMLTextAreaElement.cols", "cols")}}
  - : عددی که ویژگی [`cols`](/en-US/docs/Web/HTML/Reference/Elements/textarea#cols) عنصر را نشان می‌دهد و عرض قابل مشاهدهٔ ناحیهٔ متن را مشخص می‌کند.
- {{domxref("HTMLTextAreaElement.defaultValue", "defaultValue")}}
  - : رشته‌ای که مقدار پیش‌فرض کنترل را نشان می‌دهد و مانند ویژگی {{domxref("Node.textContent")}} رفتار می‌کند.
- {{domxref("HTMLTextAreaElement.dirName", "dirName")}}
  - : رشته‌ای که جهت‌دار بودن متن عنصر را نشان می‌دهد.
- {{domxref("HTMLTextAreaElement.disabled", "disabled")}}
  - : یک بولین که ویژگی [`disabled`](/en-US/docs/Web/HTML/Reference/Elements/textarea#disabled) عنصر را نشان می‌دهد و مشخص می‌کند که کنترل برای تعامل در دسترس نیست.
- {{domxref("HTMLTextAreaElement.form", "form")}} {{ReadOnlyInline}}
  - : ارجاعی به عنصر فرم والد را برمی‌گرداند. اگر این عنصر در یک فرم قرار نداشته باشد، می‌تواند ویژگی [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) هر عنصر {{HTMLElement("form")}} در همان سند یا مقدار `null` باشد.
- {{domxref("HTMLTextAreaElement.labels", "labels")}} {{ReadOnlyInline}}
  - : یک {{domxref("NodeList")}} از عناصر {{HTMLElement("label")}} مرتبط با این عنصر را برمی‌گرداند.
- {{domxref("HTMLTextAreaElement.maxLength", "maxLength")}}
  - : عددی که ویژگی [`maxlength`](/en-US/docs/Web/HTML/Reference/Elements/textarea#maxlength) عنصر را نشان می‌دهد و حداکثر تعداد کاراکترهایی را که کاربر می‌تواند وارد کند مشخص می‌کند. این محدودیت فقط زمانی ارزیابی می‌شود که مقدار تغییر کند.
- {{domxref("HTMLTextAreaElement.minLength", "minLength")}}
  - : عددی که ویژگی [`minlength`](/en-US/docs/Web/HTML/Reference/Elements/textarea#minlength) عنصر را نشان می‌دهد و حداقل تعداد کاراکترهایی را که کاربر می‌تواند وارد کند مشخص می‌کند. این محدودیت فقط زمانی ارزیابی می‌شود که مقدار تغییر کند.
- {{domxref("HTMLTextAreaElement.name", "name")}}
  - : رشته‌ای که ویژگی [`name`](/en-US/docs/Web/HTML/Reference/Elements/textarea#name) عنصر را نشان می‌دهد و شامل نام کنترل است.
- {{domxref("HTMLTextAreaElement.placeholder", "placeholder")}}
  - : رشته‌ای که ویژگی [`placeholder`](/en-US/docs/Web/HTML/Reference/Elements/textarea#placeholder) عنصر را نشان می‌دهد و شامل راهنمایی به کاربر دربارهٔ آنچه باید در کنترل وارد کند است.
- {{domxref("HTMLTextAreaElement.readOnly", "readOnly")}}
  - : یک بولین که ویژگی [`readonly`](/en-US/docs/Web/HTML/Reference/Elements/textarea#readonly) عنصر را نشان می‌دهد و مشخص می‌کند که کاربر نمی‌تواند مقدار کنترل را تغییر دهد.
- {{domxref("HTMLTextAreaElement.required", "required")}}
  - : یک بولین که ویژگی [`required`](/en-US/docs/Web/HTML/Reference/Elements/textarea#required) عنصر را نشان می‌دهد و مشخص می‌کند که کاربر باید قبل از ارسال فرم، مقداری را مشخص کند.
- {{domxref("HTMLTextAreaElement.rows", "rows")}}
  - : عددی که ویژگی [`rows`](/en-US/docs/Web/HTML/Reference/Elements/textarea#rows) عنصر را نشان می‌دهد و تعداد خطوط متنی قابل مشاهده برای کنترل را مشخص می‌کند.
- {{domxref("HTMLTextAreaElement.selectionDirection", "selectionDirection")}}
  - : رشته‌ای که جهتی را که انتخاب در آن رخ داده است نشان می‌دهد. اگر انتخاب در جهت شروع به پایان در زبان/منطقهٔ فعلی انجام شده باشد، `forward` است و در جهت مخالف `backward` است. اگر جهت ناشناخته باشد، می‌تواند `none` نیز باشد.
- {{domxref("HTMLTextAreaElement.selectionEnd", "selectionEnd")}}
  - : عددی که اندیس پایان متن انتخاب‌شده را نشان می‌دهد. اگر متنی انتخاب نشده باشد، شامل اندیس کاراکتری است که بعد از مکان‌نمای ورودی قرار دارد. هنگام تنظیم، کنترل طوری رفتار می‌کند که گویی `setSelectionRange()` با این مقدار به‌عنوان آرگومان دوم و `selectionStart` به‌عنوان آرگومان اول فراخوانی شده است.
- {{domxref("HTMLTextAreaElement.selectionStart", "selectionStart")}}
  - : عددی که اندیس شروع متن انتخاب‌شده را نشان می‌دهد. اگر متنی انتخاب نشده باشد، شامل اندیس کاراکتری است که بعد از مکان‌نمای ورودی قرار دارد. هنگام تنظیم، کنترل طوری رفتار می‌کند که گویی `setSelectionRange()` با این مقدار به‌عنوان آرگومان اول و `selectionEnd` به‌عنوان آرگومان دوم فراخوانی شده است.
- {{domxref("HTMLTextAreaElement.textLength", "textLength")}} {{ReadOnlyInline}}
  - : طول کدپوینت `value` کنترل را برمی‌گرداند. همانند خواندن `value.length`.
- {{domxref("HTMLTextAreaElement.type", "type")}} {{ReadOnlyInline}}
  - : رشتهٔ `textarea` را برمی‌گرداند.
- {{domxref("HTMLTextAreaElement.validationMessage", "validationMessage")}} {{ReadOnlyInline}}
  - : یک پیام محلی‌سازی‌شده را برمی‌گرداند که محدودیت‌های اعتبارسنجیِ برآورده‌نشدهٔ کنترل را توصیف می‌کند (در صورت وجود). اگر کنترل کاندیدای اعتبارسنجی محدودیت نباشد (`willValidate` مقدار `false` داشته باشد) یا محدودیت‌های خود را برآورده کند، این رشته خالی است.
- {{domxref("HTMLTextAreaElement.validity", "validity")}} {{ReadOnlyInline}}
  - : وضعیت اعتبارسنجی‌ای را که این عنصر در آن قرار دارد برمی‌گرداند.
- {{domxref("HTMLTextAreaElement.value", "value")}}
  - : رشته‌ای که مقدار خام موجود در کنترل را نشان می‌دهد.
- {{domxref("HTMLTextAreaElement.willValidate", "willValidate")}} {{ReadOnlyInline}}
  - : برمی‌گرداند که آیا عنصر کاندیدای اعتبارسنجی محدودیت است یا خیر. اگر هر شرایطی آن را از اعتبارسنجی محدودیت منع کند، `false` است؛ از جمله اگر ویژگی `readOnly` یا `disabled` آن `true` باشد.
- {{domxref("HTMLTextAreaElement.wrap", "wrap")}}
  - : رشته‌ای که ویژگی [`wrap`](/en-US/docs/Web/HTML/Reference/Elements/textarea#wrap) عنصر را نشان می‌دهد و نحوهٔ شکستن متن توسط کنترل را مشخص می‌کند.

## روش‌های نمونه

_همچنین روش‌ها را از رابط والد خود، {{DOMxRef("HTMLElement")}} به ارث می‌برد._

- {{domxref("HTMLTextAreaElement.checkValidity", "checkValidity()")}}
  - : اگر عنصر کاندیدای اعتبارسنجی محدودیت باشد و محدودیت‌های خود را برآورده نکند، `false` برمی‌گرداند. در این حالت، یک رویداد قابل‌لغو `invalid` نیز در کنترل ایجاد می‌کند. اگر کنترل کاندیدای اعتبارسنجی محدودیت نباشد یا محدودیت‌های خود را برآورده کند، `true` برمی‌گرداند.
- {{domxref("HTMLTextAreaElement.reportValidity", "reportValidity()")}}
  - : این روش مشکلات مربوط به محدودیت‌های عنصر (در صورت وجود) را به کاربر گزارش می‌دهد. اگر مشکلی وجود داشته باشد، رویداد قابل‌لغو `invalid` را در عنصر ایجاد کرده و `false` برمی‌گرداند؛ اگر مشکلی نباشد، `true` برمی‌گرداند.
- {{domxref("HTMLTextAreaElement.select", "select()")}}
  - : محتویات کنترل را انتخاب می‌کند.
- {{domxref("HTMLTextAreaElement.setCustomValidity", "setCustomValidity()")}}
  - : یک پیام اعتبارسنجی سفارشی برای عنصر تنظیم می‌کند. اگر این پیام رشتهٔ خالی نباشد، عنصر دارای خطای اعتبارسنجی سفارشی است و اعتبارسنجی نمی‌شود.
- {{domxref("HTMLTextAreaElement.setRangeText", "setRangeText()")}}
  - : بازه‌ای از متن در عنصر را با متن جدید جایگزین می‌کند.
- {{domxref("HTMLTextAreaElement.setSelectionRange", "setSelectionRange()")}}
  - : بازه‌ای از متن در عنصر را انتخاب می‌کند (اما آن را فوکوس نمی‌کند).

## رویدادها

_همچنین رویدادها را از رابط والد خود، {{DOMxRef("HTMLElement")}} به ارث می‌برد._

برای گوش دادن به این رویدادها از {{domxref("EventTarget/addEventListener", "addEventListener()")}} استفاده کنید یا یک شنوندهٔ رویداد را به ویژگی `oneventname` این رابط اختصاص دهید:

- رویداد {{domxref("HTMLTextAreaElement/select_event", "select")}}
  - : وقتی برخی از متن‌ها انتخاب شده‌اند، ایجاد می‌شود.
- رویداد {{domxref("HTMLTextAreaElement/selectionchange_event", "selectionchange")}}
  - : وقتی انتخاب متن در یک عنصر {{HTMLElement("textarea")}} تغییر کرده باشد، ایجاد می‌شود.

## مثال‌ها

### مثال textarea با رشد خودکار

یک textarea را در حین تایپ به‌صورت خودکار بزرگ کنید:

#### JavaScript

```js
function autoGrow(field) {
  if (field.scrollHeight > field.clientHeight) {
    field.style.height = `${field.scrollHeight}px`;
  }
}

document.querySelector("textarea").addEventListener("keyup", (e) => {
  autoGrow(e.target);
});
```

#### CSS

```css
textarea.no-scrollbars {
  overflow: hidden;
  width: 300px;
  height: 100px;
}
```

#### HTML

```html
<form>
  <fieldset>
    <legend>Your comments</legend>
    <p><textarea class="no-scrollbars"></textarea></p>
    <p><input type="submit" value="Send" /></p>
  </fieldset>
</form>
```

{{EmbedLiveSample('Autogrowing_textarea_example', 600, 300)}}

### مثال درج تگ‌های HTML

برخی تگ‌های HTML را در یک textarea درج کنید:

```js live-sample___insert-html
function insert(startTag, endTag) {
  const textArea = document.myForm.myTextArea;
  const start = textArea.selectionStart;
  const end = textArea.selectionEnd;
  const oldText = textArea.value;

  const prefix = oldText.substring(0, start);
  const inserted = startTag + oldText.substring(start, end) + endTag;
  const suffix = oldText.substring(end);

  textArea.value = `${prefix}${inserted}${suffix}`;

  const newStart = start + startTag.length;
  const newEnd = end + startTag.length;

  textArea.setSelectionRange(newStart, newEnd);
  textArea.focus();
}

function insertURL() {
  const newURL = prompt("Enter the full URL for the link");
  if (newURL) {
    insert(`<a href="${newURL}">`, "</a>");
  } else {
    document.myForm.myTextArea.focus();
  }
}

const strong = document.querySelector("#format-strong");
const em = document.querySelector("#format-em");
const link = document.querySelector("#format-link");
const code = document.querySelector("#format-code");

strong.addEventListener("click", (e) => insert("<strong>", "</strong>"));
em.addEventListener("click", (e) => insert("<em>", "</em>"));
link.addEventListener("click", (e) => insertURL());
code.addEventListener("click", (e) => insert("<code>", "</code>"));
```

عنصر span را طوری تزئین کنید که مانند یک پیوند رفتار کند:

```css live-sample___insert-html
.intLink {
  cursor: pointer;
  text-decoration: underline;
  color: blue;
}
```

```html live-sample___insert-html
<form name="myForm">
  <p>
    [
    <span class="intLink" id="format-strong"><strong>Bold</strong></span> |
    <span class="intLink" id="format-em"><em>Italic</em></span> |
    <span class="intLink" id="format-link">URL</span> |
    <span class="intLink" id="format-code">code</span> ]
  </p>

  <p>
    <textarea name="myTextArea" rows="10" cols="50">
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Ut facilisis, arcu vitae adipiscing placerat, nisl lectus accumsan nisi, vitae iaculis sem neque vel lectus. Praesent tristique commodo lorem quis fringilla. Sed ac tellus eros. 
    </textarea>
  </p>
</form>
```

{{EmbedLiveSample('insert-html', , '300', , , , , 'allow-modals')}}

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}