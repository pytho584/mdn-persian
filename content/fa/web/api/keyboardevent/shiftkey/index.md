---
title: "KeyboardEvent: shiftKey property"
short-title: shiftKey
slug: Web/API/KeyboardEvent/shiftKey
page-type: web-api-instance-property
browser-compat: api.KeyboardEvent.shiftKey
---

{{APIRef("UI Events")}}

ویژگی فقط‌خواندنی **`KeyboardEvent.shiftKey`** یک مقدار بولی است که نشان می‌دهد آیا کلید <kbd>shift</kbd> هنگام رخ‌دادن رویداد فشرده شده است (`true`) یا نه (`false`).

فشردن کلید shift ممکن است مقدار {{domxref("KeyboardEvent/key", "key")}} رویداد را نیز تغییر دهد. برای مثال، فشردن <kbd>B</kbd> مقدار `key: "b"` را تولید می‌کند، در حالی که فشردن هم‌زمان <kbd>Shift</kbd> مقدار `key: "B"` را تولید می‌کند.

## مقدار

یک مقدار بولی.

## مثال‌ها

```html
<p>
  Press any character key, with or without holding down the SHIFT key.<br />
  You can also use the SHIFT key together with the ALT key.
</p>
<pre id="output"></pre>
```

```js
const output = document.getElementById("output");

function showChar(e) {
  output.textContent = `Key KeyDown: "${e.key}"
SHIFT key KeyDown: ${e.shiftKey}
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