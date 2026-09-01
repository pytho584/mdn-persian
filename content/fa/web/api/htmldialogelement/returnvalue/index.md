---
title: "HTMLDialogElement: returnValue property"
---

---
title: "HTMLDialogElement: returnValue property"
short-title: returnValue
slug: Web/API/HTMLDialogElement/returnValue
page-type: web-api-instance-property
browser-compat: api.HTMLDialogElement.returnValue
---

{{ APIRef("HTML DOM") }}

ویژگی **`returnValue`** از رابط {{domxref("HTMLDialogElement")}} رشته‌ای است که مقدار بازگشتی برای یک عنصر {{htmlelement("dialog")}} را هنگام بسته‌شدن نشان می‌دهد. می‌توانید این مقدار را مستقیماً تنظیم کنید (`dialog.returnValue = "result"`) یا مقدار را به‌صورت آرگومان رشته‌ای به {{domxref("HTMLDialogElement.close()", "close()")}} یا {{domxref("HTMLDialogElement.requestClose()", "requestClose()")}} بدهید.

## مقدار

رشته‌ای که `returnValue` گفتگو را نشان می‌دهد. پیش‌فرض آن رشتهٔ خالی (`""`) است.

## مثال‌ها

### بررسی مقدار بازگشتی

مثال زیر دکمه‌ای برای باز کردن یک گفتگو نشان می‌دهد. گفتگو از کاربر می‌پرسد که آیا با شرایط خدمات موافق است.

گفتگو حاوی دکمه‌هایی به نام‌های «Accept» و «Decline» است: وقتی کاربر روی یکی از این دکمه‌ها کلیک می‌کند، کنترل‌کنندهٔ کلیکِ آن دکمه گفتگو را می‌بندد و انتخاب کاربر را به تابع {{domxref("HTMLDialogElement.close()", "close()")}} می‌فرستد. این کار انتخاب را به ویژگی `returnValue` گفتگو اختصاص می‌دهد.

در کنترل‌کنندهٔ رویداد {{domxref("HTMLDialogElement.close_event", "close")}} گفتگو، مثال متن وضعیتِ صفحهٔ اصلی را به‌روزرسانی می‌کند تا `returnValue` را ثبت کند.

اگر کاربر بدون کلیک روی هیچ دکمه‌ای گفتگو را ببندد (برای مثال با فشردن کلید <kbd>Esc</kbd>)، مقدار بازگشتی تنظیم نمی‌شود.

#### HTML

```html
<dialog id="dialog">
  <p>Do you agree to the Terms of Service (link)?</p>
  <button id="decline" value="declined">Decline</button>
  <button id="accept" value="accepted">Accept</button>
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

```js
const dialog = document.getElementById("dialog");
const openButton = document.getElementById("open");
const declineButton = document.getElementById("decline");
const acceptButton = document.getElementById("accept");

openButton.addEventListener("click", () => {
  // Reset the return value on each open
  dialog.returnValue = "";
  updateReturnValue();
  // Show the dialog
  dialog.showModal();
});

function closeDialog(event) {
  const button = event.target;
  dialog.close(button.value);
}

function updateReturnValue() {
  log(`Return value: "${dialog.returnValue}"`);
}

declineButton.addEventListener("click", closeDialog);
acceptButton.addEventListener("click", closeDialog);

dialog.addEventListener("close", updateReturnValue);
```

#### نتیجه

روی «Open Dialog» کلیک کنید، سپس در گفتگو دکمهٔ «Accept» یا «Decline» را انتخاب کنید، یا با فشردن کلید <kbd>Esc</kbd> گفتگو را ببندید. به‌روزرسانی‌های مختلف وضعیت را مشاهده کنید.

{{ EmbedLiveSample('Checking the return value', '100%', "250px")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- عنصر HTML {{htmlelement("dialog")}}