---
title: "autocorrect HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/autocorrect"
translated_by: "n8n + AI"
---

# ویژگی سراسری `autocorrect`

ویژگی سراسری (global attribute) **`autocorrect`** یک ویژگی شمارشی (enumerated attribute) است که مشخص می‌کند آیا تصحیح خودکار غلط‌های املایی و نگارشی در متن قابل‌ویرایش فعال باشد یا خیر.

رفتار دقیق تصحیح خودکار، از جمله اینکه کدام کلمات جایگزین می‌شوند، به user agent و سرویس‌های دستگاه زیرین بستگی دارد.  
برای مثال در macOS، user agent ممکن است از [متن‌ها و علائم نگارشی جایگزین ثبت‌شده](https://support.apple.com/en-vn/guide/mac-help/mh35735/mac) استفاده کند. دستگاه‌ها و مرورگرهای دیگر ممکن است رویکرد متفاوتی داشته باشند.

تصحیح خودکار برای عناصر متنی قابل‌ویرایش کاربرد دارد:

- عناصر {{htmlelement("input")}}، به جز [`password`](/en-US/docs/Web/HTML/Reference/Elements/input/password)، [`email`](/en-US/docs/Web/HTML/Reference/Elements/input/email) و [`url`](/en-US/docs/Web/HTML/Reference/Elements/input/url) که از تصحیح خودکار پشتیبانی نمی‌کنند.
- عناصر {{htmlelement("textarea")}}.
- هر عنصری که ویژگی [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable) روی آن تنظیم شده باشد.

در عناصر قابل‌ویرایش، تصحیح خودکار به‌طور پیش‌فرض فعال است، مگر درون یک عنصر {{htmlelement("form")}} که مقدار پیش‌فرض ممکن است از فرم به ارث برسد. تنظیم صریح این ویژگی، مقدار پیش‌فرض را نادیده می‌گیرد.

## مقدار

مقادیر ممکن عبارتند از:

- `on` یا `""` (رشتهٔ خالی)
  - : تصحیح خودکار غلط‌های املایی و نگارشی را فعال می‌کند.
- `off`
  - : تصحیح خودکار متن قابل‌ویرایش را غیرفعال می‌کند.

انواع عنصر `<input>` که از تصحیح خودکار پشتیبانی نمی‌کنند، همیشه در حالت `off` هستند: [`password`](/en-US/docs/Web/HTML/Reference/Elements/input/password)، [`email`](/en-US/docs/Web/HTML/Reference/Elements/input/email) و [`url`](/en-US/docs/Web/HTML/Reference/Elements/input/url).

برای سایر عناصر قابل‌ویرایش، هر مقدار دیگری غیر از موارد بالا، معادل `on` در نظر گرفته می‌شود. مقدار پیش‌فرض برای عناصری که درون `<form>` نیستند، `on` است.

وقتی درون یک `<form>` قرار دارند، عناصر زیر مقدار پیش‌فرض `autocorrect` را از فرم به ارث می‌برند (اگر در فرم تنظیم شده باشد): {{htmlelement("button")}}، {{htmlelement("fieldset")}}، {{htmlelement("input")}}، {{htmlelement("output")}}، {{htmlelement("select")}} و {{htmlelement("textarea")}}.

## مثال‌ها

### مثال ساده

این مثال استفادهٔ پایه‌ای از ویژگی `autocorrect` را نشان می‌دهد.

#### HTML

دو عنصر `<input>` متنی با مقادیر متفاوت برای `autocorrect` تعریف می‌کنیم:

```html
<label for="vegetable">یک سبزی: </label>
<input id="vegetable" name="vegetable" type="text" autocorrect="on" />

<label for="fruit">یک میوه: </label>
<input id="fruit" name="fruit" type="text" autocorrect="off" />
```

#### نتیجه

متن نامعتبری را در فیلدهای ورودی سبزی و میوه وارد کنید. اگر مرورگر شما از تصحیح خودکار پشتیبانی کند و دستگاه زیرین جایگزین مناسبی داشته باشد، اشتباه تایپی در نام سبزی تصحیح می‌شود. در فیلد نام میوه، اشتباهات تایپی تصحیح نخواهند شد.

### فعال و غیرفعال کردن تصحیح خودکار

این مثال نشان می‌دهد چگونه می‌توان با ویژگی `autocorrect` تصحیح خودکار را فعال یا غیرفعال کرد.

#### HTML

کد HTML شامل یک دکمه {{htmlelement("button")}}، یک عنصر ورودی «نام» از نوع `<input type="text">`، یک عنصر «بیوگرافی» {{htmlelement("textarea")}} و دو عنصر {{htmlelement("label")}} است.

المان «username» مقدار `autocorrect="off"` را دارد، چون تصحیح خودکار یک نام آزاردهنده است!  
المان bio مقدار `autocorrect` را مشخص نکرده است؛ یعنی این قابلیت فعال است (ما می‌توانستیم هر مقدار دیگری به‌جز `off` تنظیم کنیم).

```html
<button id="reset">Reset</button>
<label for="username">Name: </label>
<input id="username" name="username" type="text" autocorrect="off" />
<label for="bio">Biography: </label>
<textarea id="bio" name="bio"></textarea>
```

```html hidden
<pre id="log"></pre>
```

```css hidden
#log {
  height: 75px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}

button,
input,
textarea {
  display: block;
}
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

#### جاوااسکریپت

کد بررسی می‌کند که آیا `autocorrect` پشتیبانی می‌شود؛ این کار با بررسی وجود آن روی prototype انجام می‌شود. اگر وجود نداشته باشد، این موضوع در log ثبت می‌شود. اگر وجود داشته باشد، مقدار property است `autocorrect` برای هر کدام از المان‌های ورودی متن در log ثبت می‌شود.

یک click handler برای دکمه اضافه شده است که به شما امکان می‌دهد متن واردشده و log را بازنشانی کنید.

```js
const resetButton = document.querySelector("#reset");
const userNameElement = document.querySelector("#username");
const bioElement = document.querySelector("#bio");

if (!("autocorrect" in HTMLElement.prototype)) {
  log("autocorrect not supported");
} else {
  log(`userNameElement.autocorrect: ${userNameElement.autocorrect}`);
  log(`bioElement.autocorrect: ${bioElement.autocorrect}`);
}

resetButton.addEventListener("click", (e) => {
  userNameElement.value = "";
  bioElement.value = "";
});
```

#### نتایج

اگر تصحیح خودکار توسط مرورگر شما پشتیبانی شود، ناحیهٔ log زیر ورودی‌های «Biography» و «Name» باید نشان دهد که این قابلیت برای ورودی‌های «Biography» فعال است، اما برای ورودی‌های «Name» نه.

در کادرهای ورودی متن Name و Biography، متن نامعتبر وارد کنید. اگر دستگاه جایگزینی برای کلمهٔ واردشده داشته باشد، از این جایگزین برای autocorrect کردن متن در ورودی «Biography» (فقط) استفاده می‌شود.

## همچنین ببینید

- همهٔ [attribute های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes).
- [`spellcheck`](/en-US/docs/Web/HTML/Reference/Global_attributes/spellcheck).