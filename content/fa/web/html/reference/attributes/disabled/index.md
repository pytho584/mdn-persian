---
title: "disabled HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/disabled"
translated_by: "n8n + AI"
---

# `disabled` HTML attribute

ویژگی بولی **`disabled`**، وقتی روی عنصر وجود داشته باشد، آن را غیرقابل ویرایش، غیرقابل فوکوس و حتی غیرقابل ارسال با فرم می‌کند. کاربر نه می‌تواند کنترل را ویرایش یا فوکوس کند و نه کنترل‌های فرزندِ آن را.

اغلب مرورگرها این کنترل‌ها را خاکستری نشان می‌دهند و هیچ رویداد مرورگری مانند کلیک ماوس یا رویدادهای مرتبط با فوکوس دریافت نمی‌کنند.

ویژگی `disabled` توسط عناصر `<button>`، `<fieldset>`، `<optgroup>`، `<option>`، `<select>`، `<textarea>` و `<input>` پشتیبانی می‌شود.

```html
<form>
  <label for="name">Name:</label>
  <input id="name" name="name" type="text" />

  <label for="emp">Employed:</label>
  <select id="emp" name="emp" disabled>
    <option>No</option>
    <option>Yes</option>
  </select>

  <label for="empDate">Employment Date:</label>
  <input id="empDate" name="empDate" type="date" disabled />

  <label for="resume">Resume:</label>
  <input id="resume" name="resume" type="file" />
</form>
```

```css
label {
  display: block;
  margin-top: 1em;
}

*:disabled {
  background-color: dimgrey;
  color: linen;
  opacity: 1;
}
```

## Overview

این ویژگی بولی نشان می‌دهد که کاربر نمی‌تواند با کنترل یا کنترل‌های فرزند آن تعامل کند.

اگر این ویژگی مشخص نشده باشد، کنترل وضعیت خود را از عنصر والد می‌گیرد، مثلاً `fieldset`. اگر هیچ عنصر والدی ویژگی `disabled` را نداشته باشد و خود کنترل هم این ویژگی را نداشته باشد، کنترل فعال (enabled) است.

اگر روی `<optgroup>` تنظیم شده باشد، `<select>` همچنان تعاملی است (مگر اینکه جای دیگری غیرفعال شده باشد)، اما هیچ‌کدام از گزینه‌های آن گروه قابل انتخاب نیستند.

> [!NOTE]
> اگر `<fieldset>` غیرفعال باشد، همهٔ کنترل‌های فرمِ فرزند آن غیرفعال می‌شوند، به‌جز کنترل‌های داخل `<legend>`.

وقتی یک عنصر پشتیبانی‌کننده، ویژگی `disabled` را داشته باشد، شبه‌کلاس `:disabled` نیز روی آن اعمال می‌شود. برعکس، عناصری که ویژگی `disabled` را پشتیبانی می‌کنند اما آن را تنظیم نکرده‌اند، با شبه‌کلاس `:enabled` مطابقت دارند.

این ویژگی بولی از تعامل کاربر با دکمه جلوگیری می‌کند. اگر این ویژگی تنظیم نشده باشد، دکمه ممکن است توسط عنصر والد، مثلاً `<fieldset>`، غیرفعال شود. اگر هیچ عنصر والدی با ویژگی `disabled` وجود نداشته باشد، دکمه فعال است.

برخلاف سایر مرورگرها، فایرفاکس وضعیت غیرفعال بودن پویای `<button>` را در بارگذاری‌های مختلف صفحه حفظ می‌کند. برای کنترل این رفتار از ویژگی [`autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete) استفاده کنید.

### Attribute interactions

تفاوت `disabled` و [`readonly`](/en-US/docs/Web/HTML/Reference/Attributes/readonly) این است که کنترل‌های read-only همچنان کار می‌کنند و قابل فوکوس هستند؛ اما کنترل‌های disabled نمی‌توانند فوکوس بگیرند، همراه فرم ارسال نمی‌شوند و تا وقتی فعال نشوند معمولاً به‌عنوان کنترل عمل نمی‌کنند.

چون مقدار یک فیلد غیرفعال (disabled) قابل تغییر نیست، [`required`](/en-US/docs/Web/HTML/Reference/Attributes/required) روی inputهایی که `disabled` هم دارند تأثیری ندارد. همچنین، از آنجا که این عناصر تغییرناپذیر می‌شوند، بیشتر ویژگی‌های دیگر مثل [`pattern`](/en-US/docs/Web/HTML/Reference/Attributes/pattern) نیز تا زمانی که کنترل فعال نشود، بی‌اثر هستند.

> [!NOTE]
> ویژگی `required` در inputهایی که `disabled` دارند مجاز نیست.

### کاربردپذیری

مرورگرها کنترل‌های فرم غیرفعال را به‌صورت خاکستری و کمرنگ نمایش می‌دهند، چون این کنترل‌ها تغییرناپذیرند، فوکس نمی‌گیرند، هیچ رویداد مرورگری (مثل کلیک ماوس یا رویدادهای مرتبط با فوکس) را دریافت نمی‌کنند و همراه با فرم ارسال نمی‌شوند.

اگر این ویژگی روی عناصر پشتیبان‌کننده وجود داشته باشد، شبه‌کلاس {{cssxref(':disabled')}} اعمال می‌شود. اگر ویژگی وجود نداشته باشد، شبه‌کلاس {{cssxref(':enabled')}} اعمال می‌شود. اگر عنصر از ویژگی `disabled` پشتیبانی نکند، این ویژگی هیچ تأثیری ندارد، از جمله اینکه باعث تطبیق با شبه‌کلاس‌های `:disabled` و `:enabled` نمی‌شود.

### اعتبارسنجی محدودیت

اگر عنصر `disabled` باشد، مقدار آن نمی‌تواند فوکس بگیرد، توسط کاربر به‌روزرسانی نشود و در اعتبارسنجی محدودیت (constraint validation) شرکت نمی‌کند.

## نمونه‌ها

وقتی کنترل‌های فرم غیرفعال می‌شوند، بسیاری از مرورگرها به‌طور پیش‌فرض آن‌ها را با رنگ روشن‌تر و خاکستری نمایش می‌دهند. در زیر نمونه‌هایی از یک چک‌باکس غیرفعال، دکمه رادیویی، {{ HTMLElement("option") }} و {{ HTMLElement("optgroup") }} و همچنین برخی کنترل‌های فرم که با تنظیم ویژگی `disabled` روی عنصر والد `{{ HTMLElement("fieldset")}}` غیرفعال شده‌اند، آورده شده است. {{ HTMLElement("option") }}ها غیرفعال هستند، اما خود {{ HTMLElement("select") }} غیرفعال نیست. می‌توانستیم با اضافه کردن ویژگی به خود عنصر به‌جای فرزندانش، کل {{ HTMLElement("select") }} را غیرفعال کنیم.

```html
<fieldset>
  <legend>Checkboxes</legend>
  <p>
    <label>
      <input type="checkbox" name="ch-box" value="regular" /> Regular
    </label>
  </p>
  <p>
    <label>
      <input type="checkbox" name="ch-box" value="disabled" disabled /> disabled
    </label>
  </p>
</fieldset>

<fieldset>
  <legend>Radio buttons</legend>
  <p>
    <label> <input type="radio" name="radio" value="regular" /> Regular </label>
  </p>
  <p>
    <label>
      <input type="radio" name="radio" value="disabled" disabled /> disabled
    </label>
  </p>
</fieldset>

<p>
  <label
    >Select an option:
    <select>
      <optgroup label="Group 1">
        <option>Option 1.1</option>
      </optgroup>
      <optgroup label="Group 2">
        <option>Option 2.1</option>
        <option disabled>Option 2.2</option>
        <option>Option 2.3</option>
      </optgroup>
      <optgroup label="Group 3" disabled>
        <option>Disabled 3.1</option>
        <option>Disabled 3.2</option>
        <option>Disabled 3.3</option>
      </optgroup>
    </select>
  </label>
</p>

<fieldset disabled>
  <legend>Disabled fieldset</legend>
  <p>
    <label>
      Name: <input type="radio" name="radio" value="regular" /> Regular
    </label>
  </p>
  <p>
    <label>Number: <input type="number" /></label>
  </p>
</fieldset>
```

## همچنین ببینید

- `:disabled` و `:enabled`