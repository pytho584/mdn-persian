---
title: "Document: createTextNode() method"
short-title: createTextNode()
slug: Web/API/Document/createTextNode
page-type: web-api-instance-method
browser-compat: api.Document.createTextNode
---

{{APIRef("DOM")}}

یک گره جدید از نوع {{domxref("Text")}} ایجاد می‌کند. از این متد می‌توان برای escape کردن نویسه‌های HTML استفاده کرد.

## دستور نحوی (Syntax)

```js-nolint
createTextNode(data)
```

### پارامترها

- `data`
  - : رشته‌ای شامل داده‌ای که قرار است در گره متنی قرار گیرد.

### مقدار بازگشتی

یک گره از نوع {{domxref("Text")}}.

## مثال‌ها

```html
<button>YES!</button>
<button>NO!</button>
<button>WE CAN!</button>

<hr />

<p id="p1">First line of paragraph.</p>
```

```js
function addTextNode(text) {
  const newText = document.createTextNode(text);
  const p1 = document.getElementById("p1");

  p1.appendChild(newText);
}

document.querySelectorAll("button").forEach((button) => {
  button.addEventListener("click", (event) => {
    addTextNode(`${event.target.textContent} `);
  });
});
```

{{EmbedLiveSample('Examples')}}

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}