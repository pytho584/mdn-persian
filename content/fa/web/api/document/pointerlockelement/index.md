---
title: "Document: pointerLockElement property"
---

---
title: "Document: pointerLockElement property"
short-title: pointerLockElement
slug: Web/API/Document/pointerLockElement
page-type: web-api-instance-property
browser-compat: api.Document.pointerLockElement
---

{{APIRef("Pointer Lock API")}}

ویژگی فقط‌خواندنی **`pointerLockElement`** در رابط {{domxref("Document")}}، عنصری را برمی‌گرداند که هنگام قفل بودن اشاره‌گر به‌عنوان هدف رویدادهای ماوس تعیین شده است. اگر قفل در حالت انتظار (pending) باشد، اشاره‌گر قفل نباشد، یا هدف در سند دیگری قرار داشته باشد، مقدار آن `null` است.

## مقدار

یک {{domxref("Element")}} یا `null`.

## مثال‌ها

### بررسی وضعیت قفل اشاره‌گر

این مثال شامل یک عنصر {{htmlelement("div")}} است که درون خود یک {{htmlelement("button")}} دارد. با کلیک روی دکمه، قفل اشاره‌گر برای `<div>` درخواست می‌شود.

این مثال همچنین به رویداد {{domxref("Document/pointerlockchange_event", "pointerlockchange")}} گوش می‌دهد. وقتی این رویداد رخ دهد، کنترل‌کنندهٔ رویداد، اگر عنصری در سند قفل اشاره‌گر را در اختیار داشته باشد، دکمهٔ «Lock» را غیرفعال می‌کند و در غیر این صورت دکمه را فعال می‌کند.

نتیجهٔ این کار این است که اگر روی دکمهٔ «Lock» کلیک کنید، اشاره‌گر قفل می‌شود و دکمه غیرفعال می‌گردد؛ سپس اگر از حالت قفل اشاره‌گر خارج شوید (مثلاً با فشردن کلید <kbd>Escape</kbd>)، دکمه دوباره فعال می‌شود.

#### HTML

```html
<div id="container">
  <button id="lock">Lock</button>
</div>
```

#### CSS

```css
div {
  height: 100px;
  width: 200px;
  border: 2px solid blue;
}
```

#### JavaScript

```js
const lock = document.querySelector("#lock");
const container = document.querySelector("#container");

lock.addEventListener("click", () => {
  container.requestPointerLock();
});

document.addEventListener("pointerlockchange", () => {
  const locked = document.pointerLockElement;
  lock.disabled = Boolean(locked);
});
```

#### نتیجه

{{EmbedLiveSample("Checking pointer lock status")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{ domxref("Document.exitPointerLock()") }}
- {{ domxref("Element.requestPointerLock()") }}
- [Pointer Lock](/en-US/docs/Web/API/Pointer_Lock_API)
