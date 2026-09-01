---
title: "HTMLFormElement"
slug: Web/API/HTMLFormElement
page-type: web-api-interface
browser-compat: api.HTMLFormElement
---

{{APIRef("HTML DOM")}}

رابط **`HTMLFormElement`** یک عنصر {{HTMLElement("form")}} را در DOM نمایش می‌دهد. این رابط امکان دسترسی به جنبه‌های فرم و در برخی موارد تغییر آن‌ها را فراهم می‌کند، همچنین دسترسی به عناصر تشکیل‌دهنده آن را نیز ممکن می‌سازد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌هایی را از والد خود، {{domxref("HTMLElement")}}، به ارث می‌برد._

- {{domxref("HTMLFormElement.acceptCharset")}}
  - : یک رشته که مقدار ویژگی HTML [`accept-charset`](/en-US/docs/Web/HTML/Reference/Elements/form#accept-charset) فرم را منعکس می‌کند.
- {{domxref("HTMLFormElement.action")}}
  - : یک رشته که مقدار ویژگی HTML [`action`](/en-US/docs/Web/HTML/Reference/Elements/form#action) فرم را منعکس می‌کند و شامل URI برنامه‌ای است که اطلاعات ارسال‌شده توسط فرم را پردازش می‌کند.
- {{domxref("HTMLFormElement.autocomplete")}}
  - : یک رشته که مقدار ویژگی HTML [`autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete) فرم را منعکس می‌کند و نشان می‌دهد که آیا کنترل‌های این فرم می‌توانند مقادیر خود را به‌طور خودکار توسط مرورگر پر کنند.
- {{domxref("HTMLFormElement.encoding")}} یا {{domxref("HTMLFormElement.enctype")}}
  - : یک رشته که مقدار ویژگی HTML [`enctype`](/en-US/docs/Web/HTML/Reference/Elements/form#enctype) فرم را منعکس می‌کند و نوع محتوایی را که برای ارسال فرم به سرور استفاده می‌شود، مشخص می‌کند. فقط مقادیر مشخص‌شده قابل تنظیم هستند. این دو ویژگی مترادف هستند.
- {{domxref("HTMLFormElement.elements")}} {{ReadOnlyInline}}
  - : یک {{domxref("HTMLFormControlsCollection")}} که تمام کنترل‌های فرم متعلق به این عنصر فرم را در خود نگه می‌دارد.
- {{domxref("HTMLFormElement.length")}} {{ReadOnlyInline}}
  - : یک `long` که تعداد کنترل‌های موجود در فرم را منعکس می‌کند.
- {{domxref("HTMLFormElement.name")}}
  - : یک رشته که مقدار ویژگی HTML [`name`](/en-US/docs/Web/HTML/Reference/Elements/form#name) فرم را منعکس می‌کند و شامل نام فرم است.
- {{domxref("HTMLFormElement.noValidate")}}
  - : یک مقدار بولی که مقدار ویژگی HTML [`novalidate`](/en-US/docs/Web/HTML/Reference/Elements/form#novalidate) فرم را منعکس می‌کند و نشان می‌دهد که آیا فرم نباید اعتبارسنجی شود.
- {{domxref("HTMLFormElement.method")}}
  - : یک رشته که مقدار ویژگی HTML [`method`](/en-US/docs/Web/HTML/Reference/Elements/form#method) فرم را منعکس می‌کند و روش HTTP مورد استفاده برای ارسال فرم را مشخص می‌کند. فقط مقادیر مشخص‌شده قابل تنظیم هستند.
- {{domxref("HTMLFormElement.rel")}}
  - : یک رشته که مقدار ویژگی HTML [`rel`](/en-US/docs/Web/HTML/Reference/Attributes/rel) فرم را منعکس می‌کند و نشان می‌دهد که فرم چه نوع پیوندهایی را به عنوان یک فهرست جدا شده با فاصله از مقادیر شمارشی ایجاد می‌کند.
- {{domxref("HTMLFormElement.relList")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMTokenList")}} که ویژگی HTML [`rel`](/en-US/docs/Web/HTML/Reference/Attributes/rel) را به عنوان یک فهرست از توکن‌ها منعکس می‌کند.
- {{domxref("HTMLFormElement.target")}}
  - : یک رشته که مقدار ویژگی HTML [`target`](/en-US/docs/Web/HTML/Reference/Elements/form#target) فرم را منعکس می‌کند و مشخص می‌کند که نتایج دریافتی از ارسال فرم در کجا نمایش داده شود.

ورودی‌های نام‌دار به عنوان ویژگی‌هایی به نمونه فرم مالک خود اضافه می‌شوند و در صورت اشتراک نام می‌توانند ویژگی‌های بومی را بازنویسی کنند (مثلاً، یک فرم با ورودی به نام `action` ویژگی `action` خود را به جای ویژگی HTML [`action`](/en-US/docs/Web/HTML/Reference/Elements/form#action) فرم، آن ورودی را برمی‌گرداند).

## روش‌های نمونه

_این رابط همچنین روش‌هایی را از والد خود، {{domxref("HTMLElement")}}، به ارث می‌برد._

- {{domxref("HTMLFormElement.checkValidity", "checkValidity()")}}
  - : اگر کنترل‌های فرزند عنصر تحت [اعتبارسنجی محدودیت](/en-US/docs/Web/HTML/Guides/Constraint_validation) قرار گیرند و آن محدودیت‌ها را برآورده کنند، `true` برمی‌گرداند؛ اگر برخی کنترل‌ها محدودیت‌های خود را برآورده نکنند، `false` برمی‌گرداند. یک رویداد به نام {{domxref("HTMLInputElement/invalid_event", "invalid")}} در هر کنترلی که محدودیت‌های خود را برآورده نمی‌کند، فعال می‌کند؛ چنین کنترل‌هایی در صورت لغو نشدن رویداد، نامعتبر در نظر گرفته می‌شوند. این به برنامه‌نویس بستگی دارد که چگونه به `false` پاسخ دهد.
- {{domxref("HTMLFormElement.reportValidity", "reportValidity()")}}
  - : اگر کنترل‌های فرزند عنصر [محدودیت‌های اعتبارسنجی](/en-US/docs/Web/HTML/Guides/Constraint_validation) خود را برآورده کنند، `true` برمی‌گرداند. وقتی `false` برگردانده شود، رویدادهای قابل لغو {{domxref("HTMLInputElement/invalid_event", "invalid")}} برای هر فرزند نامعتبر فعال شده و مشکلات اعتبارسنجی به کاربر گزارش می‌شود.
- {{domxref("HTMLFormElement.requestSubmit", "requestSubmit()")}}
  - : درخواست ارسال فرم با استفاده از دکمه ارسال مشخص‌شده و پیکربندی متناظر آن را می‌کند.
- {{domxref("HTMLFormElement.reset", "reset()")}}
  - : فرم را به حالت اولیه خود بازنشانی می‌کند.
- {{domxref("HTMLFormElement.submit", "submit()")}}
  - : فرم را به سرور ارسال می‌کند.

## رویدادها

با استفاده از `addEventListener()` یا با انتساب یک شنونده رویداد به ویژگی `oneventname` این رابط به این رویدادها گوش دهید.

- {{domxref("HTMLFormElement/formdata_event", "formdata")}}
  - : رویداد `formdata` پس از ساخته شدن فهرست ورودی‌هایی که داده‌های فرم را نشان می‌دهند، فعال می‌شود.
- {{domxref("HTMLFormElement/reset_event", "reset")}}
  - : رویداد `reset` زمانی فعال می‌شود که یک فرم بازنشانی می‌شود.
- {{domxref("HTMLFormElement/submit_event", "submit")}}
  - : رویداد `submit` زمانی فعال می‌شود که یک فرم ارسال می‌شود.

## نکات استفاده

### به دست آوردن یک شیء عنصر فرم

برای به دست آوردن یک شیء `HTMLFormElement`، می‌توانید از یک [انتخاب‌گر CSS](/en-US/docs/Web/CSS/Guides/Selectors) با {{domxref("Document.querySelector", "querySelector()")}} استفاده کنید، یا می‌توانید با استفاده از ویژگی {{domxref("Document.forms", "forms")}} آن، فهرستی از تمام فرم‌های موجود در سند را دریافت کنید.

{{domxref("Document.forms")}} آرایه‌ای از اشیاء `HTMLFormElement` را برمی‌گرداند که هر یک از فرم‌های صفحه را فهرست می‌کند. سپس می‌توانید از هر یک از نحوهای زیر برای به دست آوردن یک فرم خاص استفاده کنید:

- `document.forms[index]`
  - : فرم را در `index` مشخص‌شده در آرایه فرم‌ها برمی‌گرداند.
- `document.forms[id]`
  - : فرمی را که شناسه آن `id` است برمی‌گرداند.
- `document.forms[name]`
  - : فرمی را که مقدار ویژگی `name` آن `name` است برمی‌گرداند.

### دسترسی به عناصر فرم

با بررسی ویژگی {{domxref("HTMLFormElement.elements", "elements")}} فرم می‌توانید به فهرست عناصر حاوی داده فرم دسترسی پیدا کنید. این یک {{domxref("HTMLFormControlsCollection")}} را برمی‌گرداند که تمام عناصر ورود داده کاربر فرم را فهرست می‌کند، هم آن‌هایی که از نوادگان `<form>` هستند و هم آن‌هایی که با استفاده از ویژگی `form` خود به اعضای فرم تبدیل شده‌اند.

همچنین می‌توانید عنصر فرم را با استفاده از ویژگی `name` آن به عنوان کلید `form` به دست آورید، اما استفاده از `elements` رویکرد بهتری است—زیرا _فقط_ عناصر فرم را شامل می‌شود و نمی‌تواند با سایر ویژگی‌های `form` مخلوط شود.

### مشکلات نام‌گذاری عناصر

برخی نام‌ها در دسترسی جاوااسکریپت به ویژگی‌ها و عناصر فرم اختلال ایجاد می‌کنند.

به عنوان مثال:

- `<input name="id">` بر `<form id="…">` اولویت خواهد داشت. این بدان معناست که `form.id` به شناسه فرم اشاره نمی‌کند، بلکه به عنصری که نام آن `"id"` است اشاره می‌کند. این مورد برای سایر ویژگی‌های فرم نیز صادق است، مانند `<input name="action">` یا `<input name="post">`.
- `<input name="elements">` مجموعه `elements` فرم را غیرقابل دسترسی می‌کند. اکنون مرجع `form.elements` به عنصر منفرد اشاره خواهد کرد.

برای جلوگیری از چنین مشکلاتی با نام عناصر:

- _همیشه_ از مجموعه `elements` استفاده کنید تا از ابهام بین نام یک عنصر و ویژگی فرم جلوگیری شود.
- _هرگز_ از `"elements"` به عنوان نام یک عنصر استفاده نکنید.

اگر از جاوااسکریپت استفاده نمی‌کنید، این مشکل ایجاد نخواهد شد.

### عناصری که کنترل‌های فرم در نظر گرفته می‌شوند

عناصری که توسط `HTMLFormElement.elements` و `HTMLFormElement.length` شامل می‌شوند، عبارتند از:

- {{HTMLElement("button")}}
- {{HTMLElement("fieldset")}}
- {{HTMLElement("input")}} (به استثنای آن‌هایی که [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#type) آن‌ها `"image"` است، که به دلایل تاریخی حذف شده‌اند)
- {{HTMLElement("object")}}
- {{HTMLElement("output")}}
- {{HTMLElement("select")}}
- {{HTMLElement("textarea")}}

هیچ عنصر دیگری در فهرست بازگردانده‌شده توسط `elements` گنجانده نشده است، که این امر آن را به روشی عالی برای دسترسی به مهم‌ترین عناصر هنگام پردازش فرم‌ها تبدیل می‌کند.

## مثال‌ها

ایجاد یک عنصر فرم جدید، تغییر ویژگی‌های آن و سپس ارسال آن:

```js
const f = document.createElement("form"); // Create a form
document.body.appendChild(f); // Add it to the document body
f.action = "/cgi-bin/some.cgi"; // Add action and method attributes
f.method = "POST";
f.submit(); // Call the form's submit() method
```

استخراج اطلاعات از یک عنصر `<form>` و تنظیم برخی از ویژگی‌های آن:

```html
<form name="formA" action="/cgi-bin/test" method="post">
  <p>Press "Info" for form details, or "Set" to change those details.</p>
  <p>
    <button type="button" id="info">Info</button>
    <button type="button" id="set-info">Set</button>
    <button type="reset">Reset</button>
  </p>

  <textarea id="form-info" rows="15" cols="20"></textarea>
</form>
```

```js
document.getElementById("info").addEventListener("click", () => {
  // Get a reference to the form via its name
  const f = document.forms["formA"];
  // The form properties we're interested in
  const properties = [
    "elements",
    "length",
    "name",
    "charset",
    "action",
    "acceptCharset",
    "action",
    "enctype",
    "method",
    "target",
  ];
  // Iterate over the properties, turning them into a string that we can display to the user
  const info = properties
    .map((property) => `${property}: ${f[property]}`)
    .join("\n");

  // Set the form's <textarea> to display the form's properties
  document.forms["formA"].elements["form-info"].value = info; // document.forms["formA"]['form-info'].value would also work
});

document.getElementById("set-info").addEventListener("click", (e) => {
  // Get a reference to the form via the event target
  // e.target is the button, and .form is the form it belongs to
  const f = e.target.form;
  // Argument should be a form element reference.
  f.action = "a-different-url.cgi";
  f.name = "a-different-name";
});
```

ارسال یک `<form>` به یک پنجره جدید:

```html
<form action="test.php" target="_blank">
  <p>
    <label>First name: <input type="text" name="first-name" /></label>
  </p>
  <p>
    <label>Last name: <input type="text" name="last-name" /></label>
  </p>
  <p>
    <label><input type="password" name="pwd" /></label>
  </p>

  <fieldset>
    <legend>Pet preference</legend>

    <p>
      <label><input type="radio" name="pet" value="cat" /> Cat</label>
    </p>
    <p>
      <label><input type="radio" name="pet" value="dog" /> Dog</label>
    </p>
  </fieldset>

  <fieldset>
    <legend>Owned vehicles</legend>

    <p>
      <label
        ><input type="checkbox" name="vehicle" value="Bike" />I have a
        bike</label
      >
    </p>
    <p>
      <label
        ><input type="checkbox" name="vehicle" value="Car" />I have a car</label
      >
    </p>
  </fieldset>

  <p><button>Submit</button></p>
</form>
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML که این رابط را پیاده‌سازی می‌کند: {{HTMLElement("form")}}.
