---
title: "KeyboardEvent: altKey property"
short-title: altKey
slug: Web/API/KeyboardEvent/altKey
page-type: web-api-instance-property
browser-compat: api.KeyboardEvent.altKey
---

{{APIRef("UI Events")}}

ویژگی فقط‑خواندنی **`KeyboardEvent.altKey`** یک مقدار بولی (boolean) است که نشان می‌دهد آیا کلید <kbd>alt</kbd> (در macOS کلید <kbd>Option</kbd> یا <kbd>⌥</kbd>) در زمان وقوع رویداد فشرده شده بود (`true`) یا خیر (`false`).

## مقدار

یک مقدار بولی.

## مثال‌ها

```html
<p>
  Press any character key, with or without holding down the ALT key.<br />
  You can also use the SHIFT key together with the ALT key.
</p>
<pre id="output"></pre>
```

```js
const output = document.getElementById("output");

function showChar(e) {
  output.textContent = `Key KeyDown: "${e.key}"
ALT key KeyDown: ${e.altKey}
`;
}

document.addEventListener("keydown", showChar);
```

{{EmbedLiveSample("examples", "", "400")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{ domxref("KeyboardEvent") }}