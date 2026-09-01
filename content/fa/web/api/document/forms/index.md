---
title: "Document: forms property"
short-title: forms
slug: Web/API/Document/forms
page-type: web-api-instance-property
browser-compat: api.Document.forms
---

{{APIRef("DOM")}}

خاصیت فقط‌خواندنی **`forms`** در رابط {{domxref("Document")}} یک {{domxref("HTMLCollection")}} برمی‌گرداند که تمام عناصر {{HTMLElement("form")}} موجود در سند را فهرست می‌کند.

> [!NOTE]
> به همین ترتیب، می‌توانید با استفاده از خاصیت {{domxref("HTMLFormElement.elements")}} به فهرست عناصر ورودی کاربر یک فرم دسترسی پیدا کنید.

همچنین می‌توانید عناصر `<form>` نام‌گذاری‌شده را به عنوان خاصیت‌های شیء `document` فراخوانی کنید. برای مثال، `document["login-form"]` و `document.forms["login-form"]` هر دو می‌توانند برای دسترسی به فرمی با نام `login-form` استفاده شوند.

> [!WARNING]
> اتکا به الگوی `document["form-name"]` خطرناک و ناامیدکننده است، زیرا می‌تواند منجر به تداخل‌های غیرمنتظره با APIهای موجود یا آینده در مرورگر شود. برای مثال، اگر در آینده مرورگر یک خاصیت داخلی `document["login-form"]` معرفی کند، کد شما ممکن است دیگر نتواند به عنصر فرم دسترسی پیدا کند. برای جلوگیری از چنین تداخل‌هایی، همیشه از `document.forms` برای دسترسی به فرم‌های نام‌گذاری‌شده استفاده کنید.

## مقدار

یک شیء {{domxref("HTMLCollection")}} که تمام فرم‌های سند را فهرست می‌کند. هر آیتم در این مجموعه یک {{domxref("HTMLFormElement")}} است که یک عنصر `<form>` را نمایش می‌دهد.

اگر سند هیچ فرمی نداشته باشد، مجموعه برگشتی خالی بوده و طول آن صفر است.

## مثال‌ها

### دریافت اطلاعات فرم

```html
<form id="robby">
  <input type="button" value="robby's form" />
</form>

<form id="dave">
  <input type="button" value="dave's form" />
</form>

<form id="paul">
  <input type="button" value="paul's form" />
</form>
```

```js
document.querySelectorAll("input[type=button]").forEach((button, i) => {
  button.addEventListener("click", (event) => {
    console.log(document.forms[i].id);
  });
});
```

### دریافت یک عنصر از داخل یک فرم

```js
const selectForm = document.forms[index];
const selectFormElement = document.forms[index].elements[index];
```

### دسترسی به فرم‌های نام‌گذاری‌شده

```html
<form name="login">
  <input name="email" type="email" />
  <input name="password" type="password" />
  <button type="submit">Log in</button>
</form>
```

```js
const loginForm = document.forms.login; // Or document.forms['login']
loginForm.elements.email.placeholder = "test@example.com";
loginForm.elements.password.placeholder = "password";
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [HTML forms](/en-US/docs/Learn_web_development/Extensions/Forms)
- {{HTMLElement("form")}} و رابط {{domxref("HTMLFormElement")}}