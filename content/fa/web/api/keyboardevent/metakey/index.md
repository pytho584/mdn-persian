---
title: "KeyboardEvent: metaKey property"
short-title: metaKey
slug: Web/API/KeyboardEvent/metaKey
page-type: web-api-instance-property
browser-compat: api.KeyboardEvent.metaKey
---

{{APIRef("UI Events")}}

ویژگی فقط‌خواندنی **`KeyboardEvent.metaKey`** یک مقدار بولی برمی‌گرداند که نشان می‌دهد آیا کلید <kbd>Meta</kbd> هنگام رخداد رویداد فشرده شده بود (`true`) یا نه (`false`). برخی سیستم‌عامل‌ها ممکن است این کلید را رهگیری کنند، به‌گونه‌ای که هرگز شناسایی نشود.

> [!NOTE]
> در صفحه‌کلیدهای مکینتاش، این کلید <kbd>⌘ Command</kbd> است.

> [!NOTE]
> قبل از Firefox 118، کلید <kbd>⊞ Windows</kbd> به‌جای کلید «Meta» به‌عنوان کلید «OS» مدیریت می‌شد. هنگام فشردن کلید <kbd>⊞ Windows</kbd>، مقدار `KeyboardEvent.metaKey` برابر `false` بود.

## Value

یک مقدار بولی.

## Examples

```html
<button>Click me with the meta key</button>

<p id="output"></p>
```

```js
document.querySelector("button").addEventListener("click", (e) => {
  document.querySelector("#output").textContent =
    `metaKey pressed? ${e.metaKey}`;
});
```

### Result

{{ EmbedLiveSample('Examples', 400, 90) }}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{ domxref("KeyboardEvent") }}
