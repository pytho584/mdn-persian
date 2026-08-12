---
title: <input type="radio"> HTML attribute value
source: >-
  https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/radio
translated_by: n8n + AI
---

# \<input type="radio"> HTML attribute value

عناصر `<input>` از نوع **`radio`** معمولاً در **گروه‌های رادیویی** استفاده می‌شوند – مجموعه‌ای از دکمه‌های رادیویی که یک دسته از گزینه‌های مرتبط را توصیف می‌کنند.

در هر گروه رادیویی فقط یک دکمه می‌تواند هم‌زمان انتخاب شود. دکمه‌های رادیویی معمولاً به صورت دایره‌های کوچک نمایش داده می‌شوند که وقتی انتخاب می‌شوند، پر یا برجسته می‌شوند.

```html
<fieldset>
  <legend>Select a maintenance drone:</legend>

  <div>
    <input type="radio" id="huey" name="drone" value="huey" checked />
    <label for="huey">Huey</label>
  </div>

  <div>
    <input type="radio" id="dewey" name="drone" value="dewey" />
    <label for="dewey">Dewey</label>
  </div>

  <div>
    <input type="radio" id="louie" name="drone" value="louie" />
    <label for="louie">Louie</label>
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

به این‌ها دکمه‌های رادیویی می‌گویند، چون ظاهر و عملکردشان شبیه دکمه‌های فشاری رادیوهای قدیمی است (مانند تصویر زیر).

> \[!NOTE] [چک‌باکس‌ها](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/checkbox/) مشابه دکمه‌های رادیویی هستند، اما با یک تفاوت مهم: دکمه‌های رادیویی برای انتخاب یک مقدار از میان یک مجموعه طراحی شده‌اند، در حالی که چک‌باکس‌ها به شما اجازه می‌دهند هر مقدار را به‌طور جداگانه فعال یا غیرفعال کنید. در جایی که چند کنترل وجود دارد، دکمه‌های رادیویی فقط امکان انتخاب یکی از بین همه را می‌دهند، اما چک‌باکس‌ها اجازه انتخاب چندین مقدار را می‌دهند.

### مقدار (value)

ویژگی `value` یک رشته است که مقدار دکمه رادیویی را مشخص می‌کند. این مقدار هرگز توسط \{{Glossary("user agent")\}} به کاربر نمایش داده نمی‌شود. در عوض، از آن برای شناسایی دکمه رادیویی انتخاب‌شده در یک گروه استفاده می‌شود.

#### تعریف یک گروه رادیویی

یک گروه رادیویی با دادن [`name`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#name) یکسان به هر یک از دکمه‌های رادیویی در گروه تعریف می‌شود. پس از ایجاد یک گروه رادیویی، انتخاب هر دکمه رادیویی در آن گروه به‌طور خودکار دکمه رادیویی انتخاب‌شده قبلی را در همان گروه لغو می‌کند (deselect).

می‌توانید هر تعداد گروه رادیویی که می‌خواهید در یک صفحه داشته باشید، تا زمانی که هر گروه یک `name` منحصربه‌فرد داشته باشد.

برای مثال، اگر فرم شما نیاز دارد که کاربر روش تماس ترجیحی خود را انتخاب کند، می‌توانید سه دکمه رادیویی ایجاد کنید، هر کدام با ویژگی `name` برابر با `contact`، اما یکی با مقدار `email`، یکی با مقدار `phone` و یکی با مقدار `mail`. کاربر هرگز `value` یا `name` را نمی‌بیند (مگر اینکه شما صریحاً کدی برای نمایش آن اضافه کنید).

HTML نهایی به این شکل خواهد بود:

```html
<form>
  <fieldset>
    <legend>لطفاً روش تماس ترجیحی خود را انتخاب کنید:</legend>
    <div>
      <input type="radio" id="contactChoice1" name="contact" value="email" />
      <label for="contactChoice1">ایمیل</label>

      <input type="radio" id="contactChoice2" name="contact" value="phone" />
      <label for="contactChoice2">تلفن</label>

      <input type="radio" id="contactChoice3" name="contact" value="mail" />
      <label for="contactChoice3">پست</label>
    </div>
    <div>
      <button type="submit">ارسال</button>
    </div>
  </fieldset>
</form>
```

در اینجا سه دکمه رادیویی را می‌بینید که هر کدام `name` برابر با `contact` دارند و هر کدام یک `value` منحصربه‌فرد دارند که آن دکمه رادیویی را در گروه مشخص می‌کند. همچنین هر کدام یک \{{domxref("Element.id", "id")\}} منحصربه‌فرد دارند که توسط ویژگی [`for`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/label/#for) عنصر \{{HTMLElement("label")\}} برای مرتبط کردن برچسب‌ها با دکمه‌های رادیویی استفاده می‌شود.

می‌توانید این مثال را در اینجا امتحان کنید:

بهجای `{{EmbedLiveSample('Defining_a_radio_group', 600, 130)}}`، نمونه زنده در نسخه نهایی حذف شده است.

#### نمایش دادههای یک گروه رادیویی

وقتی فرم بالا با انتخاب یک دکمه رادیویی ارسال شود، دادههای فرم شامل یک ورودی به شکل `contact=value` خواهند بود. برای مثال، اگر کاربر روی دکمه رادیویی «Phone» کلیک کند و فرم را ارسال کند، دادههای فرم شامل خط `contact=phone` میشود.

اگر attribute با نام `value` را در HTML حذف کنید، دادههای فرم ارسالی مقدار `on` را به گروه اختصاص میدهند. در این حالت، اگر کاربر گزینه «Phone» را انتخاب کرده و فرم را ارسال کند، دادههای فرم بهصورت `contact=on` خواهد بود که چندان مفید نیست. پس یادتان باشد attribute های `value` را حتماً تنظیم کنید.

> \[!NOTE] اگر هنگام ارسال فرم هیچ دکمه رادیوییای انتخاب نشده باشد، گروه رادیویی بههیچوجه در دادههای ارسالی فرم قرار نمیگیرد، چون مقداری برای گزارش وجود ندارد.

واقعاً غیرمعمول است که بخواهید فرم بدون انتخاب هیچکدام از دکمههای رادیویی گروه ارسال شود، بنابراین معمولاً عاقلانه است که یکی از آنها بهصورت پیشفرض در حالت `checked` باشد. به بخش [انتخاب پیشفرض یک دکمه رادیویی](index.md#selecting_a_radio_button_by_default) در پایین مراجعه کنید.

بیایید کمی کد به مثال قبلی اضافه کنیم تا بتوانیم دادههای تولیدشده توسط این فرم را بررسی کنیم. HTML را تغییر میدهیم تا یک بلوک `<pre>` برای خروجی دادههای فرم اضافه شود:

```html
<form>
  <fieldset>
    <legend>Please select your preferred contact method:</legend>
    <div>
      <input type="radio" id="contactChoice1" name="contact" value="email" />
      <label for="contactChoice1">Email</label>
      <input type="radio" id="contactChoice2" name="contact" value="phone" />
      <label for="contactChoice2">Phone</label>
      <input type="radio" id="contactChoice3" name="contact" value="mail" />
      <label for="contactChoice3">Mail</label>
    </div>
    <div>
      <button type="submit">Submit</button>
    </div>
  </fieldset>
</form>
<pre id="log"></pre>
```

سپس کمی [JavaScript](../../../../../../../../en-US/docs/Web/JavaScript/) اضافه میکنیم تا یک event listener روی رویداد `submit` تنظیم کنیم؛ این رویداد وقتی ارسال میشود که کاربر دکمه «Submit» را کلیک کند:

```js
const form = document.querySelector("form");
const log = document.querySelector("#log");

form.addEventListener("submit", (event) => {
  const data = new FormData(form);
  let output = "";
  for (const entry of data) {
    output = `${output}${entry[0]}=${entry[1]}\r`;
  }
  log.innerText = output;
  event.preventDefault();
});
```

این مثال را امتحان کنید و ببینید که برای گروه `contact` هیچوقت بیش از یک نتیجه وجود ندارد.

### ویژگیهای اضافی

علاوه بر attributeهای مشترکی که همه عناصر `<input>` دارند، ورودیهای `radio` از attributeهای زیر پشتیبانی میکنند.

* `checked`
  *   : یک attribute بولی که اگر وجود داشته باشد، نشان میدهد این دکمه رادیویی بهصورت پیشفرض در گروه انتخاب شده است.

      برخلاف سایر مرورگرها، فایرفاکس بهصورت پیشفرض [حالت checked پویا](https://stackoverflow.com/questions/5985839/bug-with-firefox-disabled-attribute-of-input-not-resetting-when-refreshing) یک `<input>` را در بارگذاریهای مختلف صفحه حفظ میکند. برای کنترل این ویژگی از attribute [`autocomplete`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#autocomplete) استفاده کنید.
* `value`
  * : attribute «value» یکی از attributeهای مشترک بین همه `<input>`هاست؛ با این حال، برای ورودیهای از نوع `radio` کاربرد خاصی دارد: وقتی فرم ارسال میشود، فقط دکمههای رادیویی که در حال حاضر checked هستند به سرور ارسال میشوند و مقدار گزارششده برابر با مقدار attribute «value» است. اگر مقدار `value` به شکل دیگری مشخص نشده باشد، بهطور پیشفرض رشته `on` است. این موضوع در بخش [Value](index.md#value) بالا نشان داده شده است.
* [`required`](../../../../../../../../en-US/docs/Web/HTML/Reference/Attributes/required/)
  * : ویژگی `required` یکی از attributeهایی است که بیشتر `input`ها به اشتراک دارند. اگر هر دکمه رادیویی در یک گروه همنام از دکمههای رادیویی دارای این attribute باشد، باید حتماً یکی از دکمههای آن گروه انتخاب شده باشد؛ البته لازم نیست همان دکمهای باشد که attribute روی آن اعمال شده است.

### کار با دکمههای رادیویی

در بالا مبانی دکمههای رادیویی را پوشش دادیم. حالا به سایر ویژگیها و تکنیکهای رایج مرتبط با دکمههای رادیویی میپردازیم که ممکن است به آنها نیاز داشته باشید.

#### انتخاب پیش‌فرض یک دکمه رادیویی

برای اینکه یک دکمه رادیویی به‌صورت پیش‌فرض انتخاب شود، ویژگی `checked` را اضافه کنید؛ همانطور که در این نسخه اصلاح‌شده از مثال قبلی نشان داده شده است:

```html
<form>
  <fieldset>
    <legend>Please select your preferred contact method:</legend>
    <div>
      <input
        type="radio"
        id="contactChoice1"
        name="contact"
        value="email"
        checked />
      <label for="contactChoice1">Email</label>

      <input type="radio" id="contactChoice2" name="contact" value="phone" />
      <label for="contactChoice2">Phone</label>

      <input type="radio" id="contactChoice3" name="contact" value="mail" />
      <label for="contactChoice3">Mail</label>
    </div>
    <div>
      <button type="submit">Submit</button>
    </div>
  </fieldset>
</form>
```

در این حالت، اولین دکمه رادیویی به‌صورت پیش‌فرض انتخاب می‌شود.

> \[!NOTE] اگر ویژگی `checked` را روی بیش از یک دکمه رادیویی قرار دهید، نمونه‌های بعدی بر نمونه‌های قبلی اولویت پیدا می‌کنند؛ یعنی آخرین دکمه رادیویی که `checked` دارد، انتخاب خواهد شد. دلیلش این است که در هر گروه فقط یک دکمه رادیویی می‌تواند در یک زمان انتخاب شود و عامل کاربر (user agent) به‌طور خودکار بقیه را هر بار که یک مورد جدید به‌عنوان checked علامت‌گذاری می‌شود، از حالت انتخاب خارج می‌کند.

#### ایجاد ناحیه کلیک بزرگ‌تر برای دکمه‌های رادیویی

در مثال‌های بالا، شاید متوجه شده باشید که می‌توانید یک دکمه رادیویی را با کلیک روی عنصر `<label>` مرتبط با آن انتخاب کنید، و همچنین روی خود دکمه رادیویی. این یک ویژگی واقعاً مفید از برچسب‌های فرم HTML است که کاربر را برای کلیک روی گزینه موردنظر آسان‌تر می‌کند، به‌خصوص در صفحه‌نمایش‌های کوچک مثل گوشی‌های هوشمند. فراتر از دسترس‌پذیری، این دلیل خوب دیگری است برای اینکه عناصر `<label>` را به‌درستی در فرم‌های خود تنظیم کنید.

### اعتبارسنجی

در مورد یک دکمه رادیویی که ویژگی [`required`](../../../../../../../../en-US/docs/Web/HTML/Reference/Attributes/required/) روی آن تنظیم شده، یا گروه همنامی از دکمه‌های رادیویی که حداقل یکی از اعضای آن `required` را تنظیم شده داشته باشد، برای اینکه کنترل معتبر در نظر گرفته شود، یک دکمه رادیویی باید انتخاب شده باشد. اگر هیچ دکمه رادیویی انتخاب نشده باشد، ویژگی [`valueMissing`](../../../../../../../../en-US/docs/Web/API/ValidityState/valueMissing/) از یک شیء `ValidityState` در طول اعتبارسنجی مقدار `true` برمی‌گرداند و مرورگر از کاربر می‌خواهد یک گزینه انتخاب کند.

### استایل‌دهی به دکمه‌های رادیویی

مثال زیر نسخه‌ای کمی کامل‌تر از مثالی است که در طول مقاله دیده‌ایم، با استایل‌دهی بیشتر و معناشناسی بهتر از طریق استفاده از عناصر تخصصی. HTML به این صورت است:

```html
<form>
  <fieldset>
    <legend>Please select your preferred contact method:</legend>
    <div>
      <input
        type="radio"
        id="contactChoice1"
        name="contact"
        value="email"
        checked />
      <label for="contactChoice1">Email</label>

      <input type="radio" id="contactChoice2" name="contact" value="phone" />
      <label for="contactChoice2">Phone</label>

      <input type="radio" id="contactChoice3" name="contact" value="mail" />
      <label for="contactChoice3">Mail</label>
    </div>
    <div>
      <button type="submit">Submit</button>
    </div>
  </fieldset>
</form>
```

CSS استفاده‌شده در این مثال کمی قابل‌توجه‌تر است:

```css
html {
  font-family: sans-serif;
}
```

```css
div:first-of-type {
  display: flex;
  align-items: flex-start;
  margin-bottom: 5px;
}

label {
  margin-right: 15px;
  line-height: 32px;
}

input {
  appearance: none;

  border-radius: 50%;
  width: 16px;
  height: 16px;

  border: 2px solid #999999;
  transition: 0.2s all linear;
  margin-right: 5px;

  position: relative;
  top: 4px;
}

input:checked {
  border: 6px solid black;
}

button,
legend {
  color: white;
  background-color: black;
  padding: 5px 10px;
  border-radius: 0;
  border: 0;
  font-size: 14px;
}

button:hover,
button:focus {
  color: #999999;
}

button:active {
  background-color: white;
  color: black;
  outline: 1px solid black;
}
```

نکتهٔ قابل توجه در اینجا استفاده از ویژگی `appearance` است (با پیشوندهایی که برای پشتیبانی برخی مرورگرها لازم است). به‌طور پیش‌فرض، دکمه‌های رادیویی (و [چک‌باکس‌ها](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/checkbox/)) با استایل‌های بومی سیستم‌عامل برای این کنترل‌ها استایل می‌گیرند. با تنظیم `appearance: none` می‌توانید استایل بومی را کاملاً حذف کرده و استایل‌های خودتان را برای آن‌ها ایجاد کنید. در اینجا از `border` به همراه `border-radius` و `transition` استفاده کرده‌ایم تا یک انتخاب رادیویی متحرک و زیبا بسازیم. همچنین توجه کنید که از شبه‌کلاس `:checked` برای مشخص کردن استایل ظاهر دکمهٔ رادیویی در حالت انتخاب‌شده استفاده شده است.

> \[!NOTE] اگر می‌خواهید از ویژگی `appearance` استفاده کنید، آن را با دقت زیادی آزمایش کنید. اگرچه در بیشتر مرورگرهای مدرن پشتیبانی می‌شود، پیاده‌سازی آن بسیار متفاوت است. در مرورگرهای قدیمی‌تر، حتی کلیدواژهٔ `none` در مرورگرهای مختلف اثر یکسانی ندارد و برخی اصلاً آن را پشتیبانی نمی‌کنند. در جدیدترین مرورگرها این تفاوت‌ها کمتر است.

توجه کنید که هنگام کلیک روی یک دکمهٔ رادیویی، یک افکت محو شدن/ظاهر شدن نرم و روان هنگام تغییر وضعیت دو دکمه رخ می‌دهد. علاوه بر این، استایل و رنگ‌بندی `legend` و دکمهٔ `submit` با کنتراست بالا سفارشی شده‌اند. این شاید ظاهری نباشد که در یک برنامهٔ وب واقعی بخواهید، اما قطعاً امکانات را نشان می‌دهد.

### خلاصهٔ فنی

| **مقدار**                       | رشته‌ای که مقدار دکمهٔ رادیویی را نشان می‌دهد. |
| ------------------------------- | ---------------------------------------------- |
| **رویدادها**                    | `change` و `input`                             |
| **ویژگی‌های رایج پشتیبانی‌شده** | `checked`, `value` و `required`                |
| **ویژگی‌های IDL**               | `checked` و `value`                            |
| **رابط DOM**                    | `HTMLInputElement`                             |
| **نقش ضمنی ARIA**               | `radio`                                        |

### مشخصات

### سازگاری مرورگر

### همچنین ببینید

* `<input>` و رابط `HTMLInputElement` که آن را پیاده‌سازی می‌کند.
* `RadioNodeList`: رابطی که فهرستی از دکمه‌های رادیویی را توصیف می‌کند.
