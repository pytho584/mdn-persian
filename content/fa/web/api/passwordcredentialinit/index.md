---
title: PasswordCredentialInit
slug: Web/API/PasswordCredentialInit
page-type: web-api-interface
spec-urls: https://w3c.github.io/webappsec-credential-management/#typedefdef-passwordcredentialinit
---

{{APIRef("Credential Management API")}}

دیکشنری **`PasswordCredentialInit`** همان شیئی است که هنگام ایجاد یک گواهینامه (credential) رمز عبور، به عنوان مقدار گزینهٔ `password` به {{domxref("CredentialsContainer.create()")}} ارسال می‌شود.

## مقداردهی اولیه از یک فرم

به‌جای ارسال مستقیم این دیکشنری، یک وب‌سایت می‌تواند یک {{domxref("HTMLFormElement")}} ارسال کند؛ در این صورت پیاده‌سازی `create()` داده‌های گواهینامه را بر اساس مقادیر عناصر قابل ارسالِ فرم، با توجه به مقدار ویژگی [`autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete) آن عناصر، پر می‌کند.

| مقدارِ `autocomplete`                    | ویژگی هدف در گواهینامه |
| ---------------------------------------- | ---------------------- |
| `"username"`                             | `id`                   |
| `"name"` یا `"nickname"`                 | `name`                 |
| `"new-password"` یا `"current-password"` | `password`             |
| `"photo"`                                | `iconURL`              |

اگر فرم شامل هر دو عنصر `"new-password"` و `"current-password"` باشد، مقدارِ `"new-password"` استفاده خواهد شد.

ویژگی `origin` برابر با مبدأ (origin) سندی که {{domxref("HTMLFormElement")}} در آن قرار دارد، تنظیم می‌شود.

## ویژگی‌های نمونه

- `iconURL` {{optional_inline}}
  - : یک رشته (string) که نشانی URL یک آیکون یا آواتار را نشان می‌دهد که باید با گواهینامه مرتبط شود.
- `id`
  - : یک رشته که بخش نام کاربری از ترکیب نام کاربری/رمز عبور را نشان می‌دهد.
- `name` {{optional_inline}}
  - : یک رشته که یک نام قابل‌فهم برای انسان را نشان می‌دهد که با گواهینامه مرتبط است و هدف آن کمک به کاربر برای انتخاب این گواهینامه در یک رابط کاربری است.
- `origin`
  - : یک رشته که مبدأ گواهینامه را نشان می‌دهد. اشیاء {{domxref("PasswordCredential")}} به مبدأ وابسته هستند (origin-bound)؛ به این معنی که فقط در همان مبدأ مشخصی که برای آن در نظر گرفته شده‌اند قابل استفاده خواهند بود.
- `password`
  - : یک رشته که رمز عبور گواهینامه را نشان می‌دهد.

## مثال‌ها

### ایجاد گواهینامه رمز عبور از یک شیء Literal

این مثال یک شیء literal برای مقداردهی اولیه یک گواهینامه رمز عبور می‌سازد.

```js
const credInit = {
  id: "serpent1234", // "username" در یک جفت نام کاربری/رمز عبور معمولی
  name: "Serpentina", // نام نمایشی گواهینامه
  origin: "https://example.org",
  password: "the last visible dog",
};

const makeCredential = document.querySelector("#make-credential");

makeCredential.addEventListener("click", async () => {
  const cred = await navigator.credentials.create({
    password: credInit,
  });
  console.log(cred.name);
  // Serpentina
  console.log(cred.id);
  // serpent1234
  console.log(cred.password);
  // the last visible dog
});
```

### ایجاد گواهینامه رمز عبور از یک فرم

این مثال از یک فرم برای مقداردهی اولیه یک گواهینامه رمز عبور استفاده می‌کند.

#### HTML

HTML یک {{HTMLElement("form")}} شامل سه عنصر قابل ارسال را اعلام می‌کند که به ترتیب شناسه کاربر، نام نمایشی کاربر و رمز عبور را نشان می‌دهند.

```html
<form>
  <div>
    <label for="displayname">Enter your display name: </label>
    <input
      type="text"
      name="displayname"
      id="displayname"
      autocomplete="name" />
  </div>
  <div>
    <label for="username">Enter your username: </label>
    <input type="text" name="username" id="username" autocomplete="username" />
  </div>
  <div>
    <label for="password">Enter your password: </label>
    <input
      type="password"
      name="password"
      id="password"
      autocomplete="new-password" />
  </div>
</form>

<button id="make-credential">Make credential</button>

<pre id="log"></pre>
```

```css hidden
form {
  display: table;
}

div {
  display: table-row;
}

label,
input {
  display: table-cell;
  margin-bottom: 10px;
}

label {
  padding-right: 10px;
}

#log {
  height: 60px;
  padding: 0.5rem;
  border: 1px solid black;
}
```

#### JavaScript

جاوااسکریپت، فرم را به `create()` منتقل می‌کند و برخی از مقادیر گواهینامهٔ حاصل را در خروجی (log) ثبت می‌کند.

اگر فرم شامل مقادیر لازم برای ویژگی‌های اجباری گواهینامه نباشد، Promise برگشتی از `create()` رد (reject) خواهد شد.

```js
const makeCredential = document.querySelector("#make-credential");
const formCreds = document.querySelector("form");

makeCredential.addEventListener("click", async () => {
  try {
    const credential = await navigator.credentials.create({
      password: formCreds,
    });
    log(
      `New credential:\ndisplay name: ${credential.name}, username: ${credential.id}, password: ${credential.password}`,
    );
  } catch (e) {
    if (e.name === "TypeError") {
      log("Error creating credential\nMake sure you filled in all the fields");
    }
  }
});

const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = text;
}
```

#### نتیجه

{{EmbedLiveSample("Creating a password credential from a form", "", "260")}}

## مشخصات

{{Specifications}}