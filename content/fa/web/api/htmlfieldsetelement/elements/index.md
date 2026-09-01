---
title: "HTMLFieldSetElement: elements property"
short-title: elements
slug: Web/API/HTMLFieldSetElement/elements
page-type: web-api-instance-property
browser-compat: api.HTMLFieldSetElement.elements
---

{{APIRef("HTML DOM")}}

خاصیت فقط‌خواندنی **`elements`** از رابط {{domxref("HTMLFieldSetElement")}} یک شیء {{domxref("HTMLCollection")}} برمی‌گرداند که شامل تمام عناصر کنترل فرم ({{htmlelement("button")}}، {{htmlelement("fieldset")}}، {{htmlelement("input")}}، {{htmlelement("object")}}، {{htmlelement("output")}}، {{htmlelement("select")}} و {{htmlelement("textarea")}}) است که از فرزندان این fieldset محسوب می‌شوند.

می‌توانید با استفاده از یک ایندکس یا ویژگی‌های `name` یا `id` عنصر، به یک کنترل فرم خاص در مجموعه برگشتی دسترسی پیدا کنید. اگر چندین کنترل فرم نام یکسانی داشته باشند (که در مورد گروهی از دکمه‌های رادیو رایج است)، استفاده از نام مشترک اولین عنصر با آن مقدار را برمی‌گرداند.

## مقدار

یک {{domxref("HTMLCollection")}}.

## مثال‌ها

```html
<form id="my-form">
  <fieldset id="my-fieldset">
    <legend>My fieldset</legend>
    <p>
      <label for="username">Username:</label>
      <input type="text" id="username" name="username" />
    </p>
    <p>
      <label for="password">Password:</label>
      <input type="password" id="password" name="password" />
    </p>
    <p>
      <input type="checkbox" id="remember-me" name="remember-me" />
      <label for="remember-me">Remember me</label>
    </p>
  </fieldset>
</form>
```

```js
const fieldset = document.getElementById("my-fieldset");
console.log(fieldset.elements.length); // 3
console.log(fieldset.elements["remember-me"].value); // "on"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLFieldSetElement")}}
- {{domxref("HTMLFormElement.elements")}}
- {{HTMLElement("fieldset")}}