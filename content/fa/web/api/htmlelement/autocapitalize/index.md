```
---
title: "HTMLElement: autocapitalize property"
short-title: autocapitalize
slug: Web/API/HTMLElement/autocapitalize
page-type: web-api-instance-property
browser-compat: api.HTMLElement.autocapitalize
---

{{APIRef("HTML DOM")}}

**`autocapitalize`** — ویژگی From the {{domxref("HTMLElement")}} interface، رفتار حروف بزرگ کردن ورودی کاربر را نشان میدهد. این ویژگی روی همهٔ تگهای HTML در دسترس است، اما روی همهٔ آنها تأثیر نمیگذارد؛ تگهای متأثر عبارتند از:

- عناصر {{htmlelement("input")}} و {{htmlelement("textarea")}}.
- هر عنصری که ویژگی [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable) روی آن تنظیم شده باشد.

`autocapitalize` وقتی کاربر با صفحهکلید فیزیکی تایپ میکند، هیچ تأثیری ندارد؛ بلکه بر رفتار سایر روشهای ورودی مانند صفحهکلید مجازی در دستگاههای همراه و ورودی صوتی تأثیر میگذارد. این قابلیت میتواند با بزرگ کردن خودکار حرف اول هر جمله، ورود داده را سریعتر و آسانتر کند.

این ویژگی، مقدار ویژگی سراسری HTML [`autocapitalize`](/en-US/docs/Web/HTML/Reference/Global_attributes/autocapitalize) را بازتاب میدهد.

## مقدار

یک رشته که رفتار بزرگ کردن حروف را برای ورودی کاربر در آن عنصر نشان میدهد. مقادیر معتبر به این شرح است:

- `none` یا `off`
  - : هیچ بزرگنویسی خودکاری اعمال نشود؛ یعنی همهٔ حروف به صورت پیشفرض کوچک باشند.
- `sentences` یا `on`
  - : حرف اول هر جمله به صورت پیشفرض بزرگ باشد؛ بقیهٔ حروف کوچک بمانند.
- `words`
  - : حرف اول هر کلمه به صورت پیشفرض بزرگ باشد؛ بقیهٔ حروف کوچک بمانند.
- `characters`
  - : همهٔ حروف به صورت پیشفرض بزرگ باشند.

## مثالها

مثال زیر نشان میدهد که چگونه میتوان رفتار بزرگنویسی ورودی کاربر را با اسکریپت کنترل کرد:

```html
<div>Current capitalization behavior is: <span id="ac-label"></span></div>
<div id="ac-element" contenteditable="true" autocapitalize="default">
  input here
</div>
<select id="ac-controller" type="checkbox" checked>
  <option value="default">default</option>
  <option value="none">none</option>
  <option value="sentences">sentences</option>
  <option value="words">words</option>
  <option value="characters">characters</option></select
>Select the capitalization behavior
```

```js
const label = document.getElementById("ac-label");
const element = document.getElementById("ac-element");
const controller = document.getElementById("ac-controller");

controller.addEventListener("input", (e) => {
  const behavior = e.target.value;
  label.textContent = behavior;
  element.autocapitalize = behavior;
});
```

{{EmbedLiveSample('Examples', 600, 200)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی سراسری HTML [`autocapitalize`](/en-US/docs/Web/HTML/Reference/Global_attributes/autocapitalize)
```