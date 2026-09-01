---
title: "DocumentFragment: getElementById() method"
---

---
title: "DocumentFragment: getElementById() method"
short-title: getElementById()
slug: Web/API/DocumentFragment/getElementById
page-type: web-api-instance-method
browser-compat: api.DocumentFragment.getElementById
---

{{ ApiRef("DOM") }}

متد **`getElementById()`** از {{domxref("DocumentFragment")}} یک شیء {{domxref("Element")}} برمی‌گرداند که نشان‌دهندهٔ عنصری است که ویژگی {{domxref("Element.id", "id")}} آن با رشتهٔ مشخص‌شده مطابقت دارد. از آنجا که شناسه‌های عناصر در صورت تعیین باید یکتا باشند، این شناسه‌ها راهی مفید برای دسترسی سریع به یک عنصر خاص فراهم می‌کنند.

اگر نیاز به دسترسی به عنصری دارید که شناسه ندارد، می‌توانید از {{domxref("Document.querySelector", "querySelector()")}} برای یافتن عنصر با استفاده از هر {{Glossary("CSS selector", "selector")}} استفاده کنید.

> [!NOTE]
> شناسه‌ها باید درون یک قطعه‌سند یکتا باشند. اگر دو یا چند عنصر در یک قطعه‌سند دارای شناسهٔ یکسان باشند، این متد اولین عنصر یافت‌شده را برمی‌گرداند.

## Syntax

```js-nolint
getElementById(id)
```

> [!NOTE]
> بزرگ و کوچک بودن حروف `"Id"` در نام این متد _باید_ برای کار کردن کد درست باشد؛ `getElementByID()` _معتبر نیست_ و کار نخواهد کرد، هرچند که ممکن است طبیعی به نظر برسد.

### Parameters

- `id`
  - : شناسهٔ عنصر موردنظر برای مکان‌یابی. این شناسه یک رشتهٔ حساس به بزرگی و کوچکی حروف است که درون قطعه‌سند یکتاست: فقط یک عنصر باید دارای هر شناسهٔ داده‌شده باشد.

### Return value

یک شیء {{domxref("Element")}} که عنصر DOM منطبق با شناسهٔ مشخص‌شده را توصیف می‌کند، یا اگر عنصر منطبقی در قطعه‌سند یافت نشود، `null` برمی‌گرداند.

## Examples

### Extend a list of elements

در این مثال، سند شامل یک فهرست با یک آیتم به نام `Cherry` است. ما همچنین یک قطعه‌سند حاوی چهار آیتم دیگر، یعنی `Apple`، `Orange`، `Banana` و `Melon`، می‌سازیم.

سپس نتیجهٔ استفاده از `getElementById()` را برای جستجوی `Apple` و `Cherry` در سند و در قطعه‌سند ثبت می‌کنیم. در این مرحله، `Cherry` فقط در سند دیده می‌شود، در حالی که `Apple` فقط در قطعه‌سند وجود دارد.

اگر روی دکمهٔ «Add fragment to document» کلیک کنید، قطعه‌سند را به فهرست داخل سند اضافه می‌کنیم و دوباره نتیجهٔ جستجوی `Apple` و `Cherry` را در سند و قطعه‌سند ثبت می‌کنیم. این بار، هر دو `Apple` و `Cherry` در سند دیده می‌شوند و هیچ‌کدام در قطعه‌سند نیستند.

دلیل این است که افزودن یک قطعه‌سند به سند، گره‌های آن را به DOM منتقل می‌کند و یک `DocumentFragment` خالی بر جای می‌گذارد.

#### HTML

```html
<button id="add">Add fragment to document</button>
<button id="reset">Reset example</button> <br />
List content:
<ul>
  <li id="Cherry">Cherry</li>
</ul>
Fragment content:
<ul id="fragment"></ul>
Current status:
<pre id="log"></pre>
```

```css hidden
button {
  margin-bottom: 10px;
}
```

#### JavaScript

```js
// Create the document fragment with its initial content
const fragment = new DocumentFragment();
["Apple", "Orange", "Banana", "Melon"].forEach((fruit) => {
  const li = document.createElement("li");
  li.textContent = fruit;
  li.id = fruit;
  fragment.append(li);
});

// When the button is clicked, add the fragment to the list
document.getElementById("add").addEventListener("click", () => {
  document.querySelector("ul").append(fragment);
  displayStatus();
});

// Log the results of both getElementById()
function displayStatus() {
  const log = document.getElementById("log");
  log.textContent = "";
  ["Apple", "Cherry"].forEach((id) => {
    log.textContent += `document.getElementById("${id}") ${
      document.getElementById(id) ? "Yes" : "No"
    }\n`;
    log.textContent += `fragment.getElementById("${id}") ${
      fragment.getElementById(id) ? "Yes" : "No"
    }\n`;
  });

  // Empty the fragment viewer and fill it with the current content
  const fragmentViewer = document.getElementById("fragment");
  while (fragmentViewer.hasChildNodes()) {
    fragmentViewer.removeChild(fragmentViewer.lastChild);
  }
  for (const entry of fragment.children) {
    fragmentViewer.appendChild(entry.cloneNode(true));
  }
}

// Log the initial state
displayStatus();

// Hook the reset button
document.getElementById("reset").addEventListener("click", () => {
  document.location.reload();
});
```

#### Result

{{EmbedLiveSample('Examples', '100%', '410px')}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Document.getElementById()")}}