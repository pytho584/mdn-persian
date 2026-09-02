---
title: "KeyboardEvent: key property"
short-title: key
slug: Web/API/KeyboardEvent/key
page-type: web-api-instance-property
browser-compat: api.KeyboardEvent.key
---

{{APIRef("UI Events")}}

ویژگی فقط‌خواندنی **`key`** در رابط {{domxref("KeyboardEvent")}}، مقدار کلیدی را که کاربر فشرده است برمی‌گرداند؛ به‌گونه‌ای که وضعیت کلیدهای اصلاح‌کننده مانند <kbd>Shift</kbd> و همچنین منطقه (locale) و چیدمان صفحه‌کلید را در نظر می‌گیرد.

## مقدار

یک رشته (string).

مقدار آن به صورت زیر تعیین می‌شود:

- اگر کلیدِ فشرده‌شده یک نمایشِ نوشتاری (قابل‌چاپ) داشته باشد، مقدار برگشتی یک رشته‌ی ناتهی از کاراکترهای یونیکد است که نمایشِ قابل‌چاپِ آن کلید را دربردارد. برای مثال: اگر کلید فشرده‌شده <kbd>Space</kbd> باشد، مقدار برگشتی یک فاصله (`" "`) است. اگر کلید فشرده‌شده <kbd>B</kbd> باشد، مقدار برگشتی رشته‌ی `"b"` است. با این حال، اگر هم‌زمان کلید <kbd>Shift</kbd> نیز فشرده شده باشد (یعنی {{domxref("KeyboardEvent/shiftKey", "shiftKey")}} برابر `true` باشد)، مقدار برگشتی رشته‌ی `"B"` خواهد بود.
- اگر کلید فشرده‌شده یک کلید کنترلی یا کاراکتر ویژه باشد، مقدار برگشتی یکی از [مقدارهای کلیدِ از پیش تعریف‌شده](/en-US/docs/Web/API/UI_Events/Keyboard_event_key_values) است.
- اگر {{domxref("KeyboardEvent")}} نمایانگر فشردن یک [کلید مُرده (dead key)](https://en.wikipedia.org/wiki/Dead_key) باشد، مقدار `key` باید `"Dead"` باشد.
- برخی از کلیدهای ویژه‌ی صفحه‌کلید (مانند کلیدهای گسترش‌یافته برای کنترل رسانه در صفحه‌کلیدهای چندرسانه‌ای) در ویندوز کد کلید تولید نمی‌کنند؛ در عوض، رویدادهای `WM_APPCOMMAND` را راه‌اندازی می‌کنند. این رویدادها به رویدادهای صفحه‌کلید DOM نگاشت می‌شوند و در فهرست «Virtual key codes» ویندوز قرار می‌گیرند؛ حتی اگر در واقع کد کلید نباشند.
- اگر کلید قابل شناسایی نباشد، مقدار برگشتی `Unidentified` است.

> [!CALLOUT]
>
> [فهرست کامل مقدارهای کلید را ببینید](/en-US/docs/Web/API/UI_Events/Keyboard_event_key_values).

## توالی رویدادهای KeyboardEvent

هر رویداد {{domxref("KeyboardEvent")}} در یک توالیِ از پیش تعیین‌شده صادر می‌شود. برای یک بار فشردنِ کلید مشخص، با فرض اینکه {{domxref("Event.preventDefault")}} فراخوانی نشود، توالی رویدادهای {{domxref("KeyboardEvent")}} به این صورت است:

1. ابتدا یک رویداد {{domxref("Element/keydown_event", "keydown")}} صادر می‌شود. اگر کلید همچنان نگه داشته شود و آن کلید یک کلید کاراکتری تولید کند، رویداد در بازه‌ی زمانیِ وابسته به پیاده‌سازیِ سکو (platform) به انتشار ادامه می‌دهد و ویژگی فقط‌خواندنی {{domxref("KeyboardEvent.repeat")}} روی `true` تنظیم می‌شود.
2. اگر کلیدِ فشرده‌شده یک کلید کاراکتری تولید کند که به درج شدن یک کاراکتر در یک {{HTMLElement("input")}}، {{HTMLElement("textarea")}} یا عنصری با {{domxref("HTMLElement.contentEditable")}} برابر `true` منجر شود، رویدادهای {{domxref("Element/beforeinput_event", "beforeinput")}} و {{domxref("Element/input_event", "input")}} به همین ترتیب صادر می‌شوند. توجه داشته باشید که برخی پیاده‌سازی‌های دیگر ممکن است در صورت پشتیبانی، رویداد {{domxref("Element/keypress_event", "keypress")}} را نیز صادر کنند. این رویدادها تا زمانی که کلید نگه داشته شده است، به‌طور مکرر صادر خواهند شد.
3. به محض رها شدن کلید، یک رویداد {{domxref("Element/keyup_event", "keyup")}} صادر می‌شود. با این کار فرایند کامل می‌شود.

در مرحله‌های ۱ و ۳، ویژگی `KeyboardEvent.key` تعریف شده و مطابق قواعدی که پیش‌تر بیان شد، روی مقدار مناسبی تنظیم می‌شود.

## مثالی از توالی رویدادهای KeyboardEvent

توالی رویدادهایی را در نظر بگیرید که هنگام تعامل با کلیدهای <kbd>Shift</kbd> و <kbd>2</kbd> با چیدمان صفحه‌کلید آمریکایی (U.S) در مقایسه با چیدمان صفحه‌کلید بریتانیایی (UK) تولید می‌شود.

با دو مورد آزمایشی زیر آزمایش کنید:

1. کلید <kbd>Shift</kbd> را فشار دهید و نگه دارید، سپس <kbd>2</kbd> را فشار دهید و رها کنید. در ادامه، کلید <kbd>Shift</kbd> را رها کنید.
2. کلید <kbd>Shift</kbd> را فشار دهید و نگه دارید، سپس <kbd>2</kbd> را فشار دهید و نگه دارید. کلید <kbd>Shift</kbd> را رها کنید. در نهایت، <kbd>2</kbd> را رها کنید.

### HTML

```html
<div class="fx">
  <div>
    <textarea rows="5" name="test-target" id="test-target"></textarea>
    <button type="button" name="btn-reset" id="btn-reset">Reset</button>
  </div>
  <div class="flex">
    <pre id="console-log"></pre>
  </div>
</div>
```

### CSS

```css
.fx {
  -webkit-display: flex;
  display: flex;
  margin-left: -20px;
  margin-right: -20px;
}

.fx > div {
  padding-left: 20px;
  padding-right: 20px;
}

.fx > div:first-child {
  width: 30%;
}

.flex {
  -webkit-flex: 1;
  flex: 1;
}

#test-target {
  display: block;
  width: 100%;
  margin-bottom: 10px;
}
```

### JavaScript

```js
const textarea = document.getElementById("test-target");
const consoleLog = document.getElementById("console-log");
const btnReset = document.getElementById("btn-reset");

function logMessage(message) {
  consoleLog.innerText += `${message}\n`;
}

textarea.addEventListener("keydown", (e) => {
  if (!e.repeat) {
    logMessage(`Key "${e.key}" pressed [event: keydown]`);
  } else {
    logMessage(`Key "${e.key}" repeating [event: keydown]`);
  }
});

textarea.addEventListener("beforeinput", (e) => {
  logMessage(`Key "${e.data}" about to be input [event: beforeinput]`);
});

textarea.addEventListener("input", (e) => {
  logMessage(`Key "${e.data}" input [event: input]`);
});

textarea.addEventListener("keyup", (e) => {
  logMessage(`Key "${e.key}" released [event: keyup]`);
});

btnReset.addEventListener("click", (e) => {
  let child = consoleLog.firstChild;
  while (child) {
    consoleLog.removeChild(child);
    child = consoleLog.firstChild;
  }
  textarea.value = "";
});
```

### نتیجه

{{EmbedLiveSample('KeyboardEvent_sequence_example')}}

> [!NOTE]
> در مرورگرهایی که رابط {{domxref("InputEvent")}} را به‌طور کامل پیاده‌سازی نمی‌کنند — رابطی که برای رویدادهای {{domxref("Element/beforeinput_event", "beforeinput")}} و {{domxref("Element/input_event", "input")}} استفاده می‌شود — ممکن است خروجیِ آن خطوط در لاگ نادرست باشد.

### مورد ۱

هنگامی که کلید Shift فشرده می‌شود، ابتدا یک رویداد {{domxref("Element/keydown_event", "keydown")}} صادر می‌شود و مقدار ویژگی `key` روی رشته‌ی `Shift` تنظیم می‌شود. تا زمانی که این کلید را نگه می‌داریم، رویداد {{domxref("Element/keydown_event", "keydown")}} به‌طور مکرر صادر نمی‌شود؛ زیرا این کلید، کلید کاراکتری تولید نمی‌کند.

هنگامی که کلید 2 فشرده می‌شود، رویداد {{domxref("Element/keydown_event", "keydown")}} دیگری نیز برای این فشردنِ جدید صادر می‌شود. به دلیل فعال بودن کلید اصلاح‌کننده‌ی `shift`، مقدار ویژگی `key` در این رویداد، برای چیدمان صفحه‌کلید آمریکایی رشته‌ی `@` و برای چیدمان صفحه‌کلید بریتانیایی رشته‌ی `"` است. سپس، چون یک کلید کاراکتری تولید شده است، رویدادهای {{domxref("Element/beforeinput_event", "beforeinput")}} و {{domxref("Element/input_event", "input")}} صادر می‌شوند.

هنگامی که کلید 2 را رها می‌کنیم، یک رویداد {{domxref("Element/keyup_event", "keyup")}} صادر می‌شود و ویژگی `key` مقدارهای رشته‌ای `@` و `"` را به‌ترتیب برای آن دو چیدمان مختلف صفحه‌کلید حفظ می‌کند.

در نهایت، وقتی کلید shift را رها می‌کنیم، رویداد {{domxref("Element/keyup_event", "keyup")}} دیگری برای آن صادر می‌شود و مقدار ویژگی `key` همچنان `Shift` باقی می‌ماند.

### مورد ۲

هنگامی که کلید Shift فشرده می‌شود، ابتدا یک رویداد {{domxref("Element/keydown_event", "keydown")}} صادر می‌شود و مقدار ویژگی `key` روی رشته‌ی `Shift` تنظیم می‌شود. تا وقتی این کلید را نگه می‌داریم، رویداد {{domxref("Element/keydown_event", "keydown")}} به‌طور مکرر صادر نمی‌شود؛ زیرا هیچ کلید کاراکتری تولید نکرده است.

هنگامی که کلید 2 فشرده می‌شود، رویداد {{domxref("Element/keydown_event", "keydown")}} دیگری برای این فشردنِ جدید صادر می‌شود. به دلیل فعال بودن کلید اصلاح‌کننده‌ی `shift`، مقدار ویژگی `key` در این رویداد، برای چیدمان صفحه‌کلید آمریکایی `@` و برای چیدمان صفحه‌کلید بریتانیایی `"` خواهد بود. سپس، چون یک کلید کاراکتری تولید شده است، رویدادهای {{domxref("Element/beforeinput_event", "beforeinput")}} و {{domxref("Element/input_event", "input")}} صادر می‌شوند. تا وقتی که کلید را نگه داشته‌ایم، رویداد {{domxref("Element/keydown_event", "keydown")}} به‌طور مکرر صادر می‌شود و ویژگی {{domxref("KeyboardEvent.repeat")}} روی `true` تنظیم است. رویدادهای {{domxref("Element/beforeinput_event", "beforeinput")}} و {{domxref("Element/input_event", "input")}} نیز به‌طور مکرر صادر می‌شوند.

هنگامی که کلید Shift را رها می‌کنیم، یک رویداد {{domxref("Element/keyup_event", "keyup")}} برای آن صادر می‌شود و مقدار ویژگی `key` همچنان `Shift` است. در این مرحله توجه کنید که ویژگی `key` در رویداد keydown تکراریِ مربوط به فشردن کلید 2، حالا `"2"` است؛ زیرا کلید اصلاح‌کننده‌ی `shift` دیگر فعال نیست. در مورد ویژگی {{domxref("InputEvent.data")}} رویدادهای {{domxref("Element/beforeinput_event", "beforeinput")}} و {{domxref("Element/input_event", "input")}} نیز وضعیت به همین صورت است.

در نهایت، وقتی کلید 2 را رها می‌کنیم، یک رویداد {{domxref("Element/keyup_event", "keyup")}} صادر می‌شود؛ اما چون کلید اصلاح‌کننده‌ی `shift` دیگر فعال نیست، ویژگی `key` برای هر دو چیدمان صفحه‌کلید روی مقدار رشته‌ای `2` تنظیم خواهد شد.

## مثال‌ها

در این مثال از {{domxref("EventTarget.addEventListener()")}} برای گوش دادن به رویدادهای {{domxref("Element/keydown_event", "keydown")}} استفاده شده است. هنگام وقوع این رویدادها، مقدار `key` بررسی می‌شود تا مشخص شود آیا یکی از کلیدهایی است که کد با آن‌ها کاری دارد یا نه؛ اگر بله، آن کلید به شکلی پردازش می‌شود (مثلاً برای هدایت یک فضاپیما یا تغییر سلول انتخاب‌شده در یک صفحه‌گسترده).

```js
window.addEventListener("keydown", (event) => {
  if (event.defaultPrevented) {
    return; // Do nothing if the event was already processed
  }

  switch (event.key) {
    case "ArrowDown":
      // Do something for "down arrow" key press.
      break;
    case "ArrowUp":
      // Do something for "up arrow" key press.
      break;
    case "ArrowLeft":
      // Do something for "left arrow" key press.
      break;
    case "ArrowRight":
      // Do something for "right arrow" key press.
      break;
    case "Enter":
      // Do something for "enter" or "return" key press.
      break;
    case " ":
      // Do something for "space" key press.
      break;
    case "Escape":
      // Do something for "esc" key press.
      break;
    default:
      return; // Quit when this doesn't handle the key event.
  }

  // Cancel the default action to avoid it being handled twice
  event.preventDefault();
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
