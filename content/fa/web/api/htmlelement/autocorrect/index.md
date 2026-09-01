---
title: "HTMLElement: autocorrect property"
short-title: autocorrect
slug: Web/API/HTMLElement/autocorrect
page-type: web-api-instance-property
browser-compat: api.HTMLElement.autocorrect
---

{{APIRef("HTML DOM")}}

ویژگی **`autocorrect`** از رابط {{domxref("HTMLElement")}} کنترل می‌کند که آیا تصحیح خودکار متن قابل ویرایش برای خطاهای املایی و/یا نگارشی فعال است یا خیر.

رفتار خاص تصحیح خودکار، از جمله اینکه کدام واژه‌ها جایگزین می‌شوند، به عامل کاربر (user agent) و سرویس‌های ارائه‌شده توسط دستگاه زیربنایی بستگی دارد.
برای مثال، در macOS ممکن است یک عامل کاربر بر [متن‌های جایگزین و علائم نگارشی ثبت‌شده](https://support.apple.com/en-vn/guide/mac-help/mh35735/mac) تکیه کند.
سایر دستگاه‌ها و مرورگرها ممکن است از رویکرد متفاوتی استفاده کنند.

این ویژگی منعکس‌کننده مقدار [ویژگی سراسری HTML `autocorrect`](/en-US/docs/Web/HTML/Reference/Global_attributes/autocorrect) است.

## مقدار

اگر تصحیح خودکار برای عنصر فعال باشد `true` و در غیر این صورت `false`.

## مثال‌ها

### فعال و غیرفعال کردن تصحیح خودکار

این مثال نشان می‌دهد که چگونه می‌توانید تصحیح خودکار را فعال و غیرفعال کنید.

#### HTML

مارک‌آپ HTML شامل یک دکمه تغییر وضعیت (toggle) و یک عنصر {{htmlelement("input")}} با [`type="search"`](/en-US/docs/Web/HTML/Reference/Elements/input/search) است.
توجه داشته باشید که اگر تصحیح خودکار پشتیبانی شود، به‌طور پیش‌فرض فعال خواهد بود.

```html
<button id="toggleAutocorrect">Unknown</button>
<input type="search" id="searchinput" />
```

```html hidden
<pre id="log"></pre>
```

```css hidden
#log {
  height: 100px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

#### JavaScript

کد ابتدا بررسی می‌کند که آیا `autocorrect` پشتیبانی می‌شود یا خیر، با بررسی وجود آن در پروتوتایپ `HTMLElement`.
اگر وجود داشته باشد، یک کنترل‌کننده کلیک اضافه می‌شود که به شما امکان می‌دهد مقدار را تغییر دهید.
اگر وجود نداشته باشد، رابط کاربری عناصر تعاملی را پنهان می‌کند و پیامی مبنی بر عدم پشتیبانی از `autocorrect` ثبت می‌کند.

```js
const toggleButton = document.querySelector("button");
const searchInput = document.querySelector("#searchinput");

function setButtonText() {
  toggleButton.textContent = searchInput.autocorrect ? "Enabled" : "Disabled";
  log(`autocorrect: ${searchInput.autocorrect}`);
}

if (`autocorrect` in HTMLElement.prototype) {
  setButtonText();

  toggleButton.addEventListener("click", (e) => {
    searchInput.autocorrect = !searchInput.autocorrect;
    setButtonText();
  });
} else {
  toggleButton.hidden = true;
  searchInput.hidden = true;
  log("autocorrect not supported");
}
```

#### نتیجه

<!-- cSpell:ignore Carot -->

دکمه را برای تغییر مقدار تصحیح خودکار فعال کنید.
متن نامعتبری مانند «Carot» را در کادر متن وارد کنید.
وقتی تصحیح خودکار فعال باشد و اگر پیاده‌سازی واژه جایگزین مناسب یعنی «carrot» را داشته باشد، متن به‌طور خودکار اصلاح می‌شود.

{{EmbedLiveSample("Enable and disable autocorrection", "100%", "200")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [`autocapitalize`](/en-US/docs/Web/HTML/Reference/Global_attributes/autocapitalize) ویژگی سراسری HTML