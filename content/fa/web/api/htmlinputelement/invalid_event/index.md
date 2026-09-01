---
title: "HTMLInputElement: invalid event"
short-title: invalid
slug: Web/API/HTMLInputElement/invalid_event
page-type: web-api-event
browser-compat: api.HTMLInputElement.invalid_event
---

{{APIRef("HTML DOM")}}

رویداد **`invalid`** زمانی شلیک می‌شود که یک عنصر قابل ارسال (submittable element) از نظر اعتبارسنجی بررسی شده و محدودیت‌های خود را برآورده نکند.

این رویداد می‌تواند برای نمایش خلاصه‌ای از مشکلات موجود در یک فرم هنگام ارسال مفید باشد. هنگام ارسال یک فرم، رویدادهای `invalid` برای هر کنترل فرمی که نامعتبر است، شلیک می‌شوند. اعتبار عناصر قابل ارسال قبل از ارسال {{HtmlElement("form")}} والد آن‌ها، یا پس از فراخوانی متد [`checkValidity()`](/en-US/docs/Web/API/HTMLInputElement/checkValidity) عنصر یا `<form>` والد آن بررسی می‌شود.

این رویداد در رویداد {{domxref("Element/blur_event", "blur")}} بررسی نمی‌شود.

## نحو

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا با تنظیم یک ویژگی‌کننده رویداد (event handler property) استفاده کنید.

```js-nolint
addEventListener("invalid", (event) => { })

oninvalid = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

اگر یک فرم با مقدار نامعتبر ارسال شود، عناصر قابل ارسال بررسی می‌شوند و در صورت یافتن خطا، رویداد `invalid` روی عنصر `invalid` شلیک خواهد شد. در این مثال، هنگامی که یک رویداد نامعتبر به دلیل مقدار نامعتبر در ورودی شلیک می‌شود، مقدار نامعتبر در لاگ ثبت می‌شود.

### HTML

```html
<form action="#">
  <div>
    <label>
      یک عدد صحیح بین ۱ تا ۱۰ وارد کنید:
      <input type="number" min="1" max="10" required />
    </label>
  </div>
  <div><input type="submit" value="ارسال" /></div>
</form>
<hr />
مقادیر نامعتبر:
<ul id="log"></ul>
```

### JavaScript

```js
const input = document.querySelector("input");
const log = document.getElementById("log");

input.addEventListener("invalid", (e) => {
  log.appendChild(document.createElement("li")).textContent = JSON.stringify(
    e.target.value,
  );
});
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- عنصر HTML {{HtmlElement("form")}}
- رویداد مرتبط: {{domxref("HTMLFormElement/submit_event", "submit")}}
- شبه‌کلاس CSS {{cssxref(":invalid")}}