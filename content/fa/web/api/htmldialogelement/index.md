---
title: HTMLDialogElement
slug: Web/API/HTMLDialogElement
page-type: web-api-interface
browser-compat:
  - api.HTMLDialogElement
  - api.HTMLElement.beforetoggle_event.dialog_elements
  - api.HTMLElement.toggle_event.dialog_elements
---

{{APIRef("HTML DOM")}}

رابط **`HTMLDialogElement`** متدهایی برای کنترل عناصر {{HTMLElement("dialog")}} فراهم می‌کند. این رابط ویژگی‌ها و متدها را از رابط {{domxref("HTMLElement")}} به ارث می‌برد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_همچنین ویژگی‌ها را از رابط والد خود، {{domxref("HTMLElement")}} به ارث می‌برد._

- {{domxref("HTMLDialogElement.closedBy")}}
  - : یک رشته است که صفت HTML [`closedby`](/en-US/docs/Web/HTML/Reference/Elements/dialog#closedby) را تنظیم یا برمی‌گرداند و انواع اقدام‌های کاربر را مشخص می‌کند که می‌توانند برای بستن دیالوگ استفاده شوند.
- {{domxref("HTMLDialogElement.open")}}
  - : یک مقدار بولی که صفت HTML [`open`](/en-US/docs/Web/HTML/Reference/Elements/dialog#open) را منعکس می‌کند و نشان می‌دهد که آیا دیالوگ برای تعامل در دسترس است.
- {{domxref("HTMLDialogElement.returnValue")}}
  - : یک رشته که مقدار بازگشتی دیالوگ را تنظیم یا برمی‌گرداند.

## متدهای نمونه

_همچنین متدها را از رابط والد خود، {{domxref("HTMLElement")}} به ارث می‌برد._

- {{domxref("HTMLDialogElement.close()")}}
  - : دیالوگ را می‌بندد. یک رشته اختیاری می‌تواند به‌عنوان آرگومان ارسال شود و {{domxref("HTMLDialogElement.returnValue", "returnValue")}} دیالوگ را به‌روزرسانی کند.
- {{domxref("HTMLDialogElement.requestClose()")}}
  - : درخواست بستن دیالوگ را می‌کند. یک رشته اختیاری می‌تواند به‌عنوان آرگومان ارسال شود و {{domxref("HTMLDialogElement.returnValue", "returnValue")}} دیالوگ را به‌روزرسانی کند.
- {{domxref("HTMLDialogElement.show()")}}
  - : دیالوگ را به‌صورت غیرمودال نمایش می‌دهد، یعنی همچنان امکان تعامل با محتوای خارج از دیالوگ فراهم است.
- {{domxref("HTMLDialogElement.showModal()")}}
  - : دیالوگ را به‌صورت مودال و در بالای هر دیالوگ دیگری که ممکن است وجود داشته باشد نمایش می‌دهد. همه‌چیز خارج از دیالوگ {{DOMxRef("HTMLElement.inert", "inert")}} (غیرفعال) است و تعامل‌های خارج از دیالوگ مسدود می‌شوند.

## رویدادها

_همچنین رویدادها را از رابط والد خود، {{DOMxRef("HTMLElement")}} به ارث می‌برد._

برای گوش دادن به این رویدادها از {{DOMxRef("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید یا یک شنونده رویداد را به ویژگی `oneventname` این رابط اختصاص دهید.

- {{domxref("HTMLDialogElement/cancel_event", "cancel")}}
  - : هنگامی که درخواست بستن دیالوگ داده می‌شود، چه با کلید <kbd>Esc</kbd> و چه از طریق متد {{domxref("HTMLDialogElement.requestClose()", "requestClose()")}}، این رویداد فعال می‌شود. اگر رویداد لغو شود (از طریق {{domxref("Event.preventDefault()")}})، دیالوگ باز می‌ماند. اگر لغو نشود، دیالوگ بسته می‌شود و رویداد {{domxref("HTMLDialogElement/close_event", "close")}} فعال می‌شود.
- {{domxref("HTMLDialogElement/close_event", "close")}}
  - : هنگامی که دیالوگ بسته می‌شود، فعال می‌شود.

## مثال‌ها

### باز کردن / بستن یک دیالوگ مودال

مثال زیر دکمه‌ای را نشان می‌دهد که با کلیک روی آن، از تابع {{domxref("HTMLDialogElement.showModal()", "showModal()")}} برای باز کردن یک دیالوگ مودال حاوی فرم استفاده می‌شود.

در حالی که دیالوگ باز است، همه‌چیز به‌جز محتوای دیالوگ مودال غیرفعال (inert) است. می‌توانید روی دکمه _Close_ (بستن) کلیک کنید تا دیالوگ (از طریق تابع {{domxref("HTMLDialogElement.close()", "close()")}}) بسته شود، یا فرم را از طریق دکمه _Confirm_ (تأیید) ارسال کنید.

این مثال موارد زیر را نشان می‌دهد:

1. بستن یک فرم با تابع {{domxref("HTMLDialogElement.close()", "close()")}}
2. بستن فرم هنگام ارسال فرم و تنظیم {{domxref("HTMLDialogElement.returnValue", "returnValue")}} دیالوگ
3. بستن فرم با کلید <kbd>Esc</kbd>
4. رویدادهای «تغییر حالت» که می‌توانند روی دیالوگ فعال شوند: {{domxref("HTMLDialogElement/cancel_event", "cancel")}} و {{domxref("HTMLDialogElement/close_event", "close")}}، و رویدادهای به‌ارث‌برده {{domxref("HTMLElement/beforetoggle_event", "beforetoggle")}} و {{domxref("HTMLElement/toggle_event", "toggle")}}.

#### HTML

```html
<dialog id="dialog">
  <button id="close" type="button">Close</button>
  <form method="dialog" id="form">
    <p>
      <label for="fav-animal">Favorite animal:</label>
      <select id="fav-animal" name="favAnimal" required>
        <option></option>
        <option>Brine shrimp</option>
        <option>Red panda</option>
        <option>Spider monkey</option>
      </select>
    </p>
    <div>
      <button id="submit" type="submit">Confirm</button>
    </div>
  </form>
</dialog>

<button id="open">Open dialog</button>
```

```html hidden
<pre id="log"></pre>
```

```css hidden
#log {
  height: 170px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

```js hidden
const logElement = document.getElementById("log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

#### JavaScript

##### باز کردن دیالوگ

کد ابتدا اشیاء مربوط به عنصر {{htmlelement("dialog")}}، عناصر {{htmlelement("button")}} و عنصر {{htmlelement("select")}} را دریافت می‌کند. سپس یک شنونده اضافه می‌کند تا وقتی دکمه _Open Dialog_ کلیک شد، تابع {{domxref("HTMLDialogElement.showModal()")}} فراخوانی شود.

```js
const dialog = document.getElementById("dialog");
const openButton = document.getElementById("open");

// Open button opens a modal dialog
openButton.addEventListener("click", () => {
  log(`dialog: showModal()`);
  dialog.showModal();
});
```

##### بستن دیالوگ وقتی دکمه _Close_ کلیک می‌شود

سپس یک شنونده به رویداد {{domxref("Element/click_event", "click")}} دکمه _Close_ اضافه می‌کنیم. کنترل‌کننده مقدار {{domxref("HTMLDialogElement.returnValue", "returnValue")}} را تنظیم می‌کند و تابع {{domxref("HTMLDialogElement.close()", "close()")}} را برای بستن دیالوگ فراخوانی می‌کند.

```js
// Close button closes the dialog box
const closeButton = document.getElementById("close");
closeButton.addEventListener("click", () => {
  dialog.returnValue = ""; // Reset return value
  log(`dialog: close()`);
  dialog.close();
  // Alternatively, we could use dialog.requestClose(""); with an empty return value.
});
```

##### بستن دیالوگ هنگام کلیک روی دکمه _Confirm_ از طریق ارسال فرم

سپس یک شنونده به رویداد {{domxref("HTMLFormElement.submit_event", "submit")}} عنصر {{htmlelement("form")}} اضافه می‌کنیم. فرم زمانی ارسال می‌شود که عنصر الزامی {{htmlelement("select")}} دارای مقدار باشد و دکمه _Confirm_ کلیک شده باشد. اگر عنصر {{htmlelement("select")}} مقدار نداشته باشد، فرم ارسال نمی‌شود و دیالوگ باز می‌ماند.

```js
// Confirm button closes dialog if there is a selection.
const form = document.getElementById("form");
const selectElement = document.getElementById("fav-animal");
form.addEventListener("submit", () => {
  log(`form: submit`);
  // Set the return value to the selected option value
  dialog.returnValue = selectElement.value;
  // We don't need to close the dialog here
  // submitting the form with method="dialog" will do that automatically.
  // dialog.close();
});
```

##### دریافت `returnValue` در رویداد `close`

فراخوانی {{domxref("HTMLDialogElement.close()", "close()")}} (یا ارسال موفق فرم با `method="dialog"`") رویداد {{domxref("HTMLDialogElement/close_event", "close")}} را فعال می‌کند که در ادامه با ثبت مقدار بازگشتی دیالوگ در log آن را پیاده‌سازی می‌کنیم.

```js
dialog.addEventListener("close", (event) => {
  log(`close_event: (dialog.returnValue: "${dialog.returnValue}")`);
});
```

##### رویداد `cancel`

رویداد {{domxref("HTMLDialogElement/cancel_event", "cancel")}} زمانی فعال می‌شود که از «روش‌های خاص پلتفرم» برای بستن دیالوگ استفاده شود، مانند کلید <kbd>Esc</kbd>. همچنین زمانی که متد {{domxref("HTMLDialogElement.requestClose()", "requestClose()")}} فراخوانی شود، این رویداد فعال می‌شود. این رویداد «قابل لغو» (cancelable) است، یعنی می‌توانیم از آن برای جلوگیری از بسته‌شدن دیالوگ استفاده کنیم. در اینجا ما فقط cancel را به‌عنوان یک عملیات «بستن» در نظر می‌گیریم و مقدار {{domxref("HTMLDialogElement.returnValue", "returnValue")}} را به `""` بازنشانی می‌کنیم تا هر مقدار احتمالی پاک شود.

```js
dialog.addEventListener("cancel", (event) => {
  log(`cancel_event: (dialog.returnValue: "${dialog.returnValue}")`);
  dialog.returnValue = ""; // Reset value
});
```

##### رویداد `toggle`

رویداد {{domxref("HTMLElement/toggle_event", "toggle")}} (که از {{domxref("HTMLElement", "HTMLElement")}} به ارث رسیده است) درست بعد از باز یا بسته‌شدن دیالوگ فعال می‌شود (اما قبل از رویداد {{domxref("HTMLDialogElement/close_event", "close")}}).

در اینجا یک شنونده اضافه می‌کنیم تا زمان باز و بسته‌شدن دیالوگ را در log ثبت کند.

> [!NOTE]
> رویدادهای {{domxref("HTMLElement/toggle_event", "toggle")}} و {{domxref("HTMLElement/beforetoggle_event", "beforetoggle")}} ممکن است روی عناصر dialog در همه مرورگرها فعال نشوند. در این نسخه‌های مرورگر، می‌توانید به‌جای آن پس از تلاش برای باز/بستن دیالوگ، ویژگی {{domxref("HTMLDialogElement.open", "open")}} را بررسی کنید.

```js
dialog.addEventListener("toggle", (event) => {
  log(`toggle event: newState: ${event.newState}`);
});
```

##### رویداد `beforetoggle`

رویداد {{domxref("HTMLElement/beforetoggle_event", "beforetoggle")}} (که از {{domxref("HTMLElement", "HTMLElement")}} به ارث رسیده است) یک رویداد قابل لغو است که درست قبل از باز یا بسته‌شدن دیالوگ فعال می‌شود. در صورت نیاز، می‌توان از آن برای جلوگیری از نمایش دیالوگ یا انجام اقدام‌هایی روی عناصر دیگر که تحت تأثیر وضعیت باز/بسته دیالوگ قرار می‌گیرند استفاده کرد، مانند افزودن کلاس‌هایی به آن‌ها برای راه‌اندازی انیمیشن.

در این مورد، فقط وضعیت قبلی و جدید را در log ثبت می‌کنیم.

```js
dialog.addEventListener("beforetoggle", (event) => {
  log(
    `beforetoggle event: oldState: ${event.oldState}, newState: ${event.newState}`,
  );

  // Call event.preventDefault() to prevent a dialog opening
  /*
    if (shouldCancel()) {
        event.preventDefault();
    }
  */
});
```

#### نتیجه

مثال زیر را امتحان کنید. توجه داشته باشید که هر دو دکمه `Confirm` و `Close` باعث فعال‌شدن رویداد {{domxref("HTMLDialogElement/close_event", "close")}} می‌شوند و نتیجه باید منعکس‌کننده گزینه انتخاب‌شده در دیالوگ باشد.

{{EmbedLiveSample("Open / close a modal dialog", '100%', "250px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML {{htmlelement("dialog")}}