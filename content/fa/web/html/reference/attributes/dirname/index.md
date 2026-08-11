---
title: "dirname HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/dirname"
translated_by: "n8n + AI"
---

ویژگی `dirname` را می‌توان روی عنصر `<textarea>` و چند نوع `<input>` به کار برد. این ویژگی جهت‌دار بودن (directionality) محتوای متنی عنصر را هنگام ارسال فرم مشخص می‌کند. مرورگر با استفاده از مقدار این ویژگی تشخیص می‌دهد که متن واردشده توسط کاربر به صورت چپ‌به‌راست (LTR) است یا راست‌به‌چپ (RTL). وقتی از این ویژگی استفاده شود، مقدار جهت‌دار بودن عنصر همراه با مقدار `dirname` به عنوان نام فیلد در داده‌های ارسالی فرم قرار می‌گیرد.

## نکات استفاده

ویژگی `dirname` را می‌توان روی هر عنصر `<textarea>` یا هر عنصر `<input>` با یکی از انواع زیر به کار برد: `hidden`، `text`، `search`، `tel`، `url`، `email`، `password`، `submit`، `reset` و `button`.

قالب داده‌های ارسالی به صورت `{dirname_value}={direction}` است که `{dirname_value}` مقدار ویژگی `dirname` و `{direction}` جهت‌دار بودن متن است. برای مثال، اگر کاربر در عنصری با ویژگی‌های `name="comment"` و `dirname="comment-direction"` عبارت "Hello" را وارد کند، داده‌های ارسالی فرم (با کدگذاری URL) برای درخواست‌های GET به صورت `comment=Hello&comment-direction=ltr` خواهد بود. مقدار `direction` یکی از موارد زیر است:

- `rtl`
  - : متن واردشده توسط کاربر در جهت راست‌به‌چپ نوشته شده است.
- `ltr`
  - : متن واردشده توسط کاربر در جهت چپ‌به‌راست نوشته شده است.

اگر جهت‌دار بودن متنی مشخص نشده باشد، مرورگر از جهت‌دار بودن عنصر والد فرم استفاده می‌کند و اگر آن هم مشخص نباشد، از جهت‌دار بودن پیش‌فرض مرورگر استفاده می‌کند.

## مثال‌ها

### جهت‌دار بودن در عنصر textarea

در این مثال، ویژگی `dir="auto"` روی عنصر textarea باعث می‌شود جهت‌دار بودن متن به صورت خودکار بر اساس متن واردشده توسط کاربر تعیین شود:

```html
<form method="get" action="https://www.example.com/submit">
  <textarea name="comment" dir="auto" dirname="comment-direction">سيب</textarea>
  <button type="submit">Send my greetings</button>
</form>
```

وقتی کاربر فرم را ارسال می‌کند، مرورگر دو فیلد را شامل می‌کند: یکی با نام `comment` و مقدار "سيب" و دیگری با نام `comment-direction` و مقدار "rtl". بدنه ارسالی با کدگذاری URL به این صورت است:

```url
https://www.example.com/submit?comment=%D8%B3%D9%8A%D8%A8&comment-direction=rtl
```

### جهت‌دار بودن در عنصر input

در این مثال، ویژگی `dir="auto"` روی عنصر input باعث می‌شود جهت‌دار بودن متن به صورت خودکار بر اساس متن واردشده توسط کاربر تعیین شود:

```html
<form method="get" action="https://www.example.com/submit">
  <input
    type="text"
    name="comment-input"
    dir="auto"
    dirname="comment-direction"
    value="Hello" />
  <button type="submit">Send my greetings</button>
</form>
```

وقتی کاربر فرم را ارسال می‌کند، مرورگر دو فیلد را شامل می‌کند: یکی با نام `comment-input` و مقدار "Hello" و دیگری با نام `comment-direction` و مقدار "ltr":

```url
https://www.example.com/submit?comment-input=Hello&comment-direction=ltr
```

### ارث‌بری جهت‌دار بودن

در نمونه زیر، عناصر `<input>` و `<textarea>` فاقد ویژگی `dir` هستند، بنابراین جهت‌دار بودن صریح عنصر والد خود را که `rtl` است به ارث می‌برند:

```html
<div dir="rtl">
  <textarea name="comment" dirname="comment-direction">سيب</textarea>
  <input
    type="text"
    name="comment-input"
    dirname="comment-direction"
    value="Hello" />
</div>
```

```markdown
# ویژگی `dirname`

ویژگی `dirname` به مرورگر می‌گوید که جهت نوشتار (جهت متن) یک فیلد `<input>` یا `<textarea>` را به همراه داده‌های فرم ارسال کند. وقتی فرم ارسال می‌شود، مرورگر یک پارامتر اضافی با نامی که در این ویژگی مشخص کرده‌اید به داده‌های فرم اضافه می‌کند؛ مقدار این پارامتر یا `rtl` است یا `ltr`.

این ویژگی برای زمانی مفید است که بخواهید ونویس جهت نوشتار را به صورت خودکار و همراه با ورودی کاربر دریافت کنید.

## مثال

در مثال زیر، دو فیلد `<input>` و `<textarea>` هر دو دارای ویژگی `dirname` هستند. نام پارامتر جهت برای اولی `user-direction` و برای دومی `comment-direction` است:

```html
<div dir="rtl">
  <form method="get" action="https://www.example.com/submit">
    <input
      type="text"
      name="user"
      dirname="user-direction"
      value="LTR Username" />
    <textarea name="comment" dirname="comment-direction">LTR Comment</textarea>
    <button type="submit">Post Comment</button>
  </form>
</div>
```

هنگامی که فرم ارسال می‌شود، بدنهٔ درخواست به شکل زیر خواهد بود (مقادیر به صورت URL-encoded):

```url
https://www.example.com/submit?user=LTR+Username&user-direction=rtl&comment=LTR+Comment&comment-direction=rtl
```

در این خروجی، پارامترهای `user-direction` و `comment-direction` جهت متن هر فیلد را مشخص می‌کنند. در این مثال، هر دو مقدار `rtl` دارند، حتی با اینکه مقدار خود فیلدها LTR است.

## مشخصات

## سازگاری مرورگر

## جستارهای وابسته

- [ویژگی `dir`](/en-US/docs/Web/HTML/Reference/Global_attributes/dir)
- `<input>`
- `<textarea>`
```