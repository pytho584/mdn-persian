---
title: "multiple HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/multiple"
translated_by: "n8n + AI"
---

ویژگی بولی **`multiple`** در HTML، وقتی تنظیم شود، به این معنی است که کنترل فرم می‌تواند یک یا چند مقدار را دریافت کند. این ویژگی برای نوع‌های ورودی {{HTMLElement("input/email", "email")}} و {{HTMLElement("input/file", "file")}} و همچنین عنصر {{HTMLElement("select")}} معتبر است. نحوه انتخاب چند مقدار توسط کاربر به نوع کنترل فرم بستگی دارد.

```html
<label for="recipients">Where should we send the receipt?</label>
<input id="recipients" name="recipients" type="email" multiple />

<label for="shakes">Which shakes would you like to order?</label>
<select id="shakes" name="shakes" multiple>
  <option>Vanilla Shake</option>
  <option>Strawberry Shake</option>
  <option>Chocolate Shake</option>
</select>

<label for="payment">How would you like to pay?</label>
<select id="payment" name="payment">
  <option>Credit card</option>
  <option>Bank Transfer</option>
</select>
```

```css
label {
  display: block;
  margin-top: 1em;
}

input,
select {
  width: 100%;
}

input:invalid {
  background-color: lightpink;
}
```

## بررسی کلی

بسته به نوع کنترل فرم، ظاهر آن ممکن است با وجود ویژگی `multiple` تغییر کند. برای نوع ورودی `file`، پیام‌های پیش‌فرض مرورگر متفاوت می‌شود. مثلاً در فایرفاکس، وقتی این ویژگی وجود داشته باشد، ورودی فایل «هیچ فایلی انتخاب نشده» (No files selected) و وقتی وجود نداشته باشد «هیچ فایلی انتخاب نشده» (No file selected) را نشان می‌دهد. اکثر مرورگرها برای عنصر {{HTMLElement("select")}} با ویژگی `multiple`، یک لیست پیمایش‌دار (scrolling list box) نمایش می‌دهند و در صورت فقدان آن، یک منوی بازشوی تک‌خطی نشان می‌دهند. ورودی {{HTMLElement("input/email", "email")}} چه ویژگی `multiple` داشته باشد چه نداشته باشد، ظاهر یکسانی دارد، اما اگر ویژگی وجود نداشته باشد و کاربر بیش از یک آدرس ایمیل (جدا شده با کاما) وارد کند، با شبه‌کلاس {{cssxref(':invalid')}} مطابقت پیدا می‌کند.

وقتی `multiple` روی نوع ورودی {{HTMLElement("input/email", "email")}} تنظیم شود، کاربر می‌تواند صفر (اگر ویژگی [`required`](/en-US/docs/Web/HTML/Reference/Attributes/required) هم وجود نداشته باشد)، یک یا چند آدرس ایمیل (جدا شده با کاما) وارد کند.

```html
<input type="email" multiple name="emails" id="emails" />
```

فقط در صورتی که ویژگی `multiple` مشخص شده باشد، مقدار می‌تواند لیستی از آدرس‌های ایمیل معتبر (جدا شده با کاما) باشد. فاصله‌های ابتدا و انتهای هر آدرس در لیست حذف می‌شود.

وقتی `multiple` روی نوع ورودی {{HTMLElement("input/file", "file")}} تنظیم شود، کاربر می‌تواند یک یا چند فایل را انتخاب کند. کاربر می‌تواند با روش‌های پلتفرم خود (مثلاً با نگه‌داشتن <kbd>Shift</kbd> یا <kbd>Control</kbd> و کلیک کردن) چند فایل را از پنجره انتخاب فایل برگزیند.

```html
<input type="file" multiple name="uploads" id="uploads" />
```

وقتی این ویژگی وجود نداشته باشد، کاربر فقط می‌تواند یک فایل در هر `<input>` انتخاب کند.

ویژگی `multiple` روی عنصر {{HTMLElement("select")}} نشان‌دهنده یک کنترل برای انتخاب صفر یا چند گزینه از لیست است. در غیر این صورت، {{HTMLElement("select")}} برای انتخاب یک {{HTMLElement("option")}} از لیست استفاده می‌شود.

```html
<select multiple name="dwarfs" id="dwarfs">
  <option>Grumpy</option>
  <option>Happy</option>
  <option>Sleepy</option>
  <option>Bashful</option>
  <option>Sneezy</option>
  <option>Dopey</option>
  <option>Doc</option>
</select>
```

وقتی `multiple` مشخص شده باشد، اکثر مرورگرها به جای یک منوی تک‌خطی، یک لیست پیمایش‌دار نمایش می‌دهند.

چندین گزینه انتخاب‌شده با استفاده از قرارداد آرایه‌ای {{domxref("URLSearchParams")}} ارسال می‌شوند، یعنی به صورت `name=value1&name=value2`.

## ملاحظات دسترسی

(در متن اصلی بخشی برای accessibility وجود ندارد، اما عنوان در ساختار اصلی نبود. در صورت نیاز می‌توان اضافه کرد. اینجا خالی می‌ماند.)

## راهنمای تکمیل فرم و استفاده از کنترل‌های ورودی

برای پر کردن فرم و استفاده از هر کنترل ورودی، باید اطلاعات مورد نیاز را مشخص کنید. فیلدهای اجباری و اختیاری، قالب‌های داده و سایر جزئیات را در ادامه توضیح می‌دهیم.

### ویژگی `multiple`

اگر از ویژگی `multiple` استفاده می‌کنید، کاربر می‌تواند چند مقدار وارد کند. برای مثال، در یک فیلد ایمیل، باید آدرس‌ها را با کاما از هم جدا کنید:  
«آدرس‌های ایمیل را با کاما از هم جدا کنید.»

### نکته مهم درباره `select` چند انتخابی

تنظیم `size="1"` روی یک `select` با ویژگی `multiple` ممکن است در برخی مرورگرها آن را شبیه یک `select` تکی نشان دهد، اما در این حالت با فوکوس کردن، لیست باز نمی‌شود و تجربه کاربری بدی ایجاد می‌کند. از این کار خودداری کنید. حتی اگر ظاهر `select` را تغییر می‌دهید، حتماً به کاربر اطلاع دهید که می‌تواند بیش از یک گزینه را انتخاب کند (مثلاً با نگه داشتن کلید Ctrl).

---

## مثال‌ها

### فیلد ایمیل

```html
<label for="emails">چه کسانی را ایمیل می‌زنید؟</label>
<input
  type="email"
  multiple
  name="emails"
  id="emails"
  list="dwarf-emails"
  required
  size="64" />

<datalist id="dwarf-emails">
  <option value="grumpy@woodworkers.com">Grumpy</option>
  <option value="happy@woodworkers.com">Happy</option>
  <option value="sleepy@woodworkers.com">Sleepy</option>
  <option value="bashful@woodworkers.com">Bashful</option>
  <option value="sneezy@woodworkers.com">Sneezy</option>
  <option value="dopey@woodworkers.com">Dopey</option>
  <option value="doc@woodworkers.com">Doc</option>
</datalist>
```

اگر و فقط اگر ویژگی `multiple` مشخص شده باشد، مقدار ورودی می‌تواند لیستی از آدرس‌های ایمیل معتبر باشد که با کاما از هم جدا شده‌اند. فاصله‌های اضافی ابتدا و انتهای هر آدرس حذف می‌شود. اگر ویژگی `required` وجود داشته باشد، حداقل یک آدرس ایمیل الزامی است.

برخی مرورگرها از نمایش لیست گزینه‌های `datalist` برای آدرس‌های بعدی (هنگام استفاده از `multiple`) پشتیبانی می‌کنند، اما برخی دیگر نه.

### فیلد فایل

وقتی ویژگی `multiple` روی فیلد `file` تنظیم شود، کاربر می‌تواند یک یا چند فایل را انتخاب کند:

```html
<form method="post" enctype="multipart/form-data">
  <p>
    <label for="uploads">تصاویر مورد نظر برای آپلود را انتخاب کنید:</label>
    <input
      type="file"
      id="uploads"
      name="uploads"
      accept=".jpg, .jpeg, .png, .svg, .gif"
      multiple />
  </p>
  <p>
    <label for="text">یک فایل متنی برای آپلود انتخاب کنید:</label>
    <input type="file" id="text" name="text" accept=".txt" />
  </p>
  <p>
    <input type="submit" value="ارسال" />
  </p>
</form>
```

تفاوت ظاهری بین فیلد `file` با `multiple` و بدون آن قابل مشاهده است.

هنگام ارسال فرم، اگر از `method="get"` استفاده می‌کردیم، نام هر فایل انتخاب‌شده به عنوان پارامتر URL اضافه می‌شد (مثلاً `?uploads=img1.jpg&uploads=img2.svg`). اما چون از داده‌های چندبخشی (multipart form data) استفاده می‌کنیم، باید از `method="post"` استفاده کنیم. برای اطلاعات بیشتر به عنصر `<form>` و [ارسال داده‌های فرم](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Forms/Sending_and_retrieving_form_data#the_method_attribute) مراجعه کنید.

### فیلد `select` چند انتخابی

ویژگی `multiple` روی عنصر `<select>` یک کنترل برای انتخاب صفر یا چند گزینه از لیست گزینه‌ها ایجاد می‌کند. در غیر این صورت، `<select>` یک کنترل برای انتخاب یک `<option>` از لیست است. ظاهر کنترل معمولاً با وجود ویژگی `multiple` تغییر می‌کند: بیشتر مرورگرها به جای یک dropdown تکی، یک لیست پیمایشی (scrolling list box) نمایش می‌دهند.

```html
<form method="get" action="#">
  <p>
    <label for="dwarfs">Select the dwarf woodsman you like:</label>
    <select multiple name="dwarfs" id="dwarfs">
      <option>grumpy@woodworkers.com</option>
      <option>happy@woodworkers.com</option>
      <option>sleepy@woodworkers.com</option>
      <option>bashful@woodworkers.com</option>
      <option>sneezy@woodworkers.com</option>
      <option>dopey@woodworkers.com</option>
      <option>doc@woodworkers.com</option>
    </select>
  </p>
  <p>
    <label for="favoriteOnly">Select your favorite:</label>
    <select name="favoriteOnly" id="favoriteOnly">
      <option>grumpy@woodworkers.com</option>
      <option>happy@woodworkers.com</option>
      <option>sleepy@woodworkers.com</option>
      <option>bashful@woodworkers.com</option>
      <option>sneezy@woodworkers.com</option>
      <option>dopey@woodworkers.com</option>
      <option>doc@woodworkers.com</option>
    </select>
  </p>
  <p>
    <input type="submit" value="Submit" />
  </p>
</form>
```

به تفاوت ظاهری بین این دو کنترل فرم دقت کنید.

```css
/* uncomment this CSS to make the multiple the same height as the single */

/*
select[multiple] {
  height: 1.5em;
  vertical-align: top;
}
select[multiple]:focus,
select[multiple]:active {
  height: auto;
}
*/
```

چند راه برای انتخاب چند گزینه در یک `<select>` با ویژگی `multiple` وجود دارد. کاربران ماوس می‌توانند بسته به سیست عامل، کلیدهای <kbd>Ctrl</kbd>، <kbd>Command</kbd> یا <kbd>Shift</kbd> را نگه دارند و سپس روی چند گزینه کلیک کنند تا آن‌ها را انتخاب یا از انتخاب خارج کنند. کاربران کیبورد می‌توانند با تمرکز روی عنصر `<select>`، یک گزینه در ابتدا یا انتهای محدوده مورد نظر را با کلیدهای مکان‌نمای <kbd>Up</kbd> و <kbd>Down</kbd> انتخاب کنند. انتخاب گزینه‌های غیرمتوالی (non-contiguous) چندان پشتیبانی نمی‌شود: انتظار می‌رود که با فشار دادن <kbd>Space</kbd> بتوان گزینه‌ها را انتخاب یا از انتخاب خارج کرد، اما این قابلیت در مرورگرهای مختلف متفاوت است.

## همچنین ببینید

- `<input>`
- `<select>`
- [اجازه دادن به چندین آدرس ایمیل](/en-US/docs/Web/HTML/Reference/Elements/input/email#allowing_multiple_email_addresses)