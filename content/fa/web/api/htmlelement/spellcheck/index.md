---
title: "HTMLElement: spellcheck property"
short-title: spellcheck
slug: Web/API/HTMLElement/spellcheck
page-type: web-api-instance-property
browser-compat: api.HTMLElement.spellcheck
---

{{APIRef("HTML DOM")}}

ویژگی **`spellcheck`** در رابط {{domxref("HTMLElement")}} یک مقدار بولی است که نشانهٔ [بررسی املا](/en-US/docs/Web/HTML/Reference/Global_attributes/spellcheck) را کنترل می‌کند. این ویژگی روی همهٔ عناصر HTML در دسترس است، هرچند روی همهٔ آن‌ها تأثیر ندارد.

این ویژگی منعکس‌کنندهٔ مقدار صفت سراسری HTML [`spellcheck`](/en-US/docs/Web/HTML/Reference/Global_attributes/spellcheck) است.

## مقدار

یک مقدار بولی: اگر املا و دستور زبان محتوای متنی عنصر قابل بررسی باشد، `true` و در غیر این صورت `false` خواهد بود.

## مثال‌ها

مثال زیر نشان می‌دهد که چگونه می‌توان نشانهٔ [بررسی املا](/en-US/docs/Web/HTML/Reference/Global_attributes/spellcheck) را از طریق اسکریپت کنترل کرد:

```html
<div>
  <span id="sc-label">The spelling and grammar may be checked: </span>
  <span id="sc-element" contenteditable="true" spellcheck="true">test</span>
</div>
<input id="sc-controller" type="checkbox" checked />Enable spelling and grammar
check
```

```js
const label = document.getElementById("sc-label");
const element = document.getElementById("sc-element");
const controller = document.getElementById("sc-controller");

controller.addEventListener("change", (e) => {
  if (controller.checked) {
    element.spellcheck = true;
    label.innerText = "The spelling and grammar may be checked: ";
  } else {
    element.spellcheck = false;
    label.innerText = "The spelling and grammar may not be checked: ";
  }
});
```

{{EmbedLiveSample('Examples', 600, 200)}}

توجه داشته باشید که باید تنظیمات مرورگر را برای بررسی املا و دستور زبان فعال کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [`spellcheck`](/en-US/docs/Web/HTML/Reference/Global_attributes/spellcheck) صفت سراسری HTML
