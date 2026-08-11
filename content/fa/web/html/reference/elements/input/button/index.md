---
title: "<input type=\"button\"> HTML attribute value"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/button"
translated_by: "n8n + AI"
---

عناصر `<input>` با نوع **`button`** به‌صورت دکمه‌های فشاری رندر می‌شوند. با اختصاص دادن یک تابع مدیریت رویداد (معمولاً برای رویداد `click`)، می‌توان از آن‌ها برای کنترل عملکرد دلخواه در هر نقطه از صفحه وب استفاده کرد.

> [!NOTE]
> در حالی که عناصر `<input>` با نوع `button` همچنان HTML معتبر هستند، عنصر جدیدتر `<button>` روش ترجیحی برای ایجاد دکمه‌ها است. از آنجا که متن برچسب `<button>` بین تگ باز و بسته قرار می‌گیرد، می‌توانید HTML را در برچسب قرار دهید، حتی تصاویر.

## مقدار

### دکمه با `value`

ویژگی [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) در یک `<input type="button">` یک رشته است که به‌عنوان برچسب دکمه استفاده می‌شود. مقدار `value` همچنین به‌عنوان accessible description برای دکمه عمل می‌کند.

```html
<input type="button" value="Click Me" />
```

### دکمه بدون `value`

اگر `value` را مشخص نکنید، یک دکمه خالی دریافت می‌کنید:

```html
<input type="button" />
```

## استفاده از دکمه‌ها

عناصر `<input type="button">` رفتار پیش‌فرضی ندارند (هم‌خانواده‌های آن‌ها، `<input type="submit">` و [`<input type="reset">`](/en-US/docs/Web/HTML/Reference/Elements/input/reset) به‌ترتیب برای ارسال و بازنشانی فرم‌ها استفاده می‌شوند). برای اینکه دکمه‌ها کاری انجام دهند، باید کد جاوااسکریپت بنویسید.

### یک دکمه ساده

ما با ایجاد یک دکمه ساده شروع می‌کنیم که دارای رویداد `click` است و ماشین را روشن می‌کند (در واقع، مقدار `value` دکمه و متن پاراگراف بعدی را تغییر می‌دهد):

```html
<form>
  <input type="button" value="Start machine" />
</form>
<p>The machine is stopped.</p>
```

```js
const button = document.querySelector("input");
const paragraph = document.querySelector("p");

button.addEventListener("click", updateButton);

function updateButton() {
  if (button.value === "Start machine") {
    button.value = "Stop machine";
    paragraph.textContent = "The machine has started!";
  } else {
    button.value = "Start machine";
    paragraph.textContent = "The machine is stopped.";
  }
}
```

اسکریپت ارجاعی به آبجکت `HTMLInputElement` که نمایانگر `<input>` در DOM است را در متغیر `button` ذخیره می‌کند. سپس از `addEventListener()` استفاده می‌شود تا تابعی تعریف شود که هنگام رخ دادن رویداد `click` روی دکمه اجرا شود.

### افزودن میان‌برهای صفحه‌کلید به دکمه‌ها

کلیدهای میانبر (keyboard shortcuts) که با نام‌های access keys یا keyboard equivalents هم شناخته می‌شوند، به کاربر اجازه می‌دهند با فشردن یک کلید یا ترکیبی از کلیدها روی صفحه‌کلید، یک دکمه را فعال کند. برای افزودن کلید میانبر به یک دکمه — درست مثل هر {{HTMLElement("input")}} دیگری که این کار برایش منطقی است — از attribute سراسری [`accesskey`](/en-US/docs/Web/HTML/Reference/Global_attributes/accesskey) استفاده می‌کنید.

در این مثال، کلید <kbd>s</kbd> به عنوان access key تعیین شده (باید کلید <kbd>s</kbd> را به همراه کلیدهای اصلاح‌کننده‌ی مخصوص مرورگر/سیستم‌عامل خود فشار دهید؛ لیست کاملی از این ترکیب‌ها را در صفحه [accesskey](/en-US/docs/Web/HTML/Reference/Global_attributes/accesskey) ببینید).

```html
<form>
  <input type="button" value="Start machine" accesskey="s" />
</form>
<p>The machine is stopped.</p>
```

```js hidden
const button = document.querySelector("input");
const paragraph = document.querySelector("p");

button.addEventListener("click", updateButton);

function updateButton() {
  if (button.value === "Start machine") {
    button.value = "Stop machine";
    paragraph.textContent = "The machine has started!";
  } else {
    button.value = "Start machine";
    paragraph.textContent = "The machine is stopped.";
  }
}
```

> **نکته:** مشکل مثال بالا این است که کاربر دقیقاً نمی‌داند access key چیست! در یک سایت واقعی باید این اطلاعات را به گونه‌ای ارائه دهید که با طراحی سایت تداخل نداشته باشد (مثلاً با ارائه یک لینک ساده که به صفحه‌ای با اطلاعات access keys سایت اشاره می‌کند).

### غیرفعال و فعال کردن یک دکمه

برای غیرفعال کردن یک دکمه، attribute سراسری [`disabled`](/en-US/docs/Web/HTML/Reference/Attributes/disabled) را روی آن قرار دهید:

```html
<input type="button" value="Disable me" disabled />
```

#### تنظیم attribute disabled

می‌توانید دکمه‌ها را در زمان اجرا با تنظیم `disabled` روی `true` یا `false` فعال یا غیرفعال کنید. در این مثال، دکمه در ابتدا فعال است، اما اگر آن را فشار دهید، با `button.disabled = true` غیرفعال می‌شود. سپس یک تابع {{domxref("Window.setTimeout", "setTimeout()")}} بعد از دو ثانیه دکمه را دوباره به حالت فعال برمی‌گرداند.

```html
<input type="button" value="Enabled" />
```

```js
const button = document.querySelector("input");

button.addEventListener("click", disableButton);

function disableButton() {
  button.disabled = true;
  button.value = "Disabled";
  setTimeout(() => {
    button.disabled = false;
    button.value = "Enabled";
  }, 2000);
}
```

#### ارث‌بری وضعیت disabled

اگر attribute `disabled` مشخص نشده باشد، دکمه وضعیت `disabled` خود را از عنصر والدش به ارث می‌برد. این امکان را فراهم می‌کند که گروهی از عناصر را یک‌باره با قرار دادن آنها در یک کانتینر مثل {{HTMLElement("fieldset")}} و سپس تنظیم `disabled` روی کانتینر، فعال یا غیرفعال کنید.

مثال زیر این کار را نشان می‌دهد. بسیار شبیه مثال قبلی است، با این تفاوت که وقتی اولین دکمه فشار داده می‌شود، attribute `disabled` روی `<fieldset>` تنظیم می‌شود — این باعث می‌شود هر سه دکمه تا پایان زمان دو ثانیه‌ای غیرفعال بمانند.

```html
<fieldset>
  <legend>Button group</legend>
  <input type="button" value="Button 1" />
  <input type="button" value="Button 2" />
  <input type="button" value="Button 3" />
</fieldset>
```

```js
const button = document.querySelector("input");
const fieldset = document.querySelector("fieldset");

button.addEventListener("click", disableButton);

function disableButton() {
  fieldset.disabled = true;
  setTimeout(() => {
    fieldset.disabled = false;
  }, 2000);
}
```

> **نکته:** برخلاف سایر مرورگرها، فایرفاکس حالت غیرفعال (`disabled`) یک عنصر `<input>` را حتی پس از بارگذاری مجدد صفحه حفظ می‌کند. به‌عنوان راه‌حل، ویژگی `autocomplete` را روی `off` تنظیم کنید. (برای جزئیات بیشتر به [Firefox bug 654072](https://bugzil.la/654072) مراجعه کنید.)

## اعتبارسنجی

دکمه‌ها در اعتبارسنجی محدودیت‌ها (Constraint Validation) شرکت نمی‌کنند؛ مقدار واقعی برای اعمال محدودیت ندارند.

## مثال‌ها

مثال زیر یک اپلیکیشن نقاشی بسیار ساده را نشان می‌دهد که با یک عنصر `<canvas>` و مقداری CSS و JavaScript ساخته شده است (برای اختصار، CSS را مخفی کرده‌ایم). دو کنترل بالایی به شما امکان انتخاب رنگ و اندازه قلم نقاشی را می‌دهند. با کلیک روی دکمه، تابعی فراخوانی می‌شود که بوم (canvas) را پاک می‌کند.

```html
<div class="toolbar">
  <input type="color" aria-label="select pen color" />
  <input
    type="range"
    min="2"
    max="50"
    value="30"
    aria-label="select pen size" /><span class="output">30</span>
  <input type="button" value="Clear canvas" />
</div>

<canvas class="myCanvas">
  <p>Add suitable fallback here.</p>
</canvas>
```

```css hidden
body {
  background: #cccccc;
  margin: 0;
  overflow: hidden;
}

.toolbar {
  background: #cccccc;
  width: 150px;
  height: 75px;
  padding: 5px;
}

input[type="color"],
input[type="button"] {
  width: 90%;
  margin: 0 auto;
  display: block;
}

input[type="range"] {
  width: 70%;
}

span {
  position: relative;
  bottom: 5px;
}
```

```js
const canvas = document.querySelector(".myCanvas");
const width = (canvas.width = window.innerWidth);
const height = (canvas.height = window.innerHeight - 85);
const ctx = canvas.getContext("2d");

ctx.fillStyle = "rgb(0 0 0)";
ctx.fillRect(0, 0, width, height);

const colorPicker = document.querySelector('input[type="color"]');
const sizePicker = document.querySelector('input[type="range"]');
const output = document.querySelector(".output");
const clearBtn = document.querySelector('input[type="button"]');

// covert degrees to radians
function degToRad(degrees) {
  return (degrees * Math.PI) / 180;
}

// update size picker output value

sizePicker.oninput = () => {
  output.textContent = sizePicker.value;
};

// store mouse pointer coordinates, and whether the button is pressed
let curX;
let curY;
let pressed = false;

// update mouse pointer coordinates
document.onmousemove = (e) => {
  curX = e.pageX;
  curY = e.pageY;
};

canvas.onmousedown = () => {
  pressed = true;
};

canvas.onmouseup = () => {
  pressed = false;
};

clearBtn.onclick = () => {
  ctx.fillStyle = "rgb(0 0 0)";
  ctx.fillRect(0, 0, width, height);
};

function draw() {
  if (pressed) {
    ctx.fillStyle = colorPicker.value;
    ctx.beginPath();
    ctx.arc(
      curX,
      curY - 85,
      sizePicker.value,
      degToRad(0),
      degToRad(360),
      false,
    );
    ctx.fill();
  }

  requestAnimationFrame(draw);
}

draw();
```

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <td><strong><a href="#value">Value</a></strong></td>
      <td>یک رشته (String) که به‌عنوان برچسب دکمه استفاده می‌شود.</td>
    </tr>
    <tr>
      <td><strong>رویدادها</strong></td>
      <td><code>click</code></td>
    </tr>
    <tr>
      <td><strong>ویژگی‌های رایج پشتیبانی‌شده</strong></td>
      <td>
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#type"><code>type</code></a> و
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#value"><code>value</code></a>
      </td>
    </tr>
    <tr>
      <td><strong>ویژگی‌های IDL</strong></td>
      <td><code>value</code></td>
    </tr>
    <tr>
      <td><strong>رابط DOM</strong></td>
      <td><p><code>HTMLInputElement</code></p></td>
    </tr>
    <tr>
      <td><strong>نقش ARIA ضمنی</strong></td>
      <td><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role"><code>button</code></a></td>
    </tr>
  </tbody>
</table>

## سازگاری مرورگر

## همچنین ببینید

- المان `<input>` و رابط `HTMLInputElement` که آن را پیاده‌سازی می‌کند.
- المان جدیدتر `<button>`.