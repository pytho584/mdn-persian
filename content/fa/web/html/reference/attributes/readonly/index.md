---
title: "readonly HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/readonly"
translated_by: "n8n + AI"
---

ویژگی بولی **`readonly`** وقتی وجود داشته باشد، عنصر را غیرقابل‌تغییر می‌کند؛ یعنی کاربر نمی‌تواند کنترل را ویرایش کند.

```html interactive-example
<label for="firstName">First Name:</label>
<input id="firstName" name="firstName" type="text" value="Adam" />

<label for="age">Age:</label>
<input id="age" name="age" type="number" value="42" readonly />

<label for="hobbies">Hobbies:</label>
<textarea id="hobbies" name="hobbies" readonly>Baseball</textarea>
```

```css interactive-example
label {
  display: block;
  margin-top: 1em;
}

input:read-only,
textarea:read-only {
  background-color: silver;
}
```

## نمای کلی

اگر ویژگی `readonly` روی یک عنصر `input` تنظیم شده باشد، چون کاربر نمی‌تواند ورودی را ویرایش کند، این عنصر در اعتبارسنجی محدودیت‌ها شرکت نمی‌کند.

ویژگی `readonly` توسط کنترل‌های متنی فرم پشتیبانی می‌شود، از جمله:

- عناصر `<input>` از نوع:
  - `text`
  - `search`
  - `tel`
  - `url`
  - `email`
  - `password`
  - `date`
  - `month`
  - `week`
  - `time`
  - `datetime-local`
  - `number`
- `<textarea>`

این ویژگی برای سایر عناصر، از جمله `<select>` و `<button>`، کاربرد ندارد. همچنین برای عناصر ورودی غیرمتنی از جمله موارد زیر اعمال نمی‌شود:

- `hidden`
- `range`
- `color`
- `checkbox`
- `radio`
- `file`
- `submit`
- `image`
- `reset`
- `button`

ورودی‌هایی که ویژگی `readonly` را پشتیبانی می‌کنند اما این ویژگی روی آن‌ها تنظیم نشده است، با شبه‌کلاس `:read-write` مطابقت می‌کنند. همه عناصر دیگر با شبه‌کلاس `:read-only` مطابقت دارند.

### تعامل ویژگی‌ها

تفاوت بین [`disabled`](/en-US/docs/Web/HTML/Reference/Attributes/disabled) و `readonly` این است که کنترل‌های read-only همچنان کار می‌کنند و قابل فوکوس هستند، در حالی که کنترل‌های غیرفعال نمی‌توانند فوکوس بگیرند، با فرم ارسال نمی‌شوند و معمولاً تا زمانی که فعال نشوند، به عنوان کنترل عمل نمی‌کنند.

چون مقدار یک فیلد read-only نمی‌تواند توسط تعامل کاربر تغییر کند، [`required`](/en-US/docs/Web/HTML/Reference/Attributes/required) روی ورودی‌هایی که ویژگی `readonly` نیز دارند تأثیری ندارد.

تنها راه تغییر پویای مقدار ویژگی `readonly`، از طریق اسکریپت است.

> [!NOTE]
> ویژگی `required` روی ورودی‌هایی که ویژگی `readonly` دارند مجاز نیست.

### کاربرد

مرورگرها ویژگی `readonly` را نمایش می‌دهند.

### اعتبارسنجی محدودیت‌ها

اگر عنصر read-only باشد، مقدار آن توسط کاربر نمی‌تواند به‌روزرسانی شود و در اعتبارسنجی محدودیت‌ها شرکت نمی‌کند.

## مثال

### HTML

```markdown
```html
<div class="group">
  <input type="text" value="Some value" readonly id="text" />
  <label for="text">Text box</label>
</div>
<div class="group">
  <input type="date" value="2020-01-01" readonly id="date" />
  <label for="date">Date</label>
</div>
<div class="group">
  <input type="email" value="Some value" readonly id="email" />
  <label for="email">Email</label>
</div>
<div class="group">
  <input type="password" value="Some value" readonly id="pwd" />
  <label for="pwd">Password</label>
</div>
<div class="group">
  <textarea readonly id="ta">Some value</textarea>
  <label for="ta">Message</label>
</div>
```

### نتیجه

## مشخصات

## سازگاری مرورگرها

## جستارهای وابسته

- `:read-only` و `:read-write`
- `<input>`
- `<select>`
```