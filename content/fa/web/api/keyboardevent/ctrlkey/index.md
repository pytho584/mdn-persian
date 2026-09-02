---
title: "KeyboardEvent: ctrlKey property"
short-title: ctrlKey
slug: Web/API/KeyboardEvent/ctrlKey
page-type: web-api-instance-property
browser-compat: api.KeyboardEvent.ctrlKey
---

{{APIRef("UI Events")}}

ویژگی فقطخواندنی **`KeyboardEvent.ctrlKey`** یک مقدار بولی برمی‌گرداند که نشان می‌دهد آیا کلید <kbd>control</kbd> هنگام وقوع رویداد فشرده شده بود (`true`) یا نه (`false`).

## مقدار

یک مقدار بولی.

## مثال‌ها

```html
<p>
  Press any character key, with or without holding down the CTRL key.<br />
  You can also use the SHIFT key together with the CTRL key.
</p>
<pre id="output"></pre>
```

```js
const output = document.getElementById("output");

function showChar(e) {
  output.textContent = `Key KeyDown: "${e.key}"
CTRL key KeyDown: ${e.ctrlKey}
`;
}

document.addEventListener("keydown", showChar);
```

{{EmbedLiveSample("examples", "", "400")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{ domxref("KeyboardEvent") }}