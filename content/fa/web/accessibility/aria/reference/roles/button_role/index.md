---
title: "ARIA: button role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role"
translated_by: "n8n + AI"
---

نقش `button` برای عناصر قابل کلیک است که با فعال‌سازی توسط کاربر پاسخی را ایجاد می‌کنند. افزودن `role="button"` به صفحه‌خوان می‌گوید که عنصر یک دکمه است، اما قابلیت‌های معمول دیگر دکمه مانند رویدادهای کلیک و مدیریت صفحه‌کلید را فراهم نمی‌کند. شما می‌توانید این موارد را خود اضافه کنید، اما به طور کلی بهتر است از {{HTMLElement("button")}} یا {{HTMLElement("input")}} با `type="button"` استفاده کنید.

## توضیحات

نقش دکمه یک عنصر را به عنوان دکمه به فناوری‌های کمکی مانند صفحه‌خوان‌ها معرفی می‌کند. دکمه یک ویجت است که برای انجام کارهایی مانند ارسال فرم، باز کردن یک دیالوگ، لغو یک عمل، یا اجرای یک فرمان مانند درج رکورد جدید یا نمایش اطلاعات استفاده می‌شود. افزودن `role="button"` به فناوری کمکی می‌گوید که عنصر یک دکمه است، اما قابلیت‌های معمول دیگر دکمه مانند رویدادهای کلیک و مدیریت صفحه‌کلید را فراهم نمی‌کند. شما می‌توانید این موارد را خود اضافه کنید، اما به طور کلی بهتر است از {{HTMLElement("button")}} یا {{HTMLElement("input")}} با `type="button"` استفاده کنید.

این نقش `button` می‌تواند در ترکیب با ویژگی [`aria-pressed`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-pressed) برای [ایجاد دکمه‌های تغییر وضعیت](#toggle_buttons) استفاده شود.

```html
<div id="saveChanges" tabindex="0" role="button" aria-pressed="false">Save</div>
```

مثال بالا یک دکمه قابل تمرکز ایجاد می‌کند، اما برای ظاهر و عملکرد دکمه نیاز به JavaScript و CSS دارد. این ویژگی‌ها به طور پیش‌فرض هنگام استفاده از عناصر {{HTMLElement("button")}} و {{HTMLElement("input")}} با `type="button"` فراهم می‌شوند:

```html
<button type="button" id="saveChanges">Save</button>
```

> [!NOTE]
> اگر به جای عناصر معنایی `<button>` یا `<input type="button">` از `role="button"` استفاده می‌کنید، باید عنصر را قابل تمرکز کنید و کنترل‌کننده‌های رویداد برای {{domxref("Element/click_event", "click")}} و {{domxref("Element/keydown_event", "keydown")}} تعریف کنید. این شامل مدیریت فشار کلیدهای <kbd>Enter</kbd> و <kbd>Space</kbd> برای پردازش همه اشکال ورودی کاربر است. به [کد مثال رسمی WAI-ARIA](https://www.w3.org/WAI/ARIA/apg/patterns/button/examples/button/) مراجعه کنید.

علاوه بر ویجت دکمه معمولی، `role="button"` باید هنگام ایجاد یک دکمه تغییر وضعیت یا دکمه منو با استفاده از یک عنصر غیر دکمه گنجانده شود.

یک دکمه تغییر وضعیت یک دکمه دو حالته است که می‌تواند خاموش (فشار داده نشده) یا روشن (فشار داده شده) باشد. مقادیر ویژگی [`aria-pressed`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-pressed) برابر با `true` یا `false` یک دکمه را به عنوان دکمه تغییر وضعیت شناسایی می‌کنند.

دکمه منو یک دکمه است که یک منو را کنترل می‌کند و ویژگی [`aria-haspopup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-haspopup) آن روی `menu` یا `true` تنظیم شده است.

### همه فرزندان نمایشی هستند

برخی انواع اجزای رابط کاربری وجود دارند که وقتی در API دسترس‌پذیری پلتفرم نمایش داده می‌شوند، فقط می‌توانند حاوی متن باشند. APIهای دسترس‌پذیری راهی برای نمایش عناصر معنایی موجود در یک `button` ندارند. برای مقابله با این محدودیت، مرورگرها به طور خودکار نقش [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) را به همه عناصر فرزند هر عنصر `button` اعمال می‌کنند، زیرا این نقشی است که از فرزندان معنایی پشتیبانی نمی‌کند.

به عنوان مثال، عنصر `button` زیر را در نظر بگیرید که شامل یک عنوان است.

```html
<div role="button"><h3>Title of my button</h3></div>
```

از آنجایی که فرزندان `button` نمایشی هستند، کد زیر معادل است:

```html
<div role="button"><h3 role="presentation">Title of my button</h3></div>
```

از دیدگاه کاربر فناوری کمکی، عنوان وجود ندارد زیرا قطعه کدهای قبلی با موارد زیر در [درخت دسترس‌پذیری](/en-US/docs/Glossary/Accessibility_tree) معادل هستند:

```html
<div role="button">Title of my button</div>
```

### نقش‌ها، حالت‌ها و ویژگی‌های ARIA مرتبط

- [`aria-pressed`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-pressed)
  - : ویژگی `aria-pressed` دکمه را به عنوان یک دکمه تغییر وضعیت تعریف می‌کند. مقدار حالت دکمه را توصیف می‌کند. مقادیر شامل `aria-pressed="false"` زمانی که دکمه در حال حاضر فشار داده نشده است، `aria-pressed="true"` برای نشان دادن فشار داده شدن دکمه، و `aria-pressed="mixed"` اگر دکمه به صورت جزئی فشار داده شده در نظر گرفته شود. اگر ویژگی حذف شود یا به مقدار پیش‌فرض `aria-pressed="undefined"` تنظیم شود، عنصر از فشار دادن پشتیبانی نمی‌کند.
- [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded)
  - : اگر دکمه گروهی از عناصر دیگر را کنترل کند، حالت `aria-expanded` نشان می‌دهد که آیا گروه کنترل‌شده در حال حاضر باز است یا بسته. اگر دکمه دارای `aria-expanded="false"` باشد، گروه در حال حاضر باز نیست. اگر دکمه دارای `aria-expanded="true"` باشد، در حال حاضر باز است؛ اگر دکمه دارای `aria-expanded="undefined"` باشد یا ویژگی حذف شود، قابل باز شدن نیست.

### دکمه‌های پایه

دکمه‌ها همیشه باید یک نام قابل دسترس داشته باشند. برای اکثر دکمه‌ها، این نام همان متن داخل دکمه، بین تگ‌های باز و بسته است. در برخی موارد، مثلاً دکمه‌هایی که با آیکون نمایش داده می‌شوند، نام قابل دسترس ممکن است از ویژگی‌های [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) یا [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) تأمین شود.

### دکمه‌های تغییر وضعیت

یک دکمه تغییر وضعیت معمولاً دو حالت دارد: فشار داده شده و فشار داده نشده. یک حالت مختلط سوم نیز برای دکمه‌های تغییر وضعیتی که عناصر دیگر مانند دکمه‌های تغییر وضعیت دیگر یا چک‌باکس‌ها را کنترل می‌کنند و همه آنها مقدار یکسانی ندارند، در دسترس است. اینکه یک عنصر دکمه تغییر وضعیت است یا نه می‌تواند با ویژگی [`aria-pressed`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-pressed) علاوه بر نقش `button` (اگر عنصر از قبل یک عنصر دکمه بومی نباشد) نشان داده شود:

- اگر `aria-pressed` استفاده نشود یا روی حالت "undefined" تنظیم شود، دکمه یک دکمه تغییر وضعیت نیست.
- اگر `aria-pressed="false"` استفاده شود، دکمه یک دکمه تغییر وضعیت است که در حال حاضر فشار داده نشده است.
- اگر `aria-pressed="true"` استفاده شود، دکمه یک دکمه تغییر وضعیت است که در حال حاضر فشار داده شده است.
- اگر `aria-pressed="mixed"` استفاده شود، دکمه به صورت جزئی فشار داده شده در نظر گرفته می‌شود.

به عنوان مثال، دکمه بی‌صدا در یک پخش‌کننده صدا با برچسب "Mute" می‌تواند با تنظیم حالت `aria-pressed` روی true نشان دهد که صدا قطع شده است. برچسب یک دکمه تغییر وضعیت نباید با تغییر حالت آن تغییر کند. در مثال ما برچسب "Mute" باقی می‌ماند و صفحه‌خوان بسته به مقدار `aria-pressed` عبارت "Mute toggle button pressed" یا "Mute toggle button not pressed" را می‌خواند. اگر طراحی ایجاب می‌کرد که برچسب دکمه از "Mute" به "Unmute" تغییر کند، دکمه تغییر وضعیت مناسب نبود، بنابراین ویژگی `aria-pressed` حذف می‌شد.

### تعاملات صفحه‌کلید

| کلید              | عملکرد              |
| ---------------- | --------------------- |
| <kbd>Enter</kbd> | دکمه را فعال می‌کند. |
| <kbd>Space</kbd> | دکمه را فعال می‌کند  |

پس از فعال‌سازی دکمه، فوکوس بسته به نوع عملی که دکمه انجام می‌دهد تنظیم می‌شود. برای مثال، اگر کلیک روی دکمه یک دیالوگ باز کند، فوکوس باید به دیالوگ منتقل شود. اگر دکمه یک دیالوگ را ببندد، فوکوس باید به دکمه‌ای که دیالوگ را باز کرده بازگردد، مگر اینکه عملکرد انجام‌شده در زمینه دیالوگ به طور منطقی به عنصر دیگری منجر شود. اگر دکمه زمینه فعلی را تغییر دهد، مانند قطع و وصل صدا در یک فایل صوتی، فوکوس معمولاً روی دکمه باقی می‌ماند.

### ویژگی‌های ضروری جاوااسکریپت

#### کنترل‌کننده‌های رویداد ضروری

دکمه‌ها می‌توانند توسط کاربران ماوس، لمسی و صفحه‌کلید کار کنند. برای عناصر بومی HTML `<button>`، رویداد `onclick` دکمه برای کلیک‌های ماوس و زمانی که کاربر در حالی که دکمه فوکوس دارد کلیدهای <kbd>Space</kbd> یا <kbd>Enter</kbd> را فشار می‌دهد، فعال می‌شود. اما اگر از تگ دیگری برای ایجاد دکمه استفاده شود، رویداد `onclick` فقط زمانی فعال می‌شود که با نشانگر ماوس کلیک شود، حتی اگر از `role="button"` استفاده شده باشد. به همین دلیل، باید کنترل‌کننده‌های رویداد جداگانه‌ای برای کلید به عنصر اضافه شود تا دکمه هنگام فشار دادن کلید <kbd>Space</kbd> یا <kbd>Enter</kbd> فعال شود.

- `onclick`
  - : رویداد ناشی از فعال‌سازی دکمه با کلیک ماوس یا رویداد لمسی را مدیریت می‌کند.
- `onKeyDown`
  - : رویداد ناشی از فعال‌سازی دکمه با کلید Enter یا Space روی صفحه‌کلید را مدیریت می‌کند. (توجه: [onKeyPress منسوخ شده](/en-US/docs/Web/API/Element/keypress_event) را نه)

## مثال‌ها

### مثال دکمه پایه

در این مثال، یک عنصر span نقش `button` را دریافت کرده است. از آنجایی که از عنصر `<span>` استفاده شده است، ویژگی `tabindex` برای قابل تمرکز کردن دکمه و بخشی از ترتیب تب صفحه لازم است. استایل CSS ارائه شده برای شبیه‌سازی ظاهر دکمه به عنصر `<span>` و ارائه نشانه‌های بصری هنگام فوکوس دکمه استفاده شده است.

کنترل‌کننده‌های رویداد `handleBtnClick` و `handleBtnKeyDown` عمل دکمه را هنگام فعال‌سازی با کلیک ماوس یا کلید <kbd>Space</kbd> یا <kbd>Enter</kbd> انجام می‌دهند. در این مورد، عمل اضافه کردن یک نام جدید به لیست نام‌ها است.

مثال را با افزودن یک نام به جعبه متن امتحان کنید. دکمه باعث می‌شود نام به لیست اضافه شود.

#### HTML

```html
<h1>ARIA Button Example</h1>
<ul id="nameList"></ul>
<label for="newName">Enter your Name: </label>
<input type="text" id="newName" />
<span role="button" tabindex="0">Add Name</span>
```

#### CSS

```css
[role="button"] {
  padding: 2px;
  background-color: navy;
  color: white;
  cursor: default;
}
[role="button"]:hover,
[role="button"]:focus,
[role="button"]:active {
  background-color: white;
  color: navy;
}
ul {
  list-style: none;
}
```

#### JavaScript

```js
function handleCommand(event) {
  // Handles both mouse clicks and keyboard
  // activate with Enter or Space

  // Key presses other than Enter and Space should not trigger a command
  if (
    event instanceof KeyboardEvent &&
    event.key !== "Enter" &&
    event.key !== " "
  ) {
    return;
  }

  // Get the new name value from the input element
  const newNameInput = document.getElementById("newName");
  const name = newNameInput.value;
  newNameInput.value = ""; // clear the text field
  newNameInput.focus(); // give the text field focus to enable entering and additional name.

  // Don't add blank entries to the list.
  if (name.length > 0) {
    const listItem = document.createElement("li");
    listItem.appendChild(document.createTextNode(name));

    // Add the new name to the list.
    const list = document.getElementById("nameList");
    list.appendChild(listItem);
  }
}

const btn = document.querySelector("span[role='button']");
btn.addEventListener("click", handleCommand);
btn.addEventListener("keydown", handleCommand);
```

{{EmbedLiveSample("Basic_button_example")}}

### مثال دکمه تغییر وضعیت

در این قطعه کد، یک عنصر {{HTMLElement("span")}} با استفاده از نقش `button` و ویژگی `aria-pressed` به یک دکمه تغییر وضعیت تبدیل می‌شود. هنگامی که دکمه فعال می‌شود، مقدار `aria-pressed` حالت خود را تغییر می‌دهد؛ از `true` به `false` و دوباره برمی‌گردد.

#### HTML

```html
<button type="button">Mute Audio</button>

<span role="button" tabindex="0" aria-pressed="false"> Mute Audio </span>

<audio
  id="audio"
  src="https://soundbible.com/mp3/Tyrannosaurus%20Rex%20Roar-SoundBible.com-807702404.mp3">
  Your browser does not support the `audio` element.
</audio>
```

#### CSS

```css
button,
[role="button"] {
  padding: 3px;
  border: 2px solid transparent;
}

button:active,
button:focus,
[role="button"][aria-pressed="true"] {
  border: 2px solid black;
}
```

#### JavaScript

```js
function handleBtnClick(event) {
  toggleButton(event.target);
}

function handleBtnKeyDown(event) {
  // Check to see if space or enter were pressed
  // "Spacebar" for IE11 support
  if (event.key === " " || event.key === "Enter" || event.key === "Spacebar") {
    // Prevent the default action to stop scrolling when space is pressed
    event.preventDefault();
    toggleButton(event.target);
  }
}

function toggleButton(element) {
  const audio = document.getElementById("audio");

  // Check to see if the button is pressed
  const pressed = element.getAttribute("aria-pressed") === "true";

  // Change aria-pressed to the opposite state
  element.setAttribute("aria-pressed", !pressed);

  // Toggle the play state of the audio file
  if (pressed) {
    audio.pause();
  } else {
    audio.play();
  }
}

const button = document.querySelector("button");
const spanButton = document.querySelector("span[role='button']");
button.addEventListener("click", handleBtnClick);
button.addEventListener("keydown", handleBtnKeyDown);
spanButton.addEventListener("click", handleBtnClick);
spanButton.addEventListener("keydown", handleBtnKeyDown);
```

#### Result

{{EmbedLiveSample('Toggle_button_example')}}

## ملاحظات دسترس‌پذیری

دکمه‌ها کنترل‌های تعاملی هستند و بنابراین قابل تمرکزند. اگر نقش `button` به عنصری اضافه شود که به خودی خود قابل تمرکز نیست (مانند `<span>`، `<div>` یا `<p>`) آنگاه باید از ویژگی `tabindex` برای قابل تمرکز کردن دکمه استفاده شود.

> [!WARNING]
> هنگام علامت‌گذاری پیوندها با نقش دکمه مراقب باشید. انتظار می‌رود دکمه‌ها با استفاده از کلید <kbd>Space</kbd> یا <kbd>Enter</kbd> فعال شوند، در حالی که پیوندها با استفاده از کلید <kbd>Enter</kbd> فعال می‌شوند. به عبارت دیگر، وقتی پیوندها مانند دکمه رفتار می‌کنند، افزودن `role="button"` به تنهایی کافی نیست. همچنین باید یک کنترل‌کننده رویداد کلید اضافه شود که به کلید <kbd>Space</kbd> گوش دهد تا با دکمه‌های بومی سازگار باشد.

هنگامی که نقش `button` استفاده می‌شود، صفحه‌خوان‌ها عنصر را به عنوان یک دکمه اعلام می‌کنند، معمولاً می‌گویند "click" و سپس نام قابل دسترس دکمه. نام قابل دسترس یا محتوای عنصر است یا مقدار یک `aria-label` یا عنصری که توسط ویژگی `aria-labelledby` ارجاع داده شده است، یا توضیحات، در صورت وجود.

## بهترین روش‌ها

اگر یک پیوند عمل یک دکمه را انجام دهد، دادن نقش `button` به عنصر به کاربران فناوری کمکی کمک می‌کند تا عملکرد عنصر را درک کنند. با این حال، راه حل بهتر این است که طراحی بصری را طوری تنظیم کنید که با عملکرد و نقش ARIA مطابقت داشته باشد. در صورت امکان، توصیه می‌شود به جای نقش `button` از دکمه‌های بومی HTML (`<button>`، `<input type="button">`، `<input type="submit">`، `<input type="reset">` و `<input type="image">`) استفاده کنید، زیرا دکمه‌های بومی HTML توسط همه عامل‌های کاربر و فناوری کمکی پشتیبانی می‌شوند و به طور پیش‌فرض نیازمندی‌های صفحه‌کلید و فوکوس را بدون نیاز به سفارشی‌سازی اضافی فراهم می‌کنند.

## مشخصات

{{Specifications}}

## همچنین ببینید

- عنصر {{HTMLElement('button')}}
- عنصر {{HTMLElement("input")}}
- [`<input type="button">`](/en-US/docs/Web/HTML/Reference/Elements/input/button)
- [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit)
- [`<input type="reset">`](/en-US/docs/Web/HTML/Reference/Elements/input/reset)
- [`aria-pressed`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-pressed)
- [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded)
- [`aria-haspopup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-haspopup)
- [معناشناسی بومی قوی در HTML5](https://html.spec.whatwg.org/multipage/dom.html#aria-usage-note)
- [یادداشت‌هایی در مورد استفاده از ARIA در HTML](https://w3c.github.io/using-aria/)
- [کد مثال رسمی WAI-ARIA](https://www.w3.org/WAI/ARIA/apg/patterns/button/examples/button/)