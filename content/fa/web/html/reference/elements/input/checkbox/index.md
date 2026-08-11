---
title: "<input type=\"checkbox\"> HTML attribute value"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/checkbox"
translated_by: "n8n + AI"
---

عنصر `<input>` با نوع **`checkbox`** به‌صورت پیش‌فرض به شکل کادرهایی نمایش داده می‌شود که هنگام فعال‌سازی علامت می‌خورند؛ مانند آنچه در فرم‌های کاغذی دولتی می‌بینید. ظاهر دقیق آن به تنظیمات سیستم عاملی بستگی دارد که مرورگر در آن اجرا می‌شود. معمولاً این کادر مربع است، اما ممکن است گوشه‌های گرد داشته باشد. چک‌باکس به شما امکان می‌دهد مقدار مشخصی را برای ارسال در فرم انتخاب کنید (یا نه).

```html
<fieldset>
  <legend>Choose your monster's features:</legend>

  <div>
    <input type="checkbox" id="scales" name="scales" checked />
    <label for="scales">Scales</label>
  </div>

  <div>
    <input type="checkbox" id="horns" name="horns" />
    <label for="horns">Horns</label>
  </div>
</fieldset>
```

```css
p,
label {
  font:
    1rem "Fira Sans",
    sans-serif;
}

input {
  margin: 0.4rem;
}
```

> **نکته:**
> [دکمه‌های رادیویی](/en-US/docs/Web/HTML/Reference/Elements/input/radio) مشابه چک‌باکس هستند، اما یک تفاوت مهم دارند — [دکمه‌های رادیویی با نام یکسان](/en-US/docs/Web/HTML/Reference/Elements/input/radio#defining_a_radio_group) در یک مجموعه گروه‌بندی می‌شوند که در آن فقط یک دکمه رادیویی در هر زمان می‌تواند انتخاب شود، در حالی که چک‌باکس‌ها به شما امکان می‌دهند مقادیر جداگانه را روشن یا خاموش کنید. در جایی که چند کنترل با نام یکسان وجود دارند، دکمه‌های رادیویی فقط اجازه انتخاب یک مورد را از بین همه می‌دهند، در حالی که چک‌باکس‌ها امکان انتخاب چند مقدار را فراهم می‌کنند.

## مقدار

یک رشته (string) که مقدار چک‌باکس را نشان می‌دهد. این مقدار در سمت کلاینت نمایش داده نمی‌شود، اما در سمت سرور، `value` داده‌ای است که همراه با `name` چک‌باکس ارسال می‌شود. به مثال زیر توجه کنید:

```html
<form>
  <div>
    <input
      type="checkbox"
      id="subscribeNews"
      name="subscribe"
      value="newsletter" />
    <label for="subscribeNews">Subscribe to newsletter?</label>
  </div>
  <div>
    <button type="submit">Subscribe</button>
  </div>
</form>
```

در این مثال، `name` برابر با `subscribe` و `value` برابر با `newsletter` است. وقتی فرم ارسال می‌شود، جفت نام/مقدار به صورت `subscribe=newsletter` خواهد بود.

اگر ویژگی `value` حذف شود، مقدار پیش‌فرض چک‌باکس `on` خواهد بود، بنابراین داده ارسالی در این حالت `subscribe=on` است.

> **نکته:**
> اگر چک‌باکس هنگام ارسال فرم بدون علامت باشد، نه `name` و نه `value` به سرور ارسال نمی‌شود. هیچ روش صرفاً مبتنی بر HTML برای نمایش حالت بدون علامت چک‌باکس وجود ندارد (مثلاً `value=unchecked`). اگر می‌خواهید وقتی چک‌باکس بدون علامت است، یک مقدار پیش‌فرض ارسال کنید، می‌توانید از JavaScript برای ایجاد یک `<input type="hidden">` در فرم استفاده کنید که مقدار آن حالت بدون علامت را نشان می‌دهد.

## ویژگی‌های اضافی

علاوه بر [ویژگی‌های مشترک](/en-US/docs/Web/HTML/Reference/Elements/input#attributes) که بین همه عناصر `<input>` مشترک است، ورودی‌های `checkbox` از ویژگی‌های زیر پشتیبانی می‌کنند.

- `checked`
  - : یک ویژگی [boolean](/en-US/docs/Glossary/Boolean/HTML) که مشخص می‌کند آیا این checkbox به‌طور پیش‌فرض (هنگام بارگذاری صفحه) علامت‌خورده است یا خیر. این ویژگی _نشان نمی‌دهد_ که checkbox در حال حاضر علامت‌خورده است: اگر وضعیت checkbox تغییر کند، این ویژگی محتوایی (content attribute) تغییر را منعکس نمی‌کند. (فقط ویژگی IDL `checked` متعلق به `HTMLInputElement` به‌روز می‌شود.)

    > [!NOTE]
    > برخلاف سایر کنترل‌های ورودی، مقدار یک checkbox تنها در صورتی در داده‌های ارسالی گنجانده می‌شود که checkbox در حال حاضر `checked` باشد. اگر چنین باشد، مقدار ویژگی `value` آن checkbox به‌عنوان مقدار ورودی گزارش می‌شود، یا اگر `value` تنظیم نشده باشد، مقدار `on` گزارش می‌شود.
    > برخلاف سایر مرورگرها، Firefox به‌طور پیش‌فرض [حالت checked پویا](https://stackoverflow.com/questions/5985839/bug-with-firefox-disabled-attribute-of-input-not-resetting-when-refreshing) یک `<input>` را در طول بارگذاری مجدد صفحه حفظ می‌کند. از ویژگی [`autocomplete`](/en-US/docs/Web/HTML/Reference/Elements/input#autocomplete) برای کنترل این ویژگی استفاده کنید.

- `value`
  - : ویژگی `value` یکی از ویژگی‌های مشترک همه‌ی `<input>`ها است؛ اما برای ورودی‌های از نوع `checkbox` کاربرد ویژه‌ای دارد: هنگامی که یک فرم ارسال می‌شود، تنها checkboxهایی که در حال حاضـر `checked` هستند به سرور ارسال می‌شوند و مقدار گزارش‌شده همان مقدار ویژگی `value` است. اگر `value` مشخص نشده باشد، مقدار پیش‌فرض رشته‌ی `on` است. این موضوع در بخش [Value](#value) در بالا نشان داده شده است.

- `switch`
  - : یک ویژگی [boolean](/en-US/docs/Glossary/Boolean/HTML) که فقط برای ورودی‌های `checkbox` کاربرد دارد. وقتی وجود داشته باشد، نشان می‌دهد که این `checkbox` به‌جای یک `checkbox` معمولی، یک کلید روشن/خاموش (`switch`) است. ظاهر کنترل `checkbox` را تغییر می‌دهد، اما رفتار اصلی آن همانند یک `checkbox` معمولی باقی می‌ماند.

    > [!NOTE]
    > این ویژگی به عامل‌های کاربر اجازه می‌دهد تا معنای ARIA `switch` را برای فناوری‌های کمکی افشا کنند — بدون اینکه نیاز باشد سند به‌صراحت `role="switch"` را مشخص کند. نشانه‌گذاری (markup) و API مشابه checkboxها هستند، با این تفاوت که شبه‌کلاس `:indeterminate` هرگز با آن مطابقت نمی‌کند.

    > [!WARNING]
    > این ویژگی هنوز آزمایشی است و پشتیبانی مرورگر محدودی دارد. در مرورگرهای ناسازگار، این ویژگی نادیده گرفته می‌شود.

## استفاده از ورودی‌های checkbox

قبلاً ساده‌ترین کاربرد checkboxها را پوشش دادیم. حالا بیایید به سایر ویژگی‌ها و تکنیک‌های رایج مرتبط با checkbox که نیاز خواهید داشت نگاهی بیندازیم.

### مدیریت چندین checkbox

مثالی که در بالا دیدیم فقط یک checkbox داشت؛ در موقعیت‌های واقعی، احتمالاً با چندین checkbox مواجه خواهید شد. اگر کاملاً نامرتبط باشند، می‌توانید هرکدام را جداگانه مدیریت کنید، همانطور که در بالا نشان داده شد. اما اگر همه مرتبط باشند، اوضاع به این سادگی نیست.

برای مثال، در دموی زیر چندین checkbox قرار داده‌ایم تا کاربر بتواند علایق خود را انتخاب کند (نسخه‌ی کامل را در بخش [Examples](#examples) ببینید).

```html
<fieldset>
  <legend>Choose your interests</legend>
  <div>
    <input type="checkbox" id="coding" name="interest" value="coding" />
    <label for="coding">Coding</label>
  </div>
  <div>
    <input type="checkbox" id="music" name="interest" value="music" />
    <label for="music">Music</label>
  </div>
</fieldset>
```

در این مثال می‌بینید که به هر checkbox یک `name` یکسان داده‌ایم. اگر هر دو checkbox علامت‌خورده باشند و سپس فرم ارسال شود، یک رشته از جفت‌های name/value مانند این دریافت خواهید کرد: `interest=coding&interest=music`. وقتی این رشته به سرور می‌رسد، باید آن را به‌جای یک آرایه‌ی انجمنی (associative array) به‌گونه‌ای تجزیه کنید که همه‌ی مقادیر `interest`، نه فقط آخرین مقدار، گرفته شوند. برای مثال، برای یک تکنیک مورد استفاده در Python، به [Handle Multiple Checkboxes with a Single Serverside Variable](https://stackoverflow.com/questions/18745456/handle-multiple-checkboxes-with-a-single-serverside-variable) مراجعه کنید.

### علامت‌گذاری پیش‌فرض جعبه‌ها

برای اینکه یک checkbox به‌صورت پیش‌فرض تیک‌خورده باشد، کافی است attribute ای به نام `checked` به آن بدهید. مثال زیر را ببینید:

```html
<fieldset>
  <legend>Choose your interests</legend>
  <div>
    <input type="checkbox" id="coding" name="interest" value="coding" checked />
    <label for="coding">Coding</label>
  </div>
  <div>
    <input type="checkbox" id="music" name="interest" value="music" />
    <label for="music">Music</label>
  </div>
</fieldset>
```

### استفاده از checkbox به‌عنوان کلید روشن/خاموش

مثال زیر نشان می‌دهد که چطور می‌توان یک checkbox را طوری نمایش داد و نگه داشت که مثل یک کلید روشن/خاموش (on/off) دیده و عمل کند.

```html
<form>
  <fieldset>
    <legend>Adjust your setting</legend>
    <div>
      <label for="theme">Dark mode</label>
      <input type="checkbox" name="theme" id="theme" switch checked />
    </div>
    <div>
      <label for="notifications">Notifications</label>
      <input type="checkbox" name="notifications" id="notifications" switch />
    </div>
    <button type="submit">Submit</button>
  </fieldset>
</form>
```

> [!NOTE]
> در حالی که تنها برخی از مرورگرها checkbox را به‌صورت سوییچ نمایش می‌دهند، رفتار آن در همه مرورگرها یکسان است.

### ایجاد ناحیهٔ کلیک بزرگ‌تر برای checkbox ها

در مثال‌های بالا، شاید متوجه شده باشید که می‌توانید یک checkbox را هم با کلیک روی خود checkbox و هم با کلیک روی عنصر `<label>` مرتبط با آن toggle کنید. این یک قابلیت بسیار کاربردی در label های فرم HTML است که انتخاب گزینهٔ موردنظر را آسان‌تر می‌کند، به‌ویژه در دستگاه‌های با صفحهٔ کوچک مثل گوشی‌های هوشمند.

علاوه بر دسترس‌پذیری (accessibility)، این مورد دلیل خوب دیگری برای تنظیم درست عناصر `<label>` در فرم‌هایتان است.

### حالت Indeterminate در checkbox ها

یک checkbox می‌تواند در حالت **indeterminate** باشد. این حالت با استفاده از property ای به نام [`indeterminate`](/en-US/docs/Web/API/HTMLInputElement/indeterminate) در شیء `HTMLInputElement` و از طریق JavaScript تنظیم می‌شود (نمی‌توان آن را با یک HTML attribute تنظیم کرد):

```js
inputInstance.indeterminate = true;
```

> [!NOTE]
> این صرفاً یک تغییر ظاهری است. هیچ تأثیری بر استفاده شدن `value` مربوط به checkbox در ارسال فرم ندارد. این موضوع با توجه به حالت `checked` تعیین می‌شود، مستقل از حالت `indeterminate`.

کاربردهای زیادی برای این property وجود ندارد. رایج‌ترین حالت، وقتی است که یک checkbox مالک چند زیرگزینه (که آن‌ها هم checkbox هستند) باشد. اگر همهٔ زیرگزینه‌ها تیک خورده باشند، checkbox والد نیز تیک می‌خورد؛ اگر همه تیک نخورده باشند، checkbox والد نیز تیک نخورده است. اگر یک یا چند زیرگزینه وضعیتی متفاوت از بقیه داشته باشند، checkbox والد در حالت indeterminate قرار می‌گیرد.

این موضوع را می‌توانید در مثال زیر ببینید (با تشکر از [CSS Tricks](https://css-tricks.com/indeterminate-checkboxes/) برای الهام). در این مثال، مواد اولیه‌ای را که برای یک دستور پخت جمع‌آوری می‌کنیم، پیگیری می‌کنیم. وقتی checkbox یک ماده را تیک می‌زنید یا تیک آن را برمی‌دارید، یک تابع JavaScript تعداد مواد تیک‌خورده را بررسی می‌کند:

- اگر هیچ‌کدام تیک نخورده باشند، checkbox نام دستور پخت روی حالت unchecked قرار می‌گیرد.
- اگر یکی یا دو مورد تیک خورده باشند، checkbox نام دستور پخت روی حالت `indeterminate` قرار می‌گیرد.
- اگر هر سه تیک خورده باشند، checkbox نام دستور پخت روی حالت `checked` قرار می‌گیرد.

بنابراین در این حالت، `indeterminate` برای نشان دادن این استفاده می‌شود که جمع‌آوری مواد شروع شده، اما دستور پخت هنوز کامل نشده است.

```js live-sample___indeterminate_state
const overall = document.querySelector("#enchantment");
const ingredients = document.querySelectorAll("ul input");

overall.addEventListener("click", (e) => {
  e.preventDefault();
});

for (const ingredient of ingredients) {
  ingredient.addEventListener("click", updateDisplay);
}
```

```js
function updateDisplay() {
  let checkedCount = 0;
  for (const ingredient of ingredients) {
    if (ingredient.checked) {
      checkedCount++;
    }
  }

  if (checkedCount === 0) {
    overall.checked = false;
    overall.indeterminate = false;
  } else if (checkedCount === ingredients.length) {
    overall.checked = true;
    overall.indeterminate = false;
  } else {
    overall.checked = false;
    overall.indeterminate = true;
  }
}
```

```html live-sample___indeterminate_state
<form>
  <fieldset>
    <legend>Complete the recipe</legend>
    <div>
      <input type="checkbox" id="enchantment" name="enchantment" />
      <label for="enchantment">Enchantment table</label>
      <ul>
        <li>
          <input type="checkbox" id="book" name="ingredient" value="book" />
          <label for="book">Book</label>
        </li>
        <li>
          <input
            type="checkbox"
            id="diamonds"
            name="ingredient"
            value="diamonds" />
          <label for="diamonds">Diamonds (x2)</label>
        </li>
        <li>
          <input
            type="checkbox"
            id="obsidian"
            name="ingredient"
            value="obsidian" />
          <label for="obsidian">Obsidian (x4)</label>
        </li>
      </ul>
    </div>
  </fieldset>
</form>
```

## اعتبارسنجی

چکباکسها از اعتبارسنجی پشتیبانی میکنند (این قابلیت برای همهٔ inputها ارائه شده). با این حال، بیشتر `ValidityState`ها همیشه `false` هستند. اگر چکباکس دارای attribute به نام [`required`](/en-US/docs/Web/HTML/Reference/Elements/input#required) باشد، اما تیک نخورده باشد، `ValidityState.valueMissing` برابر با `true` خواهد بود.

## مثال‌ها

مثال زیر نسخهٔ توسعه‌یافته‌ای از مثال «چک‌باکس‌های متعدد» است که در بالا دیدیم. گزینه‌های استاندارد بیشتری دارد و علاوه بر آن، یک چک‌باکس «سایر» (Other) نیز دارد؛ با تیک زدن این چک‌باکس، یک فیلد متنی برای وارد کردن مقدار «سایر» ظاهر می‌شود. این کار با یک بلوک کوتاه JavaScript انجام شده است. این مثال شامل labelهای ضمنی است؛ یعنی `<input>` مستقیماً داخل `<label>` قرار گرفته است. فیلد متنی که label قابل مشاهده ندارد، از attribute به نام [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) استفاده می‌کند که نام دسترس‌پذیر (accessible name) آن را فراهم می‌کند. همچنین برای بهبود استایل، چند CSS نیز در این مثال استفاده شده است.

### HTML

```html
<form>
  <fieldset>
    <legend>Choose your interests</legend>
    <div>
      <label>
        <input type="checkbox" id="coding" name="interest" value="coding" />
        Coding
      </label>
    </div>
    <div>
      <label>
        <input type="checkbox" id="music" name="interest" value="music" />
        Music
      </label>
    </div>
    <div>
      <label>
        <input type="checkbox" id="art" name="interest" value="art" />
        Art
      </label>
    </div>
    <div>
      <label>
        <input type="checkbox" id="sports" name="interest" value="sports" />
        Sports
      </label>
    </div>
    <div>
      <label>
        <input type="checkbox" id="cooking" name="interest" value="cooking" />
        Cooking
      </label>
    </div>
    <div>
      <label>
        <input type="checkbox" id="other" name="interest" value="other" />
        Other
      </label>
      <input
        type="text"
        id="otherValue"
        name="other"
        aria-label="Other interest" />
    </div>
    <div>
      <button type="submit">Submit form</button>
    </div>
  </fieldset>
</form>
```

### CSS

```css
html {
  font-family: sans-serif;
}

form {
  width: 600px;
  margin: 0 auto;
}

div {
  margin-bottom: 10px;
}

fieldset {
  background: cyan;
  border: 5px solid blue;
}

legend {
  padding: 10px;
  background: blue;
  color: cyan;
}
```

### JavaScript

```js
const otherCheckbox = document.querySelector("#other");
const otherText = document.querySelector("#otherValue");
otherText.style.visibility = "hidden";
```

```javascript
otherCheckbox.addEventListener("change", () => {
  if (otherCheckbox.checked) {
    otherText.style.visibility = "visible";
    otherText.value = "";
  } else {
    otherText.style.visibility = "hidden";
  }
});
```

## خلاصهٔ فنی

<table class="properties">
  <tbody>
    <tr>
      <td><strong><a href="#value">مقدار</a></strong></td>
      <td>یک رشته که مقدار checkbox را مشخص می‌کند.</td>
    </tr>
    <tr>
      <td><strong>رویدادها</strong></td>
      <td><code>change</code> و <code>input</code></td>
    </tr>
    <tr>
      <td><strong>ویژگی‌های عمومی پشتیبانی‌شده</strong></td>
      <td>
        <code><a href="#checked">checked</a></code> و
        <code><a href="#switch">switch</a></code>
      </td>
    </tr>
    <tr>
      <td><strong>ویژگی‌های IDL</strong></td>
      <td>
        <a href="/en-US/docs/Web/API/HTMLInputElement/checked"><code>checked</code></a>,
        <a href="/en-US/docs/Web/API/HTMLInputElement/indeterminate"><code>indeterminate</code></a> و
        <a href="/en-US/docs/Web/API/HTMLInputElement/value"><code>value</code></a>
      </td>
    </tr>
    <tr>
      <td><strong>رابط DOM</strong></td>
      <td><code>HTMLInputElement</code></td>
    </tr>
    <tr>
      <td><strong>نقش ARIA ضمنی</strong></td>
      <td><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role"><code>checkbox</code></a></td>
    </tr>
  </tbody>
</table>

## همچنین ببینید

- `:checked` و `:indeterminate`: سلکتورهای CSS که به شما امکان می‌دهند ظاهر checkboxها را بر اساس وضعیت فعلی آن‌ها تغییر دهید.
- `HTMLInputElement`: رابط DOM مربوط به HTML که المنت `<input>` را پیاده‌سازی می‌کند.