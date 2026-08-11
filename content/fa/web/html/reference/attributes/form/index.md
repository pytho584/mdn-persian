---
title: "form HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/form"
translated_by: "n8n + AI"
---

ویژگی `form` در HTML، یک عنصر مرتبط با فرم را به عنصر `<form>` در همان سند متصل می‌کند. این ویژگی روی عناصر `<button>`، `<fieldset>`، `<input>`، `<object>`، `<output>`، `<select>` و `<textarea>` اعمال می‌شود.

## مقادیر

مقدار `id` عنصر `<form>`ای است که عنصر باید با آن مرتبط شود.

## نکات استفاده

به‌طور پیش‌فرض، کنترل‌های فرم با نزدیک‌ترین جد `<form>` خود مرتبط می‌شوند. کنترل‌های فرمی که داخل یک `<form>` قرار نمی‌گیرند، با هیچ فرمی مرتبط نیستند. ویژگی `form` امکان نادیده گرفتن این رفتارهای پیش‌فرض را می‌دهد.

ویژگی `form` در عناصر `<button>`، `<fieldset>`، `<input>`، `<object>`، `<output>`، `<select>` و `<textarea>` به شما امکان می‌دهد مالک فرم را به‌صورت صریح مشخص کنید؛ بنابراین می‌توانید کنترل‌های فرم را در هر جای سند به هر عنصر `<form>` که در همان سند قرار دارد متصل کنید.

وقتی فرمی ارسال می‌شود، نام و مقدار کنترل‌های مرتبط با عنصر `<form>` ارسال می‌شوند، چه به‌صورت فیزیکی داخل آن `<form>` باشند یا نباشند، و حتی اگر داخل یک `<form>` دیگر قرار گرفته باشند.

ویژگی `form` یک کنترل، مقدار `id` عنصر `<form>` موردنظر را می‌گیرد. هر مقدار دیگری که برای این ویژگی تنظیم شده باشد نادیده گرفته می‌شود.

اگرچه تنظیم مقدار ویژگی روی `id` نزدیک‌ترین جد `<form>` ضروری نیست، اما تعریف صریح ارتباط بین یک کنترل فرم و نزدیک‌ترین فرم جد، تضمین می‌کند که اگر اسکریپت‌ها یا HTML نامعتبر باعث شوند که آن `<form>` خاص دیگر نزدیک‌ترین جدِ کنترل نباشد، کنترل فرم از فرمش جدا نشود.

### ارتباط با فرمی غیر از جد

ویژگی `form` می‌تواند برای مرتبط کردن یک کنترل فرم که داخل یک `<form>` قرار دارد با یک `<form>` دیگر استفاده شود.

در این مثال کد، `<input>` نام کاربری داخل `internalForm` قرار دارد، اما ویژگی `form` کنترل را از فرم جد خود جدا کرده و به‌جای آن به `externalForm` متصل می‌کند:

```html
<form id="externalForm"></form>
<form id="internalForm">
  <label for="username">Username:</label>
  <input form="externalForm" type="text" name="username" id="username" />
</form>
```

در این حالت، نام کاربری با ارسال `externalForm` ارسال می‌شود، در حالی که `internalForm` هیچ کنترل فرم مرتبطی ندارد.

### به ارث نرسیدن ویژگی `form`

ویژگی `form` فقط عنصری را که روی آن تنظیم شده مرتبط می‌کند. رفتار این ویژگی به ارث نمی‌رسد. مثلاً وقتی ویژگی `form` روی یک عنصر `<fieldset>` تنظیم شود، فقط خود `<fieldset>` را مرتبط می‌کند؛ و کنترل‌های فرمی که داخل آن `<fieldset>` هستند را **به‌طور خودکار** مرتبط نمی‌کند.

در این مثال، `<fieldset>` و `<input>` نام کاربری با `exampleForm` مرتبط هستند و در `HTMLFormControlsCollection` خاصیت `HTMLFormElement.elements` قرار می‌گیرند، اما `password` نه. فقط `username` با ارسال `exampleForm` ارسال می‌شود:

```html
<form id="exampleForm"></form>

<fieldset form="exampleForm">
  <legend>Login information</legend>
  <label
    >Username: <input form="exampleForm" type="text" name="username"
  /></label>
  <label>Password: <input type="password" name="password" /></label>
</fieldset>
```

هر عنصر مرتبط با فرم، یا باید داخل خود فرم قرار گرفته باشد یا ویژگی `form` خودش را داشته باشد. می‌توانید با جاوااسکریپت و از طریق [HTMLFormElement.elements](/en-US/docs/Web/API/HTMLFormElement/elements) بررسی کنید که کدام عناصر با یک فرم مرتبط شده‌اند.

### ارسال فرم

داشتن ویژگی `form` به این معنی نیست که عنصر هنگام ارسال فرم، همراه با آن ارسال می‌شود. فقط عناصر قابل ارسال — از جمله `<button>`، `<input>`، `<select>` و `<textarea>` — نام و مقدارهایشان هنگام ارسال فرم مرتبط، ارسال می‌شود.

در این مثال، با اینکه `<output>` هم به صورت ضمنی و هم به صورت صریح با `calcForm` مرتبط است، هنگام ارسال `calcForm`، مقدار `result` همراه با `a` و `b` ارسال نمی‌شود. با این حال، این عنصر بخشی از `HTMLFormControlsCollection` فرم است.

```html
<form id="calcForm">
  <label>First number: <input id="a" value="2" type="number" /></label>
  <label>Second number: <input id="b" value="3" type="number" /></label>
  <label>Sum: <output name="result" for="a b" form="calcForm">5</output></label>
</form>
```

## مثال‌ها

### مثال پایه

این مثال نشان می‌دهد که چگونه عناصر مرتبط با فرم می‌توانند با استفاده از ویژگی `form` به یک عنصر `<form>` متصل شوند، حتی اگر به طور مستقیم داخل فرم قرار نداشته باشند. همهٔ عناصر مرتبط با فرم در این مثال، یا به صورت ضمنی (با قرار گرفتن مستقیم در داخل فرم) یا به صورت صریح از طریق ویژگی `form` با `loginForm` مرتبط شده‌اند. هنگام ارسال فرم ورود، نام و مقدار هر عنصر قابل ارسال در داده‌های ارسالی قرار می‌گیرد.

```html
<form id="loginForm">
  <label>Username: <input type="text" name="username" /></label>
</form>

<label
  >Password: <input form="loginForm" type="password" name="password"
/></label>
<label>
  Choose an option:
  <select form="loginForm" name="options">
    <option value="A">A</option>
    <option value="B">B</option>
  </select>
</label>
<label
  >Description:
  <textarea form="loginForm" rows="4" name="description">
Hello, World!</textarea>
</label>
<button form="loginForm" type="submit" name="submitLogin" value="Login">
  Submit
</button>
```

### عنصر مرتبط با یک فرم دیگر

در این مثال، دو عنصر `<form>` داریم: `parentForm` و `targetForm`. دکمهٔ `<button>` داخل `parentForm` ویژگی `form` خود را برابر `targetForm` قرار داده است؛ بنابراین این دکمه از نزدیک‌ترین عنصر والد، یعنی `parentForm` جدا شده و با `targetForm` مرتبط می‌شود. وقتی دکمهٔ ارسال فعال می‌شود، فرم `targetForm` ارسال می‌شود، نه والد `parentForm`.

```html
<form id="targetForm">
  <input type="text" name="targetInput" />
</form>
<form id="parentForm">
  <button form="targetForm" type="submit" name="submitTarget" value="Target">
    Submit target form
  </button>
</form>
```

## همچنین ببینید

- [جایگزینی رفتارهای پیش‌فرض فرم](/en-US/docs/Web/HTML/Reference/Elements/input/image#overriding_default_form_behaviors)