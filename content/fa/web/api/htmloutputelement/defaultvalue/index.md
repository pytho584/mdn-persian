---
title: "HTMLOutputElement: defaultValue property"
short-title: defaultValue
slug: Web/API/HTMLOutputElement/defaultValue
page-type: web-api-instance-property
browser-compat: api.HTMLOutputElement.defaultValue
---

{{ APIRef("HTML DOM") }}

ویژگی **`defaultValue`** در رابط {{DOMxRef("HTMLOutputElement")}}، محتوای متنی پیش‌فرض این عنصر {{htmlelement("output")}} را نشان می‌دهد. خواندن و نوشتن این مقدار معادل خواندن و نوشتن {{domxref("Node.textContent", "textContent")}} روی همان عنصر {{htmlelement("output")}} است.

## مقدار

یک رشته (string).

## مثال‌ها

در مثال زیر، `defaultValue` همچنان مقداری را برمی‌گرداند که در ابتدا در HTML نوشته شده است. تغییرات {{domxref("HTMLOutputElement.value", "value")}} تأثیری بر `defaultValue` یا `textContent` آن در DOM ندارد.

```html
<fieldset>
  <legend>Add two numbers</legend>
  <p>
    <input type="number" id="operand1" value="5" aria-label="First number" />
    +
    <input type="number" id="operand2" value="7" aria-label="Second number" />
    =
    <output
      id="result"
      for="operand1 operand2"
      aria-live="polite"
      aria-controls="output"
      >12</output
    >
  </p>
</fieldset>
<pre id="logs" aria-live="polite"></pre>
```

```js
const logs = document.getElementById("logs");
const operand1 = document.getElementById("operand1");
const operand2 = document.getElementById("operand2");
const result = document.getElementById("result");

function updateResult() {
  result.value = operand1.valueAsNumber + operand2.valueAsNumber;
  logs.innerText = `result.defaultValue: ${result.defaultValue}\nresult.value: ${result.value}`;
}

operand1.addEventListener("input", updateResult);
operand2.addEventListener("input", updateResult);
updateResult();
```

{{EmbedLiveSample("examples", "", "150")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("output")}}
- {{DOMXref("HTMLOutputElement.value")}}